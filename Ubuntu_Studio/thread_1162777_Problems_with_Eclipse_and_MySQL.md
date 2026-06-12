---
title: "Problems with Eclipse and MySQL"
date: 2009-05-18
forum: Ubuntu Studio
---

### Post by eddiemolko on 2009-05-18
First of all, sorry if my english is not so good, i'm from argentina.

I'm a web developer.
I have a php page that makes consultes to MySQL.
I'm using Eclipse to make the site.
But when i try to preview that php page, i get the next thing:



( ! ) Warning: mysql_connect() [function.mysql-connect]: Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2) in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 31
Call Stack
# Time Function Location
1 0.0001 {main}( ) ../noticias.php:0
2 0.0027 include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' ) ../noticias.php:4
3 0.0029 mysql_connect( ) ../news.php:31

( ! ) Warning: mysql_select_db() [function.mysql-select-db]: Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2) in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 32
Call Stack
# Time Function Location
1 0.0001 {main}( ) ../noticias.php:0
2 0.0027 include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' ) ../noticias.php:4
3 0.0037 mysql_select_db( ) ../news.php:32

( ! ) Warning: mysql_select_db() [function.mysql-select-db]: A link to the server could not be established in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 32
Call Stack
# Time Function Location
1 0.0001 {main}( ) ../noticias.php:0
2 0.0027 include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' ) ../noticias.php:4
3 0.0037 mysql_select_db( ) ../news.php:32

( ! ) Warning: mysql_query() [function.mysql-query]: Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2) in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 35
Call Stack
# Time Function Location
1 0.0001 {main}( ) ../noticias.php:0
2 0.0027 include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' ) ../noticias.php:4
3 0.0042 mysql_query( ) ../news.php:35

( ! ) Warning: mysql_query() [function.mysql-query]: A link to the server could not be established in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 35
Call Stack
# Time Function Location
1 0.0001 {main}( ) ../noticias.php:0
2 0.0027 include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' ) ../noticias.php:4
3 0.0042 mysql_query( ) ../news.php:35

( ! ) Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 38
Call Stack
# Time Function Location
1 0.0001 {main}( ) ../noticias.php:0
2 0.0027 include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' ) ../noticias.php:4
3 0.0046 mysql_fetch_array( ) ../news.php:38

( ! ) Warning: mysql_query() [function.mysql-query]: Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2) in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 150
Call Stack
# Time Function Location
1 0.0001 {main}( ) ../noticias.php:0
2 0.0027 include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' ) ../noticias.php:4
3 0.0052 news( ) ../news.php:60
4 0.0052 mysql_query( ) ../news.php:150

( ! ) Warning: mysql_query() [function.mysql-query]: A link to the server could not be established in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 150
Call Stack
# Time Function Location
1 0.0001 {main}( ) ../noticias.php:0
2 0.0027 include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' ) ../noticias.php:4
3 0.0052 news( ) ../news.php:60
4 0.0052 mysql_query( ) ../news.php:150

( ! ) Warning: mysql_fetch_assoc(): supplied argument is not a valid MySQL result resource in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 152
Call Stack
# Time Function Location
1 0.0001 {main}( ) ../noticias.php:0
2 0.0027 include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' ) ../noticias.php:4
3 0.0052 news( ) ../news.php:60
4 0.0057 mysql_fetch_assoc( ) ../news.php:152



Anyone knows what can that be?
Thanks

---

