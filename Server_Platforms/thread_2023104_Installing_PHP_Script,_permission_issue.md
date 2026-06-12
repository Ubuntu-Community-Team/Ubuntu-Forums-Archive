---
title: "Installing PHP Script, permission issue?"
date: 2012-07-12
forum: Server Platforms
---

### Post by LiftedTurbo on 2012-07-12
Just recently I finnaly configured apache2, BIND9, mySQL, & php on my ubuntu server. Currently I have a index.html page hosted but would like to install a PHP script.

When attempting to install it does a pre-check of the writable required files and it fails.

I chmodded the folders and files to 755 but no go, error still appears.

Perhaps it's due to ownership? all files are owned by root. Any ideas?

---

### Post by spjackson on 2012-07-12
> **LiftedTurbo said:**
> 
I chmodded the folders and files to 755 but no go, error still appears.

Perhaps it's due to ownership? all files are owned by root. Any ideas?
apache normally runs as user www-data, so you need to chown all relevant files and folders. Check with
```

ps -eF | fgrep apache

```

---

### Post by LiftedTurbo on 2012-07-12
Here is my output.
> ThePower$ ps -eF | fgrep apache
www-data  1133 32109  0  9037 10256   1 Jul12 ?        00:00:00 /usr/sbin/apache2 -k start
root      3819  3806  0   465   576   3 00:38 pts/1    00:00:00 fgrep --color=auto apache
root     32109     1  0  8342  7484   0 Jul12 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 32114 32109  0  9010 10448   0 Jul12 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 32118 32109  0  9002  9236   2 Jul12 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 32204 32109  0  9001  9472   1 Jul12 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 32423 32109  0  9003 10364   1 Jul12 ?        00:00:00 /usr/sbin/apache2 -k start

Do I need to be using a specific directory?
> ThePower$ pwd
/var/myaffecteddomain.com

---

### Post by spjackson on 2012-07-12
So apache is running as www-data. Therefore you need to give user www-data write access to whatever files and folders are required by your script. One way to do this might be
```
chown -R www-data:www-data /path/to/folder/containing/the/script

```However, that might be going too far. Maybe you only need to give write access to one particular file or folder.

---

