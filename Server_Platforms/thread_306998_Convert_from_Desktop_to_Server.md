---
title: "Convert from Desktop to Server???"
date: 2006-11-25
forum: Server Platforms
---

### Post by shane2peru on 2006-11-25
Ok, here is my situation.  I'm currently running Dapper (Gnome desktop - standard install) on a Toshiba Laptop with plenty of ram (around 730MB).  I have DSL, and I believe I am setup with a static IP address, at least I am on my router.  I have been really tinkering around with the idea of running my web page off my computer, or at least running a second not so important web page off my computer.  I need a howto that is simple to follow.  Also can I run 1 PC as a server and use it as my desktop too, or do I need a dedicated PC for a server?  I'm not new to Computers, I'm completely new to servers, however very willing to learn.

Shane

PS most howto's tend to start from a new installation, not a desktop installation.

---

### Post by fritz_monroe on 2006-11-25
I can only give my opinion on this.  You can use your desktop as a server.  The thing that will change is you will be running Apache.  You will take a performance hit on the desktop apps and the server apps.

If I was looking at doing this, I'd scrounge up another system to use as a server.  Find a 500MHz system, max out the RAM and put in a hard drive.  It will work fine for what you have in mind.

---

### Post by shane2peru on 2006-11-25
getting another system right now is not in the budget.  We live in Peru, South America, and picking up a used computer somewhere is not that simple, in the US, it is a lot easier,  I know plenty of people with comptuers setting around not being used.  If I can successfully run it off this my computer for now, I may look into that option.  I'm using a Celeron M processor, I forget what speed and am not sure how to find that in Linux, I know how in XP.  :)  But, I'm going to have to set it up, and prove that I can do it, and have the time to do it before investing $.10 into it.  Besides, it can't be that bad of a performance hit, I used to use Windows! :) - That is a performance hit!

Shane

---

### Post by rbalfour on 2006-11-25
> **shane2peru said:**
> Ok, here is my situation.  I'm currently running Dapper (Gnome desktop - standard install) on a Toshiba Laptop with plenty of ram (around 730MB).  I have DSL, and I believe I am setup with a static IP address, at least I am on my router.  I have been really tinkering around with the idea of running my web page off my computer, or at least running a second not so important web page off my computer.  I need a howto that is simple to follow.  Also can I run 1 PC as a server and use it as my desktop too, or do I need a dedicated PC for a server?  I'm not new to Computers, I'm completely new to servers, however very willing to learn.

Shane

PS most howto's tend to start from a new installation, not a desktop installation.

Yes, you can run a desktop and a server service side by side. You will take a performance hit on heavy loads.
I currently run WEB/DB/PHP5 on a laptop that I use for work. (testing/debugging stuff). I really don't see a major performance hit. You can see my specs in the sig.


$ apt-get install apache2

this will install a webserver for you.

See my output from the test:

```

root@underworld:/home/mod# apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2-common apache2-mpm-worker apache2-utils
Suggested packages:
  apache2-doc
The following NEW packages will be installed:
  apache2 apache2-common apache2-mpm-worker apache2-utils
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 1145kB of archives.
After unpacking 3994kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com edgy/main apache2-utils 2.0.55-4ubuntu4 [93.1kB]
Get:2 http://us.archive.ubuntu.com edgy/main apache2-common 2.0.55-4ubuntu4 [807kB]
Get:3 http://us.archive.ubuntu.com edgy/main apache2-mpm-worker 2.0.55-4ubuntu4 [209kB]
Get:4 http://us.archive.ubuntu.com edgy/main apache2 2.0.55-4ubuntu4 [36.0kB]
Fetched 1145kB in 3s (321kB/s)  
Selecting previously deselected package apache2-utils.
(Reading database ... 154972 files and directories currently installed.)
Unpacking apache2-utils (from .../apache2-utils_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package apache2-common.
Unpacking apache2-common (from .../apache2-common_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package apache2-mpm-worker.
Unpacking apache2-mpm-worker (from .../apache2-mpm-worker_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package apache2.
Unpacking apache2 (from .../apache2_2.0.55-4ubuntu4_i386.deb) ...
Setting up apache2-utils (2.0.55-4ubuntu4) ...
Setting up apache2-common (2.0.55-4ubuntu4) ...
Setting Apache2 to Listen on port 80. If this is not desired, please edit /etc/apache2/ports.conf as desired. Note that the Port directive no longer works.
Module userdir installed; run /etc/init.d/apache2 force-reload to enable.

Setting up apache2-mpm-worker (2.0.55-4ubuntu4) ...
 * Starting apache 2.0 web server...                                            apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ ok ]

Setting up apache2 (2.0.55-4ubuntu4) ...


```

Then open a webbrowser on the same machine to [http://127.0.0.1](http://127.0.0.1) to test the install

---

### Post by jjross on 2006-11-25
I am running a server on my desktop computer and it has definitly been the most fun and challenging experience I have had.
Its not that hard to do and it will run fine along with everything else as long as you are not getting non stop traffic on your web site. ( I get about 5 a day). 
All of the information you need is here on the forum, just use the search bar and read. Read a lot and you will get there.
Not to mention there are a lot of good people here to answer most any question.
Good Luck :D

---

### Post by shane2peru on 2006-11-25
Hey thanks guys!  That is what I like about the Linux community there is always help available!  Installed apache2.  Went to and get a nice looking little page with a folder.  Wow, that step was easy.  :D  Ok, what next?  Is there some howto's out there.  I did search, and read a few howto's however they all were for server setup with a disk, and installing server LAMP.  

Shane

---

### Post by rbalfour on 2006-11-26
> **shane2peru said:**
> Hey thanks guys!  That is what I like about the Linux community there is always help available!  Installed apache2.  Went to and get a nice looking little page with a folder.  Wow, that step was easy.  :D  Ok, what next?  Is there some howto's out there.  I did search, and read a few howto's however they all were for server setup with a disk, and installing server LAMP.  

Shane

The root folder of the web server is located at /var/www

You will need to be root (sudo su) to edit the files there.

LAMP is okay if you need MySQL database or PHP to run scripts. I tend to install LAMP only on server, on the desktops, I install everything by hand. makes it easier to start and stop servers. Sorry there really are no HOW-TO that I can remember. A good start would be to lookup HOW-TO each service you reuqire. ie. HOW-To setup apache2

BTW, what is your goal on setting up a webserver? That might help narrow down the help, as you can tell Linux is a BIG universe..

---

### Post by shane2peru on 2006-11-26
> **rbalfour said:**
> The root folder of the web server is located at /var/www

You will need to be root (sudo su) to edit the files there.

LAMP is okay if you need MySQL database or PHP to run scripts. I tend to install LAMP only on server, on the desktops, I install everything by hand. makes it easier to start and stop servers. Sorry there really are no HOW-TO that I can remember. A good start would be to lookup HOW-TO each service you reuqire. ie. HOW-To setup apache2

BTW, what is your goal on setting up a webserver? That might help narrow down the help, as you can tell Linux is a BIG universe..
Thanks rbalfour,
I guess I should have stated that int he beginning a little clearer.  I would like to host my web site.  I have had so many problems with web hosting companies, and email etc, that I thought, I have linux, I can do this.  I will probably setup a web different website that is less important to see how things go and to learn with.  As far as what things I use on my existing web page hosted externally:  
I currently use PHPList - a mailing list, this would be nice to run off my computer it uses mysql.
I also use Photogallery - works off mysql.
Some streaming video, and audio - not much though, and not heavily accessed. 
Email.  

These are the type of things I would like to incorporate into this depending on how things go.  For the time being I would like to learn how to have a simple web page that others can see that is hosted on my computer.  Thanks for the help!

Shane

**EDIT:**  Oh, a counter and some stats would be nice too.

---

### Post by 5h4rk on 2006-11-26
Hi, actually i'm looking for something similar, have bee searching but couldnt find anything... :(

Im running Edgy desktop, and I would like to set up a files server or a ssh server so I can control my laptop remotely...

Does anyone have any link or how to for that?

Thanks.

---

### Post by rbalfour on 2006-11-26
> **5h4rk said:**
> Hi, actually i'm looking for something similar, have bee searching but couldnt find anything... :(

Im running Edgy desktop, and I would like to set up a files server or a ssh server so I can control my laptop remotely...

Does anyone have any link or how to for that?

Thanks.

$ sudo apt-get install openssh-server

you're done.

Files server? You mean like a windows file sharing..

Right click on a folder you want to share out.
You will see "Share Folder"

Follow the directions after that.

---

### Post by shane2peru on 2006-11-26
Ok, I put my web page in var/www/ and chmod it to 644.  However the Pictures are not showing up.  The folder is there, the link is correct, but they don't show up.  Also, how can I make this accessible to the outside world?  Is there some documentation to read on this?  Is it covered in the apache page?  I visited there page, but they need to work on user friendliness on their web page.

Shane

---

### Post by rbalfour on 2006-11-26
Shane2Peru.

Get ready to WORK! lol!

1) MySQL

$ sudo apt-get install mysql-server mysql-client libmysqlclient12-dev

next

$ sudo nano /etc/mysql/my.cnf

Find this and comment it out.

```

[...]
#bind-address           = 127.0.0.1
[...]

```

Restart MySql

$sudo /etc/init.d/mysql restart

now PROTECT your MySql install

$ sudo mysqladmin -u root password **changeme**
$ sudo mysqladmin -h localhost -u root password **changeme**


2) Apache2 (for PHP)

$ sudo apt-get install apache2 apache2-common apache2-doc apache2-mpm-prefork apache2-utils libapr0 libexpat1 ssl-cert

(it's okay if somethings are already installed)

3) Install php5 (I prefer it, because it's newer, we like new, yes we do)

$ sudo apt-get install autoconf automake1.4 autotools-dev libapache2-mod-php5 php5 php5-common php5-curl php5-dev php5-gd php-pear php5-ldap php5-mhash php5-mysql php5-mysqli php5-snmp php5-sqlite php5-xmlrpc php5-xsl php5-imap php5-mcrypt php5-pspell

You system will pop you a question

```
Continue installing libc-client without Maildir support? <-- Yes
```

4) Housekeeping

$ sudo nano /etc/apache2/apache2.conf

look for this

```

[...]
DirectoryIndex index.html index.htm index.shtml index.cgi index.php index.php3 index.pl index.xhtml
[...]

```

and change to this

```

[...]
DirectoryIndex index.php index.html 
[...]

```

Next

$ sudo nano /etc/apache2/ports.conf

add

```

Listen 443

```

Next

$ sudo a2enmod ssl
$ sudo a2enmod rewrite
$ sudo a2enmod suexec
$ sudo a2enmod include

lets kick the tires now.

$ sudo /etc/init.d/apache2 force-reload

okay, you still with me...next thing is...

$ sudo nano /etc/mime.types

find
```

[...]
application/x-httpd-php                                phtml pht php
application/x-httpd-php-source                 phps
application/x-httpd-php3                       php3
application/x-httpd-php3-preprocessed          php3p
application/x-httpd-php4                       php4
[...]

```

change
```

[...]
#application/x-httpd-php                                phtml pht php
#application/x-httpd-php-source                 phps
#application/x-httpd-php3                       php3
#application/x-httpd-php3-preprocessed          php3p
#application/x-httpd-php4                       php4
[...]

```

next

$ sudo nano /etc/apache2/mods-enabled/php5.conf

Find

```

<IfModule mod_php5.c>
 AddType application/x-httpd-php .php .phtml .php3
 AddType application/x-httpd-php-source .phps
</IfModule>

```

change to 

```

<IfModule mod_php5.c>
#  AddType application/x-httpd-php .php .phtml .php3
#  AddType application/x-httpd-php-source .phps
</IfModule>

```

Turn the engine over and let's see if it works.

$ sudo /etc/init.d/apache2 restart


Guess what, if everything went well you now have a LAMP5.
I will save the "mail server" for later...it's late and the process is somewhat time consuming to write up. Btw, this is the way I install my LAMP5, by hand. I can't remember where I got it from, but it has always worked for me. BTw, you should be able to hit your website either [http://localhost](http://localhost) or [https://localhost](https://localhost)

gl

---

### Post by rbalfour on 2006-11-26
> **shane2peru said:**
> Ok, I put my web page in var/www/ and chmod it to 644.  However the Pictures are not showing up.  The folder is there, the link is correct, but they don't show up.  Also, how can I make this accessible to the outside world?  Is there some documentation to read on this?  Is it covered in the apache page?  I visited there page, but they need to work on user friendliness on their web page.

Shane

How are the links inside the html file? hardcore ie, [http://blaah/pictures?](http://blaah/pictures?)
Also, did you chmod 644 on the folder and contents?

chmod -R 644 <your foldername>

I knew that would be your next question...hahahahaa

first

How is your internet connected?

A) PC <-----> router <----> cable/telephone

or

B) PC <------> cable / ADSL modem <-------> line (RJ11/coaxial)

I can help with A. B I am not to sure about, as modem are different from provider to provider.

Check your FQIP here -> [https://www.thugcrew.com/checkip.php](https://www.thugcrew.com/checkip.php)

what it gives back is your outside facing IP address..

---

### Post by shane2peru on 2006-11-26
> **rbalfour said:**
> How are the links inside the html file? hardcore ie, [http://blaah/pictures?](http://blaah/pictures?)
Also, did you chmod 644 on the folder and contents?
The pictures are linked to /pictures/picture.jpg.  It works fine in my /home directory.  The link address doesn't contain a http: before it, is just folders so it will work anywhere, makes my checking job easier.  
> **rbalfour said:**
> 
chmod -R 644 <your foldername>

I knew that would be your next question...hahahahaa
  Yep, that is what I did.  is 644 the right setting?  I think it is I have seen it in FTP-ing so much that I just remember the numbers.  I have a basic understanding of permissions, just don't remember the numbers well.

> **rbalfour said:**
> 
first

How is your internet connected?

A) PC <-----> router <----> cable/telephone

or

B) PC <------> cable / ADSL modem <-------> line (RJ11/coaxial)

I can help with A. B I am not to sure about, as modem are different from provider to provider.

Check your FQIP here -> [https://www.thugcrew.com/checkip.php](https://www.thugcrew.com/checkip.php)

what it gives back is your outside facing IP address..

Yes I'm set up with A  - WWW Internet - DSL Modem - Router (Hawkings) - My PC.  I got my IP, I'm about 90% sure they set me up with a Static IP.

> **rbalfour said:**
> 
now PROTECT your MySql install

$ sudo mysqladmin -u root password **changeme**
$ sudo mysqladmin -h localhost -u root password **changeme**
 ok, made it this far and get this error.  
```

Setting up mysql-server (5.0.22-0ubuntu6.06.2) ...
sdrice@shane-laptop:/var/www$ sudo nano /etc/mysql/my.cnf
sdrice@shane-laptop:/var/www$ sudo etc/init.d/mysql restart
sudo: etc/init.d/mysql: command not found
sdrice@shane-laptop:/var/www$ sudo /etc/init.d/mysql restart
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld.
sdrice@shane-laptop:/var/www$ sudo mysqladmin -u root password ******
sdrice@shane-laptop:/var/www$ sudo mysqladmin -h localhost -u root password ******
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
sdrice@shane-laptop:/var/www$ sudo mysqladmin -h localhost -u root password *****
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
sdrice@shane-laptop:/var/www$ sudo mysqladmin -h localhost -u root password *****
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
sdrice@shane-laptop:/var/www$ sudo /etc/init.d/mysql restart
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld.
sdrice@shane-laptop:/var/www$ sudo mysqladmin -h localhost -u root password *****
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
sdrice@shane-laptop:/var/www$ sudo mysqladmin -u root password *****
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
sdrice@shane-laptop:/var/www$ sudo mysqladmin -u root password *****
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```[COLOR=Red]I replaced all my passwords with *****.  [COLOR=Black]?  I'm going on to step two, and will come back to this step. - Ok, got through all the steps except the bumb in the road mentioned above.  Also, how can people on the internet access this page?  Is it through the MY IP address and the 127.0.0.1 or localhost?  [/COLOR][/COLOR]


Thanks for the Help!
Shane

---

### Post by shane2peru on 2006-11-26
Ok, the picture problem is solved.  It was a permissions problem.  I needed 755, not 644.  Apparently opening the folder is considered Executing, and the folder needs 755, even if the picture doesn't the folder where it is seems to need that.  When I tried ```
cd Pictures
``` it wouldn't let  me access the folder without being sudo.  So, I changed the folder to 755 and presto, now I can cd to that directory and pictures appear in the browser too.  

Shane

---

### Post by rbalfour on 2006-11-26
$ sudo nano /etc/mysql/my.cnf

Find this and uncomment it.

Code:

[...] bind-address = 127.0.0.1 [...]

Restart MySql

$sudo /etc/init.d/mysql restart

Then try your password again. My bad, I told you to block localhost, then I told you to login via localhost...duH! what was I thinking, lol.

The above change will unblock localhost, so you can login via localhost.

As for the router, can you can settings on it. Ie, does it have a web interface. If so, look for a section on "port forwarding"

Or post the router model number.

---

### Post by shane2peru on 2006-11-26
> **rbalfour said:**
> $ sudo nano /etc/mysql/my.cnf

Find this and uncomment it.

Code:

[...] bind-address = 127.0.0.1 [...]

Restart MySql

$sudo /etc/init.d/mysql restart

Then try your password again. My bad, I told you to block localhost, then I told you to login via localhost...duH! what was I thinking, lol.

The above change will unblock localhost, so you can login via localhost.

As for the router, can you can settings on it. Ie, does it have a web interface. If so, look for a section on "port forwarding"

Or post the router model number.
I'm still getting the same error with the mysql, evan after uncommenting the bind-address.  As far as my router, yes, it is conigurable.  I have messed with it before a little bit.  Here is the info on it:

```
Device Name:   HWR54G       Firmware Version:  Version 1.0 Release 11
```

How would this be accessed from the other computers?  Would people access this with my IP address?  When I tried my IP it asks for my user name and password.  I tried it from a friends computer to and had the same results.  I'm guessing this has to do with my router not being properly setup.  I was reading another post about port forwarding etc.  I assume it has to do with that.  I'm a real newbie, when it comes to servers, etc. 

Shane

---

### Post by rbalfour on 2006-11-26
> **shane2peru said:**
> 
How would this be accessed from the other computers?  Would people access this with my IP address?  When I tried my IP it asks for my user name and password.  I tried it from a friends computer to and had the same results.  I'm guessing this has to do with my router not being properly setup.  I was reading another post about port forwarding etc.  I assume it has to do with that.  

The reason the login is coming up is because the router is not setup to forward port 80 to anywhere. So you will have to port forward 80 to your server.

---

### Post by shane2peru on 2006-11-26
I was just playing with that setting.  I tried forwarding it to 8080, and it didn't work.  I don't know what I should set it to.  It kept saying that that port was not available.  What port do I need, or where do I find the specified port?  Thanks!

Shane

Oh, and is that TCP or TCP/UDP
I have an internal port 80~80
External port 80~80 
That is the defualt setting.

---

### Post by rbalfour on 2006-11-26
> **shane2peru said:**
> I was just playing with that setting.  I tried forwarding it to 8080, and it didn't work.  I don't know what I should set it to.  It kept saying that that port was not available.  What port do I need, or where do I find the specified port?  Thanks!

Shane

Oh, and is that TCP or TCP/UDP
I have an internal port 80~80
External port 80~80 
That is the defualt setting.
Please post a screen shot of the about window.

---

### Post by shane2peru on 2006-11-27
Ok, here is the screen shot.  In my setup this is under virtual servers and this window pops up.  I also attached hawking-options these are all the choices I have under Advanced.

Shane

---

### Post by rbalfour on 2006-11-27
> **shane2peru said:**
> Ok, here is the screen shot.  In my setup this is under virtual servers and this window pops up.  I also attached hawking-options these are all the choices I have under Advanced.

Shane

Yep, You have the right screen on Virtual Servers
Now you need to check the enable box and see if you can access from the outside world.

---

### Post by shane2peru on 2006-11-27
Ok, when I leave the settings as seen in the screenshot, I get this error.  ```
Error.  Data could not be saved.  Port number is unavailable, Please try others.
```Also when I try my IP address, it is not the same log in screen as my router.  It asks me to enter user name and password for "SmartAX MT880"  You can see the same screen by going to: xx.xxx.xxx.x.xx   Ok, I just checked and we are getting blocked at the modem!  My modem is a SmartAX MT880 - from Telefonica (a Spain based telephone company here in Peru and most of Latin America).That appears to be the model number, the type is Huawei.  This isn't looking good.  :-k

Shane

---

### Post by rbalfour on 2006-11-27
> **shane2peru said:**
> Ok, when I leave the settings as seen in the screenshot, I get this error.  ```
Error.  Data could not be saved.  Port number is unavailable, Please try others.
``` 

Also when I try my IP address, it is not the same log in screen as my router.  It asks me to enter user name and password for "SmartAX MT880"  You can see the same screen by going to: xx.xx.xx.xx  .  Ok, I just checked and we are getting blocked at the modem!  My modem is a SmartAX MT880 - from Telefonica (a Spain based telephone company here in Peru and most of Latin America).That appears to be the model number, the type is Huawei.  This isn't looking good.  :-k

Shane

Please PM me. It's quite urgent!

---

### Post by johneedoe on 2006-11-27
It's almost like a cliffhanger from an X-Files season finale!

---

### Post by shane2peru on 2006-11-27
I'm hung up at the modem.  I'm reconfiguring another modem to connect to the internet, but it is not cooperating with me.  That seems to be where I'm stuck.  Will let you know if I get any further, don't want to keep you hanging, I know the suspense would be a lot. :D

Shane

---

### Post by rbalfour on 2006-11-28
> **shane2peru said:**
> I'm hung up at the modem.  I'm reconfiguring another modem to connect to the internet, but it is not cooperating with me.  That seems to be where I'm stuck.  Will let you know if I get any further, don't want to keep you hanging, I know the suspense would be a lot. :D

Shane

good luck with the modem. Once that is done, you web server will work.

---

### Post by shane2peru on 2006-11-28
Ok, I got my modem semi-configured.  That was a real pain.  I cannot connect through a static IP address on my computer now.  Before I could, now it won't only through DHCP.  If anyone knows of a setting I'm missing on this thing and can let me know that would be great!  It is a ZTE ZDSL.  Anyway I set the port forwarding to my LAN IP on my computer.  And when I go to the WAN IP address, no web page, just the admin thing. ???  I keep hitting a brick wall here.  

Shane

---

### Post by shane2peru on 2006-11-29
> **rbalfour said:**
> $ sudo nano /etc/mysql/my.cnf

Find this and uncomment it.

Code:

[...] bind-address = 127.0.0.1 [...]

Restart MySql

$sudo /etc/init.d/mysql restart

Then try your password again. My bad, I told you to block localhost, then I told you to login via localhost...duH! what was I thinking, lol.

The above change will unblock localhost, so you can login via localhost.

As far as this problem, I still can't seem to use mysql.  I was reading the man pages, and tried this: ```
shane@shane-laptop:~$ mysqladmin ping
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'shane'@'localhost' (using password: NO)'
shane@shane-laptop:~$ sudo mysqladmin ping
Password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```  the bind-address is uncommented.  Any ideas?  - Oh, by the way, I'm using Edgy now, a fresh install, I ran through all the steps again t configure everything.  Works great except this little problem, and my modem configuration.   I need to find some simple step reading to figure some of these things out.  Thanks for the help!

Shane

**EDIT**:  Never mind - [here]("http://www.ubuntuforums.org/showthread.php?t=288606&highlight=mysql+howto") is a good post that covers this.

---

### Post by jkroto on 2006-12-20
> **rbalfour said:**
> The root folder of the web server is located at /var/www


rbalfour and shane2peru,
Thanks for all the info in this thread.  I'm going to attempt to follow the setup in this thread.  

One question I have is can I make all the parts of LAMP install on a particular partition.  I have an extra drive (physically separate) that I set as /var when I installed.  If I install Mysql, etc., will it install to that drive/partition or do I have to tell it to do that... or did I already screw up and should I start over.
Thanks for any advice.

---

