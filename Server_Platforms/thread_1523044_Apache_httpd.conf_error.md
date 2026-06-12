---
title: "Apache httpd.conf error"
date: 2010-07-03
forum: Server Platforms
---

### Post by redfox1160 on 2010-07-03
I cannot start my apache server. When I type
```
sudo /etc/init.d/apache2 start
```
the following prints on the screen
```
* Starting web server apache2
Syntax error on line 48 of /etc/apache2/httpd.conf:
Invalid command 'ServerType', perhaps misspelled or defined by a module not included
in the server configuration
                                                                               [[COLOR="Red"]fail[/COLOR]]
```
I do not know how to fix this. Any help would be appreciated.

---

### Post by sjinks on 2010-07-04
Try to comment out/delete line 48 of your /etc/apache2/httpd.conf

---

### Post by infamous-online on 2010-07-09
Whatever is on line 48 is the problem, look there and see what's the issue there. As a test, comment it out, save your settings and restart the server, if you get no errors then whatever is in that line is the problem. Also if you could post what's in line 48, so we can assist you better if you don't mind.

---

