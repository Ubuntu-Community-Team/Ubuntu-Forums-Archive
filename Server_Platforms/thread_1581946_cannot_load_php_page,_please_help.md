---
title: "cannot load php page, please help"
date: 2010-09-25
forum: Server Platforms
---

### Post by feelexit on 2010-09-25
I have nginx, php 5 and php5-fpm installed on ubuntu 10.04 server edition.

After I started the nginx server, I have no problem loading the regular html pages.  but all .php pages cannot be viewed, firefox just pop out a window asking me if I wnat to download the file.

I also tried IE, on IE, it just shows the source code.

I checked both nginx and php5-fpm error log files, didn't see any errors. did I miss something during the configuration?

---

### Post by endotherm on 2010-09-25
in windows IIS (I;ve never seriously administered apache), that means that your server does not have a mimetype or httphandlers for your file type (eg .php). 

hope that helps you track it down.

---

### Post by lisati on 2010-09-25
Sometimes installing libapache2-mod-php or clearing your browser cache will do the trick.
Have a look here: [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205)

---

### Post by feelexit on 2010-09-25
> **lisati said:**
> Sometimes installing libapache2-mod-php or clearing your browser cache will do the trick.
Have a look here: [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205)

cleared my cache, still doesn't work.

the link you posted and this file "libapache2-mod-php", they wont work, cuz I am using nginx http server, not apache.

---

