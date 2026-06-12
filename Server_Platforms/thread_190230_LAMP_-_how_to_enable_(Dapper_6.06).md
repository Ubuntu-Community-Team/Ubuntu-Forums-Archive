---
title: "LAMP - how to enable (Dapper 6.06)"
date: 2006-06-06
forum: Server Platforms
---

### Post by skafiskafnjak on 2006-06-06
I installed server version of Dapper. 
There is few things that I do not understand and need help.

- Is LAMP installed by default if Server option is selected during the installation process?

- If so how do I start it because if I type [http://192.168.0.2](http://192.168.0.2) or [http://localhost](http://localhost) from other computers in network nothing heppend..

If I log-in via SSH and try to execute  **/etc/init.d/apache2 start** i got "No such file or directory".

Also I can not enter into **/etc** or any toher directory by typing **cd \** "No usch file or directory".

What I am missing?

---

### Post by skafiskafnjak on 2006-06-06
It says here:

> In about 15 minutes, the time it takes to install Ubuntu Server Edition, you can have a LAMP server up and ready to go. This feature, exclusive to Ubuntu Server Edition, is available at the time of installation.

So it should be installed..

> A key lesson from the Debian heritage is that of security by default. The Ubuntu Server has no open ports after the installation and contains only the essential software needed to build a secure server.

Does it mean that I need to open port 80 to be able to access Apache?

Still I am confused... please help.

---

### Post by az on 2006-06-06
Did you select the LAMP option when you booted the server installer?

If not, just install apache, mysql and php.  You will end up with exactly the same thing.


sudo apt-get install apache2 php5 mysql-server
(I beleive those are the packages...)

---

### Post by hagen00 on 2006-06-06
and a couple of other things you'll need to install...

sudo apt-get install libapache2-mod-php5 php5-mysql php5-gd

before you apt-get install, do an apt-cache search and type in those name to verify that I got them correct.

---

### Post by skafiskafnjak on 2006-06-06
Is there a diference in commands if I need PHP4 instead of PHP5?

Also I did not see LAMP option during the boot process....  ??????

---

### Post by Randomskk on 2006-06-06
The LAMP boot option is only from the server CD, not the Ubuntu Desktop one.

---

### Post by skafiskafnjak on 2006-06-06
I installed from the disk where is OEM, Text, and Server version available.

I installed server version and now I see command line only.

Is there another installation CD for server only that i am missing?

Also how do I check if LAMP is already installed?

---

### Post by Randomskk on 2006-06-06
Unless you've install the programs in LAMP - Apache2, PHP, MySQL - LAMP is not installed.
It sounds like you installed from the Alternate Install disk, that's fine, but to get the LAMP option at bootup you use the server CD.

Don't worry, though, as already said in this thread you can just use apt-get to install the LAMP apps on your current install.

---

### Post by skafiskafnjak on 2006-06-06
>  but to get the LAMP option at bootup you use the server CD.

Yes I installed from alternate disk, where do I download server disk?

---

### Post by skafiskafnjak on 2006-06-06
Done!

Now, what should I do in order to be able to access server with FTP?

(like when you purchase hosting you can access root directory with FTP)

????

---

### Post by DjDarkman on 2006-06-07
You need to install an ftp deamon to be able to acces the server via ftp protocol ,for example you can install proftpd : **sudo apt-get install proftpd**

---

### Post by adamkane on 2006-06-07
Easy way to install LAMP + phpmyadmin:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by skafiskafnjak on 2006-06-07
Installed LAMP and VSFTPD.

Using SCP to manage files.

Thanks all

---

### Post by s0me0ne on 2006-06-10
I installed using the server version, and realized i dont know how to use the command prompt and stuff, so i reinstalled using the Desktop verison  and so I tried the following code:

```
sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql
```

it gave me some error saying it couldnt find PHP4 but the rest seemed to work. 

[SIZE="4"]**So how do i get PHP4 and after that how do i get the rest setup?**[/SIZE]

Yes I have to use the desktop version because I need a GUI, im just doing some basic testing of web stuff in Ubutu Dapper Drake, I dont plan to be a linux guru

---

### Post by nommo on 2006-06-19
[QUOTE=adamkane]
Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```
[/QUOTE]
Do I need to add another repository apart from the default ones in /etc/apt/sources.list ??


Even with all those uncommented I am getting:
```

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package phpmyadmin

```

I am sure there will be a recipe 'out there' for installing phpMyAdmin manually, but - hey this is the 21st century :-)

---

### Post by Jeruvy on 2006-06-19
Well I'm at this phase.  I've downloaded the phpmyadmin to another machine but now stuck trying to copy the file over to ubuntu.  I suppose I could just wget it on the ubuntu box also...but this shouldn't be a problem.

I don't have any active shares or nfs running between the server and the desktops and I want to leave it that way.  I'll install vsftpd if that helps me get big files over for installation.  

Now I would typically login via SFTP or SCP via SSH, and copy files, but for some reason doing this simply causes the connection to hang until the server simply stops responding to anything and needs to be rebooted.

Ideas?

---

