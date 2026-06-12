---
title: "I want to get this fixed"
date: 2005-06-29
forum: Server Platforms
---

### Post by sesstreets on 2005-06-29
The first time I ever saw Ubuntu at work was when a friend gave me a live CD of it, it worked briliantly. This was about 3 months ago, and I have since built a PC for server use, I tried to use XAMMP, but found it annoying that when I went to my domain, I got a login page (I secured it), plus it was on windows 2000. Now I went back to my friend and he gave me one of the install CD's (the ones ubuntu can send you) of Hoary Hedgehog, so i dug up a 7200rpm hard drive and latched it onto my server, then followed the installation on the second hard drive, I liked the fact that I could basically walk away from the installation and check on it every once in a while. I told it to install the boot maneger in case I didn't like it and I could go back to windows if I wanted to. I liked the interface and went right to work making a server, now the server is basically just to host some files and have a forum, and MAYBE sell space on it :smile:,  so I went to ubuntuguide.org and followed the steps to install it using apt-get on a terminal:

[SIZE=1]sudo apt-get install apache2[/SIZE]

Then I installed php4 because I use alot of php scripts:

[SIZE=1]sudo apt-get install php4
sudo gedit /var/www/testphp.php
Insert the following line into the new folder:
<?php phpinfo(); ?>[/SIZE]

Then the first bad signs appeared when I tried to install mySQL:

[SIZE=1]sudo apt-get install libapache2-mod-auth-mysql
sudo apt-get install php4-mysql
sudo /etc/init.d/apache2 restart[/SIZE]

For some reason it didn't want to work...so I decided to try ftp:

[SIZE=1]sudo apt-get install proftpd[/SIZE]

It said something like package proftpd does not exist.

As of right now I would want to start over from scratch, but I am afraid of doing this as I dont know what would happen to the boot loader. So this is my list:

-Get Ubuntu re-installed to start from a clean slate without destroying my windows server on the other hard-drive.

-Get apache2 server up and running.

-Get Php4 installed and working.

-Get mySQL and mySQL control center working.

-Get ftp client up and running.

One more thing, how can I administrate my mySQL servers from another computer? I don't know if phpAdmin works on linux.

And is it possible to do this with that auto package installer that starts with an "S"?

I want to go back to my server (I am not at home right now) with a complete guide on how to get this done. 

Please help

---

### Post by codejunkie on 2005-06-29
did you follow the steps to add extra repositories to your /etc/apt/sources.list file at ubuntuguide [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) the packages your looking for my be on the backports server and it is not added to the /etc/apt/sources.list file by default.

---

### Post by sesstreets on 2005-06-29
ahh i see, so that covers the mysql issue and the proftpd issue...so what about the rest of it?¿

---

### Post by LordHunter317 on 2005-06-29
To get PHP support in Apache2, you need libapache2-mod-php4
For mysql, you need mysql-server-4.1.
phpMyAdmin works on Linux, but I recommend you learn how to use the command tools, and just SSH in and admin.

---

### Post by deBaas on 2005-06-29
[QUOTE=sesstreets]
One more thing, how can I administrate my mySQL servers from another computer? I don't know if phpAdmin works on linux.
[/QUOTE]

Give your topic a deacent title next time please,

to administrate MySQL you could try the webmin module, but running phpmyadim from another pc sould also be possible.

---

### Post by sesstreets on 2005-06-30
[QUOTE=deBaas]Give your topic a deacent title next time please,

to administrate MySQL you could try the webmin module, but running phpmyadim from another pc sould also be possible.[/QUOTE]
 so anybody wanna make a list?

---

### Post by sundancer on 2005-07-05
I think you will use synaptic to install the packages. So the packages are:

" -Get apache2 server up and running: "

[list]
[*] apache2
[*] apache2-mpm-prefork
[*] apache2-doc
[/list] 

" -Get Php4 installed and working: "

[list]
[*] libapache2-mod-php4
[*] php4-mysql
[/list]

" -Get mySQL and mySQL control center working: "
[list]
[*] mysql-server-4.1
[/list]

" -Get ftp client up and running: "
Don't know what ftp-client you like - perhaps you try
gftp-gtk

OK. After installing the packages, they need to be configured. For apache2 the php4 related config consists of creating two symlinks:
```

cd /etc/apache2/mods-enabled
sudo ln -s /etc/apache2/mods-available/php4.conf .
sudo ln -s /etc/apache2/mods-available/php4.load .

```

Then the php4-module will work - you could test this with your phpinfo()-example

For mysql edit /etc/php4/apache2/php.ini (The mysql config section should already be there, but you have to enable the mysql extension be inserting the following
```

extension=mysql.so

```

phpinfo should show the new extension after reloading apache2  :grin: 

Now for phpmyadmin (i guess you know which package you need to install  :wink: ):
It will work out-of-the-box and be available under [http://yourhostname/phymyadmin](http://yourhostname/phymyadmin)

That's it

If there are problems - just ask  :-P

---

