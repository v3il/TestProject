# Test project
Йоу, прийшов час показати свою скілуху і наскільки ти добре закріпив пройдені теми! 

## Завдання 
Полягає в тому, щоб маючи каркас невеликого апчику, повністю реалізувати його логіку. Апчик складається з однієї 
сторінки, на якій виводиться табличка з даними користувачів і парочки контролів, за допомогою яких можна фільтрувати 
і сортувати користувачів в таблиці.

Нічого супер складного, брав лише теми, які ти проходив + будуть покрокові підказки, так що проблем виникати не має.

## Підготовчі дії
Перед початком роботи треба виконати кілька підготовчих дій

### 1. Установка Node.js (виконується 1 раз)
Node.js - це середовище для запуску JS-коду на компі, не використовуючи 
браузер. Активно використовується як на бекенді (пишуться серваки, разні тулзи, апчики тощо), так і на фронтенді - для 
удобної установки бібліотек, зборки статіки для сайта і т.д. Разом з собою тягне NPM (Node Package Manager) - тулзу для простого
менеджменту бібліотек, які використовуються в проекті. 

В нашому випадку я юзаю ноду саме для установки і запуска
деяких тулзів, які зроблять розробку простішою:
   1. Топай сюда - https://nodejs.org/en/download/ (не скам)
   2. Качаєш LTS версію для вінди
   3. Устанавлюєш, все дефолтнінько там, нічо мінять не треба
   4. Після установки провіряєш: откриваєш любий термінал (CMD/VSCode/GIT bash), вводиш `node -v`, ентер (показать версію ноди) i `npm -v`, ентер 
   (показать версію NPM). Якшо все ок, має бути схожий аутпут (версії можуть відрізнятись трохи, це норм) - https://i.imgur.com/RNnC5Ai.png

### 2. Скачування проекту собі на комп (виконується 1 раз)
Для скачування проекту собі на комп будем юзать GIT (в тебе наче вже встановлений). Для впевненості бахни `git --version`
в термінал, має відобразитись версія гіта, встановленого на комп. Я буду юзать гітовський термінал, він краще, чим віндовий:
1. Топай в папку, де в тебе буде лежати проект
2. ПКМ по білій області в папкі
3. Git bash here - https://i.imgur.com/QYueZPL.png
4. Виконай команду `git clone https://github.com/v3il/TestProject.git`. Юзай `Ctrl/Shift + Insert` замість `Ctrl + C/V` або `ПКМ -> Copy/Paste`. 
Результат має бути +- такий - https://i.imgur.com/gxODzW8.png
5. В папкі, де викликав термінал з'явиться папка `TestProject`, залітай туди: `cd TestProject`

### 3. Установка бібліотек (виконується 1 раз)
Серцем будь-якого серйозного JS-проекту є файл `package.json`. Він містить в собі інфо про проект (назву, автор, версію і тд), а також
`dependencies` - список бібліотек, які використовуються в проекті (пусте в цьому проекті, бо я писав все з нуля). 
Поле `devDependencies` схоже на `dependencies`, але сюди включаються бібліотеки, які потрібні для розробки/збірки 
проекту, а не для повноцінної роботи його функціоналу. 

Якшо відкриєш цей файл, побачиш секцію `devDependencies`, де вже прописані кілька бібліотек. 
`Rollup` використовується для упаковки всіх JS файлів в один для удобного його підключення в HTML файл, `eslint` використовується
для лінтінгу скриптів (щоб стиль написання всіх JS файлів був однаковий і підпорядковувався певним правилам).
Всіх їх я заюзав в проекті і зараз треба їх скачать собі локально. Для цього в терміналі виконай `npm install`. Результат
має бути приблизно такий - https://i.imgur.com/glqV2uc.png 

В корні проекта в тебе з'явилась папка `node_modules`, куди скачались всі потрібні бібліотеки і бібліотеки, які юзають ті бібліотеки.
Папки немає в гіті і править ніякі файли в ній не треба, бо
1. Можеш нарушить роботу бібліотек і потім отримати десь неочікувані результати
2. Всі правки будуть затерті при оновленні бібліотеки, наприклад

### 4. Запуск проекту (виконується кожного разу)
В `package.json` також є секція `scripts`, де описані команди, які потрібні для запуску проекту, запуску тестів і тд.

У нас є скрипт, який називається `lint`. Використовується для того, щоб прогнати `eslint` по всіх файлах в проекті і автоматом 
підфіксить проблеми, які в них є. Виконай його **один** раз: `npm run lint` - https://i.imgur.com/zceuocP.png.

Також у нас є скрипт, який називається `dev` і потрібен для запуску проекту. Він запускає бібліотеку `Rollup`, яка збирає всі скрипти 
в папкі `src` в один файлік, який ми підключаємо в хтмл файл. 
Для запуску скрипта виконай `npm run dev`. Цей термінал не закривай поки работаєш над проектом, 
бо там буде висіть процес `Rollup-у` і при змінах в файлах автоматом пересобирать той основний js-файл і примінять зміни на сторінці.
Шоб стопнуть - `Ctrl + C` 

Файл знаходиться за шляхом `build/bundle.js`, редачити його не нада, бо всі зміни будуть затерті ролапом при змінах в скриптах.

Далі просто відкрий `build/index.html` через VSCode в браузері, я юзнув екстеншен `Live Server` (https://i.imgur.com/Q5KgNOJ.png), 
всі зміни в файлах будуть автоматом показуватись в браузері (інколи може залагать і знадобиться оновити сторінку). 

Всьо, можна писать код 🎉

## Реалізація проекту
Йди по вказаному порядку, уважно читай шо треба зробить і все має ізі запрацювати.

### 1. Генерація даних про користувачів
Потрібний файл знаходиться за шляхом `src/services/DataGeneratorService.js`.
Потрібно реалізувати методи класу і згенерувати дані про користувачів, використовуючи ці методи.

`class` - це новий простіший спосіб опису функцій-конструкторів, які ти вже проходив. Познайомишся трохи пізніше, зараз деталі неважливі. \
`export/import` - це штуки, які дозволяють писати модульний JS (типу 1 модуль = 1 клас / 1 функція / 1 константа тощо, тобто, грубо кажучи,
1 ізольована штука, яка робить щось своє). За допомогою цих ключових слів можна використовувати одні модулі в інших. Це робить код
чистішим, ізольованим і немає каші, яка була б тоді, коли ти написав в одному файлі все. Теж пізніше познайомишся.

**Завдання:** 
1. Реалізувати метод `generateUpperCase`. Має повертати 1 рандомну літеру латинського алфавіту в діапазоні [A-Z]
2. Реалізувати метод `generateLowerCase`. Має повертати 1 рандомну літеру латинського алфавіту в діапазоні [a-z]
3. Реалізувати метод `generateDigit`. Має повертати 1 рандомну цифру
4. Реалізувати метод `generateId`. Має повертати рядок з `ID_LENGTH` (константа описана в тому файлі) символів, де кожен символ 
генерується по такій формулі:
   1. Якщо `випадкове число < 0.33`, символ буде результатом виклику метода `generateUpperCase`
   2. Якщо `0.33 < випадкове число < 0.66`, символ буде результатом виклику метода `generateLowerCase`
   3. Якщо `випадкове число > 0.66`, символ буде результатом виклику метода `generateDigit`
5. Реалізувати метод `generateName`. У файл імпортована константа `NAMES`, яка описана в файлі `src/consts/index.js` і
являє собою масив рядків, які є іменами. Метод має повертати рандомне ім'я з цього масиву.
6. Реалізувати метод `generateLastName`. У файл імпортована константа `LAST_NAMES`, яка описана в файлі `src/consts/index.js` і
являє собою масив рядків, які є прізвищами. Метод має повертати рандомне прізвище з цього масиву.
7. Реалізувати метод `generateAvatarId`. Має повертати рандомне число в діапазоні [1-11]
8. Реалізувати метод `generateBirthDate`. Має повертати дату з сьогоднішнім числом і місяцем. Рік має бути вибраний випадково
в діапазоні [1975-2000]
9. Реалізувати метод `generateUsersData`. Має повертати масив, що складається з `USERS_COUNT` (константа описана в тому файлі)
об'єктів. Кожен об'єкт має містити такі поля:
   1. `id` - результат виклику методу `generateId`
   2. `name` - результат виклику методу `generateName`
   3. `lastName` - результат виклику методу `generateLastName`
   4. `avatarId` - результат виклику методу `generateAvatarId`
   5. `birthDate` - результат виклику методу `generateBirthDate`

### 2. Фікс даних
Потрібний файл знаходиться за шляхом `src/services/FixDataService.js`.
Один злобний чєл (я) перехватив твої дані про юзерів і трошки їх поламав. Потрібно реалізувати метод класу і відновити 
дані користувачів.

**Завдання:**

Реалізувати метод `fixData`, який відновить поламані дані. Метод приймає 1 параметр - `brokenUsersJson` - масив об'єктів з 
поламаними даними про користувачів, закодований в форматі **JSON (JSON-рядок)**. Кожен об'єкт в цьому масиві містить такі поля:
   1. `id` - масив з двома елементами, останній з яких містить оригінальний `id`, до якого додали трохи пробілів попереду і позаду
   2. `name` - рядок, в якому оригінальний `name` продублювали 3 рази і склеїли їх за допомогою '__' (2 андерскора)
   3. `lastName` - оригінальний `lastName`, в якому першу літеру зробити маленькою, всі інші - великими
   4. `avatarId` - об'єкт, в якому є поле `value`, значення якого є значенням оригінального `avatarId`, піднесеного в квадрат
   5. `birthDate` - число, в якому мілісекунди з оригінальної `birthDate` поділили на 1000, а потім ще на 2.25
   6. `rand` - просто рандомно згенероване число, це поле ніде не юзається і його треба буде відсіяти
   
Кожне поле треба буде "очистити", якось діставши оригінальне значення поля. Можеш подебажить `brokenUsersJson`, буде більш
понятна його структура. Метод має повернути масив об'єктів з полями `id, name, lastName, avatarId, birthDate` з 
відповідними оригінальними (очищеними) значеннями. Для удобства можеш створювати в класі якісь допоміжні методи по аналогії з
`src/services/DataGeneratorService.js`, якщо є така потреба.

### 3. Створення моделей користувачів
Потрібний файл знаходиться за шляхом `src/services/UsersService.js`. Потрібно створити моделі для користувачів.

**Завдання:**

Твої очищені дані про користувачів попадають в клас, який служить для того, щоб робити з ними різні операції. 
Працювати з простими об'єктами не дуже зручно, оскільки складно розширити його функціонал (додати нові поля, провести якісь
операції над існуючими даними, додати методи тощо). 

Щоб спростити собі життя, перетворимо об'єкти з даними про користувачів в екземпляри класа. Це дозволить легко 
додавати в них нові поля і методи, що знадобиться нам у майбутньому.

Для цього я створив клас `User` і імпортував його в `UsersService`. Конструктор цього класу приймає в себе об'єкт з очищеними даними
про користувача.

Суть задачі полягає в тому, щоб в конструкторі `UsersService` кожен об'єкт з масиву `cleanedUsers` перетворити в екземпляр
класу `User` (`new User(...)`) і масив створених екземплярів присвоїти в поле `users` класу `UsersService`.

В подальшому будемо проводити операції над створеним масивом екземплярів.


### 4. Реалізація класу User
Потрібний файл знаходиться за шляхом `src/models/User.js`. Потрібно імплементувати конструктор класу, додати кілька нових полів
і методів.

**Завдання:**
1. Реалізувати конструктор класу `User`. В конструктор ми прокидуємо об'єкт `userData`, що містить очищені дані про користувача 
(об'єкт має поля `id, name, lastName, avatarId, birthDate`). Використовуючи об'єкт `userData`, потрібно додати поточному користувачу такі поля:
   1. `id` - відповідне поле з об'єкту `userData`
   2. `avatarId` - відповідне поле з об'єкту `userData`
   3. `birthDate` - відповідне поле з об'єкту `userData`
   4. `fullName` - це поле утворюється склейкою імені і прізвища користувача, розділених пробілом
   5. `postsCount` - це поле утворюється піднесенням значення поля `avatarId` в куб
   
2. Додати класу `User` новий метод `getData`. Метод має повертати об'єкт з такими полями:
   1. `id` - відповідне поле поточного користувача
   2. `fullName` - відповідне поле поточного користувача
   3. `postsCount` - відповідне поле поточного користувача
   4. `birthDate` - відповідне поле поточного користувача, відформатоване у формат dd/mm/yyyy, де dd - день, mm - місяць, yyyy - рік.
   Якщо місяць і день менше 10, до значення має спереду доклеюватись 0 (07, наприклад) 
   5. `avatarSrc` - рядок у форматі `https://ik.imagekit.io/igo1qzk1oe2z/avatars/ХХХ.webp`, де ХХХ - значення поля `avatarId` поточного користувача

### 5. Відображення даних користувача у таблиці
Потрібний файл знаходиться за шляхом `src/templates/USER_LIST_ITEM_TEMPLATE.js`. Час трохи згадати HTML (не забув ще, надіюсь?).

**Завдання:** 

Я написав простенький шаблонізатор, який дозволяє легко перетворювати рядки у спеціальному форматі, скармлюючи їм об'єкт з даними
у HTML розмітку. Приклад - шаблон `<div id="id1" class="{{ cls }}">{{ text }}</div>` (пробіли в {{ ... }} **обов'язкові!**) і об'єкт з даними `{ class: 'test', text: 'TEXT' }`
перетвориться в `<div id="id1" class="test">TEXT</div>`. Думаю, який принцип дії, понятний.

Приклад готового шаблону також можна поглянути в файлі `src/templates/SORT_BY_SELECT_OPTION_TEMPLATE.js`.

У вказаному файлі треба написать розмітку для відображення даних про користувача. Я за тебе у кожного юзера викличу метод `getData`, 
який ти додав у попередньому завданні і результат скормлю твоєму шаблону з файлу `src/templates/USER_LIST_ITEM_TEMPLATE.js`, а потім 
отриману HTML розмітку додам до таблиці. Так в нас в таблиці відобразяться дані про всіх користувачів по порядку.

Структура розмітки має бути така:
1. Кореневий елемент - рядок таблиці, в якому знаходиться 5 колонок
2. Перша колонка містить в собі картинку, атрибут `src` якого дорівнює полю `avatarSrc` з методу `getData`. Також **_картинка_** має клас `users-table__image`
3. В другій колонці виведи поле `id`
4. В третій колонці виведи `fullName`
5. В четвертій колонці виведи `birthDate`
5. В п'ятій колонці виведи `postsCount`

В результаті рядок таблиці має виглядати приблизно так - https://i.imgur.com/R9CsZU3.png 

### 6. Відображення списка доступних сортувань
Потрібний файл знаходиться за шляхом `src/views/App.js`.

**Завдання:**
На сторінці є випадаючий список доступних сортувань - https://i.imgur.com/rSBxiNa.png, зараз він пустий. Наша задача заповнити його
доступними сортуваннями.
 
У файл імпортована константа `SORT_BY_OPTIONS`, 
яка описана в файлі `src/consts/index.js` і являє собою масивом доступних сортувань. Єдине але - ці значення трохи поламані:
1. Латинська А перетворена в @
2. Латинська E перетворена в 3
3. Латинська S перетворена в $
4. Латинська O перетворена в 0 (нуль)
5. Латинська I перетворена в 1

У вказаному файлі треба реалізувати метод `getSortByOptionsData`. Метод має вернути масив з 6-ти об'єктів. \
Для кожного очищеного значення треба повернути по 2 (два) об'єкта, кожен з яких мають такі поля:
1. `sortBy` - очищене значення, приведене в lowercase, якщо є пробіл, він замінюється на _
2. `order` - має статичне значення: для першого об'єкту в парі - значення `asc`, для другого - `desc`
3. `label` - Очищене значення, приведене в lowercase + першу літеру зробити uppercase

Далі отримані об'єкти пропустяться через шаблон з файлу `src/templates/SORT_BY_SELECT_OPTION_TEMPLATE.js` і відмальовуються 
в селекті. В результаті в селекті мають відображатись такі пункти - https://i.imgur.com/zLKsLd1.png, https://i.imgur.com/rqIGIla.png
