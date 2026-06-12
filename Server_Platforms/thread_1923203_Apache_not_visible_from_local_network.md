---
title: "Apache not visible from local network"
date: 2012-02-10
forum: Server Platforms
---

### Post by robson22 on 2012-02-10
Welcom.
First thing is sorry about my english.
I have instaled apache2, php5 and mysql. The problem is somthing with configuration apache (i thing so).Apache server is started and when try connection from other computer (in my local network) [http://192.168.1.2/index.html](http://192.168.1.2/index.html) i cant connect with test website. I dont now why.
I give configuration of file /etc/apache2/sites-enabled/000-default:
```
<VirtualHost *:80>
 ServerAdmin webmaster@localhost

 DocumentRoot /var/www
 <Directory />
 Options FollowSymLinks
 AllowOverride None
 </Directory>
 <Directory /var/www/>
 Options Indexes FollowSymLinks MultiViews
 AllowOverride None
 Order allow,deny
 allow from all
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

</VirtualHost>
```

ooh and i use ubuntu 11.04

Please help me

I greet.

---

### Post by spynappels on 2012-02-10
Are you getting a timeout (50x error) or a forbidden/not found (40x error)?

Is there any content in /var/www?

---

### Post by Lars Noodén on 2012-02-10
Is Apache running? What is the output of a status query?

```

/etc/init.d/apache2 status

```

---

### Post by robson22 on 2012-02-10
There is no content in /var/www, is only index.html which contains ```
It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.
```

Browser opera try connect by few minutes(from other computer with local network) and next give me only:```
Could not connect to remote server
```

The output from the:/etc/init.d/apache2 status is```
Apache2 is running (pid 31092).
```

What i can say more is the computer where is installed apache, sharing internet connection to other computers in my local network.
I give my firewall file:
```
echo 1 > /proc/sys/net/ipv4/ip_forward
# czyszczenie starych regul
iptables -F
iptables -X
iptables -t nat -X
iptables -t nat -F
# ustawienie polityki dzialania
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT
# zezwolenie nna laczenie sie z naszym zewnetrznym ip po ssh
# iptables -A INPUT -s 0/0 -d ip.ip.ip.ip -p tcp --dport 22 -j ACCEPT
# iptables -A OUTPUT -s 0/0 -d ip.ip.ip.ip -p tcp --dport 22 -j ACCEPT
# iptables -A INPUT -s 0/0 -d ip.ip.ip.ip -p udp --dport 22 -j ACCEPT
# iptables -A OUTPUT -s 0/0 -d ip.ip.ip.ip -p udp --dport 22 -j ACCEPT
# polaczenia nawiazane
iptables -A INPUT -j ACCEPT -m state --state ESTABLISHED,RELATED
iptables -A FORWARD -j ACCEPT -m state --state ESTABLISHED,RELATED
iptables -A OUTPUT -j ACCEPT -m state --state ESTABLISHED,RELATED
# przepuszczanie loopback
iptables -A INPUT -i lo -j ACCEPT
iptables -A FORWARD -o lo -j ACCEPT
# udostepniaie internetu w sieci lokalnej
# dla kompa Aneta
iptables -t nat -A POSTROUTING -s 192.168.1.3 -j MASQUERADE 
iptables -A FORWARD -m mac --mac-source 00:1A:4D:94:FB:8F -j ACCEPT
# dla kompa Stasiek
iptables -t nat -A POSTROUTING -s 192.168.1.4 -j MASQUERADE
iptables -A FORWARD -m mac --mac-source 00:0D:61:37:9B:F0 -j ACCEPT
# dla kompa Karolina
iptables -t nat -A POSTROUTING -s 192.168.1.5 -j MASQUERADE
iptables -A FORWARD -m mac --mac-source 00:1D:7d:47:8B:99 -j ACCEPT
```



ok now im add to the firewall this line```
iptables -A INPUT -s 0/0 -d 192.168.1.2/24 -p tcp --dport 80 -j ACCEPT
```
and now when i try connect browser display```
NOT FOUND
the reqested URL /index.html was not found on this server.
Apache 2.2.17 (Ubuntu) Server at 192.168.1.2 Port 80
```

---

### Post by volkswagner on 2012-02-10
```
NOT FOUND
the reqested URL /index.html was not found on this server.
Apache 2.2.17 (Ubuntu) Server at 192.168.1.2 Port 80
```

Do you get the same error if you don't specify index.html?

What do you get if you just use  [http://192.168.1.2](http://192.168.1.2) ?

Do you have any other vhost files possibly conflicting with your request.

```
ls /etc/apache2/sites-enabled
```

I assume the error above is from the browser.  You may have more detail now in your log.

---

### Post by robson22 on 2012-02-10
yes without index.html is the same error```
NOT FOUND
the reqested URL / was not found on this server.
Apache 2.2.17 (Ubuntu) Server at 192.168.1.2 Port 80
```
the output from the: ls /etc/apache2/sites-enabled is:

000-default

from what log i can give more details, where i can find?
Sorry about this question, im layman

---

### Post by volkswagner on 2012-02-10
The default location for apache2 logs.

```
/var/log/apache2access.log
```
and
```
/var/log/apache2/error.log
```

Can you disable iptables to see if that is causing the issue?  I don't think this is it because it appears your browser is getting a response....  Still worth a try though.

What's inside /etc/apache2/ports.conf?

Do you get any errors when restarting apache?

```
sudo service apache2 restart
```

---

### Post by robson22 on 2012-02-10
What is interesting when i try (of course from other computer) [http://192.168.1.2/phpmyadmin/](http://192.168.1.2/phpmyadmin/) login panel appeared. I dont now what thinking about that.

access.log
```
192.168.1.2 - - [10/Feb/2012:06:10:13 +0100] "GET / HTTP/1.1" 200 481 "-" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
192.168.1.2 - - [10/Feb/2012:06:10:13 +0100] "GET /favicon.ico HTTP/1.1" 404 503 "http://192.168.1.2/" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
192.168.0.102 - - [10/Feb/2012:06:10:43 +0100] "GET / HTTP/1.1" 200 481 "-" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
192.168.0.102 - - [10/Feb/2012:06:10:43 +0100] "GET /favicon.ico HTTP/1.1" 404 505 "http://192.168.0.102/" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
127.0.0.1 - - [10/Feb/2012:06:26:52 +0100] "GET /info.php HTTP/1.1" 200 10163 "-" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
127.0.0.1 - - [10/Feb/2012:06:26:52 +0100] "GET /favicon.ico HTTP/1.1" 404 500 "http://localhost/info.php" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
127.0.0.1 - - [10/Feb/2012:06:26:52 +0100] "GET /info.php?=PHPE9568F34-D428-11d2-A769-00AA001ACF42 HTTP/1.1" 200 2752 "http://localhost/info.php" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
127.0.0.1 - - [10/Feb/2012:06:26:52 +0100] "GET /info.php?=SUHO8567F54-D428-14d2-A769-00DA302A5F18 HTTP/1.1" 200 3042 "http://localhost/info.php" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
127.0.0.1 - - [10/Feb/2012:06:26:52 +0100] "GET /info.php?=PHPE9568F35-D428-11d2-A769-00AA001ACF42 HTTP/1.1" 200 2374 "http://localhost/info.php" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
127.0.0.1 - - [10/Feb/2012:06:37:08 +0100] "GET /phpmyadmin HTTP/1.1" 404 502 "-" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
127.0.0.1 - - [10/Feb/2012:06:37:32 +0100] "GET /phpmyadmin HTTP/1.1" 404 502 "-" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
127.0.0.1 - - [10/Feb/2012:06:37:34 +0100] "GET /phpmyadmin HTTP/1.1" 404 502 "-" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
127.0.0.1 - - [10/Feb/2012:06:37:36 +0100] "GET /phpmyadmin HTTP/1.1" 404 502 "-" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
127.0.0.1 - - [10/Feb/2012:06:38:34 +0100] "GET /phpmyadmin HTTP/1.1" 404 502 "-" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
127.0.0.1 - - [10/Feb/2012:06:38:35 +0100] "GET /phpmyadmin HTTP/1.1" 404 502 "-" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
127.0.0.1 - - [10/Feb/2012:06:42:36 +0100] "GET /phpmyadmin HTTP/1.1" 404 502 "-" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
192.168.1.2 - - [10/Feb/2012:06:42:51 +0100] "GET /phpmyadmin HTTP/1.1" 404 504 "-" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
192.168.1.2 - - [10/Feb/2012:06:42:51 +0100] "GET /favicon.ico HTTP/1.1" 404 503 "http://192.168.1.2/phpmyadmin" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
192.168.1.2 - - [10/Feb/2012:06:50:09 +0100] "GET /phpmyadmin HTTP/1.1" 404 504 "-" "Opera/9.80 (X11; Linux i686; U; pl) Presto/2.10.229 Version/11.61"
192.168.1.2 - - [10/Feb/2012:06:50:10 +0100] "GET /phpmyadmin HTTP/1.1" 404
```

error.log
```
[Fri Feb 10 06:08:53 2012] [notice] Apache/2.2.17 (Ubuntu) configured -- resuming normal operations
[Fri Feb 10 06:10:13 2012] [error] [client 192.168.1.2] File does not exist: /var/www/favicon.ico, referer: http://192.168.1.2/
[Fri Feb 10 06:10:43 2012] [error] [client 192.168.0.102] File does not exist: /var/www/favicon.ico, referer: http://192.168.0.102/
[Fri Feb 10 06:18:36 2012] [notice] caught SIGTERM, shutting down
[Fri Feb 10 06:18:39 2012] [notice] Digest: generating secret for digest authentication ...
[Fri Feb 10 06:18:39 2012] [notice] Digest: done
[Fri Feb 10 06:18:40 2012] [notice] Apache/2.2.17 (Ubuntu) DAV/2 mod_ssl/2.2.17 OpenSSL/0.9.8o configured -- resuming normal operations
[Fri Feb 10 06:19:41 2012] [notice] caught SIGTERM, shutting down
[Fri Feb 10 06:19:49 2012] [notice] Digest: generating secret for digest authentication ...
[Fri Feb 10 06:19:49 2012] [notice] Digest: done
[Fri Feb 10 06:19:50 2012] [notice] Apache/2.2.17 (Ubuntu) DAV/2 mod_ssl/2.2.17 OpenSSL/0.9.8o configured -- resuming normal operations
[Fri Feb 10 06:20:00 2012] [notice] Graceful restart requested, doing restart
[Fri Feb 10 06:20:00 2012] [error] (9)Bad file descriptor: apr_socket_accept: (client socket)
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Feb 10 06:20:00 2012] [notice] Digest: generating secret for digest authentication ...
[Fri Feb 10 06:20:00 2012] [notice] Digest: done
[Fri Feb 10 06:20:02 2012] [notice] Apache/2.2.17 (Ubuntu) DAV/2 mod_ssl/2.2.17 OpenSSL/0.9.8o configured -- resuming normal operations
[Fri Feb 10 06:24:11 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Feb 10 06:24:11 2012] [notice] Digest: generating secret for digest authentication ...
[Fri Feb 10 06:24:11 2012] [notice] Digest: done
[Fri Feb 10 06:24:12 2012] [notice] Apache/2.2.17 (Ubuntu) DAV/2 PHP/5.3.5-1ubuntu7.4 with Suhosin-Patch mod_ssl/2.2.17 OpenSSL/0.9.8o configured -- resuming normal operations
[Fri Feb 10 06:24:52 2012] [notice] caught SIGTERM, shutting down
[Fri Feb 10 06:24:54 2012] [notice] Digest: generating secret for digest authentication ...
[Fri Feb 10 06:24:54 2012] [notice] Digest: done
[Fri Feb 10 06:24:55 2012] [notice] Apache/2.2.17 (Ubuntu) DAV/2 PHP/5.3.5-1ubuntu7.4 with Suhosin-Patch mod_ssl/2.2.17 OpenSSL/0.9.8o configured -- resuming normal operations
[Fri Feb 10 06:26:52 2012] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico, referer: http://localhost/info.php
[Fri Feb 10 06:37:08 2012] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin
[Fri Feb 10 06:37:32 2012] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin
[Fri Feb 10 06:37:34 2012] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin
[Fri Feb 10 06:37:36 2012] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin
```

after ```
sudo service apache2 restart
``` i get:

```
* Restarting web server htcacheclean                                           apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

---

### Post by vandorjw on 2012-02-10
not 100% sure but:
add a "/" after
DocumentRoot /var/www
to make it look like
DocumentRoot /var/www/
EDIT:
nevermind, that seems to make no difference to me.

> 
 Order allow,deny
 Allow from all
 </Directory>


change to 
> 
Order deny,allow
Allow from all
</Directory>


But I could be wrong twice in a row...

---

### Post by HugoSerrano on 2012-02-10
Can you do a telnet to port 80 of the server?

something like this:
telnet 192.168.1.2 80
Trying 192.168.1.2...
Connected to 192.168.1.2.
Escape character is '^]'.

Regards!

---

### Post by robson22 on 2012-02-10
cc7gir thank you very much :D its working, i change allow,deny to deny,allow and it start working:D

i greet

---

