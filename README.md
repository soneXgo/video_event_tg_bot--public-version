## Зачем нужен бот?
Бот был создан для автоматизации проведения мероприятий в Политехе. Студенты могут легко регистрировать команды на различные мероприятия, а бот — принимать их видеовизитки и загружать на Яндекс диск. Кроме того, для членов жюри также существует функционал данного бота. Они могут оценивать видеовизитки команд, а также узнавать команду-победителя по окончании голосования.
## Использование
### Ссылка на бота
https://t.me/video_event_bot
### Работа с папками и файлами на Яндекс Диске
#### Папка bot_folder
    - хранит шаблоны файлов мероприятия(list_jury.xlsx, rating.xlsx, team_info.xlsx, topics.txt) и файл name_folder_event.txt

Папка bot_folder располагается в файлах на Яндекс Диске. Она не находиться в какой-либо другой папке. 
Для корректной работы бота необходимые данные в файлах “list_jury.xlsx, rating.xlsx, team_info.xlsx, topics.txt” должны быть в обязательном порядке заполнены заранее.
Все названия файлов должны быть в точности такими же, как в шаблоне
#### Файл name_folder_event.txt
    - в файле в первой строке записано название папки(или путь к папке без отступов и пробелов), которая используется для мероприятия в текущий момент
#### Папка templates
    - содержит начальные состояния файлов list_jury.xlsx, rating.xlsx, team_info.xlsx, topics.txt(названия некоторых столбцов).
#### Файл list_jury.xlsx
    - содержит информацию о жюри: в первом столбце находятся ФИО жюри, во втором - их ссылки на профиль telegram. 
    - в начальном состоянии содержит только название столбцов ФИО и Ссылка.
    - для корректной работы бота перед началом его использования файл должен быть заполнен вручную
Пример файла с данными:

![image](https://github.com/soneXgo/video_event_tg_bot--public-version/assets/141906784/19c2f0c5-1f2a-4b77-a171-66cf9e404216)

#### Файл rating.xlsx
- в начальном состоянии содержит названия столбцов Название команды и Критерий.
- для корректной работы бота перед началом его использования должны быть заполнены вручную все названия команд, критерии и имена членов жюри
- имена членов жюри должны быть в таком же порядке, как и в файле list_jury.xlxs
- названия команд должны быть в таком же порядке, как и в файле team_info.xlxs

Пример файла с данными:

![image](https://github.com/soneXgo/video_event_tg_bot--public-version/assets/141906784/fcfeb432-42cf-42d4-b140-81c10e48f8d9)

#### Файл team_info.xlsx
- содержит информацию о зарегистрированных командах
- изначально должны быть заполнены только названия столбцов
Пример файла с данными:

#### Файл topics.txt
- содержит темы видеороликов, на которые команды будут снимать визитки
- файл заполняется организаторами вручную перед началом мероприятия
![image](https://github.com/soneXgo/video_event_tg_bot--public-version/assets/141906784/d90cee5d-524a-4e06-b791-094120215f72)

### Команды для жюри
Если юзернейм пользователя содержится в файле list_jury.txt, ему предоставляется доступ к командам для жюри
#### Поставить оценки
При выборе этой опции бот присылает подряд все видеовизитки участников, а пользователь должен оценить их по четырем критериям по шкале от 1 до 5. Когда будут оценены все видео, бот выгрузит оценки в файл rating.xlxs
#### Получить победителя
При выборе этой опции бот определяет, все ли оценки выставлены, и в таком случае подсчитывает количество баллов каждой команды. Затем бот отправляет сообщение с названием команды победителя. Если победителей несколько, бот отправит названия всех команд с максимальным баллом.

Если не все члены жюри выставили свои баллы, бот отправит сообщение о невозможности определения победителя в данный момент.
### Команды для участников
Если юзернейм пользователя не найден в списке членов жюри, ему предлагаются команды для участников.
#### Зарегистрировать команду
При выборе этой опции начнется регистрация команды. Сначала пользователь должен согласиться с правилами пользования бота, нажав кнопку “Продолжить”, иначе регистрацию придется начать заново.
Если же “Продолжить” нажата, бот будет отправлять сообщения с требуемой информацией, а пользователю нужно будет её предоставить.
После этого бот отправит сообщение с подтверждением сохранения данных. Если нажать “Сохранить”, бот выгрузит данные команды в файл team_info.xlxs, а также проведёт жеребьевку и выберет тему видео для данной команды.
Если же нажать “Начать заново”, регистрация начнется сначала.
#### Загрузить видео
При выборе этой опции пользователь может отправить свою видеовизитку. Когда участник отправит видеоролик, бот загрузит его на диск, а также добавит ссылку на него в файл team_info.xlxs
