# VCoinX

VCoinX - модификация [майнера от xTCry](https://github.com/xTCry/VCoin). Если хочется поддержать автора оригинального майнера - не используйте VCoinX.


![](https://pp.userapi.com/c855028/v855028357/1734f/9kFW8iHOxHc.jpg)


[![node version](https://img.shields.io/badge/node->%3D8.0-blue.svg?style=flat-square)](https://nodejs.org/)
[![node version](https://img.shields.io/badge/VCoin-1.3.9-purple.svg?style=flat-square)](https://github.com/xTCry/VCoin)
[![vcoin version](https://img.shields.io/badge/VCoinX-1.3.9-purple.svg?style=flat-square)](https://github.com/slmatthew/VCoinX/)

***

[Список команд в приложении](#команды)

## Для начала
> **[Node.js](https://nodejs.org/) 8.0.0 или новее**

Установить зависимости
### NPM
```shell
npm i
```

## Запуск

### Использование аргументов

![](https://pp.userapi.com/c847020/v847020485/1d72be/ktfWqwnMjEY.jpg)

* `-tforce`         - использовать токен принудительно (если в `.config.js` задана ссылка)
* `-u [URL]`        - задает ссылку
* `-t [TOKEN]`      - задает токен
* `-to [ID]`        - задает ID страницы для автоперевода `score`
* `-ti [seconds]`   - задает интервал автоперевода в секундах `[по умолчанию 3600 секунд (1 час)]`
* `-tsum [sum]`     - сколько `score` переводить (знаки до запятой)
* `-autobuy`        - автопокупка ускорений
* `-autobuyItem`    - какое покупать [ускорение](#названия-ускорений)
* `-smartbuy`       - умная покупка ускорений


Запуск поизводится из каталога приложения

Обычный запуск (если есть файл `.config.js`)
```shell
node index.js
```

Запуск через [токен](#получение-токена)
```shell
node index.js -t AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
```

Запуск через [токен](#получение-токена) и автоперевод каждые `7200` секунды (2 часа) на аккаунт `1`
```shell
node index.js -t AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -to 1 -ti 7200 
```

Запуск через [токен](#получение-токена) и автопокупка
```shell
node index.js -t AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -autobuy
```

Запуск через [токен](#получение-токена) и умная покупка
```shell
node index.js -t AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -smartbuy
```

Запуск через ссылку
```shell
node index.js -u https://coin.vkforms.ru?vk_access_token_settings=friends\&vk_app_id=6915965\&vk_...
```
> Linux: Надо обратить внимание, что перед каждым символом `&` должен быть обратный слеш (`\&`)

> Windows: ссылку указать в кавычках 


## Конфигурация из файла `.config.js`

> Если используются только аргументы при запуске, то файл можно не создавать.


| Параметр | Описание                             |
|----------|--------------------------------------|
| VK_TOKEN | [Поулчить токен](#получение-токена)  |
| DONEURL  | Ссылка на приложение                 |

Если указать только ```VK_TOKEN```, то `DONEURL` можно не указывать.

Конфиг с токеном:
```js
module.exports = {
  VK_TOKEN: "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
};
```

Конфиг с ссылкой:
```js
module.exports = {
  DONEURL: "https://coin.vkforms.ru?vk_access_token_settings=..."
};
```

### Получение токена

[Разрешить доступ, например, этому приложению](https://vk.cc/9eSo1E) и скопировать полученный токен из адрессной строки (85 символов, между `#access_token=` и `&expires_in`) 

***


## Команды

- `help` - помощь 
- `stop` - остановить майнер 
- `run` - запустить майнер 
- `tran` - перевести коины
- `price` - вывести текущие цены на ускорения 
- `buy` - покупка ускорения
- `autobuy` - вкл\выкл автопокупку ускорений
- `autoBuyItem` - выбрать какое ускорение покупать
- `smartbuy` - вкл\выкл умную покупку ускорений
- `debug` - посмотреть служебные и заданные параметры
- `color` - вкл/выкл режима цветной консоли
- `info` - показать место в ТОПе и кол-во коинов

## Названия ускорений
- `cursor` - курсор
- `cpu` - видеокарта
- `cpu_stack` - стойка видеокарт
- `computer` - суперкомпьютер
- `server_vk` - сервер ВКонтакте
- `quantum_pc` - квантовый компьютер
- `datacenter` - датацентр
- `bonus` - только один раз

## Что такое SmartBuy

### SmartBuy
Умная покупка рассчитывает для каждого ускорителя цену для скорости 1 коин в секунду и покупает самый дешевый ускоритель.
Умная покупка не может работать в паре с автопокупкой!


## З.Ы.
> Я не имею ничего против автора [оригинального майнера](https://github.com/xTCry/VCoin). Просто решил вырезать донат :)

> Если надо зайти в сервис, но выкидывает, то можно использовать команду `stop`, а для возобновления `run`

> При lineQuestion вывод лога для удобства приостанавливается
