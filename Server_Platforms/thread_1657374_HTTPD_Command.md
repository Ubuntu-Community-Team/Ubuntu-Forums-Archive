---
title: "HTTPD Command"
date: 2011-01-01
forum: Server Platforms
---

### Post by xathras1982 on 2011-01-01
Hi,
I have apache2 install as part of a LAMP Installation. I am doing some auditing on loaded modules but I am unable to submit command HTTPD -M and get the following message:
 
No command 'httpd' found, did you mean:
Command 'dhttpd' from package 'dhttpd' (universe)
Command 'xttpd' from package 'xtide' (universe)
Command 'thttpd' from package 'thttpd' (universe)
 
 
Can anyone help?
 
Server installation of 10.10 64 BIT

---

### Post by rubylaser on 2011-01-01
Here's an easy way to view your enabled mods...
```
ls /etc/apache2/mods-enabled/
```

Deb based distros(Ubuntu) come with Apache helper scripts.  You should take a look at them...
[http://www.debian-administration.org/articles/207]("http://www.debian-administration.org/articles/207")

---

### Post by xathras1982 on 2011-01-01
Thanks for the command and the link :)

---

