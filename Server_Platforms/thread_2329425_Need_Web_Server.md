---
title: "Need Web Server"
date: 2016-07-01
forum: Server Platforms
---

### Post by Mir_Ahmed on 2016-07-01
I have installed Ubuntu 16.04 I am new in ubuntu can i convert my ubuntu 16.04 to a Web server to host my domain  I need your help, can i meke this ubuntu an appache server please help me

---

### Post by howefield on 2016-07-01
Moved to the "*Server Platforms*" forum.

---

### Post by nerdtron on 2016-07-01
> **Mir_Ahmed said:**
> I have installed Ubuntu 16.04 I am new in ubuntu can i convert my ubuntu 16.04 to a Web server to host my domain  I need your help, can i meke this ubuntu an appache server please help me

Yes, of course you can. You just need to install the apache package. And you'll need to point your domain to your Ubuntu server IP.

There are a lot of things that will be needed to configure. What steps have you done so far?

---

### Post by DuckHook on 2016-07-01
:confused:

I am confused by this request: It seems that what you are asking for is a little bit like asking for instructions to build an airplane from scratch. While these forums are great for answering specific questions, they don't function well as guides or tutorials. If you are new to Ubuntu and your expertise level is that of a new user, then the level of explanation and education needed to get you to the point of building and configuring a web server is likely beyond the scope of these forums.

What would be more helpful to you is a tutorial. Try the following one for starters:
[https://www.howtoforge.com/tutorial/install-apache-with-php-and-mysql-on-ubuntu-16-04-lamp/](https://www.howtoforge.com/tutorial/install-apache-with-php-and-mysql-on-ubuntu-16-04-lamp/)

Though a little dated, the following Wiki will also prove useful:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Mir_Ahmed on 2016-07-02
I am new to ubuntu kindly send me a documentation of apache2 in ubuntu budlding a basic cloud server i have domain and i have domain but not hosted yet i want to host it on my ubuntu on my machine, my machine configuration is HP Elite 8000 2.6 GHZ 8.MB Cashe 4GBRAM 500GB HARD DRIVE

Now I am going to install APache2 through terminal i have updated my system ubuntu updates are upto date

and also i need to develop my website in WordPress

I am using this link to install apache server
[https://help.ubuntu.com/lts/serverguide/httpd.html](https://help.ubuntu.com/lts/serverguide/httpd.html)

I have installed PHP7, MysQl 5.6, APache 2 all is working and auto start enable on logon but phpmyadmin not opening please help me i have installed phpmyadmin then used this code for access of phpmyadmin but not opening 

[LIST]
[*]sudo phpenmod mcrypt 
[*]sudo phpenmod mbstring 
[/LIST]

when i go to open the phpmyadmin not opening and giving me error " FIle Not Found"
Installing PHPMyadmin from this tutorial 
[https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-16-04)

---

### Post by Graham_Willis on 2016-07-02
Can you give us the exact address that you use in order to check if phpmyadmin functions properly?

If not, let us assume that it is of the form **https**://domain_name/phpmyadmin . Then:


[LIST=1]
[*] Please check if **http**://domain_name/phpmyadmin loads properly, 
[*]Please check if **http**://IP/phpmyadmin load properly, 
[*]If the above fails pelase try **http**://domain_name and **http**://IP 
[/LIST]

Then tell us what you got out of these 3 tests.

---

### Post by Mir_Ahmed on 2016-07-03
i have tried all but not working error is "file not found" [http://localhost](http://localhost) working but when i go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) then not opening my php admin dashboard

---

### Post by Graham_Willis on 2016-07-05
OK. Please check if you have the following files:

[B]/etc/apache2/conf-available/phpmyadmin.conf
/etc/apache2/conf-enabled/phpmyadmin.conf[/B]

If not, please **cd /etc/apache2** and then **grep -Rli phpmyadmin *** .

Tell us about the results.

I just installed phpmyadmin on my Ubuntu machine and it works, so I'm convinced that it should be possible to do.

---

### Post by mastablasta on 2016-07-07
if you have trouble setting it all up, you can slap this:[https://bitnami.com/stack/wordpress/virtual-machine](https://bitnami.com/stack/wordpress/virtual-machine)

or this: 
[https://www.turnkeylinux.org/wordpress](https://www.turnkeylinux.org/wordpress)

on your server machine, set up the domain and get on with your work.

---

