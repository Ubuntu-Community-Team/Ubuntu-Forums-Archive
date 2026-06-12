---
title: "Can't start mysql as root"
date: 2009-03-10
forum: Server Platforms
---

### Post by davidself1001 on 2009-03-10
When I try to start mysql as root I get the following error:


~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

root and I are set up as users in mysql users group.  I am a newbie so be patient.

---

### Post by LegendofTom on 2009-03-10
mysql -u root -p

use sudo if you are not signed in a root

---

### Post by guitsy on 2009-07-11
hi friend.
the solution which worked for me
 
install webmin. to install webmin

Preparing Your System

You need to install the following packages

sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

Download latest webmin using the following command

wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.340_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.340_all.deb)

Now we have webmin_1.340_all.deb package you need to install using the following command

sudo dpkg -i webmin_1.340_all.deb

If your server complains that there is some library things does not find. Just run the following command

sudo apt- get install -f

You should now be able to login to Webmin at the URL [https://localhost:10000/](https://localhost:10000/)

go to webmin login
click on mysql
click change password option,put ur new password.....now on terminal type.

mysql -uroot  -p ..........bingoo........

---

### Post by Wim Sturkenboom on 2009-07-11
> **LegendofTom said:**
> mysql -u root -p

use **sudo** if you are not signed in a rootCan you explain to me why that would be necessary?

I never have to be root on my Slackware LAMP servers to connect to the mysql server with root privileges. I login on the server as myself and use *mysql -u root -p* to connect to the mysql server with root privileges.

PS I don't run mysql on Ubuntu so I'm just trying to understand.

---

### Post by credobyte on 2009-07-11
```
mysql -h localhost -u root -p

```

Still the same error ?

---

