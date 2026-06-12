---
title: "lighttpd + php5"
date: 2006-08-28
forum: Server Platforms
---

### Post by peanut butter on 2006-08-28
i am having the hardest time figuring out how to get lighttpd to work with php5. could someone please post their 10-fastcgi.conf and lighttpd.conf.
when the server actually starts it just sends me a phtml file as a download.:)

---

### Post by lamego on 2006-08-28
Translating from a portuguse article:
Install the lighttpd and php5 cgi
```
sudo apt-get install lighttpd php5-cgi
```
Edit 10-fastcgi.conf
```
## FastCGI programs have the same functionality as CGI programs,
## but are considerably faster through lower interpreter startup
## time and socketed communication
##
## Documentation: /usr/share/doc/lighttpd-doc/fastcgi.txt.gz
## página += ( "mod_fastcgi" )

## Start an FastCGI server for php5 (needs the php5-cgi package)

fastcgi.server = ( ".php" =>
( "localhost" =>
( "socket" => "/tmp/php5-fcgi.socket",
"bin-path" => "/usr/bin/php5-cgi"
)
)
```
Edit lighttpd.conf
Add "index.php" to index-file.names directive.
Create a symbolic link for the configuration:
```
cd /etc/lighttpd/conf-enabled
sudo ln -s ../conf-available/10-fastcgi.conf .
```
Now restart the service:
```
sudo /etc/init.d/lighttpd restart
```

---

### Post by peanut butter on 2006-09-17
now lighttpd wont display anything, and it wont restart or start.

---

### Post by hw-tph on 2006-09-20
The Debianized lighttpd configuration is beyond me. I just use the configuration file that ships with the lighttpd distribution instead.

You might want to read [this](http://www.ubuntuforums.org/showthread.php?t=228171).


Håkan

---

### Post by CyberX on 2006-09-23
Hi.
Lighttpd is working with fastcgi in my ubuntu ultra-light web server (installed from Xubuntu 6.06.1 CD, server installation)

I installed lighttpd with

```
sudo apt-get install lighttpd php5-cgi
```

(I also install php5-sqlite and sqlite3, because I'm using this web server with a punbb forum, with sqlite instead of mysql. But that doesn't matter for just php5)

Then I edited lighttpd.conf
```
sudo nano /etc/lighttpd/lighttpd.conf
```

to acept browsing from outside the server (just comment the line starting with "server.bind").

Then I configure php5 to fastcgi:

```
sudo lighty-enable-mod fastcgi
sudo nano /etc/lighttpd/conf-available/10-fast.conf

```

The file "10-fast.conf" is similar to this:

```
 server.modules += ( "mod_fastcgi" )
 fastcgi.server = ( ".php" =>
 ( "localhost" =>
  ( "socket" => "/tmp/php5-fcgi.socket",
    "bin-path" => "/usr/bin/php5-cgi"
   )
  )
 )

```

Then restart lighttpd:
```
sudo /etc/init.d/lighttp restart
```

---

