# PSG-protocol (Platform shooter game protocol)

Протокол обмена сообщениями между клиентом и сервером

Сообщения передаются в формате JSON

## Формат сообщений

### Запрос (Request)

    {
        // Самое действие
        "action": "<action>",

        // Параметры, специфичные для конкретного запроса
        <data>
    }

### Ответ (Response)

    {
        // В случае успешного выполнения команды "<result>" == "ok".
        // Ответы в случаях ошибок описаны отдельно для каждого запроса
        "result": "<result>",

        // Код ошибки
        "error": "<error>"

        // Текстовый комментарий. Может быть произвольным
        "message": "<message>",

        // Данные, специфичные для конкретного действия
        <data>
    }


## Действия

### signup

Параметры:

* login => строковое значение
* password => строковое значение

Коды ошибок:

* userExists (Такой пользователь уже существует)
* badLogin (Некорректный логин)
* badPassword (Некорректный пароль)

### signin

Параметры:

* login => строковое значение
* password => строковое значение

Ответ:

* sid => латинские буквы и цифры, не короче 1 символа

Коды ошибок:

* incorrect (Некорректный логин/пароль)

### signout

Параметры:

* sid => латинские буквы и цифры, не короче 1 символа

Коды ошибок:

* badSid (Некорректный sid)
