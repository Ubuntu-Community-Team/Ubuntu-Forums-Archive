---
title: "php does not parse phpmyadmin"
date: 2007-04-05
forum: Server Platforms
---

### Post by holbech on 2007-04-05
Hi there just finished installing a LAMP setup, well almost, I cant get phpmyadmin to work, whenever I enter the directory (at [http://192.168.1.12/phpmyadmin](http://192.168.1.12/phpmyadmin)) it tells me to "download the phtml file"

I've probably messed up something with symlinks along the way to, but I'm not sure thats the problem

here's pretty much what I did:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ssh openssh-server

sudo apt-get install apache2 php5 libapache2-mod-php5

sudo nano /var/www/test.php
#works

sudo apt-get install mysql-server mysql-client php5-mysql

sudo wget http://prdownloads.sourceforge.net/webadmin/webmin-1.330.tar.gz
tar xvfz webmin- TAB

sudo ./setup.sh /usr/local/webmin

mysql -u root
UPDATE mysql.user SET Password=PASSWORD('newpasswordhere') WHERE User='root';
FLUSH PRIVILEGES;
exit

http://prdownloads.sourceforge.net/phpmyadmin/phpMyAdmin-2.10.0.2-all-languages-utf-8-only.tar.gz?download
sudo tar xvfz php TAB
mv phpMyAdmin-TAB phpmyadmin

```

Everything else works fine... but not phpmyadmin 
I did install phpmyadmin through apt-get at som point, but removed it again
I did restart apache (several times)
Any clues?

btw: how do I enable the locate command? it doesn't work

Cheers
J

---

### Post by shufla on 2007-04-24
Hello,

Start apache and look in /var/log/apache2/error.log for its header - is there PHP module enabled?

Install phpmyadmin from repositories and reconfigure it with dpkg-reconfigure -plow phpmyadmin. Use dpkg -S phpmyadmin to check installed files - there shall be some in /etc, and linked into apache2 configuration directory.

Bye,
Luke

---

### Post by nityananda on 2008-03-29
I am using Ubuntu Gutsy and phpmyadmin started to do same thing.

I found that it started after activation of APC extenstion for php.

After deactivating apc.so phpmyadmin works again good.

---

