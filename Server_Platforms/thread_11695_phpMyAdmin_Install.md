---
title: "phpMyAdmin Install?"
date: 2005-01-18
forum: Server Platforms
---

### Post by Dissonance on 2005-01-18
Well, I've installed mysql according to the [Ubuntu Starter Guide](http://ubuntuguide.org/).  After that, I downloaded the package for phpMyAdmin, and extracted it to my Apache web root.  The thing is...  I can't get it to connect.  I thought the default credentials for the root account was

username: root
password: *blank*

But, it keeps saying:

> Welcome to phpMyAdmin 2.6.0-pl3

Error

MySQL said: Documentation
#2002 - Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Ok, now that I've got the situation explained, I'll ask my questions.

1. What ARE the default credentials?  (Since they aren't "root with no password")

2. What is this file? (/etc/mysql/my.cnf)  It has a place for a password, but I don't know what that does.  

3. How can I restart my MySQL server?

---

### Post by tidalwav1 on 2005-01-20
[QUOTE=Dissonance]Well, I've installed mysql according to the [Ubuntu Starter Guide](http://ubuntuguide.org/).  After that, I downloaded the package for phpMyAdmin, and extracted it to my Apache web root.  The thing is...  I can't get it to connect.  I thought the default credentials for the root account was

username: root
password: *blank*

But, it keeps saying:



Ok, now that I've got the situation explained, I'll ask my questions.

1. What ARE the default credentials?  (Since they aren't "root with no password")

2. What is this file? (/etc/mysql/my.cnf)  It has a place for a password, but I don't know what that does.  

3. How can I restart my MySQL server?[/QUOTE]
 You need to edit the config.inc.php file in the phpMyAdmin directory. Make sure the 'auth_type' option is set to 'config'. Under that, enter in the username root, and under that, enter whatever your root password is. (If you don't have one, set one using 'sudo passwd'.) phpMyAdmin should work, then--(you shouldn't need to restart mySQL), create a new mySQL user using the phpMyAdmin interface, then change your settings in config.inc.php to reflect the new user and password. If it doesn't work, try installing phpMyAdmin from a clean install, in case you accidentally tinkered with other files. Here is info about starting/restarting/stopping mySQL:

Start MySQL server:
# /etc/rc.d/init.d/mysqld start
Stop MySQL:
# /etc/rc.d/init.d/mysqld stop
Restart MySQL:
# /etc/rc.d/init.d/mysqld restart

---

### Post by az on 2005-01-20
In the mysql docs, it says all you need do is set the root password with:

mysqladmin -u root password "mypassword"

You should be good to go...


"enter whatever your root password is. (If you don't have one, set one using 'sudo passwd'.)"

I do not understand - we are not talking about the same root...

Your root user and your root mysql user are not the same...

---

### Post by tidalwav1 on 2005-01-20
[QUOTE=azz]In the mysql docs, it says all you need do is set the root password with:

mysqladmin -u root password "mypassword"

You should be good to go...


"enter whatever your root password is. (If you don't have one, set one using 'sudo passwd'.)"

I do not understand - we are not talking about the same root...

Your root user and your root mysql user are not the same...[/QUOTE]

I know what you mean about the root deal, but somehow, doing that got my mySQL setup working. ::shrugs::

---

### Post by jdong on 2005-01-20
Maybe dumb question, but did you **apt-get install mysql-server**? ;) I've forgotten that before.

Do make sure that MySQL's server is started, as mentioned above. Did you know that phpmyadmin is already packaged via APT? **apt-get install phpmyadmin**.

---

### Post by Dissonance on 2005-01-21
[QUOTE=jdong]Maybe dumb question, but did you **apt-get install mysql-server**? ;) I've forgotten that before.

Do make sure that MySQL's server is started, as mentioned above. Did you know that phpmyadmin is already packaged via APT? **apt-get install phpmyadmin**.[/QUOTE]
 Thanks for the replies everyone.  I deleted the version I had downloaded, and tried it again under apt-get install.  It installed into the same place that I had the other, but it still had the same problem.  I tried what tidalwave said, and it worked.  So, I was happy about that.  I'm thinking about dropping all these different packages and getting XAMPP for Linux.  It offers a lot more for a lot less effort.  Then again, I used to use EasyPHP under Windows, so I'm a sucker for those "do-it-all" server packages.

---

### Post by Daiver on 2006-07-07
> **azz said:**
> In the mysql docs, it says all you need do is set the root password with:

mysqladmin -u root password "mypassword"



Thanks for this.  Ive been searching like crazy for it and I couldn't find it anywhere.

---

### Post by nihilocrat on 2006-07-07
> **Daiver said:**
> Thanks for this.  Ive been searching like crazy for it and I couldn't find it anywhere.

Never forget the power of tab-completion and manpages.

---

### Post by Newmaniese on 2007-02-14
Thanks for the thread. Why would I have problems with the apt-get install phpmyadmin ? It can't find the package?

---

### Post by bkudrle on 2007-06-05
I second the problem with apt-get not finding phpmyadmin. I am using the server version 7 of Ubuntu. Any ideas?

---

### Post by supernicko on 2007-06-08
It found it for me no problems. Do you have mutliverse and universe repositories?

---

### Post by bkudrle on 2008-02-02
Yes, it turned out I did not  have universe and multiverse enabled. 

To do that, I had to do the following. 

1. Edit the /etc/apt/sources.list file and made the line look like this:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main universe multiverse restricted

(note that by default the universe, multiverse and restricted were not on the line)

2. apt-get update

This updated the packages with those from universe, multiverse and restricted. 

3. apt-get install phpmyadmin

Then I could  execute http://<my ip address>/phpmyadmin

Great!

---

### Post by Rick Z on 2008-02-15
Thank everyone... I am able to install the phpmyadmin using apt-get, but I have a questions.... 

How do I enable the SSL([https://)](https://)) after install phpmyadmin via 'apt-get instal phpmyadmin'?

---

### Post by Kumera on 2008-02-28
I have followed all the instructions and, as far as I can tell, Apache, PHP and MySQL are working fine in my Ubunto Gutsy.  If I run 'sudo apt-get install phpmyadmin' I am told that it is already installed.  But if I go to 'localhost/phpmyadmin' to try and find it, I get the 404 message:
' Not Found
The requested URL /phpmyadmin was not found on this server."

I must be missing something.

---

### Post by DarkWater on 2008-02-29
You need to add it to the Apache config files because it only installs a link to the folder in the /var/www/ folder.  I'll find the lines that you need in a minute.

---

### Post by shichuan on 2008-03-03
Add the following line of code inside apache2.conf:
Include /etc/phpmyadmin/apache.conf

here is an article that explains it in details:
[http://www.blog.highub.com/uncategorized/install-and-configure-phpmyadmin-on-ubuntu-lamp/]("http://www.blog.highub.com/uncategorized/install-and-configure-phpmyadmin-on-ubuntu-lamp/")

hope it helps! :)

---

