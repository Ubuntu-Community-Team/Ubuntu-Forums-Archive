---
title: "Apache woes ..."
date: 2006-02-05
forum: Server Platforms
---

### Post by dbee on 2006-02-05
So I'm having some issues with apache. It seems that apache can't bind to a socket on localhost because apache is already running on localhost ? I'm pretty sure that I dont' have two apaches running. 
> 
$apache2 -k stop 

>> httpd not running (no pid file)

$apache2 -k start

>> can't bind to localhost ... can't make socket .. .port80 already in use ... can't find logs

$netstat -tulp

>> tcp        0      0 localhost:www           *:*                     LISTEN     8427/apache2

$killall 9 apache2

$apache2 -k start 

>> no problem ??

... another apache difficulty - can't seem to figure out exactly what is happening. Also I've changed my hosts file to something like this ...
> 
127.0.0.1       localhost                       My_app   ubuntu64
127.0.0.1       localhost.localdomain   localhost       ubuntu64

... the idea was that it would hook up with my sites-available and let me access 
My_app. Unfortunately though, it returns a 404 on both localhost and My_app.

My sites-available looks like this ....
My_app folder
> 
NameVirtualHost My_app

<VirtualHost My_app>
ErrorLog /var/log/apache2/error_log
CustomLog /var/log/apache2/access_log combined
ServerName My_app
DocumentRoot /var/www/My_app
</VirtualHost>


Default folder
> 
NameVirtualHost *

<VirtualHost *>
ErrorLog /var/log/apache2/error_log
CustomLog /var/log/apache2/access_log combined
ServerName localhost
DocumentRoot /var/www/
</VirtualHost>

I have a link from sites-enabled to My_app. 

Help ... uniserver is looking mighty tempting right about now :???:

---

### Post by LordHunter317 on 2006-02-05
[QUOTE=dbee]So I'm having some issues with apache. It seems that apache can't bind to a socket on localhost because apache is already running on localhost ? I'm pretty sure that I dont' have two apaches running. [/quote]Don't verify it the way you did.  Use 'ps ax', or use netstat -an --inet --inet6, as root.

> My sites-available looks like this ....And it's wrong.  NameVirtualHost **must** match your Port / Listen directive.  It won't work if it doesn't.  And your <VirtualHost> directive must match the NameVirtualHost exactly as well, or it won't work. 

Fix that.  If you want to listen on localhost only, then put this in ports.conf:```
Listen 127.0.0.1:80
NameVirtualHost 127.0.0.1:80
```And remove **all** NameVirtualHost entries in sites-enabled (They shouldn't be there anyway, and the default config is stupid for putting them there).  Then, change your <VirtualHost> directives to match the above.

---

### Post by dbee on 2006-02-06
cool, thanks LH

---

### Post by dbee on 2006-02-19
Hi again,

So I've done everything you have said LH - I'm just going to dump out all my files if 
no-one minds. I can't tell you how (unneccessarily )annoying this problem is for me. But anyway ...

... this is my /var/www/
```

apache2-default my_app 

```

this is my sites-available
```

default file:

<VirtualHost 127.0.0.1:80 >
ErrorLog /var/log/apache2/error_log
CustomLog /var/log/apache2/access_log combined
ServerName localhost
DocumentRoot /var/www/
</VirtualHost>

my_app file:
NameVirtualHost *

<VirtualHost 127.0.0.1:80 >
ErrorLog /var/log/apache2/error_log
CustomLog /var/log/apache2/access_log combined
ServerName my_app
DocumentRoot /var/www/my_app
</VirtualHost>

```

sites-enabled ...

```


000-default file :
<VirtualHost 127.0.0.1:80 >
ErrorLog /var/log/apache2/error_log
CustomLog /var/log/apache2/access_log combined
ServerName localhost
DocumentRoot /var/www/
</VirtualHost>

my_app file:
<VirtualHost 127.0.0.1:80 >
ErrorLog /var/log/apache2/error_log
CustomLog /var/log/apache2/access_log combined
ServerName my_app
DocumentRoot /var/www/my_app
</VirtualHost>

```

... my ports.conf
```

Listen 127.0.0.1:80
NameVirtualHost 127.0.0.1:80

```

... trying to hack this out is now WAY beyond my patience - so I really appreciate the help here :) 

when I try to access my server on localhost - I get 
> 
he requested URL / was not found on this server.


... also, when I try to restart it ...
```

root@ubuntu64:/etc/apache2# apache2 -k restart
httpd not running, trying to start
(98)Address already in use: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs

```

my output from netstat is
```

root@ubuntu64:/etc/apache2# netstat -an --inet --inet6
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:32769         0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:32770         0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:80            0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           127.0.0.1:53816         ESTABLISHED
tcp        0      1 192.168.0.2:60745       66.235.214.232:80       LAST_ACK
tcp        0      0 192.168.0.2:60842       66.235.214.232:80       ESTABLISHED
tcp        0      0 127.0.0.1:32769         127.0.0.1:60920         ESTABLISHED
tcp        0      0 127.0.0.1:53816         127.0.0.1:631           ESTABLISHED
tcp        0      0 127.0.0.1:53816         127.0.0.1:631           ESTABLISHED
tcp        0      0 192.168.0.2:54188       83.138.8.72:21          ESTABLISHED
tcp        0      0 127.0.0.1:60920         127.0.0.1:32769         ESTABLISHED
tcp6       0      0 :::22                   :::*                    LISTEN
udp        0      0 172.16.207.1:137        0.0.0.0:*
udp        0      0 192.168.1.1:137         0.0.0.0:*
udp        0      0 192.168.0.2:137         0.0.0.0:*
udp        0      0 0.0.0.0:137             0.0.0.0:*
udp        0      0 172.16.207.1:138        0.0.0.0:*
udp        0      0 192.168.1.1:138         0.0.0.0:*
udp        0      0 192.168.0.2:138         0.0.0.0:*
udp        0      0 0.0.0.0:138             0.0.0.0:*
udp        0      0 0.0.0.0:68              0.0.0.0:*
raw        0      0 0.0.0.0:1               0.0.0.0:*  

```

---

### Post by jinacio on 2006-02-19
ok here's some thoughts, from my limited experience:

- first you should start by removing the 'NameVirtualHost' from everywhere except the apache2.conf
- 'My_app' is not the same as 'my_app' (check the hosts)
- instead of using 'apache2 -k <command>' try '/etc/init.d/apache2 <start|stop|restart>'
- are you sure there is no other app running that's taking up port 80?

good luck,
Joao Inacio

edit: try using the "-p" switch in netstat to see what  programs are binded to the sockets

---

