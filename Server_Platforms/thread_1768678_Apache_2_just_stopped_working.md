---
title: "Apache 2 just stopped working?"
date: 2011-05-27
forum: Server Platforms
---

### Post by minerbog on 2011-05-27
Hi guys,

I have just booted up to do some local work on my website and apache 2 has start throwing 403 error's at me??  phpmyadmin and other alias's I have setup work but the main root just 403's on me?? It has been working away flawlessly for months now. No system upgrade has recently updated Apache and I can see no errors in my set up files!

So, I'm not really sure what to ask here, but a fresh set of eyes on my setup files may shed some light on a very weird problem!

My default setup file:
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/gavin/wwwsite

	<Directory "/home/gavin/wwwsite">
		Options +Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

    Alias /wordpress/ "/usr/share/wwwextra/wordpress/"
    <Directory "/usr/share/wwextra/wordpress/">
	Options Indexes MultiViews FollowSymLinks
	AllowOverride None
	Order deny,allow
	Deny from all
	Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

My access.log file from today:
```
::1 - - [27/May/2011:10:13:04 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:13:04 +0100] "GET /favicon.ico HTTP/1.1" 403 502 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:13:08 +0100] "GET /favicon.ico HTTP/1.1" 403 502 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:13:09 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:13:14 +0100] "GET /phpmyadmin/ HTTP/1.1" 200 3235 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:13:15 +0100] "GET /phpmyadmin/print.css HTTP/1.1" 200 649 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:13:15 +0100] "GET /phpmyadmin/favicon.ico HTTP/1.1" 200 19199 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:13:15 +0100] "GET /phpmyadmin/themes/original/img/logo_right.png HTTP/1.1" 200 5951 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:13:15 +0100] "GET /phpmyadmin/themes/original/img/b_help.png HTTP/1.1" 200 520 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:13:15 +0100] "GET /phpmyadmin/phpmyadmin.css.php?token=c916e5a9c1163e6a82709baf5cfdc5e4&js_frame=right&nocache=3865551696 HTTP/1.1" 200 5532 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:13:18 +0100] "GET /phpmyadmin/favicon.ico HTTP/1.1" 200 19199 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:13:18 +0100] "GET /phpmyadmin/favicon.ico HTTP/1.1" 200 19199 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:13:21 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:13:35 +0100] "GET /gavinsharp.co.uk/httpdocs/index.php/admin HTTP/1.1" 403 525 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:13:41 +0100] "GET /gavinsharp.co.uk/ HTTP/1.1" 403 508 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:16:22 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:16:22 +0100] "GET /favicon.ico HTTP/1.1" 403 502 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:16:23 +0100] "GET /favicon.ico HTTP/1.1" 403 502 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:23:11 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:23:12 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:23:12 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:23:13 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:23:13 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:24:06 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:24:12 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:24:13 +0100] "GET /favicon.ico HTTP/1.1" 403 503 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:24:16 +0100] "GET /favicon.ico HTTP/1.1" 403 503 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:24:33 +0100] "GET /info.php HTTP/1.1" 403 503 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:25:05 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; Linux i686) AppleWebKit/534.24 (KHTML, like Gecko) Chrome/11.0.696.71 Safari/534.24"
::1 - - [27/May/2011:10:25:06 +0100] "GET /favicon.ico HTTP/1.1" 403 502 "-" "Mozilla/5.0 (X11; Linux i686) AppleWebKit/534.24 (KHTML, like Gecko) Chrome/11.0.696.71 Safari/534.24"
::1 - - [27/May/2011:10:25:40 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:25:40 +0100] "GET /favicon.ico HTTP/1.1" 403 502 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:25:43 +0100] "GET /favicon.ico HTTP/1.1" 403 502 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:31:09 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:31:14 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [27/May/2011:10:33:13 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:33:29 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:33:29 +0100] "GET /favicon.ico HTTP/1.1" 403 503 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:33:32 +0100] "GET /favicon.ico HTTP/1.1" 403 503 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:37:29 +0100] "GET /favicon.ico HTTP/1.1" 403 504 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:37:31 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:40:09 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:40:14 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:46:42 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:46:43 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:46:44 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:46:45 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:46:45 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:46:45 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:54:40 +0100] "GET /docs/ HTTP/1.1" 403 500 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:54:57 +0100] "GET /doc/ HTTP/1.1" 200 19611 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:55:07 +0100] "GET /icons/blank.gif HTTP/1.1" 200 439 "http://localhost/doc/" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:55:07 +0100] "GET /icons/back.gif HTTP/1.1" 200 508 "http://localhost/doc/" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:55:07 +0100] "GET /icons/folder.gif HTTP/1.1" 200 517 "http://localhost/doc/" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:55:42 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:55:44 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:56:47 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:57:07 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:57:08 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:57:09 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:57:41 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:57:42 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:58:08 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:58:10 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:58:10 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:58:11 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:58:12 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:58:12 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:58:12 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:58:13 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:58:13 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:58:13 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:58:13 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:58:13 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:58:14 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:58:14 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:58:14 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:10:58:14 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:11:00:03 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:11:00:04 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:11:01:19 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:11:01:20 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:11:01:53 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:11:01:54 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:11:02:30 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:11:02:57 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:11:10:10 +0100] "GET /pyrocms HTTP/1.1" 403 502 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:11:10:12 +0100] "GET /pyrocms/ HTTP/1.1" 404 499 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:11:10:17 +0100] "GET /wordpress HTTP/1.1" 403 501 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:11:10:20 +0100] "GET /wordpress/ HTTP/1.1" 200 347 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:11:12:36 +0100] "GET / HTTP/1.1" 403 497 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
127.0.0.1 - - [27/May/2011:11:12:37 +0100] "GET / HTTP/1.1" 403 496 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
```

My access.log file from last week!!
```
::1 - - [17/May/2011:15:01:32 +0100] "GET /gavinsharp.co.uk/httpdocs/addons/themes/main/js/cufon.js HTTP/1.1" 404 531 "http://localhost/gavinsharp.co.uk/httpdocs/index.php/blog" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:01:32 +0100] "GET /gavinsharp.co.uk/httpdocs/addons/themes/main/js/qk.font.js HTTP/1.1" 404 533 "http://localhost/gavinsharp.co.uk/httpdocs/index.php/blog" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:01:32 +0100] "GET /gavinsharp.co.uk/httpdocs/addons/themes/main/js/global.js HTTP/1.1" 404 532 "http://localhost/gavinsharp.co.uk/httpdocs/index.php/blog" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:01:42 +0100] "GET /gavinsharp.co.uk/httpdocs/index.php/blog HTTP/1.1" 200 3792 "http://localhost/gavinsharp.co.uk/httpdocs/index.php/blog/2011/03/installing-hmvc-extensions-for-codigniter-2" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:26 +0100] "GET /phpmyadmin/ HTTP/1.1" 200 1873 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:26 +0100] "GET /phpmyadmin/js/common.js HTTP/1.1" 200 3471 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:26 +0100] "GET /phpmyadmin/favicon.ico HTTP/1.1" 200 19199 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:26 +0100] "GET /phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e HTTP/1.1" 200 2308 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:26 +0100] "GET /phpmyadmin/js/navigation.js HTTP/1.1" 200 1875 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/js/functions.js HTTP/1.1" 200 12436 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/logo_left.png HTTP/1.1" 200 7147 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/b_home.png HTTP/1.1" 200 661 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/s_loggoff.png HTTP/1.1" 200 553 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/b_selboard.png HTTP/1.1" 200 565 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/b_docs.png HTTP/1.1" 200 583 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/b_sqlhelp.png HTTP/1.1" 200 578 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:26 +0100] "GET /phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e HTTP/1.1" 200 7961 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:26 +0100] "GET /phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=left&nocache=3865551696 HTTP/1.1" 200 1770 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/js/mooRainbow/mooRainbow.css HTTP/1.1" 200 1098 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/print.css HTTP/1.1" 200 648 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696 HTTP/1.1" 200 5556 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/js/mootools.js HTTP/1.1" 200 21258 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/js/mooRainbow/mooRainbow.js HTTP/1.1" 200 4824 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/js/mootools-domready-rainbow.js HTTP/1.1" 200 669 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/js/tooltip.js HTTP/1.1" 200 2026 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/s_host.png HTTP/1.1" 200 607 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/s_db.png HTTP/1.1" 200 576 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/js/mootools-more.js HTTP/1.1" 200 51105 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/b_sql.png HTTP/1.1" 200 613 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/s_status.png HTTP/1.1" 200 604 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/s_vars.png HTTP/1.1" 200 597 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/s_asci.png HTTP/1.1" 200 544 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/b_engine.png HTTP/1.1" 200 653 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/s_rights.png HTTP/1.1" 200 803 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/s_replication.png HTTP/1.1" 200 738 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/s_process.png HTTP/1.1" 200 653 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/b_export.png HTTP/1.1" 200 604 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/b_import.png HTTP/1.1" 200 601 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/s_sync.png HTTP/1.1" 200 842 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/b_help.png HTTP/1.1" 200 519 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/themes/original/img/b_info.png HTTP/1.1" 200 524 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:27 +0100] "GET /phpmyadmin/js/mooRainbow/images/rainbow.png HTTP/1.1" 200 1085 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:28 +0100] "GET /phpmyadmin/themes/original/img/window-new.png HTTP/1.1" 200 874 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:28 +0100] "GET /phpmyadmin/themes/original/img/logo_right.png HTTP/1.1" 200 5951 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:28 +0100] "GET /phpmyadmin/themes/original/img/s_passwd.png HTTP/1.1" 200 796 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:28 +0100] "GET /phpmyadmin/themes/original/img/item_ltr.png HTTP/1.1" 200 463 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:28 +0100] "GET /phpmyadmin/themes/original/img/s_loggoff.png HTTP/1.1" 200 553 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:28 +0100] "GET /phpmyadmin/themes/original/img/b_newdb.png HTTP/1.1" 200 699 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:28 +0100] "GET /phpmyadmin/themes/original/img/s_lang.png HTTP/1.1" 200 713 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:28 +0100] "GET /phpmyadmin/themes/original/img/s_theme.png HTTP/1.1" 200 1028 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:28 +0100] "GET /phpmyadmin/themes/original/img/b_docs.png HTTP/1.1" 200 583 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:28 +0100] "GET /phpmyadmin/themes/original/img/b_home.png HTTP/1.1" 200 661 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:28 +0100] "GET /phpmyadmin/themes/original/img/s_error.png HTTP/1.1" 200 563 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:28 +0100] "GET /phpmyadmin/themes/original/img/s_warn.png HTTP/1.1" 200 552 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:28 +0100] "GET /phpmyadmin/js/mooRainbow/images/moor_arrows.gif HTTP/1.1" 200 383 "http://localhost/phpmyadmin/js/mooRainbow/mooRainbow.css" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:28 +0100] "GET /phpmyadmin/js/mooRainbow/images/moor_woverlay.png HTTP/1.1" 200 1059 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:28 +0100] "GET /phpmyadmin/js/mooRainbow/images/moor_boverlay.png HTTP/1.1" 200 1090 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:28 +0100] "GET /phpmyadmin/js/mooRainbow/images/moor_cursor.gif HTTP/1.1" 200 369 "http://localhost/phpmyadmin/js/mooRainbow/mooRainbow.css" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:28 +0100] "GET /phpmyadmin/js/mooRainbow/images/moor_slider.png HTTP/1.1" 200 881 "http://localhost/phpmyadmin/main.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:30 +0100] "GET /phpmyadmin/index.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e HTTP/1.1" 200 1873 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:30 +0100] "GET /phpmyadmin/js/common.js HTTP/1.1" 200 3471 "http://localhost/phpmyadmin/index.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:30 +0100] "GET /phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms HTTP/1.1" 200 4054 "http://localhost/phpmyadmin/index.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/js/navigation.js HTTP/1.1" 200 1874 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/js/functions.js HTTP/1.1" 200 12436 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/b_sbrowse.png HTTP/1.1" 200 487 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:30 +0100] "GET /phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms HTTP/1.1" 200 7441 "http://localhost/phpmyadmin/index.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/print.css HTTP/1.1" 200 648 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=left&nocache=3865551696 HTTP/1.1" 200 1746 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/js/mootools.js HTTP/1.1" 200 21258 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/js/functions.js HTTP/1.1" 200 12436 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/js/tooltip.js HTTP/1.1" 200 2026 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/b_props.png HTTP/1.1" 200 585 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/b_search.png HTTP/1.1" 200 896 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/js/mootools-more.js HTTP/1.1" 200 51105 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/b_tblops.png HTTP/1.1" 200 636 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/b_deltbl.png HTTP/1.1" 200 655 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/s_asc.png HTTP/1.1" 200 503 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/b_browse.png HTTP/1.1" 200 556 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/b_select.png HTTP/1.1" 200 831 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/b_insrow.png HTTP/1.1" 200 574 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696 HTTP/1.1" 200 5532 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/b_empty.png HTTP/1.1" 200 589 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/b_drop.png HTTP/1.1" 200 602 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/bd_browse.png HTTP/1.1" 200 556 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/bd_select.png HTTP/1.1" 200 815 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/bd_empty.png HTTP/1.1" 200 589 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/logo_left.png HTTP/1.1" 200 7147 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/b_home.png HTTP/1.1" 200 661 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/s_loggoff.png HTTP/1.1" 200 553 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/b_selboard.png HTTP/1.1" 200 565 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/b_docs.png HTTP/1.1" 200 583 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:31 +0100] "GET /phpmyadmin/themes/original/img/b_sqlhelp.png HTTP/1.1" 200 578 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:32 +0100] "GET /phpmyadmin/themes/original/img/s_host.png HTTP/1.1" 200 607 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:32 +0100] "GET /phpmyadmin/themes/original/img/item_ltr.png HTTP/1.1" 200 463 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:32 +0100] "GET /phpmyadmin/themes/original/img/s_db.png HTTP/1.1" 200 576 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:32 +0100] "GET /phpmyadmin/themes/original/img/b_sql.png HTTP/1.1" 200 613 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:32 +0100] "GET /phpmyadmin/themes/original/img/b_export.png HTTP/1.1" 200 604 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:32 +0100] "GET /phpmyadmin/themes/original/img/b_import.png HTTP/1.1" 200 601 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:32 +0100] "GET /phpmyadmin/themes/original/img/s_rights.png HTTP/1.1" 200 803 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:32 +0100] "GET /phpmyadmin/themes/original/img/arrow_ltr.png HTTP/1.1" 200 568 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:32 +0100] "GET /phpmyadmin/themes/original/img/b_print.png HTTP/1.1" 200 865 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:32 +0100] "GET /phpmyadmin/themes/original/img/b_tblanalyse.png HTTP/1.1" 200 587 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:32 +0100] "GET /phpmyadmin/themes/original/img/b_newtbl.png HTTP/1.1" 200 700 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:32 +0100] "GET /phpmyadmin/themes/original/img/window-new.png HTTP/1.1" 200 874 "http://localhost/phpmyadmin/db_structure.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:32 +0100] "GET /phpmyadmin/themes/original/img/s_warn.png HTTP/1.1" 200 552 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:32 +0100] "GET /phpmyadmin/themes/original/img/s_notice.png HTTP/1.1" 200 537 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:34 +0100] "GET /phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0 HTTP/1.1" 200 6853 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:34 +0100] "GET /phpmyadmin/print.css HTTP/1.1" 200 648 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:34 +0100] "GET /phpmyadmin/js/mootools.js HTTP/1.1" 200 21258 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:34 +0100] "GET /phpmyadmin/js/functions.js HTTP/1.1" 200 12436 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:34 +0100] "GET /phpmyadmin/js/tooltip.js HTTP/1.1" 200 2026 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:34 +0100] "GET /phpmyadmin/themes/original/img/s_tbl.png HTTP/1.1" 200 542 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:34 +0100] "GET /phpmyadmin/themes/original/img/b_tblexport.png HTTP/1.1" 200 574 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:34 +0100] "GET /phpmyadmin/themes/original/img/b_tblimport.png HTTP/1.1" 200 571 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:34 +0100] "GET /phpmyadmin/js/mootools-more.js HTTP/1.1" 200 51105 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:34 +0100] "GET /phpmyadmin/themes/original/img/s_fulltext.png HTTP/1.1" 200 599 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:34 +0100] "GET /phpmyadmin/themes/original/img/b_edit.png HTTP/1.1" 200 742 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:34 +0100] "GET /phpmyadmin/themes/original/img/b_views.png HTTP/1.1" 200 768 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:34 +0100] "GET /phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696 HTTP/1.1" 200 5532 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/s_host.png HTTP/1.1" 200 607 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/item_ltr.png HTTP/1.1" 200 463 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/s_db.png HTTP/1.1" 200 576 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/b_browse.png HTTP/1.1" 200 556 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/b_props.png HTTP/1.1" 200 585 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/b_sql.png HTTP/1.1" 200 613 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/b_search.png HTTP/1.1" 200 896 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/b_insrow.png HTTP/1.1" 200 574 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/b_tblops.png HTTP/1.1" 200 636 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/b_empty.png HTTP/1.1" 200 589 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/b_deltbl.png HTTP/1.1" 200 655 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/b_drop.png HTTP/1.1" 200 602 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/arrow_ltr.png HTTP/1.1" 200 568 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/b_print.png HTTP/1.1" 200 865 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/s_success.png HTTP/1.1" 200 903 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/s_warn.png HTTP/1.1" 200 552 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/s_notice.png HTTP/1.1" 200 537 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:03:35 +0100] "GET /phpmyadmin/themes/original/img/window-new.png HTTP/1.1" 200 874 "http://localhost/phpmyadmin/sql.php?db=gavinsha_pyrocms&token=0cba10e5830e5d5d0d948836561b8c1e&table=blog&pos=0" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:08:44 +0100] "GET /gavinsharp.co.uk/httpdocs/index.php/blog/rss/category HTTP/1.1" 500 1348 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:08:48 +0100] "GET /gavinsharp.co.uk/httpdocs/index.php/blog/rss/category/ HTTP/1.1" 500 849 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:09:22 +0100] "GET /gavinsharp.co.uk/httpdocs/index.php/blog/rss/ HTTP/1.1" 200 1527 "-" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:10:56 +0100] "GET /phpmyadmin/index.php?token=0cba10e5830e5d5d0d948836561b8c1e&old_usr=root HTTP/1.1" 200 3401 "http://localhost/phpmyadmin/navigation.php?token=0cba10e5830e5d5d0d948836561b8c1e&db=gavinsha_pyrocms" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:10:56 +0100] "GET /phpmyadmin/print.css HTTP/1.1" 200 649 "http://localhost/phpmyadmin/index.php?token=0cba10e5830e5d5d0d948836561b8c1e&old_usr=root" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:10:56 +0100] "GET /phpmyadmin/themes/original/img/logo_right.png HTTP/1.1" 200 5951 "http://localhost/phpmyadmin/index.php?token=0cba10e5830e5d5d0d948836561b8c1e&old_usr=root" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:10:56 +0100] "GET /phpmyadmin/themes/original/img/b_help.png HTTP/1.1" 200 519 "http://localhost/phpmyadmin/index.php?token=0cba10e5830e5d5d0d948836561b8c1e&old_usr=root" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [17/May/2011:15:10:56 +0100] "GET /phpmyadmin/phpmyadmin.css.php?token=0cba10e5830e5d5d0d948836561b8c1e&js_frame=right&nocache=3865551696 HTTP/1.1" 200 5348 "http://localhost/phpmyadmin/index.php?token=0cba10e5830e5d5d0d948836561b8c1e&old_usr=root" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.17) Gecko/20110422 Ubuntu/10.10 (maverick) Firefox/3.6.17"
::1 - - [23/May/2011:14:13:50 +0100] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.16 (Ubuntu) (internal dummy connection)"
::1 - - [23/May/2011:14:13:50 +0100] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.16 (Ubuntu) (internal dummy connection)"
::1 - - [23/May/2011:14:13:50 +0100] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.16 (Ubuntu) (internal dummy connection)"
::1 - - [23/May/2011:14:13:50 +0100] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.16 (Ubuntu) (internal dummy connection)"
::1 - - [23/May/2011:14:13:50 +0100] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.16 (Ubuntu) (internal dummy connection)"
```

Any ideas would be great :)

Regards,

Gavin.
[http://www.gavinsharp.co.uk]("http://www.gavinsharp.co.uk")

---

### Post by rudelgurke on 2011-05-27
Taking a look in error.log might be more helpful than the access.log :)

Apache should log there what's wrong like permissions or something similar.

---

### Post by Lars Noodén on 2011-05-27
What does the output from the configuration test say about your configuration?
```

sudo /usr/sbin/apache2ctl configtest

```

---

