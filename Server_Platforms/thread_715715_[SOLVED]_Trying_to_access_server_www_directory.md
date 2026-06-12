---
title: "[SOLVED] Trying to access server www directory"
date: 2008-03-05
forum: Server Platforms
---

### Post by mr tim esquire on 2008-03-05
Ive put some http files in my /var/www directory on my ubuntu server but when i navigate to them from another machine on the LAN the page does not display, instead Forefox tries to download the files.

The thing is im not really sure what im doing, what packages do i need installed on my server and do i need to setup apache?

Hope you understand what im on about here.

---

### Post by faulkes on 2008-03-05
Could you be more specific on the type of "http" files? is this just pure html? what are the file extensions?

The behaviour which is being seen is typical of server not knowing how to deal with
a specific content type/format (mime-type).

If you are not sure what you are doing, I suggest the official server guide documentation
and the community based documentation.  Links to both of those are in the signature
below.

Faulkes

---

### Post by mr tim esquire on 2008-03-05
i didnt have everything installed to quite be a LAMP server
This gets everything going OK

```
apt-get install mysql-server mysql-admin apache2 php5 libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql phpmyadmin
```
Then you have to add a mysql user
```
mysql -u root -p create torrentflux
```
thanks!

---

