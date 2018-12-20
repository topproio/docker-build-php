# docker-build-php

[![npm](https://img.shields.io/badge/nginx-1.15-green.svg)]()
[![npm](https://img.shields.io/badge/PHP-7.2-orange.svg)]()
[![npm](https://img.shields.io/badge/redis-latest-red.svg)]()
[![npm](https://img.shields.io/badge/mysql-5.7-yellowgreen.svg)]()
[![npm](https://img.shields.io/badge/License-MIT-blue.svg)]()

Let us use docker to quickly build a PHP development environment!

## Preparations

1. Make sure your host env has Docker installed.
2. Port 80, 3306, 6379 is idle.
3. Specify the PHP project directory.

## Steps

In the root directory.

```
cp .env.example .env
```

And set the MySQL database name, pwd, redis pwd, and the directory where the files are stored.
User directory is suggested just like:

```
DIR_WWW=/Users/<Your_user_name>/datas/php/www/
DIR_REDIS_DATA=/Users/<Your_user_name>/datas/php/redis/data/
DIR_MYSQL_DATA=/Users/<Your_user_name>/datas/php/mysql/
```

After doing this, start pulling the mirror image to make the container.👇

### Start

```
docker-compose up -d
```

### Stop

```
docker-compose down
```

### Composer

```
docker exec -it ct-phpfpm bash

cd <php_directory_in_phpfpm>
composer install
```

## Directory and File

1. .env.example - *Env variable file template.*
2. ./Dockerfile - *Phpfpm docker mirror build file.*
3. ./docker-compose.yml - *Docker marshals file.*
4. ./docker-compose.build.yml - *Docker marshals file.(Local building)*
5. ./conf/mysql/mysql.cnf - *MySQL configuration.*
6. ./conf/nginx/nginx.conf - *Nginx configuration.*
7. ./conf/nginx/conf.d - *Nginx site configuration directory.*
8. ./conf/php/php.ini - *PHP configuration.*
9. ./log/mysql - *MySQL log file.*
10. ./log/nginx - *Nginx log file.*
11. ./log/supervisor - *Supervisor log file.*
12. ./files - *163 Mirrors URL.*

## Env variable

- MYSQL_ROOT_PASSWORD MySQL root_user pwd.
- MYSQL_DATABASE MySQL database name.
- REDIS_PASSWORD Redis pwd.
- DIR_WWW WEB project directory.
- DIR_REDIS_DATA Redis data storage directory.
- DIR_MYSQL_DATA Mysql data storage directory.

## Todo

- [X] PHP 7.2 build.
- [ ] Lavarel build.
