---
title: "local lamp server for testing ???"
date: 2007-02-04
forum: Server Platforms
---

### Post by Catsquotl on 2007-02-04
Hello,

I like to setup a local lamp server for testing purposes. Can someone talk me through or guide me to a place where i can find the options i need to enable or disable to get a lamp server witch is only open to the local machine??

thanks Cat

---

### Post by amendt on 2007-02-04
I would read this first. 
[https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP](https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP)

---

### Post by Brazen on 2007-02-04
```
sudo apt-get -y install apache2 php-mysql
```

Open the file /etc/apache2/sites-available/default

In that file there should be a 'Directory /var/www' section.  In that section, add the following lines (or change the existing lines):
```
    Order deny,allow
    Deny from all
    Allow from localhost
```

Optionally, if you want to be absolutely sure, install firestarter and block incoming port 80 connections.

---

### Post by satellite360 on 2007-04-29
[Ubuntu Documentation - Securing Apache]("https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP#head-967a645a6dc898f3e00c3dc7063c6949a4957d52")

---

