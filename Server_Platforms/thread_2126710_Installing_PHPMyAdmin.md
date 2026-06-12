---
title: "Installing PHPMyAdmin"
date: 2013-03-18
forum: Server Platforms
---

### Post by Maurices5000 on 2013-03-18
Here are my instructions: "You will need to download, read, and follow the instructions to install phpMyAdmin... Include in your httpd.conf file a section for the phpMyAdmin directory to password protect it so that any valid user can access it."

I've found instructions on installing PHPMyAdmin, but none of them include an httpd.conf file.

I found some instructions here on how to do it:
[https://www.digitalocean.com/community/articles/how-to-install-and-secure-phpmyadmin-on-ubuntu-12-04](https://www.digitalocean.com/community/articles/how-to-install-and-secure-phpmyadmin-on-ubuntu-12-04)

I also found these instructions:
[http://www.webrichsoftware.com/?p=16](http://www.webrichsoftware.com/?p=16)

The bottom article actually has the apt-get command I'm supposed to use** sudo apt-get install libapache2-mod-auth-mysql phpmyadmin**. The first one just uses **sudo apt-get install phpmyadmin**. I really don't know what the difference is, but the first one also has some info on security even though its not applied to httpd.conf.

Thanks very much!

---

### Post by slickymaster on 2013-03-18
**httpd.conf** is a configuration file used by the Apache HTTP Server. It stores information on various functions of the server, which can be edited by removing or adding a number sign "**#**" at the beginning of the line, thus setting values for each directive.

As for the installation, you can follow [this]("https://help.ubuntu.com/community/phpMyAdmin").

---

### Post by Maurices5000 on 2013-03-18
Thanks!  My **httpd.conf **is empty.  I saw online where someone just added a DIRECTORY container and put some directives the same as say 000-default.  

I was told to use [B]sudo apt-get install libapache2-mod-auth-mysql phpmyadmin. 
[/B]What's the difference between that and [B] [B]sudo apt-get install phpmyadmin?

[/B][/B]I don't know enough to risk messing anything up.

Thanks!

---

### Post by lisati on 2013-03-19
> **Maurices5000 said:**
> 
I was told to use [B]sudo apt-get install libapache2-mod-auth-mysql phpmyadmin. 
[/B]What's the difference between that and [B] [B]sudo apt-get install phpmyadmin?

The first installs both a mod for apache that lets it use mysql and phpmyadmin. The second only installs phpmyadmin.

---

### Post by Maurices5000 on 2013-03-19
Thanks for the clarification!

 I looked in mods-available and I did not see phpMyadmin. Is that normal? am I doing something wrong? What should i do?

Sorry if my questions seem a bit stupid. Where do i run these commands?

Thanks

---

### Post by lisati on 2013-03-19
Some basic information about installing and using phpmyadmin with Ubuntu 12.04 can be found at [https://help.ubuntu.com/12.04/serverguide/phpmyadmin.html](https://help.ubuntu.com/12.04/serverguide/phpmyadmin.html) - most of the commands for installation are run from the server's command line.

I don't phpmyadmin myself, but understand from the web page I just linked to that once it's installed, you access phpmyadmin from a browser, using *[http://servername/phpmyadmin](http://servername/phpmyadmin)*, replacing *serveranme* with the server's actual hostname.

---

### Post by Maurices5000 on 2013-03-19
so the server's command line is that /etc/apache2?

---

### Post by Maurices5000 on 2013-03-19
i think i got it running thanks

---

### Post by Maurices5000 on 2013-03-19
Ok if you guys can help me a little more on this.  How do i know if it installed successfully? I got some successes and some failed messages. But i don't know if It was saying something failed or if it was just making a statement. I could not understand it. when i go to my ipaddress/phpmyadmin i get page not found

---

### Post by Maurices5000 on 2013-03-19
Found the answer at [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[COLOR=#333333][FONT=Ubuntu]**f you get a 404 error upon visiting [http://localhost/phpmyadmin](http://localhost/phpmyadmin):** You will need to configure apache2.conf to work with Phpmyadmin.[/FONT][/COLOR]


$ sudo gedit /etc/apache2/apache2.conf[COLOR=#333333][FONT=Ubuntu]Include the following line at the bottom of the file, save and quit.[/FONT][/COLOR]


$ Include /etc/phpmyadmin/apache.conf

**THANKS VERY MUCH GUYS!!!!**

---

