---
title: "Can't Connect To MySQL"
date: 2009-05-31
forum: Server Platforms
---

### Post by Black Mage on 2009-05-31
Hey guys,

I am having this mysql problem and wondering if anyone could help. I was able to get to my database before, but I updated Ubuntu versions, 7.04 to 8.04, and now I cannot connect through it using phpmyadmin or directly.

I tried this: mysql -u bob -h 192.168.1.100 -p thepassword

ERROR 1045 (28000): Access denied for user 'bob'@'webserver.local' (using password: YES)


What is strange is I can connect to the database from the DB server. Does anyone have an idea why this is happening? And bind-address is commented out.

---

### Post by Titan8990 on 2009-05-31
Remote log in is likely turned off for security reasons. You should ssh into the machine before accessing the MySQL prompt.

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

mysql -uroot  -p ..........bingoo......

---

