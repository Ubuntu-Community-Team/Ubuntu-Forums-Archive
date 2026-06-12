---
title: "total n00b, Apache, PHP and MySQL"
date: 2010-06-10
forum: Server Platforms
---

### Post by jotto! on 2010-06-10
OK all, please be very gentle with me. I am a newish convert to Ubuntu and still dont even know the basics. The only web stuff I have done is using WYSIWYG type editors such as dreamweaver and I also tried kompozer.

Now, a friend is going to teach me the basics of Apache, PHP and MySQL and if Im honest...I couldnt even tell you what each of those things are.

I did a quick search on how to install these on my ubuntu box and came up with
sudo tasksel install lamp-server

I dont see any new programs listed.

SO...tell me in a way an idiot could understand what I need to do to install and run these programs.

Thanks in advance.

BTW, if this is in the wrong part of the forum, please feel free to get it moved.

---

### Post by konqueror7 on 2010-06-10
by doing that, you just installed the major components of it,,,next you would need to use a ide or a good editor, and save it to /var/www if i rememember correctly. examples are kompozer, bluefish, gedit, netbeans, eclipse, aptana, etc... the most of them you can find in synaptic.

the components you installed are the web server (apache), database, (mysql), and runtime (php), and some extra modules that allow them to interact.

i would suggest looking at this [tutorial]("http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html") just to get a starting point. a good tutorial also to learn web programming is by [W3Schools]("http://www.w3schools.com"), in case you just need a guide or just want to better understand it.

hope it helps you, there still many things, and i guarranty you that there are more posters coming to help you out.:p

---

### Post by bodhi.zazen on 2010-06-10
> **jotto! said:**
> OK all, please be very gentle with me. I am a newish convert to Ubuntu and still dont even know the basics. The only web stuff I have done is using WYSIWYG type editors such as dreamweaver and I also tried kompozer.

Now, a friend is going to teach me the basics of Apache, PHP and MySQL and if Im honest...I couldnt even tell you what each of those things are.

I did a quick search on how to install these on my ubuntu box and came up with
sudo tasksel install lamp-server

I dont see any new programs listed.

SO...tell me in a way an idiot could understand what I need to do to install and run these programs.

Thanks in advance.

BTW, if this is in the wrong part of the forum, please feel free to get it moved.

See : [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

LAMP = Linux Apache Mysql and PHP

These are command line tools.

What are you wanting to do ? If you just want to server out static html files you probably do not need Mysql or PHP. If you have to ask what they are, you almost certainly do not need them.

You then write html pages or php pages and put them in /var/www

---

### Post by clrg on 2010-06-11
Apache2 is a webserver. It serves html files to a webbrowser. PHP is a language to make dynamic websites, for example, if you want to generate a large table based on variable input data, you would use Perl or PHP. MySQL is a database server. You can use it for data warehousing or as backend for your application. Often, so-called CMS (Content Management System, some kind of n00b-manageable website) use MySQL to store their data. Linux is the kernel, enabling all other applications and services to use the hardware, and providing basic functionality for a range of operating systems (or distributions), like Ubuntu.

Usually people install LAMP when they want to develop and serve a website or a web application. For example, Facebook relies on Apache.

If you are absolutely new to web development and LAMP, I suggest you get a book and learn the basics of HTML & CSS. Later on, you may improve your website with PHP and MySQL. 

There are tons of tutorials on how to get LAMP running, but unless you learn something about web development, they won't be of much use to you.

---

### Post by webtechquery on 2010-06-11
Hi there.

To know more about LAMP (Linux Apache MySQL PHP), or how to install LAMP in Ubuntu, check out the following url:
[http://www.webtechquery.com/index.php/2010/01/install-php-mysql-and-apache-lamp-on-ubuntu-linux/](http://www.webtechquery.com/index.php/2010/01/install-php-mysql-and-apache-lamp-on-ubuntu-linux/)

To know about some Editors or IDEs for PHP etc., check out:
[http://www.webtechquery.com/index.php/2010/01/free-php-ides-for-ubuntu-linux/](http://www.webtechquery.com/index.php/2010/01/free-php-ides-for-ubuntu-linux/)

And being new to Ubuntu, I suggest you to check the following url, which could be a good one for the noobs, as it lists some of the basic software and alternative to Windows (for the ones who moved from Windows to Ubuntu) :
[http://www.webtechquery.com/index.php/2010/06/software-for-ubuntu-ubuntu-program/](http://www.webtechquery.com/index.php/2010/06/software-for-ubuntu-ubuntu-program/)

Details of Ubuntu, Ubuntu Advantages, Alternative to Windows, check out:
[http://www.webtechquery.com/index.php/2010/06/windows-alternative-windows-xp-alternative-free-linux-operating-system/](http://www.webtechquery.com/index.php/2010/06/windows-alternative-windows-xp-alternative-free-linux-operating-system/)

Thanks.

---

### Post by jotto! on 2010-06-11
Thanks for all the replies guys. 

What I am trying to do with the help of my web design friend ( he has said he will show me but I have to do it so that I learn something ) is kind of like a basic matching up/pairs type game using photos....its going to be used to raise a little money for charity as well as being a bit of a laugh.

What I will have is a database of say 100 pairs of photos. The pictures will not be the same but will be matched together. For example it might be the owner of a cars face in one pic and then a pic of his car.

The site I want to build will then allow a user to play a game where at random, say 10 pairs of these pics are shown and labelled 1-10 and A to J. The user will then have to guess what face goes with which car and input the data on a simple form.

They will then be marked and shown the correct pairings.

My friend said we could do this using the programs I have mentioned hence the need for me to install them and jump in at the deep end! lol


Ive installed and played with netbeans and on the config screen it says I cannot save to the var/www folder. I see this is a root folder so I would need to change the permissions on it, is that correct? If so what is the command to type in from terminal?
Thanks.

---

### Post by dragon4ce on 2010-06-11
>  
If so what is the command to type in from terminal?

 
first go to the directory /var/:
 
```
cd /var/
```
 
then sudo mod the rights to read write exec for every user:
 
```
sudo chmod 777 www
```

---

### Post by jotto! on 2010-06-11
> **dragon4ce said:**
> first go to the directory /var/:
 
```
cd /var/
```then sudo mod the rights to read write exec for every user:
 
```
sudo chmod 777 www
```

Thankyou!

---

### Post by bodhi.zazen on 2010-06-11
> **dragon4ce said:**
> first go to the directory /var/:
 
```
cd /var/
```then sudo mod the rights to read write exec for every user:
 
```
sudo chmod 777 www
```

I am sorry, that was just bad advice. That change to permissions of /var/www is not really very secure.

I keep things in /var/www owned by root and ro by www-data . Thus yes I make changes to these files as root.

If you need to share across several users , make them members of www-data or make a new group, "web" and keep ownership www-data:web .

If you are new to Linux, you will need to do some reading 

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions") 

Please do not start changing ownership and permissions on system files without understanding what you are doing, how to reverse these changes, and on a server the security implications of such changes.

In general on servers you want to keep permissions as tight as possible and grant various users, may of which are daemons or services, such as www-data or mysql , to a minimum.

---

### Post by sixstorm on 2010-06-11
> **bodhi.zazen said:**
> I am sorry, that was just bad advice. That change to permissions of /var/www is not really very secure.


ROFL.  Back in the day when I started messing around with Ubuntu, I used to have /var/www wide open just because the Linux permissions would drive me nuts.  I just wanted to host my own website, not deal with funky permissions.

Next time I have an Ubuntu server, I won't make that mistake again.

---

### Post by jotto! on 2010-06-12
I realise having it wide open isnt such a good idea. I have now set it so that var is still root but www is now available to me to read and write.

This is only a short term 'fix'
I am the only one that uses the ubuntu box and hopefully it is fairly secure from the outside world...having said that I guess running a server program opens it up! lol.

Im going to talk to my friend later as I have installed the programs as well as phpMyAdmin. When I type in [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) it brings up the log in screen but when I installed the various programs, Im pretty sure none of them asked for a user and password so Im stuck once again...lol

I know he said Id be in at the deep end but im drowning!!!!!!! :lolflag:

---

### Post by jotto! on 2010-06-12
Ok, did a lil digging ran 
/usr/sbin/pma-configure

Set up new user and password with all privileges and then ran

/usr/sbin/pma-secure

I can now log in to phpMyAdmin, have I done it correctly?

---

### Post by bodhi.zazen on 2010-06-13
On a desktop, it is bad enough to assume you are the only user. That assumption will cause securiyt problems on a server.

I understand you are new to all this, and we can help on these forums, but honestly you should slow down and do some reading. It is important to understand what you are doing any why.

One of the first things you have run into is Linux permissions. This a a common stumbling block.

The "solution" is to slow down, read and understand about permissions. If you have questions , ask.

Along those lines, I advise you take the time to understand what you are doing and how to undo these changes again if needed. Changing system permissions on files and directories without understanding what you are doing is asking for problems.

A few more pieces of advice :

1. On a server, when I sys admin, I usually run things as root. Use sudo -i ....

2. Be cautions with root power.

3. You have several potential solutions to Apache issues in terms of shared directories or allowing users to have a web root. This can vary from adding the user to the www-data group to using a html directory in a users home directory.

See :

[http://bigbrovar.wordpress.com/2009/02/13/configure-apache-and-public_html-on-ubuntu/](http://bigbrovar.wordpress.com/2009/02/13/configure-apache-and-public_html-on-ubuntu/)

[http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file](http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file)

The point is, there are solutions to your "problems" , take the time to research and learn your options. Ask questions first, install & configure second.

In terms of phpmyadmin - if you can log in FANTASTIC. just be sure to use strong passwords. You may want to look at password protecting the phpmyadmin login page and or limiting access via iptables.

---

