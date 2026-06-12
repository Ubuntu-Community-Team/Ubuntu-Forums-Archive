---
title: "Package Management"
date: 2006-12-11
forum: Server Platforms
---

### Post by Hotei on 2006-12-11
I have received such good help here before I am going to throw this one out there too.

I have a LAMP box running on dapper and had to compile in support for informix.  Following these guides as a model I have informix support working.
[http://nmglug.org/phorum/read.php?5,29,50](http://nmglug.org/phorum/read.php?5,29,50)
[http://www.pintmaster.com/wordpress/index.php/20060530/how-to-compile-mssql-support-into-php-in-ubuntu-dapper-drake/](http://www.pintmaster.com/wordpress/index.php/20060530/how-to-compile-mssql-support-into-php-in-ubuntu-dapper-drake/)

Problem is that now the package manager wants to update libapache2-mod-php5 php5-cgi php5-cli.  I would like to silence this.

I have read about and seen stuff on /etc/apt/preferences but they are all in relation to Debian and the different releases (stable, testing, unstable) and I am not quite sure how to make it work in my situation were I built from the repository sources.

Anyway I can get it to stop complaining about these packages?

Thanks in advance

-Hotei

---

### Post by elst on 2006-12-11
Ubuntu uses the same system as Debian, just with different identifiers, so documentation on Debian APT also works for Ubuntu.

If you source compile then you can have two independent copies of the application: the one that the package manager knows about, and the manually compiled copy. In this case, I'd remove the package installed version so that APT doesn't track it anymore.

---

### Post by az on 2006-12-11
With the following, [http://packages.ubuntu.com/dapper/web/php-db](http://packages.ubuntu.com/dapper/web/php-db)
do you have to recompile everything to enable informix and mssql?

The first howto is not Debian or ubuntu-specific.

---

