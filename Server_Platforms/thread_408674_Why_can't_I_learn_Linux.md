---
title: "Why can't I learn Linux?????"
date: 2007-04-13
forum: Server Platforms
---

### Post by tbuss on 2007-04-13
I thought that since I was using Ubuntu, and that I was starting to feel a little confident; I would try to host my own web site. I had tried earlier to share pictures and videos with family using proftpd; ended in a disaster. I had received a lot of help along the way, just wasn't able to pull it all together. Someone mentioned that I should use Gallery with a website hosted with Apache to share my pictures with family members. So I did some research, setup a website, configured apache and I'm ready to go. Now that I have the site built, I wanted to use gallery to share my photos, but......yes, there is always a but; this is what happens when I run sudo apt-get install gallery2. After some questions (which ip or domain name will host....Name of user that can change files......) I get the following:

```
Setting up gallery2 (2.1.1-1) ...
Replacing config file /etc/apache/modules.conf with new version
 * Restarting apache 1.3 web server...           [ ok ] 
 * Forcing reload of apache 2.0 web server...           apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
                                                 [fail]
invoke-rc.d: initscript apache2, action "restart" failed.
dpkg: error processing gallery2 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gallery2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It's not that I don't read and research, I'm on the computer all the time now that I have Linux. All I do is read and try to learn how do to the things Linux offers. I don't mean to sound immature, but is linux only for really smart people, because I feel extremely stupid. Nothing has worked as advertised, when I read a tutorial or a man page, it seems very easy and straight forward, but for some reason something always goes wrong and I have no idea what to do. I don't know, I guess I was excited at first at all the things I could do in Linux, and after some dedication and late nights I have learned a lot. I'm sure the above error has something to do with some configuration of ip address or localhost being changed to the server's actual ip address . "Does anyone" have any help to spare; I'm just a new user that is very frustrated. After a long list of obstacles my stamina is wearing down. But I'm still very much willing to learn.

---

### Post by Frosty Cold Drink on 2007-04-13
It looks like you may have another instance of apache running. Something is quite odd. You shouldn't have both apache 1.3 and 2.0 on the same machine. Just one or the other. I'd bet if you got that issue sorted out then you would be fine with Gallery2.

Linux as a desktop operating system is one thing. As a server is another. The interworkins of the host OS, Apache, installed web applications, and dependencies is a universe all its own. Don't run before you can walk.

---

### Post by tbuss on 2007-04-13
**Frosty Cold Drink**

> It looks like you may have another instance of apache running. Something is quite odd. You shouldn't have both apache 1.3 and 2.0 on the same machine. Just one or the other. I'd bet if you got that issue sorted out then you would be fine with Gallery2.

I just got back from the #ubuntu channel, I was told the same thing.  Goes to show how much I know about what I'm doing. I removed apache and left apache2 installed and everything works as advertised. I understand what you are saying about a server compared to a desktop environment.  I guess for me switching to Linux has been awesome, just lost a little confidence because I'm not as proficient as I was with other os's. Thanks for you help.

---

### Post by Brazen on 2007-04-13
Don't worry, even idiots can run linux :D

For one thing, I'm betting you are using Ubuntu Edgy.  Edgy is good for a desktop; I use on my laptop.  You will have better luck using Dapper on a server.

Second of all, I PERSONALLY prefer to just download the source files for php applications.  Since there is no compiling, all you do is dump the files in your website directory and web browse to the install script.

I would suggest starting over with Dapper.  You can install all the php, apache, and mysql that you need with one command:```
sudo aptitude -y install php5-mysqli mysql-server
```then download the tar.gz from gallery.menalto.org (I think that's the right address) and unpack it to your website directory (I think the default is /var/www) and then follow the install instruction on the Gallery website.

---

### Post by tbuss on 2007-04-13
**Brazen**  

I don't know man, right now I'm still trying to figure out how to do anything with Gallery2. I used apt to install Gallery2 but for some reason it seems it would have been easier to install the Tarball. I also noticed there are some All-In-One Packages available (apache + MySQL + PHP) like you mentioned [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html) 

I still have alot to learn, especially with this Gallery config, the documentation seems to jump around a bit. I just simply wanted a way for family members to download pictures of my family. I initially thought I would just setup a simple ftp server and have them download the pictures that way. But then someone mentioned Gallery and I thought it would be a nice way to share photos.

---

### Post by Frosty Cold Drink on 2007-04-13
Your best off installing everything from the Ubuntu repositor (Apache, MySQL, PHP, Gallery2). Since they are all packaged to work together, you should have less to deal with to get to done.

---

### Post by tbuss on 2007-04-13
This is what I did:
Apache already installed
Installed MySQL 
Installed PHP5 and all other entries
Removed previous installation and Installed Gallery2
at the end of Gallery2 install the following happens:

```
The following NEW packages will be installed:
  gallery2
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/10.3MB of archives.
After unpacking 129MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package gallery2.
(Reading database ... 171840 files and directories currently installed.)
Unpacking gallery2 (from .../gallery2_2.1.1-1_all.deb) ...
Setting up gallery2 (2.1.1-1) ...
 * Forcing reload of apache 2.0 web server...                                  Syntax error on line 1 of /etc/apache2/mods-enabled/php4.load:
Cannot load /usr/lib/apache2/modules/libphp4.so into server: /usr/lib/apache2/modules/libphp4.so: cannot open shared object file: No such file or directory
                                                                        [fail]
invoke-rc.d: initscript apache2, action "restart" failed.
dpkg: error processing gallery2 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gallery2
E: Sub-process /usr/bin/dpkg returned an error code (1)
tbuss@tbuss-desktop:~$ 
```

I have */etc/apache2/mods-enabled/php4.load*? Shouldn't it be *php5.load*

The path* /usr/lib/apache2/modules/libphp4.so *doesn't exist (obviously) 

I checked  */etc/apache2/mods-enabled/php5.load *and it points to file: */usr/lib/apache2/modules/libphp5.so* (which does exist)

Can I just delete* /etc/apache2/mods-enabled/php4.load *and use */etc/apache2/mods-enabled/php5.load* instead?

Or is this a sign of something else?

---

### Post by tbuss on 2007-04-13
this is what I'm talking about: 

```
 * Forcing reload of apache 2.0 web server...                           [fail] 
invoke-rc.d: initscript apache2, action "restart" failed.
dpkg: error processing gallery2 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gallery2
E: Sub-process /usr/bin/dpkg returned an error code (1)
tbuss@tbuss-desktop:~$ 
```

Reinstalled Gallery2 this time I got this error.

I'll try to configure the ftp server again and I'll work with this a little more. Just not ready for this right now, going to do a little more reading!

---

### Post by MJN on 2007-04-14
Don't give up, and don't be too put back when you just can't get the simplest of things working... We've all been down that path (indeed we're all still on it!) but you'll soon start to learn that Linux is just like that. Often bl00dy hard to get something going but once it is it goes well, very well. And all the hard work is worth it because you end up knowing how everything works inside out... Noone learns anything when it works first time.

Furthermore, the inevitable problems in the world of Linux eventually result in the greatest joy when something, anything, works! For example, setting up a troublesome printer - in Windows you'd probably plug it in and it'd work. No fun in that is there?! In Linux you'll spend hours if not days scratching your head, Googling, posting here, and when a page finally pops out of that damn thing (even if it's got no text on - one step at a time!) then you'll be over the moon!! Now *that's* what makes it all worth it!

Again, just stick with it and take one step at a time... (I would also recommend keeping notes of everything you do - there is nothing worse than having to re-solve a problem that you know you've already solved sometime in the past, somehow).

Mathew

---

### Post by tbuss on 2007-04-14
MJN,

> Furthermore, the inevitable problems in the world of Linux eventually result in the greatest joy when something, anything, works!

I agree, working with Linux as been very rewarding. I can't explain why I just don't go back to windows, where I was confident and knew how to get things to work; I just really enjoy this whole new experience. I'm still working on setting up apache2 with gallery2. I have made progress and every time I receive one less error I feel a sense of accomplishment ("over the moon!"), plus I gain a little more confidence. I have learned a lot in the process, often times I find answers  to other problems while searching for a resolution to another. 

I don't think I will give up anytime soon, working with Linux is just too rewarding.

---

### Post by Frosty Cold Drink on 2007-04-14
> **tbuss said:**
> 
I have */etc/apache2/mods-enabled/php4.load*? Shouldn't it be *php5.load*

The path* /usr/lib/apache2/modules/libphp4.so *doesn't exist (obviously) 

I checked  */etc/apache2/mods-enabled/php5.load *and it points to file: */usr/lib/apache2/modules/libphp5.so* (which does exist)

Can I just delete* /etc/apache2/mods-enabled/php4.load *and use */etc/apache2/mods-enabled/php5.load* instead?

Or is this a sign of something else?

First, check with your package manager to see if PHP4 is installed. Remove it if it is. If not, yes, just kill the php4 stuff.

---

### Post by Brazen on 2007-04-15
> **tbuss said:**
> This is what I did:
Apache already installed
Installed MySQL 
Installed PHP5 and all other entries
Removed previous installation and Installed Gallery2
at the end of Gallery2 install the following happens:

```
The following NEW packages will be installed:
  gallery2
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/10.3MB of archives.
After unpacking 129MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package gallery2.
(Reading database ... 171840 files and directories currently installed.)
Unpacking gallery2 (from .../gallery2_2.1.1-1_all.deb) ...
Setting up gallery2 (2.1.1-1) ...
 * Forcing reload of apache 2.0 web server...                                  Syntax error on line 1 of /etc/apache2/mods-enabled/php4.load:
Cannot load /usr/lib/apache2/modules/libphp4.so into server: /usr/lib/apache2/modules/libphp4.so: cannot open shared object file: No such file or directory
                                                                        [fail]
invoke-rc.d: initscript apache2, action "restart" failed.
dpkg: error processing gallery2 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gallery2
E: Sub-process /usr/bin/dpkg returned an error code (1)
tbuss@tbuss-desktop:~$ 
```

I have */etc/apache2/mods-enabled/php4.load*? Shouldn't it be *php5.load*

The path* /usr/lib/apache2/modules/libphp4.so *doesn't exist (obviously) 

I checked  */etc/apache2/mods-enabled/php5.load *and it points to file: */usr/lib/apache2/modules/libphp5.so* (which does exist)

Can I just delete* /etc/apache2/mods-enabled/php4.load *and use */etc/apache2/mods-enabled/php5.load* instead?

Or is this a sign of something else?

I'm pretty sure that's not the version of Gallery2 in Dapper.  Are you using Edgy?  I've seen a ton of people have these funky problems in Edgy.  You would have a much better time using Dapper for a server.

---

### Post by tbuss on 2007-04-15
**Okay, I decided to make a clean start. Purge and remove apache2/php4/and libapache2**

```
sudo apt-get --purge remove php4* php5* apache2* libapache2*
```
**Searched in Synaptic:**
Synaptic: Search for php4/apache/php5/
[INDENT]apache2 will be removed with configuration
apache2-common will be removed with configuration
apache2-utils will be removed with configuration
apache2-mpm-prefork will be removed
gallery2 will be removed
libapache2-mod-auth-mysql will be removed
libapache2-mod-php4 will be removed
php4 will be removed
php4-common will be removed
php4-mysql will be removed[/INDENT]

[B]Purged apache2/php4/libapache2  after the purge I try to install php4 and it tells me the newest version is 
already installed[/B]
**I then ran**
```
aptitude search apache2 php
```
**Results:** [http://paste.ubuntu-nl.org/15726/](http://paste.ubuntu-nl.org/15726/)

**I then ran **
```
sudo aptitude purge php5
```
I used **php5** in the purge but it looks like mostly **php4** files were removed
**To make sure all php5 packages were removed I ran**
```
aptitude search php5 | grep ^c
```
**I then ran sudo aptitude purge on all file listed php5 | grep ^c**
**I then reinstalled php4**

**To test if php4 installed correctly **
```
gksudo gedit /var/www/testphp.php
```

** Inserted the following line into the new file **
```
<?php phpinfo(); ?>
```

** Saved the edited file**

 [http://localhost/testphp.php](http://localhost/testphp.php) [COLOR="Green"](success)[/COLOR]

**I then configured PHP to work with MySQL:**
```
gksudo gedit /etc/php4/apache2/php.ini
```

**I uncomment the:** 
```
";extension=mysql.so"  
```

**I then saved the file**

**Restarted apache2:**
```
sudo /etc/init.d/apache2 restart
```

 [http://localhost/phpmyadmin](http://localhost/phpmyadmin)  [COLOR="Green"](success)[/COLOR]

**I then tried to install Gallery2:**

```
sudo apt-get install gallery2
sudo nano /etc/apache2/conf.d/gallery2
```
[INDENT]first line: #Alias /gallery2 /usr/share/gallery2
remove the #
crtl x
restart apache[/INDENT]
```
 sudo /etc/init.d/apache2 restart
```
[http://localhost/gallery2](http://localhost/gallery2) [COLOR="Red"](error)[/COLOR]

When I try to test the link I get this:
> Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
Apache/2.0.55 (Ubuntu) PHP/4.4.2-1.1 Server at localhost Port 80

When I test testphp.php the address used is my IP instead of localhost
When I test phpmyadmin the address used is locahost
When I test gallery2 the address used is localhost

Does this matter, with my limited experience this is the only difference I can find between the three.

---

### Post by Brazen on 2007-04-15
Did you check the log file?  I can't say it enough how much easier of a time you would have using Ubuntu Dapper and the gallery2 tar download, but you might find some clue in the apache log files under /var/log/

---

### Post by tbuss on 2007-04-15
I have up and running now, with the help of a friend who knows way more than I do. The one thing we could actually pinpoint was a htaccess file with a syntax error, getting rid of this file all together seemed to to the trick; among other things. Now all I have to do is figure out why folks from the outside cannot connect, it's seems as though my router has dumped all my port fowarding settings. I had a thread going a couple a weeks ago realting to the same problem, but with an ftp server. 

Thanks again to everyone who has posted and helped.

---

### Post by tbuss on 2007-04-16
Just in case anyone was curious about why my family could not connect; the solution was easy. After doing some searching I found out that some ISP's block incoming traffic on port 80. This was not the case for me but I did learn that adding  :80 to my ip address could be a possible solution, and it worked.

---

