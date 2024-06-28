## icloudpd for Umbrel OS

### Основные параметры
- **apple_id**: Ваш Apple ID, используемый для загрузки файлов. Обязательный параметр.
- **user**: Имя пользователя, создаваемого внутри контейнера. По умолчанию: 'user'.
- **user_id**: ID пользователя. По умолчанию: '1000'.
- **group**: Имя группы, создаваемой внутри контейнера. По умолчанию: 'group'.
- **group_id**: ID группы. По умолчанию: '1000'.
- **force_gid**: Разрешает создание группы с уже существующим ID группы.
- **TZ**: Часовой пояс для вычисления временных меток. По умолчанию: 'UTC'.
- **download_path**: Директория для загрузки файлов из iCloud. По умолчанию: "/home/${user}/iCloud".
- **synchronisation_interval**: Интервал между синхронизациями в секундах. Допустимые значения: 21600, 43200, 86400, 129600, 172800, 604800. По умолчанию: 86400.
- **synchronisation_delay**: Задержка первой синхронизации в минутах. По умолчанию: 0. Максимум: 60.
- **notification_days**: Количество дней до истечения срока действия cookie для отправки уведомления. По умолчанию: 7.
- **authentication_type**: Тип аутентификации ('MFA' для двухфакторной аутентификации или 'Web'). По умолчанию: 'MFA'.
- **directory_permissions**: Права доступа к директориям. По умолчанию: 750.
- **file_permissions**: Права доступа к файлам. По умолчанию: 640.
- **folder_structure**: Структура папок для загрузки. По умолчанию: {:%Y/%m/%d}.
- **albums_with_dates**: Создание подкаталогов в альбомах согласно `folder_structure`. По умолчанию: false.
- **libraries_with_dates**: Создание подкаталогов в библиотеках согласно `folder_structure`. По умолчанию: false.
- **skip_check**: Пропустить проверку новых файлов. Рекомендуется для больших библиотек. По умолчанию: false.
- **auto_delete**: Удаление файлов, найденных в папке "Недавно удаленные". По умолчанию: false.
- **delete_after_download**: Перемещение файла в "Недавно удаленные" после успешной загрузки. Несовместимо с `auto_delete`. По умолчанию: false.
- **photo_size**: Размер загружаемого изображения ('original', 'medium', 'thumb'). По умолчанию: original.
- **skip_live_photos**: Пропустить загрузку живых фото. По умолчанию: false.
- **live_photo_size**: Размер живого фото ('original', 'medium', 'thumb'). По умолчанию: original.
- **skip_videos**: Пропустить загрузку видео. По умолчанию: false.
- **recent_only**: Загрузить только указанное количество последних добавленных фото. По умолчанию: все фото.
- **until_found**: Загрузить последние добавленные фото, пока не будут найдены указанные количество ранее загруженных фото. По умолчанию: все фото.
- **photo_album**: Загрузка фото из указанных альбомов (через запятую). Например: `photo_album="album1,album2"`.
- **photo_library**: Загрузка фото из указанных библиотек (через запятую). Например: `photo_library="library1,library2"`.
- **skip_album**: Пропустить указанные альбомы (через запятую). Например: `skip_album="All Photos,Time-lapse"`.
- **skip_library**: Пропустить указанные библиотеки (через запятую). Например: `skip_library="PrimarySync,SharedSync"`.
- **convert_heic_to_jpeg**: Конвертировать загруженные HEIC файлы в JPEG. По умолчанию: false.
- **jpeg_path**: Путь для сохранения JPEG файлов. По умолчанию: "/home/${user}/iCloud".
- **jpeg_quality**: Качество конвертированных JPEG файлов (0-100). По умолчанию: 90.
- **single_pass**: Завершение работы после одного цикла синхронизации. По умолчанию: false.
- **keep_unicode**: Сохранить юникод символы в именах файлов. По умолчанию: false.
- **live_photo_mov_filename_policy**: Политика именования MOV файлов для живых фото ('suffix', 'original'). По умолчанию: suffix.
- **align_raw**: Обработка RAW файлов ('original', 'alternative', 'as-is'). По умолчанию: as-is.
- **file_match_policy**: Политика определения существующих файлов и устранения дубликатов ('name-size-dedup-with-suffix', 'name-id7'). По умолчанию: name-size-dedup-with-suffix.

### Параметры синхронизации с Nextcloud
- **nextcloud_delete**: Удаление файлов с Nextcloud при их удалении локально. Требует включенного `auto_delete`. По умолчанию: false.
- **nextcloud_password**: Пароль для учетной записи Nextcloud.
- **nextcloud_target_dir**: Корневая папка для размещения файлов на Nextcloud.
- **nextcloud_upload**: Загрузка файлов на сервер Nextcloud. По умолчанию: false.
- **nextcloud_url**: URL вашего сервера Nextcloud. Например: `https://my.server.local/`.
- **nextcloud_username**: Имя пользователя учетной записи Nextcloud.

### Параметры Telegram
- **telegram_token**: Токен, полученный от BotFather.
- **telegram_chat_id**: ID чата Telegram для уведомлений.
- **telegram_silent_file_notifications**: Отправка уведомлений о загрузке файлов в беззвучном режиме. По умолчанию: false.
- **telegram_polling**: Включение опроса чатов Telegram. По умолчанию: false.
- **telegram_server**: Сервер Telegram, если Telegram заблокирован в вашей стране.

### Инициализация контейнера
```docker exec -it icloudpd sync-icloud.sh --Initialise```

### Просмотр логов контейнера
```docker logs -f icloudpd```

### Перезапуск контейнера
```docker restart icloudpd```

### Удаление ключей из keyring
```docker exec -it icloudpd sync-icloud.sh --Remove-Keyring```

### Включение отладки
```docker exec -it icloudpd sync-icloud.sh --Enable-Debugging```

### Отключение отладки
```docker exec -it icloudpd sync-icloud.sh --Disable-Debugging```

### Конвертация всех HEIC в JPEG
```docker exec -it icloudpd sync-icloud.sh --Convert-All-HEICs```

### Принудительная конвертация всех HEIC в JPEG с перезаписью
```docker exec -it icloudpd sync-icloud.sh --Force-Convert-All-HEICs```

### Удаление всех JPEG файлов, имеющих соответствующие HEIC
```docker exec -it icloudpd sync-icloud.sh --Remove-All-JPGs```

### Коррекция временных меток JPEG файлов
```docker exec -it icloudpd sync-icloud.sh --Correct-JPEG-Time-Stamps```

### Список доступных альбомов
```docker exec -it icloudpd sync-icloud.sh --List-Albums```

### Список доступных библиотек
```docker exec -it icloudpd sync-icloud.sh --List-Libraries```

###Загрузка всей библиотеки на Nextcloud
```docker exec -it icloudpd sync-icloud.sh --Upload-Library-To-Nextcloud```

### Примеры конфигурации Docker Compose
```yaml
version: '3.7'

services:
  icloudpd:
    image: boredazfcuk/icloudpd
    container_name: icloudpd
    volumes:
      - /home/umbrel/umbrel/data/storage/icloud-config:/config
      - /home/umbrel/umbrel/data/storage/icloud-photos:/icloud
    environment:
      - APPLE_ID=snaizy@gmail.com
      - TZ=Europe/Madrid
      - AUTO_DELETE=true
      - DOWNLOAD_PATH=/icloud
      - DIRECTORY_PERMISSIONS=777
      - FILE_PERMISSIONS=666
      - TELEGRAM_TOKEN=your_telegram_token
      - TELEGRAM_CHAT_ID=your_chat_id
    restart: always

volumes:
  icloudpd_config: