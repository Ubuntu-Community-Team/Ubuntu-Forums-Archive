---
title: "Necesito ayuda con Eclipse y MySQL"
date: 2009-05-18
forum: Software
---

### Post by eddiemolko on 2009-05-18
Como ya sabran por algunos de mis posteos, soy diseñador web.
Tengo una pagina php que interacciona con MySQL.
Pero al darle a previsualizar en Eclipse me tira lo siguiente:


( ! ) Warning: mysql_connect() [function.mysql-connect]: Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2) in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 31
Call Stack
#	Time	Function	Location
1	0.0001	{main}( )	../noticias.php:0
2	0.0027	include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' )	../noticias.php:4
3	0.0029	mysql_connect( )	../news.php:31

( ! ) Warning: mysql_select_db() [function.mysql-select-db]: Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2) in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 32
Call Stack
#	Time	Function	Location
1	0.0001	{main}( )	../noticias.php:0
2	0.0027	include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' )	../noticias.php:4
3	0.0037	mysql_select_db( )	../news.php:32

( ! ) Warning: mysql_select_db() [function.mysql-select-db]: A link to the server could not be established in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 32
Call Stack
#	Time	Function	Location
1	0.0001	{main}( )	../noticias.php:0
2	0.0027	include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' )	../noticias.php:4
3	0.0037	mysql_select_db( )	../news.php:32

( ! ) Warning: mysql_query() [function.mysql-query]: Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2) in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 35
Call Stack
#	Time	Function	Location
1	0.0001	{main}( )	../noticias.php:0
2	0.0027	include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' )	../noticias.php:4
3	0.0042	mysql_query( )	../news.php:35

( ! ) Warning: mysql_query() [function.mysql-query]: A link to the server could not be established in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 35
Call Stack
#	Time	Function	Location
1	0.0001	{main}( )	../noticias.php:0
2	0.0027	include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' )	../noticias.php:4
3	0.0042	mysql_query( )	../news.php:35

( ! ) Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 38
Call Stack
#	Time	Function	Location
1	0.0001	{main}( )	../noticias.php:0
2	0.0027	include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' )	../noticias.php:4
3	0.0046	mysql_fetch_array( )	../news.php:38

( ! ) Warning: mysql_query() [function.mysql-query]: Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2) in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 150
Call Stack
#	Time	Function	Location
1	0.0001	{main}( )	../noticias.php:0
2	0.0027	include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' )	../noticias.php:4
3	0.0052	news( )	../news.php:60
4	0.0052	mysql_query( )	../news.php:150

( ! ) Warning: mysql_query() [function.mysql-query]: A link to the server could not be established in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 150
Call Stack
#	Time	Function	Location
1	0.0001	{main}( )	../noticias.php:0
2	0.0027	include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' )	../noticias.php:4
3	0.0052	news( )	../news.php:60
4	0.0052	mysql_query( )	../news.php:150

( ! ) Warning: mysql_fetch_assoc(): supplied argument is not a valid MySQL result resource in /opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php on line 152
Call Stack
#	Time	Function	Location
1	0.0001	{main}( )	../noticias.php:0
2	0.0027	include( '/opt/lampp/htdocs/Teledeteccion/paginas/phpnews/news.php' )	../noticias.php:4
3	0.0052	news( )	../news.php:60
4	0.0057	mysql_fetch_assoc( )	../news.php:152




No se como hacer :(

Alguien tiene alguna idea de que puede ser?

Desde ya gracias

---

### Post by guillermolisi on 2009-05-18
Por el primer mensaje de Warning pareceria que el script news.php intenta concectar con una base de datos y por cuestiones de permisos/user/password/socket incorrectas no puede y de ahi el resto de los errores.

Me fijaria en quien es el user habilitado en el servidor MySQL para conectar con la DB, su password, a que grupo pertenece, que accesos a la base y sus tablas estan permitidos y por las dudas, verifica el port que se esta usando para llegar hasta el servidor MySQL.

Por otra parte, que version de MySQL estas usando, cual de Eclipse, cual de PHP, como para completar la informacion.

En definitiva, me parece que le falta un toque de configuracion para que quede operativo.

Edit: No uso Eclipse pero seguramente habra quien si y pueda confirmar si necesitas agregarle algun componente para usar con MySQL.

---

