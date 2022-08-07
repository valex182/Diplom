## Дипломный проект профессии «ПО Тестировщик»

## Сервис заказа путешествия

### Описание приложения

**Бизнес часть**

Приложение предлагает купить тур с помощью двух способов:

1. Обычная оплата по дебетовой карте.
2. Выдача кредита по данным банковской карты.

С помощью следующих сервисов:

+ сервису платежей (далее - Payment Gate)
+ кредитному сервису (далее - Credit Gate)

Данные карт сохранять не допускается.

**Техническая часть**

Приложение расположено в файле *aqa-shop.jar* и запускается на порту 8080.

В файле *application.properties* приведён ряд типовых настроек:

+ учётные данные и url для подключения к СУБД
+ url-адреса банковских сервисов

**СУБД**

Поддержка двух СУБД:

+ MySQL
+ PostgreSQL

### Ссылки на документы проектной документации:

- [План автоматизации web-сервиса](https://github.com/valex182/Diplom/blob/master/document/Plan.md)
- [Отчет о тестировании](https://github.com/valex182/Diplom/blob/master/document/Report.md)
- [Итог](https://github.com/valex182/Diplom/blob/master/document/Summary.md)


## Инструкция по подключению БД, запуску SUT и авто-тестов

### Предусловия

При выполнении курсовой работы необходимо установить: IntelliJ IDEA, Google Chrome, Docker Desktop.

### 1. Склонировать проект
- репозиторий: https://github.com/valex182/Diplom.git
- команда: `git clone`

### 2. Скачать и запустить в Docker контейнеры
- СУБД: MySQL, PostgreSQL
- команда для запуска контейнеров: `docker-compose up`

### 3. Запустить SUT
- команда для запуска с подключением MySQL: ` java "-Dspring.datasource.url=jdbc:mysql://localhost:3306/app" -jar aqa-shop.jar`
- команда для запуска с подключением PostgreSQL: `java "-Dspring.datasource.url=jdbc:postgresql://localhost:5432/app" -jar aqa-shop.jar`
- приложение запускается по адресу: http://localhost:8080/

### 4. Запустить авто-тесты
- команда для запуска с подключением MySQL: `./gradlew clean test "-Ddb.url=jdbc:mysql://localhost:3306/app"`
- команда для запуска с подключением PostgreSQL: `./gradlew clean test "-Ddb.url=jdbc:postgresql://localhost:5432/app"`

### 5. Сгенерировать отчеты Allure
- команда для генерации: `./gradlew allureServe`
- для завершения работы allureServe выполнить команду: `Control + С`
- 
### После окончания работы:
+ Завершить работу контейнеров командой в консоли: `docker-compose down`
