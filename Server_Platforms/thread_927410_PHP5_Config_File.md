---
title: "PHP5 Config File"
date: 2008-09-22
forum: Server Platforms
---

### Post by heyman12 on 2008-09-22
I installed LAMP server and now I need to tell webmin where the PHP5 config file is.

Does anyone know?

(please forgive me, I am quite new to these systems)

---

### Post by mbeach on 2008-09-23
its likely in /etc/php5/apache2

---

### Post by wetmonkey on 2008-09-23
Use the whereis command to find where php5 is on the system.  It will return several locations, just look through those until you find the right ini file. 

```
$whereis php5
```

---

### Post by mbeach on 2008-09-23
you might get better results with:
```
locate php.ini
```
whereis "finds the binary, source and manual page files for a command"

in this case the op is looking for the php config file, normally called php.ini.  It is typically stored in the sub-folders of /etc/php5

---

### Post by zenos2 on 2009-05-20
Another note, is that I found when setting up webmin to manage my PHP configuration, I had to delete the CGI and CLI lines from the "module setup" screen in order for it to let me manage the ini file.

---

