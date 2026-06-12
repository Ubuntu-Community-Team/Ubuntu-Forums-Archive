---
title: "Ubuntu 14.04 - PHP Not Working"
date: 2014-04-27
forum: Server Platforms
---

### Post by Asif_Ahmad on 2014-04-27
Hello,

I recently installed a fresh version of Ubuntu 14.04 (desktop, but using it as server) and have tried to get LAMP working. I used the following guide:
[https://www.digitalocean.com/community/articles/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu](https://www.digitalocean.com/community/articles/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu)

However, when I try going to my php.info page ([http://localhost/info.php](http://localhost/info.php)), I get a 404.  When I hit localhost directly, I get the correct apache test-page.  

Any ideas? TIA



Thanks,
Asif

---

### Post by CharlesA on 2014-04-27
Where did you put info.php ? It should go in /var/www/

---

### Post by Asif_Ahmad on 2014-04-27
Correct, that's what I did:

aahmad@ubuntu-desktop:/var/www$ ll
total 16
drwxr-xr-x  3 root root 4096 Apr 27 11:10 **.**/
drwxr-xr-x 14 root root 4096 Apr 27 00:37 **..**/
drwxr-xr-x  2 root root 4096 Apr 27 00:37 **html**/
-rwxrwxr-x  1 root root   20 Apr 27 11:10 **info.php***

---

### Post by lisati on 2014-04-27
I read somewhere recently (citation needed) that the default location has moved in 14.04 from /var/www to /var/www/html.

---

### Post by pqwoerituytrueiwoq on 2014-04-27
one way to find out
```
cat /etc/apache2/sites-enabled/* | grep 'var/www'
```
if it says /var/www/html lisati has your issue correct

---

### Post by SeijiSensei on 2014-04-27
In 14.04, with Apache 2.4, the DocumentRoot has changed to /var/www/html.  See /etc/apache2/sites-available/000-default.

That is the same location that RedHat-flavored servers have used for years.  I'm actually quite happy about this development, because I like to put other directories under /var/www that the webserver user ("www-data" on Ubuntu) can see, but that are outside the directories visible over the web.

---

### Post by Asif_Ahmad on 2014-04-27
That was it!  This was the output of the command:

aahmad@ubuntu-desktop:~$ cat /etc/apache2/sites-enabled/* | grep 'var/www'
	DocumentRoot /**var/www**/html

I moved the info.php file to the html directory, and the PHP Info page started working correctly.

Thanks a bunch [[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]]("http://ubuntuforums.org/member.php?u=865458")[COLOR=#000000] and [/COLOR][lisati]("http://ubuntuforums.org/member.php?u=327635")[COLOR=#000000], you guys rock!  =)
[/COLOR]

--Asif

---

### Post by CharlesA on 2014-04-27
> **SeijiSensei said:**
> In 14.04, with Apache 2.4, the DocumentRoot has changed to /var/www/html.  See /etc/apache2/sites-available/000-default.

That is the same location that RedHat-flavored servers have used for years.  I'm actually quite happy about this development, because I like to put other directories under /var/www that the webserver user ("www-data" on Ubuntu) can see, but that are outside the directories visible over the web.

Good to know. Thanks!

---

### Post by Asif_Ahmad on 2014-04-27
Thanks for the update **SeijiSensei!**

---

