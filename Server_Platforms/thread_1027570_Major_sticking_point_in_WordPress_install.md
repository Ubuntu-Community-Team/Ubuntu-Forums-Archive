---
title: "Major sticking point in WordPress install"
date: 2009-01-01
forum: Server Platforms
---

### Post by PaulFXH on 2009-01-01
I'm using UbuntuEee 8.04.1 on an Asus EeePC 901 and in general it works very well.
However, I'm now trying to install WordPress using this [guide]("https://help.ubuntu.com/community/WordPress"). I have used this [additional guide]("https://help.ubuntu.com/community/ApacheMySQLPHP") to install the Lamp server and to configure all of the components (apache2, php5 and MySQL). 
As far as I can tell, I followed the guides to the letter and no error messages were received during the setup.
However, when I try to  install Wordpress in the /wordpress directory of the default web site ([http://localhost/](http://localhost/)) using these commands:
```
sudo ln -s /usr/share/wordpress /var/www/wordpress
``` 

```
sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n paul localhost
```
```
sudo /etc/init.d/apache2 restart
```
and then try to browse to [http://localhost/wordpress](http://localhost/wordpress), I get a 404 saying that [http://localhost/wordpress](http://localhost/wordpress) doesn't exist.
Can anybody please explain to me where I'm slipping up?

---

### Post by q.dinar on 2009-01-01
hello.

have you installed wordpress from repository?

and there is also better >edit: (i feel it better for me)< way to install web-scripts: download latest wordpress from wordpress site and uncompress it to /var/www/wordpress , but this way you should learn and apply proper permissions to some directories or files (or at least simply to all subdirectories and files in them) (so that apache("www-data" user) can write to them).

---

### Post by PaulFXH on 2009-01-01
Thanks for your reply.
> **q.dinar said:**
> 
have you installed wordpress from repository?
Yes, I did but I'm really not sure this is the cause of my immediate problem.
The problem is that, following [this guide]("https://help.ubuntu.com/community/WordPress"), I followed EXACTLY these steps
> The following will install Wordpress in the /wordpress directory of your default web site. To put it somewhere else, alter these commands to suit. 

sudo ln -s /usr/share/wordpress /var/www/wordpress 

sudo sh /usr/share/doc/wordpress/examples/setup-mysql -n (your mysql user) localhost # use bash instead of sh on Gutsy

sudo /etc/init.d/apache2 restart
However, Wordpress was NOT installed in [http://localhost/](http://localhost/). Nevertheless, the directory /var/www/ does contain a wordpress folder with all the necessary files/folders within this.
My question is "Why did following the steps in the quote above, not lead to the stated objective ie. install Wordpress in the /wordpress directory of the default web site?"
I believe I have messed up somewhere in the configuration of something or other rather than it being a fault of the version of Wordpress I installed.

---

### Post by q.dinar on 2009-01-02
"sudo ln -s /usr/share/wordpress /var/www/wordpress"
command should create not real, only like shortcut in windows "wordpress" folder in /var/www/ . for that is created and work it should exist in /usr/share . check it. i have not tried to install wordpress from repo. that folder should appear after that installation. do you write that commands in terminal? not in little window to write commands (applet)? if in terminal,after that commands are entered to run you can see error messages if there was.

---

### Post by PaulFXH on 2009-01-03
Thanks again for your reply.
However, the problem was that I had already changed my default site from /var/www to /home/paul/public_html as indeed is suggested in this [guide]("https://help.ubuntu.com/community/ApacheMySQLPHP").
So, therefore, the symlink
```
sudo ln -s /usr/share/wordpress /var/www/wordpress
```
didn't do anything useful.
However, when I made the following symlink
```
sudo ln -s /usr/share/wordpress /home/paul/public_html/wordpress
```
everything worked out fine. :P

---

