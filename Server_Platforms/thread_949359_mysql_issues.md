---
title: "mysql issues"
date: 2008-10-16
forum: Server Platforms
---

### Post by sil3nt on 2008-10-16
Hi guys,
        I have just recently tried to upgrade opsview and I have run into an error trying to configure the database. During install when asking for the root@localhost mysql password it fails.

I have reset my sql root password thinking that would solve the issues but it seems that there are still problems:

```
Setting up opsview-core (2.14.0.1543-1) ...
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
Failed to connect to database

``` 

Any suggestions ? It says above using password (NO) but if I don't use the correct PW when prompted it re-prompts until its correct then I get this output.

Cheers in Advance

---

### Post by Drezard on 2008-10-16
it shows in this line:

> 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)


The (using password: NO) means what ever you are trying to do, you haven't entered in a password. What exactly are you trying to do?

Daniel

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

