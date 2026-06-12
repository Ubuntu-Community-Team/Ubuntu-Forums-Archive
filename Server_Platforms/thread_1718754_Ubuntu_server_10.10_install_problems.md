---
title: "Ubuntu server 10.10 install problems"
date: 2011-03-31
forum: Server Platforms
---

### Post by zhuanga on 2011-03-31
I am the first time to install Ubuntu server 10.10 to a core 2 PC. (I used Centos 5.1 before). 
I choose to install the following server packages:
LAMP
samba
mail
manul package selection
I followed install instructions and entered the Internet porxy name e.g. [http://pwodu3:8080/](http://pwodu3:8080/) and the mail server name: pwodu2 (I intend to foward emails to the mail server "pwodu2" to send out.
Here are the problems:
1. after I complete the installation and reboot, I can login but only in consol
2. can not ping out, so I can not get to internet, although Ethernet is OK
3. the arrow key not working, so I can not repeat history command (I checked keybaord mapping, which is fine.)
4. "command tab completion" not working
5. I do: $ find / -name "*" | xargs grep pwodu3
find the file /etc/apt/apt.conf containing the proxy name "pwodu3"
thre is no /etc/X11/xorg.conf file
The delima is: I want to get graphic windows, but cannot access internet to download and install. Please help!
My email: [EMAIL="zhuanga@hotmail.com"]zhuanga@hotmail.com[/EMAIL]
Thanks!

---

### Post by egpetrich on 2011-04-02
I don't believe that you will get any type of graphical interface (like X or Gnome) installed by default with Ubuntu Server. Most would recommend that you not install a graphical interface because of the space and processing overhead that it requires. Still, it's your decision.

If you can't reach the Internet, I'd suspect that something is wrong with your network setup. (I'm not sure what you mean when you say that your Ethernet is okay.) Can you post the results of these commands?

```
cat /etc/network/interfaces
ifconfig -a
route
```

---

### Post by Adrianna_2 on 2011-04-02
> **zhuanga said:**
> I followed install instructions and entered the Internet porxy name e.g. [http://pwodu3:8080/](http://pwodu3:8080/) 
That link dont work (take a look at Screenshot bellow)
> **zhuanga said:**
> The delima is: I want to get graphic windows, but cannot access internet to download and install. Please help! 
As @egpetrich said, "you will NOT get any type of graphical interface (like X or Gnome) installed by default with Ubuntu Server"

> **zhuanga said:**
> I followed install instructions and entered the Internet porxy name e.g. [http://pwodu3:8080/](http://pwodu3:8080/) 
That link does not work (take a look at Screenshot bllow
> **zhuanga said:**
> The delima is: I want to get graphic windows, but cannot access internet to download and install. Please help! 
As @egpetrich said, "you will NOT get any type of graphical interface (like X or Gnome) installed by default with Ubuntu Server"

In order to administrated your server (with a graphical interface), you have to install some admin tool (like webmin), then you will be able to access your server with a "graphical interface" from a diferent (computer) on your own LAN or from internet.. pointing to server [https://IP_OR_DOMAIN-NAME:10000/](https://IP_OR_DOMAIN-NAME:10000/) and login with your webmin root acccount

---

### Post by gordintoronto on 2011-04-02
The other option is to install Ubuntu Desktop, then install the server components you want. If it's a low-volume server, it should work just fine. I have used that approach for web site development.

---

### Post by zhuanga on 2011-04-04
Thanks to all!

After I tried 3 times of installing Ubuntu server version 10.10 for 64bit, the problems are consistent. I can access LAN, but even I correctly configured proxy, I was not able to get internet. 

So I decided to install Ubuntu desktop 10.10 for 64bit, and it works fine. All the previous problems have been solved. Then, I installed server packages, like mySQL with postfix, web server, apache2, Bugzilla,  and other perl modules.

However, I am stuck on the "mod_perl2". When I using the command to check loaded apache modules:

$ /usr/sbin/apache2 -t -D DUMP_MODULES
apache2: bad user name ${APACHE_RUN_USER}

Do not know why. Looks like my apache2 configure has problem. Previously, I did executed:
$ sudo ./checksetup.pl  --check-module
and it finished successfully.

I also searched for the "mod_perl2" for 64bit PC, I do not find it and it seems I have to download the source code and compile it in my PC.

Any suggestions are greatly appreciated.

P.S.
I have the following apache2 modules installed:
- apache2
- apache2-mpm-worker
- apache2-utils
- apache2.2-bin
- apache2.2-common

Andy

---

### Post by usatonycuba on 2011-04-05
In order to install LAMP server, with Ubuntu desktop ev. type at terminal 
```
sudo apt-get install lamp-server^
```Then install phpmyadmin
```
sudo apt-get install libapache2-mod-auth-mysql phpmyadmin
```and you will just fine from there

Edited:
Mi postfix installation have come with this other's too ;)

```
aptitude install postfix postfix-mysql postfix-doc mysql-client mysql-server mysql-client libmysqlclient16-dev courier-authdaemon courier-authlib-mysql courier-pop courier-pop-ssl courier-imap courier-imap-ssl postfix-tls libsasl2-2 libsasl2-modules libsasl2-modules-sql sasl2-bin libpam-mysql openssl phpmyadmin apache2 libapache2-mod-php5 php5 php5-mysql libpam-smbpass 
```

---

### Post by zhuanga on 2011-04-05
Thanks [usatonycuba]("http://ubuntuforums.org/member.php?u=1243134")!

I followed your suggested commands and installed modules. However, when it starts to config with a UI, it comes with the following error:
An error occurred while installing the database:                   
 &#9474;                                                                          
 &#9474; ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using      
 &#9474; password: YES)

I tried my passwords, but the same error comes again and again. I do not know I have ever created password for "root", since in Ubuntu, there is no specific root user, but only when I do "sudo".
Now I am stuck on this. Any solution?
Thanks in advance!

P.S.
I also run the third command you suggested to reinstall all, after that, I run
$ sudo ./checksetup.pl  --check-module

it shows two errors:
run-parts --exit-on-error --lsbsysinit /etc/bugzilla3/pre-checksetup.d
run-parts --exit-on-error --lsbsysinit /etc/bugzilla3/post-checksetup.d

and there is still the error of:
$ /usr/sbin/apache2 -t -D DUMP_MODULES
apache2: bad user name ${APACHE_RUN_USER}

---

### Post by zhuanga on 2011-04-05
I did some investigation again and found at least I have following issues:

1. apache2
/usr/sbin/apache2 --> /usr/lib/apache2/mpm-prefork/apache2*    //a soft link to binary file
/etc/init.d/apache2    //a sh script that defines apache2 directory to /etc/apache2
under /apache2 there are apache2.conf, which I modified to set:
ServerRoot "/etc/apache2"
ServerName "localhost"
the httpd.conf is empty file. the "envvars" set all environ variables.
However, after I do /etc/init.d/apache2 -k restart or reboot the PC, it seems the files under /etc/apache2 never get called. So the error happens with the following:
$ /usr/sbin/apache2 -t -D DUMP_MODULES
apache2: bad user name ${APACHE_RUN_USER}  	

I do not know why and how to fix it.

2. Database
As in my previous post, I got:
while installing the database:                   
 &#9474;                                                                          
 &#9474; ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using      
 &#9474; password: YES)

3. Bugzilla
$ sudo ./checksetup.pl  --check-module

it shows two errors:
run-parts --exit-on-error --lsbsysinit /etc/bugzilla3/pre-checksetup.d
run-parts --exit-on-error --lsbsysinit /etc/bugzilla3/post-checksetup.d

Anyone help please. Thanks!

---

### Post by zhuanga on 2011-04-05
I searched apache2 site, there is no step by step setup instructions. Right now, the /etc/apache2/httpd.conf is empty, but will be read by httpd when starts. I copied apache2.conf to it, but did not work with many errors. any example of the file?
Thanks!

---

### Post by usatonycuba on 2011-04-06
> **zhuanga said:**
> I searched apache2 site, there is no step by step setup instructions. Right now, the /etc/apache2/httpd.conf is empty, but will be read by httpd when starts. I copied apache2.conf to it, but did not work with many errors. any example of the file?
Thanks!

The Debian and hence Ubuntu apache2 used apache2.conf, not httpd.conf... so httpd.conf is suppose to be empty .. in the other hand.. to be honest, I think you've mis-configured your configuration files in your apache server, you try not to do or change to everything you read on the net without first understand why and what happens "if", and you should always --- at least keep a copy of your original file..

My suggest to you, is that you better make a complete uninstall of your LAMP before reinstall back again from scratch (the whole LAMP... apache-mysql-phpmyadmin ....and the common files)

Then....
> **usatonycuba said:**
> In order to install LAMP server, with Ubuntu desktop ev. type at terminal 
```
sudo apt-get install lamp-server^
```Then install phpmyadmin
```
sudo apt-get install libapache2-mod-auth-mysql phpmyadmin
```and you will just fine from there

---

