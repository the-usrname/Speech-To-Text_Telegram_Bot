# Speech-to-Text Телеграмм Бот


## 🌟ФИШКИ🌟

- Вы можете использовать множество токенов OpenAI для экономии😉.
- Удобное управление токенами OpenAI даже в Telegram🤖
- Автоматическое удаление токенов с нулевым балансом💡
- Возможность обновления бота до актуальной версии нажатием кнопки, а также откат на предыдущие версии👾
- Администрирование пользователей👮‍♂️
- Поддержка не только голосовых, но и видеосообщений🎥
- Возможность использования в каналах и группах (разрешение на использование для всех состоящих в группе пользователей)👥
- Логи (даже внутри Telegram и с помощью отдельного бота)📝
- Вебхуки для получения сообщений 🌐
- Подробная инструкция по установке😁


## 👑Команды для Админов👑

- /restart - перезапуск бота.
- /gitupdate - обновляет бота до последней версии.
- /gitback - возвращает версию на n версий назад от последней.
- /log - отправляет файл с логами.
- /cleanlog - очищает файл с логами.
- /changelogbot - добавляет или изменяет ключ для бота с логами.
- /rlogbot - удаляет бота с логами.
- /ping - проверка доступности бота.
- /users - отправляет список пользователей.
- /addusers - добавляет пользователей.
- /rusers - удаляет пользователей.
- /groups - возвращает группы в которых бот работает для всех.
- /addgroups - добавляет группы в которых бот работает для всех.
- /rgroups - удаляет группы в которых бот работает для всех.
- /admins - отправляет список админов.
- /addadmins - добавляет админов.
- /radmins - удаляет админов.
- /tokens - отправляет количество токенов.
- /printtokens - отправляет список токенов.
- /addtokens - добавляет токены.
- /rtokens - удаляет токены.


_Добавив 1 в список групп, пользователей или админов, вы делаете бота общедоступным
(добавив в список с админами, все пользователи получают права администраторов)._


## 📚Инструкция📚

**Это руководство поможет вам настроить и использовать Speech-to-Text Телеграмм Бот на основе OpenAI Whisper.**

1. Склонируйте репозиторий с ботом на свой компьютер.
2. Создайте файл `config.json` в директории с ботом и скопируйте в него следующий шаблон:
```json
{
  "BOT_TOKEN": "YOUR_BOT_TOKEN",
  "LOG_BOT_TOKEN": "YOUR_LOG_BOT_TOKEN",
  "ALLOWED_IDS": [],
  "OWNERS_IDS": [],
  "ALLOWED_GROUPS_IDS": []
  "WEBHOOK": false,
  "WEBHOOK_HOST": "your.domain.or.ip.adress",
  "WEBAPP_HOST": "0.0.0.0",
  "WEBAPP_PORT": 8443,
  "UPDATESPENDING": true,
  "MAXCONNECTIONS": 40,
  "OPENAI_TOKENS": [
    "YOUR_OPENAI_TOKEN_1",
    "YOUR_OPENAI_TOKEN_2",
    "YOUR_OPENAI_TOKEN_3",
    "YOUR_OPENAI_TOKEN_4"
  ],
  "LOG_LEVEL": "INFO"
}
```

3. Получите токен вашего бота от BotFather в Телеграмме и вставьте его в поле `"BOT_TOKEN"` в файле `config.json`.
4. (Получите токен для бота с логами от BotFather в Телеграмме и вставьте его в поле `"LOG_BOT_TOKEN"` в файле `config.json`.)
5. (Укажите в поле `"ALLOWED_IDS"` список ID чатов или групп, в которых бот будет работать.)
6. Укажите в поле `"OWNERS_IDS"` список ID пользователей, которые будут являться администраторами бота.
7. (Укажите в поле `"ALLOWED_GROUPS_IDS"` список id групп, в которых будет разрешено пользоваться ботом для всех участников [работает и для отдельных пользователей, но для них лучше использовать `"ALLOWED_IDS"` так как они не зависят от чата])
8. Укажите `true` или `false` в `"WEBHOOK"` чтобы использовать `вебхуки` или `long polling` для получения сообщений.
9. (Укажите ваш IP или домен в поле `"WEBHOOK_HOST"`)
10. (Напишите, с каких адресов разрешено получать обновления для вебхуков в поле `"WEBAPP_HOST"`. `0.0.0.0` чтобы разрешить получение из любого источника)
11. (`"UPDATESPENDING"` - это параметр, который определяет, должны ли обновления (например, сообщения) оставаться в ожидании, пока их не обработает программа.
    Если `"UPDATESPENDING"` равен `true`, то обновления будут накапливаться, пока не будут обработаны.
    А если равен `false`, то новые обновления будут перезаписывать предыдущие, даже если они ещё не обработаны.)
12. (`MAXCONNECTIONS` - это параметр, который указывает максимальное количество одновременных соединений, которые могут быть установлены с сервером.
    Он контролирует, сколько клиентов или устройств может одновременно соединяться с сервером через вебхук. По умолчанию `40`)
12. В поле `"OPENAI_TOKENS"` добавьте токены OpenAI Whisper для использования Speech-to-Text функционала бота.
13. В параметре `"LOG_LEVEL"` укажите уровень логирования для библиотеки *logging*:
	- **DEBUG**: Самый подробный уровень логирования, используется для отладки. Для тех, кто любит копаться в деталях. 😎
	- **INFO**: Информационные сообщения, которые дают общую информацию о процессе работы программы. Не слишком подробные, но полезные. 😊
	- **WARNING**: Сообщения предупреждения, которые указывают на потенциальные проблемы или неожиданное поведение программы. 🤔
	- **ERROR**: Сообщения об ошибках, которые указывают на серьезные проблемы, но не приводят к остановке программы. Используйте их, чтобы найти и исправить ошибки. 😱
	- **CRITICAL**: Самый высокий уровень логирования, указывает на критические ошибки, которые могут привести к аварийному завершению программы.💣

15. Сохраните файл `config.json`.

*Теперь вы можете использовать ваш Speech-to-Text Телеграмм Бот для записи голосовых или видеосообщений и получения их текстовой расшифровки.*

**Удачи! 😊🤖🎉**

