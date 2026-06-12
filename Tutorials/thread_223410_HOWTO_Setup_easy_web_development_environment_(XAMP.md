---
title: "HOWTO: Setup easy web development environment (XAMPP)"
date: 2006-07-26
forum: Tutorials
---

### Post by petervk on 2006-07-26
This is a how-to for setting up a web development environment easily. This guide will install the XAMPP lampp stack into /opt, setup an easy way to start it up and shut it down, and link a folder in your home directory to the webserver.

**WARNING**
This guide is aimed at a development environment only and should not be used as a public webserver. To setup a public webserver follow the directions on the Ubuntu wiki [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

As this is Ubuntu, all the major parts of a typical web server are included (in the main repo, or on the Ubuntu Server CD) and this is a great way to setup a server. The ubuntu developers have prepared a great web server and have made the process as seemless as possible. 

But what if even the official way is still to complicated? What if you just want a quick web server for development?

Fortunately there is the XAMPP project: [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html). The XAMPP project bundles Apache, PHP4 & 5, Perl, mySQL, and a bunch of other utilities/applications into an simple package for Mac OSX, Windows, Solaris, and Linux. Obviously this HOWTO only deals with the linux version.

For those of you with already existing Apache/mySQL/php installations it installs everything into /opt so it doesn't conflict with any other installation, and it is completely setup and ready to run.

[SIZE="3"]**_Install XAMPP_**[/SIZE]

Two easy steps:
[LIST=1]
[*]Download the most recent version of XAMPP: (at time of writing 1.5.3a)
[http://prdownloads.sourceforge.net/xampp/xampp-linux-1.5.3a.tar.gz?download](http://prdownloads.sourceforge.net/xampp/xampp-linux-1.5.3a.tar.gz?download)
(Source URL: [http://www.apachefriends.org/en/xampp-linux.html#374](http://www.apachefriends.org/en/xampp-linux.html#374))
[*]Extract the archive to /opt using sudo: (make sure you are in the directory that you downloaded the archive to) ```
sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt
```
[/LIST]

[SIZE="3"]**_Start XAMPP_**[/size]

To start it up, open a terminal and type this:
```
sudo /opt/lampp/lampp start
```

[SIZE="3"]**_Stop XAMPP_**[/size]

To stop it, open a terminal and type this:
```
sudo /opt/lampp/lampp stop
```

[SIZE="3"]**_Additional XAMPP commands_**[/size]

To see additional commands, open a terminal and type this:
```
sudo /opt/lampp/lampp
```

[SIZE="3"]**_Sweet XAMPP Control Panel_**[/size]

[img]http://img108.imageshack.us/img108/5647/screenshotxamppcontrolpanelfj6.png[/img]

To use the sweet gtk/python control panel:

Run in a terminal: ```
gedit ~/.local/share/applications/xampp-control-panel.desktop
```

Paste the following into the open file and save and exit.
```
[Desktop Entry]
Comment=Start/Stop XAMPP
Name=XAMPP Control Panel
Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
Icon[en_CA]=/usr/share/icons/Tango/scalable/devices/network-wired.svg
Encoding=UTF-8
Terminal=false
Name[en_CA]=XAMPP Control Panel
Comment[en_CA]=Start/Stop XAMPP
Type=Application
Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg
```
"XAMPP Control Panel" will show up in your applications menu under Internet. Use the Alacarte Menu Editor to move it around.

[SIZE="3"]**_Test to see if XAMPP is running_**[/size]

Once XAMPP is up and running open firefox and go to: [http://localhost/](http://localhost/)

You should see the XAMPP test page:

[IMG]http://static.apachefriends.org/images/380.jpg[/IMG]

[SIZE="3"]**_Location of files and uploading_**[/size]

XAMPP by default uses /opt/lampp/htdocs as the root web directory. The easiest way to start working on files is to link a folder in your home directory into this directory.
My user name is peter so I have /home/peter/public_html linked to /opt/lampp/htdocs/peter. So if I navigate to [http://localhost/peter/](http://localhost/peter/) I get a listing of all the files/folders in that directory. (As long is there isn't a index.php/html/etc file)
To set this up, run in a terminal:
[list=1]
[*]Make public_html directory in home directory: ```
mkdir ~/public_html
```
[*]Link to /opt/lampp/htdocs ```
sudo ln -s ~/public_html /opt/lampp/htdocs/$USER
```
[/list]
Now any files and folders you place in ~/public_html will be published to your personal webserver. 

Bookmark [http://localhost/username](http://localhost/username) to make this easy to access.

[SIZE="3"]**_WARNING - SECURITY_**[/size]
[http://www.apachefriends.org/en/xampp-linux.html#381](http://www.apachefriends.org/en/xampp-linux.html#381)
Open holes:
[list=1]
[*]The MySQL administrator (root) has no password.
[*]The MySQL daemon is accessible via network.
[*]ProFTPD uses the password "lampp" for user "nobody".
[*]PhpMyAdmin is accessible via network.
[*]Examples are accessible via network.
[*]MySQL and Apache running under the same user (nobody). 
[/list]
This doesn't leave your whole system wide open, but someone could hack your XAMPP installation, so be wary.
To fix most of the security weaknesses open a terminal and run: ```
sudo /opt/lampp/lampp security
```

[SIZE="3"]**_Feedback_**[/size]
Please read [ this post](http://www.ubuntuforums.org/showpost.php?p=1310039&postcount=5).

---- EDIT - July 28, 2006 ----
Minor Edits

---- EDIT - August 1, 2006 ----
Re-did xampp control panel shortcut to make it easier.

---- EDIT - August 16, 2006 ----
Added warning for public web servers and edited intro to make it more accurate.

---- EDIT - September 1, 2006 ----
Added sudo to security command.

---

### Post by gorilla_king on 2006-07-26
contained a link to my site which had this tutorial but the one i wrote.

removed because i shut down the site

---

### Post by petervk on 2006-07-27
The url is broken for me. It could be the wierd port and the firewall here at school. Do you have it mirrored somewhere else?

---

### Post by gorilla_king on 2006-07-27
> **petervk said:**
> The url is broken for me. It could be the wierd port and the firewall here at school. Do you have it mirrored somewhere else?
yeah if your at school then i'm about 95% sure that it's broken from the firewall, and no i don't mirroed at the moment because i'm just using it as a developement server.

---

### Post by petervk on 2006-07-28
So far this post has just under 200 views, So great. If you read this and use it could you leave a reply saying if it was useful/useless? I'd like to keep improving this how-to, so feedback would be good.

Plus, replies bump it up the list.

---

### Post by DC@DR on 2006-07-28
This is a very nice Howto for me, I was wondering how to make php5 and php4 developements working seamlessly together in a handy way, and now I find out that XAMPP will be my best shot now. Thanks so much for this, and I bet that many ppl will find this helpful also, keep up the good work, petervk ;)

---

### Post by millerk123 on 2006-07-30
Very useful. That link trick alone was worth it. The .tar file didn't download for me but I just went to the XAMPP website and downloaded from one of the mirrors and then followed the rest of the instructions here.

Kevin

---

### Post by Soclix on 2006-07-31
[http://localhost/soclix](http://localhost/soclix) works great but how to make it work with my ip, for my friend to have acces to [http://myip/soclix](http://myip/soclix) ?

---

### Post by adamkane on 2006-07-31
I'm biased against XAMPP. It's too unwieldy. I will be following this thread though.

Can you advise us the version of PHP and MySQL that the latest version of XAMPP installs? PHP 5.0? MySQL 5.0?

A CMS may require the use of PHP4.0 or PHP5.1 and MySQL 4.0 or MySQL 5.1.

XAMPP is pretty though.

---

### Post by gorilla_king on 2006-07-31
> **adamkane said:**
> I'm biased against XAMPP. It's too unwieldy. I will be following this thread though.

Can you advise us the version of PHP and MySQL that the latest version of XAMPP installs? PHP 5.0? MySQL 5.0?

A CMS may require the use of PHP4.0 or PHP5.1 and MySQL 4.0 or MySQL 5.1.

XAMPP is pretty though.

xampp installs the latest mysql version and gives you the option (after the install) about which version of php you would like run.

---

### Post by adamkane on 2006-08-01
Would that be php 5.1 and mysql 5.1 or php 5.0 and mysql 5.0?

Does XAMPP install php/mysql from the repositories or from inside the XAMPP package?

Does phpmyadmin need to be installed separately?

---

### Post by louieb on 2006-08-01
[FONT=Arial Black][SIZE=2]Very nice. I got a lamp development server up and running in about an hour. Download time was most of that.    It took most of the day when I put a dev server of fendora 5.  Now I would like to add the "sweet gtk/python control panel" to a menu. but I guess i will just use the command line till I get that one figured out. It all works Apache, mysql, php, phpmyadmin. You get a :KS from me.[/SIZE][/FONT]

---

### Post by petervk on 2006-08-01
Crazy huge bold text.

I updated the XAMPP Control Panel section to hopefully make it easier.

---

### Post by petervk on 2006-08-01
This is what the XAMPP package contains: (Version 1.5.3a)
From XAMPP website:
> Apache 2.2.2, MySQL 5.0.21, PHP 5.1.4 & 4.4.2 & PEAR + SQLite 2.8.17/3.2.8 + multibyte (mbstring) support, Perl 5.8.7, ProFTPD 1.3.0, phpMyAdmin 2.8.1, OpenSSL 0.9.8b, GD 2.0.1, Freetype2 2.1.7, libjpeg 6b, libpng 1.2.7, gdbm 1.8.0, zlib 1.2.3, expat 1.2, Sablotron 1.0, libxml 2.4.26, Ming 0.3, Webalizer 2.01, pdf class 009e, ncurses 5.8, mod_perl 2.0.2, FreeTDS 0.63, gettext 0.11.5, IMAP C-Client 2004e, OpenLDAP (client) 2.3.11, mcrypt 2.5.7, mhash 0.8.18, eAccelerator 0.9.4, cURL 7.13.1, libxslt 1.1.8, phpSQLiteAdmin 0.2, libapreq 2.07, FPDF 1.53, XAMPP Control Panel 0.6

It installs each one of these into /opt. Nothing is taken from the repos, and nothing in the XAMPP package needs anything outside of the XAMPP package to run. It is a self contained, presetup LAMP stack that just works. Everything listed above is installed, configured, and ready to run.

**adamkane:**
> Would that be php 5.1 and mysql 5.1 or php 5.0 and mysql 5.0?
MySQL 5.0.21
PHP 5.1.4 and 4.4.2

> Does XAMPP install php/mysql from the repositories or from inside the XAMPP package?
Inside the package.

> Does phpmyadmin need to be installed separately?
No. It is installed and ready to run.

---

### Post by rlynch on 2006-08-01
I install this, and nothing happens when I go to [http://localhost](http://localhost)

I get this error

```
The connection has timed out

      

      
      
      

      
        
        

          

The server at 127.0.0.1 is taking too long to respond.

        


        
        


    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.
```


When I do a ps -ef I get this, so I see httpd is running
```
nobody    9986  9945  0 18:47 ?        00:00:00 /opt/lampp/sbin/mysqld --basedir=/opt/lampp --datadir=/opt/lampp/var/mysql --nobody    9988  9919  0 18:47 ?        00:00:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5
nobody    9989  9919  0 18:47 ?        00:00:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5
nobody    9990  9919  0 18:47 ?        00:00:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5
nobody    9991  9919  0 18:47 ?        00:00:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5
nobody    9992  9919  0 18:47 ?        00:00:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5
nobody    9993  9919  0 18:47 ?        00:00:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5

```

---

### Post by petervk on 2006-08-01
Try restarting XAMPP first:
```
sudo /opt/lampp/lampp restart
```

Other then that, there is a Apache Friends forum:
[http://www.apachefriends.org/f/viewforum.php?f=17&sid=48cfb0ee1c82ea7359984ccbbe4184c7](http://www.apachefriends.org/f/viewforum.php?f=17&sid=48cfb0ee1c82ea7359984ccbbe4184c7)

XAMPP Linux FAQ:
[http://www.apachefriends.org/en/faq-xampp-linux.html](http://www.apachefriends.org/en/faq-xampp-linux.html)

I'll try to help, but I really don't know much.

Oh, do you have some form of firewall running? That may be blocking local http. (Port 80)

---

### Post by Face1 on 2006-08-01
I have a question about this.  I have a fat32 partition that I would like to have my development websites on.  Is this possible to do?  I tried creating a soft link in /opt/lampp/htdocs to a folder on the fat32 partition, but it does not seem to do anything...In the directory listing for localhost/ there is only one html file that I put there.   (I took out the default files)

---

### Post by petervk on 2006-08-01
I don't think it is possible to create a soft link to a fat32 drive. I'm pretty sure its a ext2/3 only thing and cannot span different filesystems.

What you can do is change the "DocumentRoot" in the httpd.conf file for XAMPP.

Open a terminal:
```

sudo cp /opt/lampp/etc/httpd.conf /opt/lampp/etc/httpd.conf.backup
sudo gedit /opt/lampp/etc/httpd.conf

```

Now Scroll down to the line:
```
DocumentRoot "/opt/lampp/htdocs"
```
and change it to point to your fat32 drive. (? "/media/fat32/" ?) 

I'd suggest to point it only to a web subdirectory on the drive as serving up the root of the drive will put all of the files on it onto the webserver and allowing anyone to view them.

Changing this will make the fancy [http://localhost/xampp](http://localhost/xampp) test stuff stop working. (It is installed into /opt/lampp/htdocs/) Everything else should work.

Hope that helps.

---

### Post by adamkane on 2006-08-01
Nice.

Has anyone tried to add new users to mysql through phpmyadmin? Are you able to easily add new users for each database you've 
created? 

Can the XAMPP /opt directories be zipped up whole, and redeployed after a meltdown?

---

### Post by petervk on 2006-08-01
From phpmyadmin.net site:

Features of phpmyadmin:
manage MySQL users and privileges

So I'm assuming yes. I haven't tried it, but I'm sure you can do everything with phpmyadmin as it is the best web interface for mysql.

Backup: 
[http://www.apachefriends.org/en/faq-xampp-linux.html#backup](http://www.apachefriends.org/en/faq-xampp-linux.html#backup)
(The site's a little screwed up, just ignore the "XAMPP runs, but none of the images are shown?" section there, the backup how-to is right after it.)

According to the above guide all you have to do is keep the original tar.gz XAMPP archive and the xampp-backup-DD-MM-YY.sh file and you should be good. Just reinstall XAMPP and run the sh script to restore the backup.

---

### Post by Face1 on 2006-08-01
> **petervk said:**
> I don't think it is possible to create a soft link to a fat32 drive. I'm pretty sure its a ext2/3 only thing and cannot span different filesystems.

What you can do is change the "DocumentRoot" in the httpd.conf file for XAMPP.

Open a terminal:
```

sudo cp /opt/lampp/etc/httpd.conf /opt/lampp/etc/httpd.conf.backup
sudo gedit /opt/lampp/etc/httpd.conf

```

Now Scroll down to the line:
```
DocumentRoot "/opt/lampp/htdocs"
```
and change it to point to your fat32 drive. (? "/media/fat32/" ?) 

I'd suggest to point it only to a web subdirectory on the drive as serving up the root of the drive will put all of the files on it onto the webserver and allowing anyone to view them.

Changing this will make the fancy [http://localhost/xampp](http://localhost/xampp) test stuff stop working. (It is installed into /opt/lampp/htdocs/) Everything else should work.

Hope that helps.

I did this but I get a 403 forbidden error.

---

### Post by Dylan103 on 2006-08-02
I followed the tut, but when I goto [http://localhost](http://localhost), i get this
> 
Index of /

Icon  Name                    Last modified      Size  Description

Apache/2.0.55 (Ubuntu) Server at localhost Port 80


---

### Post by Dylan103 on 2006-08-02
I followed the tut, but when I goto [http://localhost](http://localhost), i get this
> 
Index of /

Icon  Name                    Last modified      Size  Description

Apache/2.0.55 (Ubuntu) Server at localhost Port 80


---

### Post by adamkane on 2006-08-02
I would assume yes too, but that isn't always the case with new apps on Ubuntu. Most apps that deal with users and permissions need to be packaged by a MOTU to function properly in Ubuntu.

See mysql-admin for example. Very hard to add new users thanks to the unique way that Ubuntu deals with sudo and permissions. Many other apps will not install/run thanks to sudo.

Right now the only reason to recommend xampp is that you have access to php 5.1, which is necessary for certain applications.

For those that require mysql4 or php4, xampp looks to be no good. Perhaps there are earlier versions of xampp that allow this.

And of course, if you can backup and redeploy, then it's, "Yeah, baby! Yeah!"

It will be a few days before I can find out for myself and report.

---

### Post by fireflymantis on 2006-08-02
I'm just wondering how upgrading is handled. Is the functionality built in or do you have to manually do updates?

---

### Post by adam.tropics on 2006-08-02
All was great and working until I did the reccomended security settings. So I am new to this side of things, but should the passwords I set not work with my username, or is there a default username, or is this an issue because in Ubuntu i have to run the security thing as sudo?

---

### Post by bulldog on 2006-08-02
If I'm correct the default username is set to "lampp".
This should work with the password you have set.
This info I saw when I run the security options.
Set another password myself and shall now test :p to see if it will work again.

---

### Post by petervk on 2006-08-02
**Face1:**
That looks like a permissions problem. Check the permissions on the directory you are accessing. It's possible that the httpd program cannot access the data therefore giving you a 403 error. If you keep having problems you could consider changing your fat32 drive to ext3 and use the ext2ifs driver for windows: [http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm) Or possibly shrink your fat32 partition and create a special ext3 web development partition. 

One thing about the ext2ifs driver: I would not recommend enabling access to your root directory through windows. Windows may screw it up. I wouldn't even give it access to your home partition (If you have it on a seperate partition). Windows makes a lot of files secretly and can mess up ext3 partitions so its best to limit its access to a controlled area.

**Dylan103:**
Did you do the "DocumentRoot" change over? Because it looks like it is pointing to an empty directory insted of the normal "/opt/lampp/htdocs"
Open the /opt/lampp/etc/httpd.conf file and check where the "DocumentRoot" is pointing too. It should be /opt/lampp/htdocs. If you changed it on purpose make sure there is something in the directory. XAMPP will not display just any file in the directory, because it hides some for security. Insert a text file or a folder to see if it is working. Apache will not just display your *.html files as it hides them, it will only start displaying your webpage if the home page is named index.html/.php.

Keep posting your questions, and I'll try to keep answering them.

---

### Post by petervk on 2006-08-02
**adamkane:**

Adding a user in phpmyadmin:

[[IMG]http://img208.imageshack.us/img208/5792/screenshotlocalhostlocalhostphpmyadmin281firefoxtx1.th.png[/IMG]](http://img208.imageshack.us/my.php?image=screenshotlocalhostlocalhostphpmyadmin281firefoxtx1.png)

[[IMG]http://img308.imageshack.us/img308/181/screenshotlocalhostlocalhostphpmyadmin281firefox1qy1.th.png[/IMG]](http://img308.imageshack.us/my.php?image=screenshotlocalhostlocalhostphpmyadmin281firefox1qy1.png)

Everything seems to just work. I'm no mysql expert, but I just created a random user with any permissions I wanted.

---

### Post by rlynch on 2006-08-02
> **rlynch said:**
> I install this, and nothing happens when I go to [http://localhost](http://localhost)

I get this error

```
The connection has timed out

      

      
      
      

      
        
        

          

The server at 127.0.0.1 is taking too long to respond.

        


        
        


    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.
```


When I do a ps -ef I get this, so I see httpd is running
```
nobody    9986  9945  0 18:47 ?        00:00:00 /opt/lampp/sbin/mysqld --basedir=/opt/lampp --datadir=/opt/lampp/var/mysql --nobody    9988  9919  0 18:47 ?        00:00:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5
nobody    9989  9919  0 18:47 ?        00:00:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5
nobody    9990  9919  0 18:47 ?        00:00:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5
nobody    9991  9919  0 18:47 ?        00:00:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5
nobody    9992  9919  0 18:47 ?        00:00:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5
nobody    9993  9919  0 18:47 ?        00:00:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5

```

bump. . .are there maybe some logs I could paste or something?

---

### Post by petervk on 2006-08-03
I don't really know. What have you tried?

I replied to you in this post: [http://ubuntuforums.org/showpost.php?p=1326864&postcount=16](http://ubuntuforums.org/showpost.php?p=1326864&postcount=16)

Did you try restarting XAMPP?

Did you check to see if a firewall is blocking the connection?

You could try removing XAMPP and reinstalling.

Try the above things and re-post what you did and what happened.

---

### Post by rlynch on 2006-08-03
> **petervk said:**
> I don't really know. What have you tried?

I replied to you in this post: [http://ubuntuforums.org/showpost.php?p=1326864&postcount=16](http://ubuntuforums.org/showpost.php?p=1326864&postcount=16)

Did you try restarting XAMPP?

Did you check to see if a firewall is blocking the connection?

You could try removing XAMPP and reinstalling.

Try the above things and re-post what you did and what happened.



I've definately tried restarting it. Rebooting, stopping, and starting it. I don't get errors when starting, each service(apache,php,mysql,proftpd) all start and stop without errors(reported by the stopping and starting).

how can I check for a firewall?

I have did the rm command posted on the xampp site, to uninstall. reinstall it, and repeated this each time I decide to try and get it working again.


Sorry I didn't reply to your last post, I thought you were talking to someone else.

---

### Post by petervk on 2006-08-04
Thanks for replying.

If your still getting a "Connection is timed out" error it could be a firewall. By default Ubuntu doesn't have any form of firewall, so nothing should stop xampp.

Have you installed firestarter? or another firewall program? Have you modified anything to do with iptables? What version of Ubuntu are you using?

---

### Post by louieb on 2006-08-04
> **petervk said:**
> Crazy huge bold text.

I updated the XAMPP Control Panel section to hopefully make it easier.
[SIZE=2]
I tried the method you sugested for adding the control panel to a menu,  it did not work.
 What I wound up doing was going into the alacarte menu editor and open up the group I wanted the xxamp control pannel to be in. Then opened File > New Entry Gave it a name and in the [COLOR="Indigo"]command text box entered:[/COLOR] ```
gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py" 
```  
 Works liked a champ. and I learned how to add a python program to a menu.[/SIZE]

---

### Post by Aurdal on 2006-08-05
How can I use Mysql-Administrator with XAMPP when I tried to connect to localhost with it I got the following error:

```
Could not connect to host 'localhost'.
MySQL Error Nr. 2002
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Click the 'Ping' button to see if there is a networking problem.
```

---

### Post by stryderjzw on 2006-08-05
Oops.

---

### Post by petervk on 2006-08-08
I'm sort of confused, is the mysql-administrator something included in the XAMPP package, or are you trying to get a Ubuntu package to interface with the XAMPP mysql?

I looked at the mysql-administrator page at MySQL AB's site and you should be able to do everything in phpmyadmin, which is included with the XAMPP package. I've heard rumors of a problem with the mysql-administrator package in Ubuntu (Sudo issues? Could someone confirm?) You could try downloading the tar.gz package from MySQL AB and installing that into /opt to try out the official package.

This is really outside my experience and I'm sort of shooting in the dark. If someone else could better help Aurdal it would be greatly appreciated.

---

### Post by Contrid on 2006-08-12
> **louieb said:**
> [SIZE=2]
I tried the method you sugested for adding the control panel to a menu,  it did not work.
 What I wound up doing was going into the alacarte menu editor and open up the group I wanted the xxamp control pannel to be in. Then opened File > New Entry Gave it a name and in the [COLOR=Indigo]command text box entered:[/COLOR] ```
gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py" 
```  
 Works liked a champ. and I learned how to add a python program to a menu.[/SIZE]

Thanks alot for that! Though I guess I don't really need the control panel, it's nice to have it. :)

---

### Post by az on 2006-08-12
> **petervk said:**
>  But it isn't that easy. Installing Apache, PHP, mySQL, Proftp, perl, etc and setting them all up to work properly together could take someone a week. (Someone with experience could probably do this in a few hours) 

Actually, it takes about four minutes using Ubuntu Dapper.

Not that Xampp is a bad thing, but that statement is wrong.

---

### Post by petervk on 2006-08-13
Ok, you may be right. I haven't actually tried it. I'll add a disclaimer.

---

### Post by jonny on 2006-08-14
I hate to sound negative, but I can't recommend this method of getting a development environment up and running unless you absolutely need MySQL 5.  In particular, do not under any circumstances be tempted to use XAMPP on a PC that has any ports exposed to the internet unles you're absolutely certain that you know what you're doing.  XAMPP is a development tool and should not be used on production boxes.

The Ubuntu way is to use software out of the repositories wherever possible.  That means that you get:

 - automatic security updates 
 - secure default settings
 - guaranteed interoperability of software packages
 - an effortless upgrade to Edgy.

These things are important, and shouldn't be lightly dismissed.

In Warty, Breezy and Hoary, setting up a LAMP server needed a fair bit of fiddling, but everything is superbly well engineered in Dapper.  Just do ```
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server phpmyadmin
``` and everything will work perfectly.

I've used XAMPP in Windows, as a WAMP server is a real pig to get running smoothly.  But it's really not appropriate for ubuntu.

---

### Post by petervk on 2006-08-14
I found this:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Still a little confusing though.

I'll try it out and possibly write a new how-to using official Ubuntu sources.

---

### Post by az on 2006-08-14
> **petervk said:**
> I found this:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Still a little confusing though.

I'll try it out and possibly write a new how-to using official Ubuntu sources.

Any improvements you can give that page are welcome.  Anyone can edit the wiki to improve it.

And what would really rock is if you could find out all of the ubuntu packages in universe that match Xampp applications and how to install and configure them.  I'm certain that the xampp control panel and some artwork is not packaged for Ubuntu, but most of the other tools are.

The advantage would be that someone could take only the neccessary bits they want from an xampp development environment and put it on a production box more easily that way.

---

### Post by Contrid on 2006-08-15
I really wish I knew how to install an SMTP server.
This is simply for the use of the PHP mail(); function.
Maybe someone has a link to a resource for me.

---

### Post by petervk on 2006-08-15
> **Contrid said:**
> I really wish I knew how to install an SMTP server.
This is simply for the use of the PHP mail(); function.
Maybe someone has a link to a resource for me.

This may help:
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

Still rather complex, and I don't know what you would do for a local computer without a domain name... Maybe set the domain name to localhost? Check it out though. Postfix is a Mail agent, so basically an STMP server.

Seriously though, this: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) is a great resource. All of the forum how-tos should be migrated here.

---

### Post by dmeehan on 2006-08-15
thanks, its just what i was looking for

---

### Post by 3r14nd on 2006-08-15
Thanx for the tut...working on getting things setup now.

Got xampp installed and openssh installed and now just to download my website from the host its on now and edit it for capitalization errors and set up the picture gallery and the vBullitin and i'm done....yeah...

Thanx a million..

---

### Post by petervk on 2006-08-16
Are you using XAMPP to host a public site on your computer? I'd really recommend not using XAMPP to host a publicly accessible site. You should really use the MySQL/apache/php that is included in dapper. 

XAMPP on dapper should only be used for developement.

If it is for a public webserver you should use this:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Dapper includes everything that is in the XAMPP package (minus mySQL 5, Dapper has mySQL 4) in the main repo (or on the Dapper server cd) so it is bug tested and supported by Canonical and it the best way to get a full server running. 

Please don't use the XAMPP package for  a public webserver. You are just looking for problems and insecurity.

---

### Post by jonny on 2006-08-17
petervk, I'm glad to see that you've updated your how-to to make it perfectly clear that your target audience is developers.  XAMPP is an excellent development tool as it installs the entire LAMP stack with the latest MySQL and a few extra useful bits in next to no time.  The caveats that I raised a few posts back were purely because I was concerned that XAMPP might be misused to create publicly accessible sites.

This is now a great how-to and, although I haven't tested it myself, I wholeheartedly endorse what you're trying to achieve.

---

### Post by foxy123 on 2006-08-17
I tried to set up XAMPP on my laptop and desktop, following this howto. Laptop works fine, but on the desktop I've got th efollowing error, when try to access [http://localhost/myusername/](http://localhost/myusername/)

```
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/opt/lampp/htdocs/myusername/index.php' for
inclusion (include_path='.:/opt/lampp/lib/php') in Unknown on line 0
```

any idea what is wrong?

---

### Post by petervk on 2006-08-17
**jonny**:
Thanks. I appreciate the comment. 

I did originally intend it for a development environment (that is what I use it for) but I did have to edit the How-to to make my intentions more clear.

**foxy123**:
Looks like a permissions error to me. Check the permissions on the link you created. It should be readable by everyone, writeable by only the owner, and executeable by everyone. (Excute on a folder is just being able to open it) And check that the php files in the directory are readable by everyone.

If this doesn't work for you, reply again.

---

### Post by foxy123 on 2006-08-17
> **petervk said:**
> 
**foxy123**:
Looks like a permissions error to me. Check the permissions on the link you created. It should be readable by everyone, writeable by only the owner, and executeable by everyone. (Excute on a folder is just being able to open it) And check that the php files in the directory are readable by everyone.

If this doesn't work for you, reply again.

cheers a lot, it helped!

---

### Post by louieb on 2006-08-18
> **azz said:**
> Actually, it takes about four minutes using Ubuntu Dapper.

Not that Xampp is a bad thing, but that statement is wrong.

Please point me to the directions and I'll check that 4 min statment out.

---

### Post by hypnoticstate on 2006-08-19
Nice guide, I'm finding it very useful for testing portals and forums etc etc, but I would really like ftp access, I've used the public_html link to the correct xampp folder and everything works fine when I goto [http://localhost/grant](http://localhost/grant) however if I start an ftp client and try [ftp://localhost/grant](ftp://localhost/grant) I get asked for username and password, which is my default login, I get a directory listing that has my home folder "grant" "webalizer" and "Xampp" I can browse the files in webalizer and xampp but if I click "grant" I get 

error 550 /grant : no such file or directory.

Is this because it is just a link ? is there a workaround, I really need local ftp access, because a portal I like relies on having ftp access to the server it resides on, ie my machine.

thx in advance.

---

### Post by guyweb on 2006-08-21
Having installed Xampp to these instructions (worked perfectly, cheers!) I have a query which ive not seen anybody else ask.

I cant write anything to the htdocs directory nor can i change the permissions on the directory using the GUI - it says i am not the owner.

Therefore i cant add any webpages to the directory which is a problem!

I have not tried to create my own web root as per the instructions though. I assumed i might not need to do this and just be able to put stuff in the htdocs folder in lamp. Seems to not be the case.

Some posts here seemt o suggest that it should be possible to put things in the lapm htdocs folder. If this is the case, how do i do it?

Many thanks, Guy.

---

### Post by az on 2006-08-21
> **louieb said:**
> Please point me to the directions and I'll check that 4 min statment out.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

1.  Install LAMP and phpmyadmin and whatever else (ftp server)
2.  Set mysql root password
3.  You're done.  Apache2, php5 and mysql already talk to each other by default.

---

### Post by mobal on 2006-08-22
Can i online Update XAMPP ?

---

### Post by petervk on 2006-08-22
Pardon?

I don't understand what your asking about. Could you please restate the question with more detail.

---

### Post by louieb on 2006-08-23
There has been a lot of discussion in the thread about using xampp vs installing the Ubuntu lamp packages. So I now I've done both and this has been my experience so far. 

Because I am an expert at screwing Ubuntu up I've also become a expert at installing it. Both machines started with a fresh install from the Ubuntu 6.06 LTS Live CD. and then software updates were installed.

XAMPP was installed on a PII 400 348MB ram. 
Using the instructions posted at the start of this thread XAMPP was downloaded and installed in about 30 minutes. Mysql is running and Phpmyadmin works. and I had my browser displaying one of my web pages about 10 min later.  

Ubuntu Lamp was installed on a PIII 433 256MB ram.
Using instructions at [https://help.Ubuntu.com/community/ApacheMySQLPHP]("https://help.Ubuntu.com/community/ApacheMySQLPHP")
the lamp package was downloaded an installed in about 30 minutes. 
```
sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server
sudo aptitude install of phpmyadmin

```
MYSQL is running. At this point Apache is running but is not talking to PHP.

The instruction page has a troubleshooting section for PHP. Took 5-10 minutes to follow and run the commands in that section. Restarted Apache and tried again. Apache is still not talking to PHP.  

For what I wanted to do which is set up a development web server XAMPP was the easiest. I followed the installation instructions and it worked.

Ubuntu lamp install was the second easiest even after I take the time to go over the Apache - PHP interface to figure out what is wrong. When I say it is the second easiest I mean it is mostly working now after spending only about 35-40 minutes. 

It took me most of a day to set up a LAMP development server on Fedora 5.

This is the reason I took up Linux. I was trying to set up a development server using Windows XP, IIS, PHP5 and MYSQL. It was a pain to get the parts to work together. I finally scraped IIS and installed Apache on the windows box and it was able to get that working.  At that point I realized I was close to having my own LAMP machine all I needed was Linux. So I went to Fry's and bought a book that had some Linux distributions. It's been interesting.

---

### Post by amaechler on 2006-08-24
Thanks for that great tutorial, that's exactly what I've been looking for! Works out of the box on dapper=D>

---

### Post by petervk on 2006-08-24
**louieb**:
Thanks for that test. I always meant to do that myself just so I could see how hard it is.

I still think the official *AMP packages are the best way to do it, but the XAMPP package is really quick and easy. (And no messing around with trying to get php & apache talking, as it just works)

But I'm confused, **azz** said eailier in this thread:
> [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

1. Install LAMP and phpmyadmin and whatever else (ftp server)
2. Set mysql root password
3. You're done. **Apache2, php5 and mysql already talk to each other by default**. (bold added by me)

**azz**: 
Could you help clear this up? Is there any reason that for louieb php & apache didn't get setup right?

---

### Post by GordonWright on 2006-08-31
Tried following the instructions but being a complete noob I'm having difficulties (at the risk of sounding like a heretic I had no problems installing Xampp on my XP machine, guess I'll grow to love Ubuntu).

I downloaded Xampp tarball to the desktop and then followed the instructions as best I could but at the first stage 

> sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt  

I keep getting file or directory does not exist/ can't be found (or similar, I'm at work right now so don't have the machine to hand to transcribe exactly).

I suspect my problem may be with

 > (make sure you are in the directory that you downloaded the archive to)

Tried extracting and copying across to /opt but I get the you do not have permission message.  Do I need to log in as root to allow this process?

---

### Post by petervk on 2006-08-31
**GordonWright**:
"make sure you are in the directory that you downloaded the archive to" means if you downloaded it to your home directory you should be in your home directory.

You may have typed the file name wrong, try typing:
```
sudo tar xvfz xampp-linux[TAB] -C /opt
```
Hitting the tab key will autocomplete the line with the true file name. (If the xampp-linux* file is in the directory you are currently in.)

And, yes. /opt is protected. You don't need to be logged in as root to access it though. Hit Alt-F2 and type in "gksudo nautilus" to start up a root file browser. Be careful though, don't delete or move anything else or you'll seriously screw up your computer.

Tell me if you get it working.

---

### Post by GordonWright on 2006-08-31
OK thanks for the help.  I still get the error running in the terminal but used nautilus to copy and paste it across and it is now running, but...

Trying to get the control panel to work I get this message in the terminal when running the following code

> gedit ~/.local/share/applications/xampp-control-panel.desktop

** (gedit:6078 ): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.


So although it opens the file for pasting the text when it comes to saving it  says file doesn't exist.  It's no real biggie though next step for me is to decide on Joomla, Mambo, Drupla or a.n.other...

Many thanks for your help petervk:)

---

### Post by petervk on 2006-08-31
Your welcome.

I guess the only disclaimer I have is that I hope you are just using xampp for just developing a website. It is really easy to setup and everything but the official ubuntu packages for mysql, php, apache, perl, and [Drupla](http://packages.ubuntu.com/dapper/web/drupal) are the best way to do a public server. They have security measures in place (unlike xampp which is wide open) and will automatically upgrade with ubuntu.

But anyways, have fun!

---

### Post by az on 2006-08-31
[QUOTE=petervk;1416819**azz**: 
Could you help clear this up? Is there any reason that for louieb php & apache didn't get setup right?[/QUOTE]

I dunno.  It works out-of-the-box.  It's packaged that way.

You cannot have both php4 and php5 using apache at the same time.  Perhaps if someone tries to do that, they will get into trouble.

But if all you do is install a fresh Dapper box and run
sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server
sudo aptitude install of phpmyadmin

all you have to do is set the mysql password and you are done.

And the download is about 40 megs or so, which is downloaded and installed in about two minutes.  I don't know why it took 30 minutes to download for him.

---

### Post by petervk on 2006-08-31
**azz:**
Thanks. I can't currently try it but thanks for replying.

---

### Post by GordonWright on 2006-08-31
> **petervk said:**
> Your welcome.

I guess the only disclaimer I have is that I hope you are just using xampp for just developing a website.

:lol: Yeah just developing something locally.  Thanks for all your help, I'm sure as I get to grips with Ubuntu that I'll solve the control panel issue.  Am enjoying the change from M$!  Learning all the time.

Started passing the Edubuntu CDs around tech support staff for all the schools in the area :p

---

### Post by ice60 on 2006-08-31
hi, to secure everything i had to run
```
sudo /opt/lampp/lampp security
```
not
```
/opt/lampp/lampp security
```

thanks for the HowTo :)

---

### Post by az on 2006-08-31
> **petervk said:**
> **azz:**
Thanks. I can't currently try it but thanks for replying.


This is from a 600 Mhz pentium III box:

andy@andy-desktop:~$ sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server phpmyadmin
Reading package lists... 6%
andy@andy-desktop:~$ time sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2-common apache2-mpm-prefork apache2-utils libapr0 libdbd-mysql-perl
  libdbi-perl libnet-daemon-perl libpcre3 libplrpc-perl mysql-client-5.0
  mysql-server-5.0 php5-cgi php5-common php5-mysqli
Suggested packages:
  apache2-doc php-pear dbishell libcompress-zlib-perl
Recommended packages:
  mailx php5-mcrypt php4-mcrypt php5-gd php4-gd
The following NEW packages will be installed:
  apache2 apache2-common apache2-mpm-prefork apache2-utils libapache2-mod-php5
  libapr0 libdbd-mysql-perl libdbi-perl libnet-daemon-perl libpcre3
  libplrpc-perl mysql-client-5.0 mysql-server mysql-server-5.0 php5-cgi
  php5-common php5-mysql php5-mysqli phpmyadmin
0 upgraded, 19 newly installed, 0 to remove and 40 not upgraded.
Need to get 40.4MB of archives.
After unpacking, 100MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main libapr0 2.0.55-4ubuntu2 [132kB]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main libpcre3 6.4-2ubuntu1 [174kB]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main apache2-utils 2.0.55-4ubuntu2 [91.6kB]
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main apache2-common 2.0.55-4ubuntu2 [786kB]
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main apache2-mpm-prefork 2.0.55-4ubuntu2 [198kB]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main apache2 2.0.55-4ubuntu2 [35.6kB]
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main php5-common 5.1.4-0.1ubuntu1 [138kB]
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main libapache2-mod-php5 5.1.4-0.1ubuntu1 [2271kB]
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main libnet-daemon-perl 0.38-1.1 [45.9kB]
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main libplrpc-perl 0.2017-1.1 [35.0kB]
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main libdbi-perl 1.51-2 [640kB]       
Get:12 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main libdbd-mysql-perl 3.0006-1 [138kB]
Get:13 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main mysql-client-5.0 5.0.22-3ubuntu1 [6285kB]
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main mysql-server-5.0 5.0.22-3ubuntu1 [21.2MB]
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main mysql-server 5.0.22-3ubuntu1 [36.6kB]
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main php5-cgi 5.1.4-0.1ubuntu1 [4481kB]
Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main php5-mysqli 5.1.4-0.1ubuntu1 [38.0kB]
Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main php5-mysql 5.1.4-0.1ubuntu1 [22.2kB]
Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe phpmyadmin 4:2.8.1-1 [3607kB]
Fetched 40.4MB in 1m9s (583kB/s)                                               
Preconfiguring packages ...
Selecting previously deselected package libapr0.
(Reading database ... 104838 files and directories currently installed.)
Unpacking libapr0 (from .../libapr0_2.0.55-4ubuntu2_i386.deb) ...
Selecting previously deselected package libpcre3.
Unpacking libpcre3 (from .../libpcre3_6.4-2ubuntu1_i386.deb) ...
Selecting previously deselected package apache2-utils.
Unpacking apache2-utils (from .../apache2-utils_2.0.55-4ubuntu2_i386.deb) ...
Selecting previously deselected package apache2-common.
Unpacking apache2-common (from .../apache2-common_2.0.55-4ubuntu2_i386.deb) ...
Selecting previously deselected package apache2-mpm-prefork.
Unpacking apache2-mpm-prefork (from .../apache2-mpm-prefork_2.0.55-4ubuntu2_i386.deb) ...
Selecting previously deselected package apache2.
Unpacking apache2 (from .../apache2_2.0.55-4ubuntu2_i386.deb) ...
Selecting previously deselected package php5-common.
Unpacking php5-common (from .../php5-common_5.1.4-0.1ubuntu1_i386.deb) ...
Selecting previously deselected package libapache2-mod-php5.
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.1.4-0.1ubuntu1_i386.deb) ...
Selecting previously deselected package libnet-daemon-perl.
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.38-1.1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2017-1.1_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.51-2_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_3.0006-1_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.22-3ubuntu1_i386.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.22-3ubuntu1_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.22-3ubuntu1_all.deb) ...
Selecting previously deselected package php5-cgi.
Unpacking php5-cgi (from .../php5-cgi_5.1.4-0.1ubuntu1_i386.deb) ...
Selecting previously deselected package php5-mysqli.
Unpacking php5-mysqli (from .../php5-mysqli_5.1.4-0.1ubuntu1_i386.deb) ...
Selecting previously deselected package php5-mysql.
Unpacking php5-mysql (from .../php5-mysql_5.1.4-0.1ubuntu1_i386.deb) ...
Selecting previously deselected package phpmyadmin.
Unpacking phpmyadmin (from .../phpmyadmin_4%3a2.8.1-1_all.deb) ...
Setting up libapr0 (2.0.55-4ubuntu2) ...
Setting up libpcre3 (6.4-2ubuntu1) ...
Setting up apache2-utils (2.0.55-4ubuntu2) ...
Setting up apache2-common (2.0.55-4ubuntu2) ...
Setting Apache2 to Listen on port 80. If this is not desired, please edit /etc/apache2/ports.conf as desired. Note that the Port directive no longer works.
Module userdir installed; run /etc/init.d/apache2 force-reload to enable.
Setting up apache2-mpm-prefork (2.0.55-4ubuntu2) ...
 * Starting apache 2.0 web server...                                            apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ ok ]
Setting up apache2 (2.0.55-4ubuntu2) ...
Setting up php5-common (5.1.4-0.1ubuntu1) ...
Setting up libapache2-mod-php5 (5.1.4-0.1ubuntu1) ...
 * Forcing reload of apache 2.0 web server...                                   apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ ok ]
Setting up libnet-daemon-perl (0.38-1.1) ...
Setting up libplrpc-perl (0.2017-1.1) ...
Setting up libdbi-perl (1.51-2) ...
Setting up libdbd-mysql-perl (3.0006-1) ...
Setting up mysql-client-5.0 (5.0.22-3ubuntu1) ...
Setting up mysql-server-5.0 (5.0.22-3ubuntu1) ...
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld.
.
.
Setting up mysql-server (5.0.22-3ubuntu1) ...
Setting up php5-cgi (5.1.4-0.1ubuntu1) ...
Setting up php5-mysql (5.1.4-0.1ubuntu1) ...
Setting up php5-mysqli (5.1.4-0.1ubuntu1) ...
Setting up phpmyadmin (2.8.1-1) ...
Creating config file /etc/phpmyadmin/apache.conf with new version
Creating config file /etc/phpmyadmin/config.footer.inc.php with new version
Creating config file /etc/phpmyadmin/config.header.inc.php with new version
Creating config file /etc/phpmyadmin/config.inc.php with new version
Creating config file /etc/phpmyadmin/htaccess with new version
real    2m33.077s
user    0m41.011s
sys     0m13.953s
andy@andy-desktop:~$ 

So that's about two minute thirty seconds.  Then I browsed localhost.  See screenshots attached:

---

### Post by petervk on 2006-09-01
Wow. Thats impressive. 2m33s to a working *amp server. Amazing.

We need to do some work on the community doc's to reflect how easy this is to do. They currently look much more involved.

Thanks for the great example.

---

### Post by louieb on 2006-09-01
With the idea of setting up a web server for use on my home LAN.
I wiped out the Ubuntu install on the PIII 433 256MB ram and did an install from the Ubuntu 6.06 i386 Server CD. I used the instructions found at [http://digg.com/linux_unix/LAMP_on_Ubuntu_6_06_for_Noobs]("http://digg.com/linux_unix/LAMP_on_Ubuntu_6_06_for_Noobs") the only difference was I installed the xubuntu-desktop instead of the ubuntu-desktop. This install took about half a day. Don't know why It went so slow, it seem to take forever to install desktop portion. Installation worked. Now I am trying to find the time to setup being able to administrate the server from one of the other P.C's on the LAN.

Azz wondered why my download took 30 min when his took 2.5 min. I am on DSL and all that means is that it faster that dial-up. In fact my provider SBC global now ATT offers 3 different DSL packages with 3 different speeds. When I download here at home the speed reported is around 140 to 160 kbps whatever that means. Whenever I download something very large I try to do it at work or school. Or just start here it and go to Bed. Makes a hell of a difference using a T1 line.

---

### Post by az on 2006-09-09
> **louieb said:**
> When I download here at home the speed reported is around 140 to 160 kbps whatever that means. Whenever I download something very large I try to do it at work or school. Or just start here it and go to Bed. Makes a hell of a difference using a T1 line.

"Fetched 40.4MB in 1m9s (583kB/s)"

So for you, that should have been something like four minutes at 150 KB/s instead of 1m9s at 580 KB/s (residential cable)

---

### Post by mustang on 2006-09-11
Very very cool m8.

I've been working on a website that needs PHP + MySQL. As of late I've been using but godawfully slow host, awardspace. Eventually I planned on moving to a paid host once I am done building it but it is a huge pain to build on awardspace. No SSH so everytime you want to modify a file, it takes about 3 clicks and a lot of scrolling.

Now I'll be able to edit in gedit, hit save, and refresh. And refreshs are instant! That cuts so many barriers. Thanks again m8.

---

### Post by toykilla on 2006-09-16
I am trying to move my database into the appropriate directory, but when trying to access:

/opt/lampp/var/mysql/database

I get: 

bash: cd: nagtrocforum/: Permission denied

---

### Post by mimine on 2006-11-02
Hi everyone!

I have a two different problems:

The fist which led me to this how to is using the xampp apache server to display SVG files. I the browsers don't display the graphic and give the svg  code instead of that. I made some research and I know that it has maybe relation with the .htaccess file. BUT I DON'T FIND THIS FILE IN XAMPP !!!

The second problem is installing the "sweet" xampp control pannel. The istructions don't give any result. I am using KDE (KUBUNTU) maybe it is not the same procedure for KDE.

Thank you guys!

---

### Post by millo on 2006-11-08
Hi,

I've got a strange problem on my xampp server which is causing me confusion. ](*,) 

What I've tried to do is set up virtual hosts, which is pretty much working correctly but every time I go to the virtual host url it always redirects to a relative folder called 'xampp'. So, in effect, if I get [www.example.com](www.example.com) set up correctly on my web server as a virtual host, configure this url into the etc/hosts file, restart apache and networking and then make request for it via my browser, it will redirect me to the url [http://www.example.com/xampp](http://www.example.com/xampp).

Can anyone explain why this could happen?

I've even gotten to the point of leaving xampp shutdown and installed apache2 from synaptic package manager, successfully installed and again set up virtual hosts but it still somehow wants to go into /xampp directory. I've tried different names for the virtual folders and all kinds of things and it appears that the virtual hosts thing is working fine but just this, it always seems to redirect into a relative folder called 'xampp'.

No clue.

Much appreciated if anyone can help.

---

### Post by millo on 2006-11-08
Ahem, gulp. Oops. That was the silly cache on my browser .... Sorry.

---

### Post by Eastex Cruiser on 2006-12-08
WINDOWS XP ------ WORKGROUP SWITCH ------- UBUNTU SERVER

Is it possible for me to write to the local computer through a networked XP computer. I have XAMPP working properly on a new Ubuntu 6.10 install. But I'm now trying to upload a website through a networked XP computer, and the Ubuntu system is telling me I don't have permission. I can, however, access the XAMPP website on the same directory. (I hope this makes sense).

In other words, I have a simple network with (1) Windows XP machine, 1 switch, and 1 Ubuntu 6.10 machine using XAMPP. Can I use FTP through my XP machine to upload my GoLive websites?

---

### Post by amk221 on 2006-12-09
I followed the tutorial exactly, and it all works well

> My user name is peter so I have /home/peter/public_html linked to /opt/lampp/htdocs/peter. So if I navigate to [http://localhost/peter/](http://localhost/peter/) I get a listing of all the files/folders in that directory. (As long is there isn't a index.php/html/etc file)

But as soon as I put files in the public_html dir, I get 403 Forbidden at [http://localhost/](http://localhost/)[username]
I expect this is simple to amend, but I don't know how... cheers

---

### Post by rustncogs on 2006-12-21
*1*

---

### Post by jcroot on 2006-12-25
I'm having the same problem as the other guy...

I download the XAMPP tar file to my Desktop so I open the terminal and enter this command:

tar xvfz xampp-linux-1.5.5a.tar.gz -C /opt

But it says:

tar: xampp-linux-1.5.3a.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


----

So, I tried this:

Open Terminal: 

cd Desktop

I get this: ~/Desktop$

And then enter: 
tar xvfz xampp-linux-1.5.5a.tar.gz -C /opt

And I'm still having the same error message... I wonder why this happen? I hope somebody can give me a hand with this.

---

### Post by 5h4rk on 2006-12-30
I got a LAMP installed, I think :S

How can I uninstall it and install XAMPP?

Or shoulnt I be doing that?

:confused:

---

### Post by Gamzarme on 2007-01-01
Great forum thread you have here, Petervk. =)

Quick question: is it possible to set up some form of a control panel with XAMPP on Ubuntu server distribution? I have the server setup and serving so everything works well, although I'd now like the options to add FTP accounts, manage sub-domains and other similar tasks from a remote web interface.

So, in other words, the server I have setup is a command line, headless system that I have setup and it just..runs. Nothing complicated, but I'd like to use my other computer and Firefox to remotely configure the server.

Does XAMPP already have a form of server configuration already included in it's packages that I maybe need to up setup?

-Patrick

---

### Post by Tjoels on 2007-01-07
This was very useful. It's easy to set up and manage, and with this, you have everything in one place. - great howto! :p

I just have a problem with mySQL, cause i want to set up amarok to use mySQL, but when i make a database and user for it, granting all permissions and everything, amarok can only connect 'sometimes', and not even rescan the collection. it's very strange... Are phpMyAdmin the right tool to set up a database for amarok?

---

### Post by pgm8705 on 2007-01-11
I have the same problem. going to localhost does nothing. help would be greatly appreciated.

---

### Post by jkeirstead on 2007-01-14
Hi,

I've got the same problem as the recent posters above.  Followed all the instructions in the first post (and read the next 9 pages).  But [http://localhost/user](http://localhost/user) still gives a 403 error (where /opt/lampp/htdocs/user is a sym link to /home/user/pub_html

Thanks

---

### Post by jd4x4 on 2007-01-16
Seems like the replies to this thread are dead, but anyway...
I got the same "xampp-linux-1.5.5a.tar.gz: Cannot open: No such file or directory", etc errors as well. After trying to add the full path to the .gz name, etc., I finally moved the file to my dir under home & extracted the files. Then I did terminal and sudo mv on the lampp folder and moved it manually to /opt. But, now when I browse to localhost I get:
 "Warning: file_get_contents(lang.tmp) [function.file-get-contents]: failed to open stream: Permission denied in /opt/lampp/htdocs/xampp/index.php on line 2

Warning: Cannot modify header information - headers already sent by (output started at /opt/lampp/htdocs/xampp/index.php:2) in /opt/lampp/htdocs/xampp/index.php on line 4"

I thought maybe all of this had something to do with trying to use XAMPP under XUbuntu, but now I'm not sure.

Anyone been sucessful in using it with XUbuntu 6.10? Or how about success under any 6.10 release??

---

### Post by jd4x4 on 2007-01-16
Hmm. Well, something must have changed with 6.10, I guess. I set my firefox default download dir to my dir rather than the default Desktop, and downloaded XAMPP again. 

Then, with terminal I did "sudo tar xvfz xampp-linux-1.5.5a.tar.gz -C /opt" and it extracted fine, and localhost now works as it should in the browser!

Just to ease my pain, I also downloaded webmin from 
[http://prdownloads.sourceforge.net/webadmin/webmin_1.310_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.310_all.deb)
and then ran (right-click) "Open with GDebi Installer" from Thumber. It too, works as advertized (I'm running XUbuntu 6.10). Now, to figure out how to get the "Sweet" interface in the menu & I'm all set!

Kewl.

---

### Post by jkeirstead on 2007-01-17
Found the problem - the sym link should be the other way around.  Not from /opt/lampp/htdocs/user to /home/user/pub_html but vice versa.  

The following fixed it.
```

sudo ln -s /opt/lampp/htdocs/$USER /home/$USER/public_html
sudo chown $USER:$USER /home/$USER/public_html
```

---

### Post by jammodotnet on 2007-01-22
> **jkeirstead said:**
> Found the problem - the sym link should be the other way around.  Not from /opt/lampp/htdocs/user to /home/user/pub_html but vice versa.  

The following fixed it.
```

sudo ln -s /opt/lampp/htdocs/$USER /home/$USER/public_html
sudo chown $USER:$USER /home/$USER/public_html
```

THANK YOU tremendously.

I reinstalled XAMPP about 3 times last night, and once again today, following all these pages of advice. But your tip was/**IS** the only one that worked for me.

Now I got my WordPress development site running. :)

---

### Post by erkki70 on 2007-01-25
> **louieb said:**
> [SIZE=2]
I tried the method you sugested for adding the control panel to a menu,  it did not work.
 What I wound up doing was going into the alacarte menu editor and open up the group I wanted the xxamp control pannel to be in. Then opened File > New Entry Gave it a name and in the [COLOR=Indigo]command text box entered:[/COLOR] ```
gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py" 
``` Works liked a champ. and I learned how to add a python program to a menu.[/SIZE]

Hi there and thanx a lot for the nice tutorial.
To get the control panel working I did some mods and had it working nicely :-)
Just add ```
Categories=Application;Network;
``` before Comment=... and it will then appear in the Applications menu under Internet.
Here's my mod:
```
[Desktop Entry]
Categories=Application;Network;
Comment=Start/Stop XAMPP
Name=XAMPP Control Panel
Exec=gksudo /opt/lampp/share/xampp-control-panel/xampp-control-panel.py
Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg
Encoding=UTF-8
NoDisplay=false
StartupNotify=true
Terminal=false
Name=XAMPP Control Panel
Comment=Start/Stop XAMPP
Type=Application
Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg

```

I also noticed that Exec=... worked without specifying python "..."

Cheers,

Erkki

---

### Post by neill on 2007-01-25
hi

if i want to use xammp to run gallery 2 on a LAN server only (ie no public face), do i have to worry too much about the security stuff ?

if i do secure the install, however, what difference does that make to the users ?

thanks

neill

---

### Post by erikringmar on 2007-01-29
Hi Peter,

This is a great how-to.  However, there is something I'm not doing right.  I still get the xampp welcome message as my default for the browser.  How to get rid of it?

Erik

---

### Post by jammodotnet on 2007-01-29
> **erikringmar said:**
> Hi Peter,

This is a great how-to.  However, there is something I'm not doing right.  I still get the xampp welcome message as my default for the browser.  How to get rid of it?

Erik
so you've got XAMPP installed right?
follow the directions in your browser. they walk you through the steps to secure your installation. without securing you installation, you are leaving your system open to outside attacks.

---

### Post by erikringmar on 2007-01-29
Hi again Peter,

Thanks.  Zampp up and running, but I can't seem to redirect the browser to my home/erik directory.  How to do this?

all the best,

Erik

---

### Post by bodhi.zazen on 2007-02-03
Nice How-to

This thread has been added to the UDSF wiki.

[XAMPP](http://doc.gwos.org/index.php/XAMPP)

---

### Post by shrek on 2007-03-02
Thanks for the tutorial. The best part of my attempt to move from XP to Ubuntu is the helpful community postings. 

I am trying to setup Joomla on XAMPP and was able to follow the post up to the section on the Sweet XAMPP Control Panel. After entering the command gedit ~/.local/share/applications/xampp-control-panel.desktop in a terminal and pasting the text into the resulting window I get the following error when trying to save the document.

** (gedit:7468): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

I see at least one other person also had a problem saving the gedit file  but no solution was posted. What do I need to do, manually create the .local/share/applications/xampp-control-panel.desktop file?

---

### Post by bryand on 2007-03-15
1

---

### Post by Raval on 2007-03-17
I got the following errors:

Warning: file_get_contents(lang.tmp) [function.file-get-contents]: failed to open stream: Permission denied in /opt/lampp/htdocs/xampp/index.php on line 2

Warning: Cannot modify header information - headers already sent by (output started at /opt/lampp/htdocs/xampp/index.php:2) in /opt/lampp/htdocs/xampp/index.php on line 4

any help?

---

### Post by Raval on 2007-03-18
> **Raval said:**
> I got the following errors:

Warning: file_get_contents(lang.tmp) [function.file-get-contents]: failed to open stream: Permission denied in /opt/lampp/htdocs/xampp/index.php on line 2

Warning: Cannot modify header information - headers already sent by (output started at /opt/lampp/htdocs/xampp/index.php:2) in /opt/lampp/htdocs/xampp/index.php on line 4

any help?

Anyone, please?

---

### Post by ziadoz on 2007-03-18
> **amk221 said:**
> I followed the tutorial exactly, and it all works well



But as soon as I put files in the public_html dir, I get 403 Forbidden at [http://localhost/](http://localhost/)[username]
I expect this is simple to amend, but I don't know how... cheers

Make sure you have read access to the files. I had exactly the same problem when I copied over all my Windows XP development files. Seemed to sort it out.

---

### Post by vnt87 on 2007-03-26
Hi
I just installed XAMPP for my Edgy box using the intrusction above. But somehow when I try to start LAMPP, only Apache and ProFTPD seem to be able to start, MySQL just refuses to work (I looked at the XAMPP Control Panel and the button next to MySQL always read 'Execute' no matter how many time I click it)
Moreover, when I navigate to localhost, I got a 403 error.
Does anybody have an idea of what went wrong here?

---

### Post by unabatedshagie on 2007-03-28
This might be a silly question but I have just installed xampp but how do I get it to start every time I log in?

I can't just add **/opt/lampp/lampp start** to the startup programs because I need to have sudo infront of it to start it in a terminal.

---

### Post by gmconie on 2007-04-11
Excellent howto.

I had problems with setting up the control panel. Fixed these by: 
[LIST]
[*]manually creating the .local/share/applications directories.
[*]And then using the config file posted by erkki70.
[/LIST]
Thanks

---

### Post by cius on 2007-04-26
Wonderful HOWTO!  I've just started my personal web site and have experimented with setting my own in-house test server on an old computer.  I was having trouble when I ran across this HOWTO.  Now I have a personal server on my main machine.  After going through the "lampp security" and setting up proper passwords for everything, I may now start the heavy lifting on my site design.  Thank you again!

---

### Post by unabatedshagie on 2007-04-26
I found the following on the apache friends website. Forgive the stupid question but could someone tell me how to do this with feisty?```
After I rebooted my Linux box XAMPP stopped running! How can I fix this?
Correct. That's normal Linux behaviour (which applies to any other Unix-like system. It's the admin's job to make sure a particular application is started at bootup.

There is no real standard way to configure the boot process of a Linux system, but most of them should allow you to start XAMPP at boot time using the following steps.

   1. First, find out your default runlevel.
      Simply type egrep :initdefault: /etc/inittab.
      You should no see a line containing a number between two colons.
      In most cases 3 or 5 (2 if you're using Debian).

   2. Go into the directory which configures this runlevel. If for example your runlevel is 3, then you have to change into the /etc/rc.d/rc3.d directory.

      If your system didn't provide /etc/rc.d/rc3.d please try also /etc/init.d/rc3.d and /etc/rc3.d.
   3. Now carry out the actual configuration by typing:

      ln -s /opt/lampp/lampp S99lampp
      ln -s /opt/lampp/lampp K01lampp

Now XAMPP should start and stop automatically if you boot or shutdown your machine.
```

---

### Post by goodtimetribe on 2007-04-27
> **petervk said:**
> So far this post has just under 200 views, So great. If you read this and use it could you leave a reply saying if it was useful/useless? I'd like to keep improving this how-to, so feedback would be good.

Plus, replies bump it up the list.

Haven't used it yet, but it's my plan to after the semester's over.

---

### Post by XTREEM|RAGE on 2007-05-15
Nice almost everything worked :D
except this...
> 
[Desktop Entry]
Comment=Start/Stop XAMPP
Name=XAMPP Control Panel
Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
Icon[en_CA]=/usr/share/icons/Tango/scalable/devices/network-wired.svg
Encoding=UTF-8
Terminal=false
Name[en_CA]=XAMPP Control Panel
Comment[en_CA]=Start/Stop XAMPP
Type=Application
Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg

That didnt work for me ;x

---

### Post by XTREEM|RAGE on 2007-05-15
> **unabatedshagie said:**
> ]

i saw that 2, but didnt work :( .
Does any1 know how we can install this as a server in feisty? So it automatically start when i boot to ubuntu?

---

### Post by jingo811 on 2007-05-20
I'm thinking about creating a MySpace like community webpage and I believe Drupal can help me with that without me having to know how to code it myself.

Does anybody have any instructions on how do install Drupal properly for XAMPP?
I couldn't find any straight forward instructions over there :(

---

### Post by jammodotnet on 2007-05-21
> **jingo811 said:**
> I'm thinking about creating a MySpace like community webpage and I believe Drupal can help me with that without me having to know how to code it myself.
impossible.
it doesn't have that ability out of the box.
you would require custom coding.

> **jingo811 said:**
> Does anybody have any instructions on how do install Drupal properly for XAMPP?
I couldn't find any straight forward instructions over there :(
the instructions shouldn't be any different than installing on a server.
i've got activeCollab, WordPress and ExpressionEngine installed on my PC. they work flawlessly.
there is no difference in installation directions.

---

### Post by nousefreak on 2007-05-22
isn't there any way to make the localhost ([http://localhost/](http://localhost/)) redirect to /home/public_html and not to the XAMPP folder without the use of a subfolder

---

### Post by jnorris235 on 2007-06-16
Unbelievable! Saved so much time over the last time I installed them all separately!

However I cannot get the link to appear in the main menu with that gedit script.
Did exactly as you said, honest!

Using feisty.
It all works fine started from terminal (but terminal is a pain if you can have a shortcut!)

---

### Post by edmondt on 2007-06-16
Great HOWTO :) Nice and Easy... Latest file is 	xampp-linux-1.6.2.tar.gz at [http://sourceforge.net/project/showfiles.php?group_id=61776&package_id=60248&release_id=511815](http://sourceforge.net/project/showfiles.php?group_id=61776&package_id=60248&release_id=511815)

---

### Post by UbuNewbie123 on 2007-06-17
Any idea how to make XAMPP auto start on every boot up on Ubuntu Server?

[http://www.apachefriends.org/en/faq-xampp-linux.html#fsl](http://www.apachefriends.org/en/faq-xampp-linux.html#fsl)

The tutorial above does not seem to apply for Ubuntu Server.

---

### Post by nikkiana on 2007-06-21
> **jingo811 said:**
> I'm thinking about creating a MySpace like community webpage and I believe Drupal can help me with that without me having to know how to code it myself.

Does anybody have any instructions on how do install Drupal properly for XAMPP?
I couldn't find any straight forward instructions over there :(

It's fairly straightforward. Install XAMPP and start it, go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin), create your database, put the drupal files into the linked folder you set up for XAMPP, and then go to localhost/username and then Drupal should step you through the rest.

---

### Post by flaming_monkey on 2007-06-21
Worked great. I've now got a clean Wordpress install to start theme up. Thanks.

---

### Post by pvilleSE on 2007-06-24
Thank you, this was very useful.

---

### Post by Skavenger on 2007-06-25
> **nousefreak said:**
> isn't there any way to make the localhost ([http://localhost/](http://localhost/)) redirect to /home/public_html and not to the XAMPP folder without the use of a subfolder
I want that too

---

### Post by asmweb on 2007-06-27
> **Skavenger said:**
> I want that too

I did uninstall the xampp and installed everything separately ... but now when I type [http://localhost](http://localhost) it redirects me to [http://localhost/xampp](http://localhost/xampp) which is not. how can i make it not do the redirect. thanks

---

### Post by cosine7 on 2007-06-30
Worked Fine first go! Thanks

---

### Post by dkc on 2007-07-11
hi, 

i'm new to linux and have just installed feisty. i'm having problems installing the Sweet XAMPP Control Panel.

when i run gedit ~/.local/share/applications/xampp-control-panel.desktop and try to save the fil contents i get the error:
Could not save the file /home/dzikamai/.local/sh…mpp-control-panel.desktop.
Unexpected error: File not found

i'm assuming this directory does not exist in my feisty folder hierarchy.
does anyone know what i need to do to fix this..

regards,

zak

---

### Post by poji23 on 2007-07-11
> **asmweb said:**
> I did uninstall the xampp and installed everything separately ... but now when I type [http://localhost](http://localhost) it redirects me to [http://localhost/xampp](http://localhost/xampp) which is not. how can i make it not do the redirect. thanks

Look in /opt/lampp/htdocs/index.html and you'll see there's this line of html code:

<meta http-equiv="refresh" content="0;url=/xampp/">

That line redirects to the /xampp folder. Just remove that line and place your files in the /opt/lampp/htdocs/ and you should be good to access [http://localhost/](http://localhost/)

---

### Post by texplorer on 2007-08-01
I cannot see the test page, I am getting the following error. I guess the permission to the folder is not sort out. 
I cannot see the control panel either.

Thanks,

Warning: file_get_contents(lang.tmp) [function.file-get-contents]: failed to open stream: Permission denied in /opt/lampp/htdocs/xampp/index.php on line 2

Warning: Cannot modify header information - headers already sent by (output started at /opt/lampp/htdocs/xampp/index.php:2) in /opt/lampp/htdocs/xampp/index.php on line 4

---

### Post by svalley on 2007-08-02
the instructions that arrived with xampp_ubuntu didn't work; yours worked perfectly

thank you for your perfectly useful posting on installation/running xampp!

---

### Post by guysmiley on 2007-08-11
I too am receiving the error:

> 
~/.local/share/applications/xampp-control-panel.desktop and try to save the fil contents i get the error:
Could not save the file /home/dzikamai/.local/sh…mpp-control-panel.desktop.
Unexpected error: File not found

How can this be fixed?

---

### Post by babacan on 2007-08-13
Hey lads I have 2 questions:
-Does XAMMP open a vulnerable port which is risky?

-I want to edit php.ini but it is under root privilage. How can I fix this so I can edit php.ini?

Cheers

---

### Post by NDPeter on 2007-08-13
Just ran through this in about 10 minutes!  Consider it impressive since I've just switched to ubuntu and have the usual aversion to using the terminal...however, I'm not a complete stranger to doing stuff that way.  Still very quick and it's all working I think.  

Thanks!

---

### Post by christom on 2007-08-15
> **guysmiley said:**
> I too am receiving the error: ..*.(of not being able to get the menu item for the Control Panel to work)* ... How can this be fixed?

I had the same problem, and fixed it by saving the file  "xampp-control-panel.desktop" to the folder "/usr/share/applications",which is where all my menu applets are saved (i.e. not in the "~/.local" folder, which does not exist on my installation of feisty; the original instructions involving that directory did not work at all.)
```

sudo gedit /usr/share/applications/xampp-control-panel.desktop

```
The code as published on page 1 of this thread did not work either. The code that worked was:
```

[Desktop Entry]
Encoding=UTF-8
Name=XAMPP Control Panel
Comment=Start and Stop XAMPP
Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg 
Terminal=false
Type=Application
Categories=GNOME;Application;Network;
StartupNotify=true

```
I had to unmark and remark the menu item in Alacarte before it appeared in my Applications|Internet menu. Reloading would likely have accomplished the same.

---

### Post by kingersoll on 2007-08-16
I have this PHP script on my working XAMPP server:
```
<?php
touch("test.txt");
?>
```

But no matter what permissions I set that script to (it's currently 777), I can't seem to create that file!
> Warning: touch() [function.touch]: Unable to create file test.txt because Permission denied in /opt/lampp/htdocs/test.php on line 2

HELP!

---

### Post by speedy23 on 2007-08-30
hello,
I dowloaded xampp 1.6.3b. and when i try to run xampp, 
there is an error like: "xampp is currently on availably as 32 bit application. Please use a 32 bit compatibility library for your system".
My system is 64bit, core 2 duo and my ubuntu s also 64 bit. What can I do to start xampp. Thanks in advance...

---

### Post by bjorntheart on 2007-08-30
> **gorilla_king said:**
> xampp installs the latest mysql version and gives you the option (after the install) about which version of php you would like run.

Is there a way to switch from MySQL 5.0.45 to 4.0.26 in LAMPP like you can switch between PHP4 and PHP5?

---

### Post by rwizibuntu on 2007-09-04
Thanks for this tutorial the installation was fine, I get all xampp test pages.
However, I have failed to get my local sites in the browser. I copied one of my site folder to myname/public_html, when say [http://localhost/mysite](http://localhost/mysite) i do not get it.  Where should i place my site files
thanks

---

### Post by TeaSwigger on 2007-09-04
Hello, I'm not the original poster nor do I profess to be an "expert," but merely someone who has used XAMPP successfully for some time now. Since the questions are seeming to go unanswered I'll attempt to address some starting from most recent.

bjorntheart,

No, but I don't know if it's overly difficult as I've not tried it. If a version difference should make it necessary, say you're using 5x and your host is back in 4x, you can try MySQL's compatibility settings when exporting / importing databases.

rwizibuntu,

Probably getting locations and/or permissions mixed. Which is very easy to do!

The easiest way to go may be as described in the HowTo. But let's try this with a more specific example. Let's say that, like the HowTo instructs, XAMPP was installed in /opt so that it's located at /opt/lampp. Let's say that your user name is oscarmoore. You want the folder containing the web projects to be in your home folder and want it to be called "woodshed." The folder containing your actual project website is named kingcoletrio, inside which is the index or root page for the site.

First you would need to create a folder in your home folder named "woodshed," just like you'd make any new folder. Then you would make "woodshed" into a "symlink" or symbolic link, putting the "real" folder into htdocs. You would have to do this operation using "sudo" (root permission) and associate it with your user in order to have permissions to use that folder, since your user name won't have permissions to manipulate files in /opt by default. To do this you would simply enter the following in a terminal:

```
sudo ln -s ~/woodshed /opt/lampp/htdocs/$USER
```

Explanation of example code: "sudo" to have root permissions to put something in /opt, "ln -s" meaning "create a symbolic link," ~/woodshed meaning you want to make the folder "woodshed" into the link ( ~/ means it's located in your home directory) and "/opt/lampp/htdocs/$USER" telling it where to put it, with $USER meaning "name it after my user name and give me permissions within it." Code sure saves a lot of typing lol

So what you'd have is a folder called /home/oscarmoore/woodshed that's really a link to the real folder which is /opt/lampp/htdocs/oscarmoore. Just think, installing a "real" public webserver gets way, way more complicated... :p

Okay, you'd plop your project folder, kingcoletrio, into the woodshed folder. On your computer then it'd be accessible at:
/home/oscarmore/woodshed/kingcoletrio
or at its real location of:
/opt/lampp/htdocs/oscarmoore/kingcoletrio

In the browser you'd access the site at:
```
http://localhost/oscarmoore/kingcoletrio
```

Do you see how the layout works now? This stuff takes some getting used to but its amazing technology. Good luck and enjoy webbing :)

---

### Post by TeaSwigger on 2007-09-04
> **speedy23 said:**
> hello,
I dowloaded xampp 1.6.3b. and when i try to run xampp, 
there is an error like: "xampp is currently on availably as 32 bit application. Please use a 32 bit compatibility library for your system".
My system is 64bit, core 2 duo and my ubuntu s also 64 bit. What can I do to start xampp. Thanks in advance...

Unfortunately XAMPP isn't available for 64 bit architecture. That doesn't mean you couldn't use it somehow; I'm sure it can be done. You'll have to search for information regarding running 32bit apps on 64bit systems or perhaps inquire in the 64bit focused forum here.

---

### Post by TeaSwigger on 2007-09-04
> **kingersoll said:**
> I have this PHP script on my working XAMPP server:
```
<?php
touch("test.txt");
?>
```

But no matter what permissions I set that script to (it's currently 777), I can't seem to create that file!

Quote:
Warning: touch() [function.touch]: Unable to create file test.txt because Permission denied in /opt/lampp/htdocs/test.php on line 2 
HELP!

Ah kinda hard to say from here... Have you checked that you have write access in the /opt/lampp/htdocs directory? Wouldn't by default. Suggest you have all relevant files for the project incl. that test.php file in a subdirectory which your user owns. Also make sure the database files aren't read only. Not sure what else to suggest with info provided.

---

### Post by niceguy123 on 2007-09-04
[*]Extract the archive to /opt using sudo: (make sure you are in the directory that you downloaded the archive to) ```
sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt
```
[/LIST]

Sorry for  obvious situation - I am very new to Unubtu:

What do you mean  >  (make sure you are in the directory that you downloaded the archive to)

I downloaded the gz to a folder  myname/downloads

I tried running ```
sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt
``` and got ```
tar: xampp-linux-1.5.3a.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

What do I do from here?

===sorry about this, I figured it out=== (Would have deleted the whole post, but that option I couldn't find.

---

### Post by niceguy123 on 2007-09-04
OK, now its running on my system. Localhost shows the test page. But after doing through the below stages I still don't see the XAMPP control panel.

Any ideas?> 

[SIZE="3"]**_Sweet XAMPP Control Panel_**[/size]

[img]http://img108.imageshack.us/img108/5647/screenshotxamppcontrolpanelfj6.png[/img]

To use the sweet gtk/python control panel:

Run in a terminal: ```
gedit ~/.local/share/applications/xampp-control-panel.desktop
```

Paste the following into the open file and save and exit.
```
[Desktop Entry]
Comment=Start/Stop XAMPP
Name=XAMPP Control Panel
Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
Icon[en_CA]=/usr/share/icons/Tango/scalable/devices/network-wired.svg
Encoding=UTF-8
Terminal=false
Name[en_CA]=XAMPP Control Panel
Comment[en_CA]=Start/Stop XAMPP
Type=Application
Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg
```
"XAMPP Control Panel" will show up in your applications menu under Internet. Use the Alacarte Menu Editor to move it around.

[SIZE="3"]**_Test to see if XAMPP is running_**[/size]

Once XAMPP is up and running open firefox and go to: [http://localhost/](http://localhost/)

You should see the XAMPP test page:

[IMG]http://static.apachefriends.org/images/380.jpg[/IMG]

---

### Post by TeaSwigger on 2007-09-04
> **niceguy123 said:**
> OK, now its running on my system. Localhost shows the test page. But after doing through the below stages I still don't see the XAMPP control panel.

Any ideas?

Hello,

If you mean that you have used the menu entry and it won't open, please do the following:

Open a terminal and enter:

```
gksudo python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py
```

The reason for this is that there may be certain things needed to display the control panel that are not yet installed on your system. By entering that command in the terminal, it will try to open it and may give us error messages that we can use to find out what is missing.

In the meantime you can run XAMPP just fine without it by entering this in a terminal: 

```
/opt/lampp/lampp start
```

It will tell you it's starting the three main components. Once it's started you can close the terminal and enjoy your new XAMPP. To stop it you do the same, just enter stop in place of start :)

There are other commands you can use listed at their web page:
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

:guitar:

---

### Post by niceguy123 on 2007-09-05
[QUOTE=TeaSwigger;3310599]Hello,

If you mean that you have used the menu entry and it won't open, please do the following:

Open a terminal and enter:

```
gksudo python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py
```

OK, I did that and the XAMPP Control Panel opened up on my screen - Great - Thanks.

Next question - I'd like to have a icon under  Applications>internet

---

### Post by TeaSwigger on 2007-09-05
> **niceguy123 said:**
> OK, I did that and the XAMPP Control Panel opened up on my screen - Great - Thanks.

Next question - I'd like to have a icon under  Applications>internet

Excellent, everything's already installed for you then. Okay to make an entry in Applications > Internet in ubuntu:

Go to System > Preferences > Main Menu. A handy menu editor will come up. Select the Internet list. If it isn't already there, you can make an entry for it. Select New Item. A box will come up. Select Application and enter the name, XAMPP Control Panel. In command, put this:

```
gksudo python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py
```

Icon and comments are optional. XAMPP has a .gif icon in /opt/lampp/htdocs that you could use, or if it has to be .xpm or .png format it should be a snap to convert it in GIMP or some such. Hope that does the trick. :)

---

### Post by webtroy on 2007-09-06
...

---

### Post by wildgene789 on 2007-09-26
nice tutorial but im getting stuck at "sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt" now i web into desktop on terminal desktop and did the command. This is wat i get
> crossfire@CrossfiresServer:~/Desktop$ su tar xvfz xampp-linux-1.6.3b.tar.gz -C /opt
su: invalid option -- C
Usage: su [options] [LOGIN]

Options:
  -c, --command COMMAND         pass COMMAND to the invoked shell
  -h, --help                    display this help message and exit
  -, -l, --login                make the shell a login shell
  -m, -p,
  --preserve-environment        do not reset environment variables, and keep
                                the same shell
  -s, --shell SHELL             use SHELL instead of the default in passwd

crossfire@CrossfiresServer:~/Desktop$ 



---

### Post by UbuNewbie123 on 2007-09-26
Try sudo instead of su.

---

### Post by Kangeek on 2007-10-15
:guitar: YO. This is me first message here!
Nice and easy, about all I love with Ubuntu. The GUI part didn't work bot I still can't understand why I tried it in a first place.

On the 6 security points mentionned the 1st 3 are covered with 
$sudo /opt/lampp/lampp security
Wot about the others?... boah, don't care anyway, still 10M times more secure than MS lost yourself.

Thanks again Peter, and now, how can I have a database up and running in 5mn?:)
SAFE

---

### Post by latheesan on 2007-10-21
quick question, does the xampp automatically start on system reboot?

---

### Post by Beanz on 2007-10-27
> **Raval said:**
> I got the following errors:

Warning: file_get_contents(lang.tmp) [function.file-get-contents]: failed to open stream: Permission denied in /opt/lampp/htdocs/xampp/index.php on line 2

Warning: Cannot modify header information - headers already sent by (output started at /opt/lampp/htdocs/xampp/index.php:2) in /opt/lampp/htdocs/xampp/index.php on line 4

any help?

I got a similar error when I first installed using these instructions when trying to include files. I managed to fix it by changing the permissions of the public_html folder to allow others to read the files within that folder. I'm not sure what security risks this opens up, but as I'm the only user on my computer, I hope I'll be OK.

---

### Post by GodsDead on 2007-10-27
HEYA wow i dont hav eth time to scroll through all this thread, but i installed XAMPP to the latest version of Ubuntu (7.10 gusty)
Im new to ubuntu, but not to xampp, i have used it on many windows systems, i want it to run on my Ubuntu machine, RIGHT! go tthat working, i cant get that "menu" thing to work at all =[ (first page)

and i cant create any bloody files in /opt/lampp/htdocs/ unless i go through teh bloody terminal (or logon to my windows machine & Go through FTP) which is stupid since the machines sitting next to me! i wanna move my entire load of files over to this new machine, IF I CAN GE TIT TO WORk, AND even though i have removed the index.htm file that origionally comes with XAMPP htdocs directory, i created anotehr index.html file, but it still redirects to localhost/xampp!? 
Im goign to be useing this machine to host some files for my mates etc etc. 


=]

---

### Post by mech7 on 2007-11-05
THe control panel does not show up with me ? anbybody know what to do :(

---

### Post by Takster on 2007-11-06
> **Skavenger said:**
> I want that too

> **asmweb said:**
> I did uninstall the xampp and installed everything separately ... but now when I type [http://localhost](http://localhost) it redirects me to [http://localhost/xampp](http://localhost/xampp) which is not. how can i make it not do the redirect. thanks
Hey there.

I can explain this method i use for virtual hosts, i like to keep the xampp folder and my website folders well apart from each other, and it makes things easier in my opinion.

So what i want to do is move all my websites away into any other folder i want. I will be using the path 

> /home/tak/www/htdocs/

to store all my websites, arranged in subfolders, that have a specific domain name pointing to them. You can have as many as you like.

[COLOR="Red"]localhost.vbulletin.com[/COLOR] **>goes to>** [COLOR="RoyalBlue"]/home/tak/www/htdocs/vbulletin[/COLOR]
[COLOR="Red"]localhost.testbed.com[/COLOR] **>goes to>**  [COLOR="RoyalBlue"]/home/tak/www/htdocs/testbed[/COLOR]

I have also set up another domain using** localhost.main.com**, this link is set up to direct me to the xampp folder/frontend in **/opt/lampp/htdocs/**

What you do is...
> sudo gedit /opt/lampp/etc/httpd.conf

make sure these are uncommented  (near the bottom)
> # Virtual hosts
Include etc/extra/httpd-vhosts.conf
# Various default settings
Include etc/extra/httpd-default.conf
# XAMPP
Include etc/extra/httpd-xampp.conf

save. Now,
>  sudo gedit /opt/lampp/etc/extra/httpd-vhosts.conf

paste all this (you can change folder names later to suit yourself, my example will get you up and running first)

```

NameVirtualHost *:80

<VirtualHost *:80>
ServerName localhost.main.com
ServerAlias localhost.main.com *.localhost.main.com
DocumentRoot "/opt/lampp/htdocs/" 
ServerAdmin admin@localhost
</VirtualHost>

<VirtualHost *:80>
ServerName localhost.vbulletin.com
ServerAlias localhost.vbulletin.com *.localhost.vbulletin.com
ServerAdmin [email]admin@domain1.co.uk[/email]
DocumentRoot "/home/**YOU**/www/htdocs/vbulletin/"
<Directory "/home/**YOU**/www/htdocs/vbulletin/">
Options ExecCGI Includes FollowSymLinks
Options +ExecCGI
AllowOverride All
Order allow,deny
Allow from all
</Directory>
</VirtualHost>

<VirtualHost *:80>
ServerName localhost.testbed.com
ServerAlias localhost.testbed.com *.localhost.testbed.com
ServerAdmin [email]admin@domain1.co.uk[/email]
DocumentRoot "/home/**YOU**/www/htdocs/testbed/"
<Directory "/home/**YOU**/www/htdocs/testbed/">
Options ExecCGI Includes FollowSymLinks
Options +ExecCGI
AllowOverride All
Order allow,deny
Allow from all
</Directory>
</VirtualHost>

```

save. Close it.

Now, make  folder/s that you want for the 'server'.

I made

```
 /home/tak/**www/htdocs/**
```
inside 'htdocs' folder i make 2 more folders, **vbulletin** and **testbed**, inside each of these i put on blank **index.html** page for now.

This will be as above:
> 
localhost.vbulletin.com **>goes to>** /home/tak/www/htdocs/vbulletin/index.html
localhost.testbed.com **>goes to>** /home/tak/www/htdocs/testbed/index.html

Now we open 
> sudo gedit /etc/hosts

we add the localhost IP plus all domains for folders we are making, like so.

```
127.0.0.1	localhost
127.0.1.1	Ubuntu

[B]127.0.1.1	localhost.vbulletin.com
127.0.1.1	localhost.main.com
127.0.1.1	localhost.testbed.com[/B]

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Now, we restart xampp server, maybe clean browser cache, and point to
localhost.vbulletin.com > go to blank index page
localhost.testbed.com > also blank index.html page we make  before
localhost.main.com > xampp control/information pages.

[SIZE="3"]**To add more sites:**[/SIZE]

we add a new container for another site in virtual host:
```
<VirtualHost *:80>
ServerName localhost.newfolder.com
ServerAlias localhost.newfolder.com *.localhost.newfolder.com
ServerAdmin [email]admin@domain1.co.uk[/email]
DocumentRoot "/home/**YOU**/www/htdocs/newfolder/"
<Directory "/home/**YOU**/www/htdocs/newfolder/">
Options ExecCGI Includes FollowSymLinks
Options +ExecCGI
AllowOverride All
Order allow,deny
Allow from all
</Directory>
</VirtualHost>
```

we make folder 
 '**newfolder**' in / www/htdocs/'newfolder'

we add again in host file 
> 127.0.1.1	localhost.newfolder.com

restart xampp, navigate to new URL 'localhost.newfolder.com'.
That is it. A little complicated but well worth it at the end.

---

### Post by chalewa on 2007-11-06
Installed all of this last night, which was a breeze. Thanks a lot for the howto.

My ultimate goal is to be able to get zussaweb or another nzb webui running. Can I do this with this type of server set up?

I am very new to using a webserver, so I am basically forging my way as I go along. Thanks

---

### Post by odysseyes on 2007-12-08
I don't know if this is adressed before but I still have a small question about the setup of teh web root.

I use Ubuntu 6.06.1 on my desktop mini PC.
I managed to setup, and it works OK!

The hardware is just a MB and a 4GB IDE flash disk. (no moving parts that is)
So now I would like to set up my webroot to link to a shared volume on or network storage device.

I tried with the command:
```
sudo ln -s smb://nas-01/htdocs/ /opt/lampp/htdocs/

```

Where nas-01 is the network name of our network storage, and htdocs the name of the shared volume on it created for use as webroot

i'm relatively new to linux so I'm not really familiar with the whole idea behind ths system.

What would be the best way to archieve this ?

Thanks for helping me out!!

---

### Post by Xiong Chiamiov on 2007-12-10
Just a btw, the part that adds the control panel to the menu obviously doesn't work for those using KDE.  You might want to make a note of that, and tell them how to add things to the menu.

---

### Post by McNee on 2007-12-11
Nice tutorial, everything set up just fine... except the control panel isn't showing up. I'll have to finish reading through the replies, maybe there's a hint in there...

---

### Post by pcjunkie on 2007-12-12
I am getting errors.

unpacked to /opt
ran start command

got this

/opt/lampp/lampp: line 74: arch: command not found
Starting XAMPP for Linux 1.6.4...
/opt/lampp/lampp: line 74: arch: command not found
/opt/lampp/lampp: line 74: arch: command not found
XAMPP: Starting Apache with SSL (and PHP5)...
/opt/lampp/lampp: line 74: arch: command not found
XAMPP: Starting MySQL...
/opt/lampp/lampp: line 74: arch: command not found

Starting XAMPP for Linux 1.6.4...

Its working fine though, so far.
Thanx guys, it was a pinch

---

### Post by dhani99 on 2007-12-14
sudo /opt/lampp/lampp start
/opt/lampp/lampp: line 74: arch: command not found
Starting XAMPP for Linux 1.6.4...
/opt/lampp/lampp: line 74: arch: command not found
/opt/lampp/lampp: line 74: arch: command not found
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Error 1! Couldn't start Apache!
XAMPP: Starting diagnose...
XAMPP: Sorry, I've no idea what's going wrong.
XAMPP: Please contact our forum [http://www.apachefriends.org/f/](http://www.apachefriends.org/f/)
/opt/lampp/lampp: line 74: arch: command not found
XAMPP: Starting MySQL...
/opt/lampp/lampp: line 74: arch: command not found
XAMPP: Starting ProFTPD...
XAMPP:  - warning: unable to determine IP address of 'desktop_ubuntu'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/opt/lampp/etc/proftpd.conf'
XAMPP: Error 1! Couln't start ProFTPD!
XAMPP for Linux started.
keval@desktop ubuntu:~$ test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator

Apache couldn't start.. and gives me  this error.. any Idea...??

---

### Post by adrianmak on 2007-12-15
i installed apache, mysq, php thru synatic manager, 
does the Sweet XAMPP Control Panel work too ?

---

### Post by Furious87 on 2007-12-16
im using ubuntu gutsy gibbon server edition and running it as a router (via iptables) and im trying to setup a webserver on it. i have followed your guide and the server seem to start. but i can not connect to it. do you think that this might have something to do with my iptabels or anyhting else.

oh and y btw. somehow i dont have the lo loopback interface on the comp so i cant access it from 127.0.0.1 i rather is trying to access the webserver from the ip of the interface eth1 (internal interface) witch is 10.10.10.1. dunno if this has somthing to do with it either

---

### Post by McNee on 2007-12-16
> **adrianmak said:**
> i installed apache, mysq, php thru synatic manager,  does the Sweet XAMPP Control Panel work too ?

I would imagine it does - the instructions given just set up a menu link for it. I had to reboot to get it to show up... but on 7.10 if you right click on the Applications menu (or anywhere on the menubar) you can choose Edit Menu and add items that way as well.

I do have a question too... how do I get XAMPP to start when the computer starts so I don't have to open the control panel all the time?

---

### Post by nieldw on 2007-12-18
This was very helpful - espesially after two days of trying to setup xampp aliasses and virtual hosts. Thank you.

---

### Post by pannerrammer on 2007-12-21
> **unabatedshagie said:**
> I found the following on the apache friends website. Forgive the stupid question but could someone tell me how to do this with feisty?```
After I rebooted my Linux box XAMPP stopped running! How can I fix this?
Correct. That's normal Linux behaviour (which applies to any other Unix-like system. It's the admin's job to make sure a particular application is started at bootup.

There is no real standard way to configure the boot process of a Linux system, but most of them should allow you to start XAMPP at boot time using the following steps.

   1. First, find out your default runlevel.
      Simply type egrep :initdefault: /etc/inittab.
      You should no see a line containing a number between two colons.
      In most cases 3 or 5 (2 if you're using Debian).

   2. Go into the directory which configures this runlevel. If for example your runlevel is 3, then you have to change into the /etc/rc.d/rc3.d directory.

      If your system didn't provide /etc/rc.d/rc3.d please try also /etc/init.d/rc3.d and /etc/rc3.d.
   3. Now carry out the actual configuration by typing:

      ln -s /opt/lampp/lampp S99lampp
      ln -s /opt/lampp/lampp K01lampp

Now XAMPP should start and stop automatically if you boot or shutdown your machine.
```

Not sure if you've sorted this yet! On Gutsy, do the 2 commands in /etc/rcS.d

---

### Post by dondad on 2007-12-21
"XAMPP by default uses /opt/lampp/htdocs as the root web directory."

How can I change this to be opt/lampp  ?

---

### Post by McNee on 2007-12-27
> **dondad said:**
> "XAMPP by default uses /opt/lampp/htdocs as the root web directory."

How can I change this to be opt/lampp  ?

In the first posting, it describes how to link to a folder under your home folder - I suppose you could change that to point to opt/lampp instead.

---

### Post by dondad on 2007-12-27
> **McNee said:**
> In the first posting, it describes how to link to a folder under your home folder - I suppose you could change that to point to opt/lampp instead.

Thanks, I figured out how to do what I was trying. What I wanted was to be able to ftp into the server at the top level so I could access cgi-bin etc. I got proftpd set up so I could do that. I want to duplicate the environment of a website that I have some dealings with so that I can play around without messing anything up on the actual server. I should be able to do that now. Thanks to all of the replies.

---

### Post by m@@dL3s on 2008-01-01
Hi, Peter,
Just wanted to say thanks for this xampp thread, it was exactly what I was looking for, and esp. the help getting XAMPP listed in Applications and linking to a folder. I'm new at ubuntu and would not have known even to ask about linking. I haven' t used all the xampp features but can work on WordPress now without being online. 

:KS:KS:KS

---

### Post by papuccino1 on 2008-01-06
> **christom said:**
> I had the same problem, and fixed it by saving the file  "xampp-control-panel.desktop" to the folder "/usr/share/applications",which is where all my menu applets are saved (i.e. not in the "~/.local" folder, which does not exist on my installation of feisty; the original instructions involving that directory did not work at all.)
```

sudo gedit /usr/share/applications/xampp-control-panel.desktop

```
The code as published on page 1 of this thread did not work either. The code that worked was:
```

[Desktop Entry]
Encoding=UTF-8
Name=XAMPP Control Panel
Comment=Start and Stop XAMPP
Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg 
Terminal=false
Type=Application
Categories=GNOME;Application;Network;
StartupNotify=true

```
I had to unmark and remark the menu item in Alacarte before it appeared in my Applications|Internet menu. Reloading would likely have accomplished the same.

christom you saved my *** :D
Thanks mate this was a really good guide indeed.

---

### Post by unabatedshagie on 2008-01-12
Just freshly installed gutsy and downloaded the latest version of xampp (1.6.5a), "installed" fine and works fine.

Now previously I have been able to run the following command          ```
sudo ln -s /home/alex/WebDesign /opt/lampp/htdocs/%USER
``` and type **localhost/alex** into firefox to view the files in the folder.

Now I'm getting an error saying that I don't have permission to access the files on the server.

As far as I can tell I have the correct permissions on the folder (I haven't changed the permission on the WebDesign folder since I backed it up and restored it)

---

### Post by martin_n_c on 2008-01-12
Hey, I've got the same problem. I followed this howto and it worked  fine under Feisty, Now I'm with a fresh install of Gutsy I can't get at my files!

---

### Post by martin_n_c on 2008-01-14
I found a partial way round it. It's not great, but you can see your documents in home (public_html in this thread's tutorial). I had to change the Apache config file:

```
sudo gedit /opt/lampp/etc/httpd.conf
```

I changed the line:
```
User nobody
```

to:
```
User Myusername
```

(see the following post for my httpd.conf file)

The downside is that I can't get the default Xampp splashscreen because now I don't have permission to view that :-(

---

### Post by martin_n_c on 2008-01-14
Here's the httpd.conf file.


EDIT: I sorted this one out. It wasn't anything to do with config files. It was me importing .html files. I've put the details in a different thread [here]("http://ubuntuforums.org/showthread.php?t=665487&page=4") (#32).

---

### Post by darck on 2008-01-17
it was pretty working, but stopped. Now Appache and Pro FTPD doesn't want to start. I haven't changed anything. I installed firestarter, but it sholdn't be a case, because i tried to stop them - didn't help. I also installed regular ubuntu updates, but am not sure when it stopped working, because i used it rarely.

now i get:
```

 sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.6.5a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Error 1! Couldn't start Apache!
XAMPP: Starting diagnose...
XAMPP: Sorry, I've no idea what's going wrong.
XAMPP: Please contact our forum http://www.apachefriends.org/f/
XAMPP: XAMPP-MySQL is already running.
XAMPP: Starting ProFTPD...
XAMPP:  - warning: unable to determine IP address of 'darck'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/opt/lampp/etc/proftpd.conf'
XAMPP: Error 1! Couln't start ProFTPD!
XAMPP for Linux started.
darck@darck:~$ 
```


```

darck@darck:~$ tail -2 /opt/lampp/logs/error_log
[Thu Jan 17 23:38:09 2008] [alert] (EAI 5)No address associated with hostname: mod_unique_id: unable to find IPv4 address of "darck"
Configuration Failed

```

---

### Post by bynary on 2008-02-02
I followed the tutorial and everything installed fine.  Here's the problem: when I open my home.html file in firefox without going through localhost, it looks like this

[IMG]http://myweb.cableone.net/ajbynum/Kidzone_good.png[/IMG]

When I view it through localhost, it looks like this

[IMG]http://myweb.cableone.net/ajbynum/Kidzone_bad.png[/IMG]

Does anyone have any idea what's going on?

---

### Post by banago on 2008-02-05
Hi all!

As a newly and happy ubuntu convert, I have a question that is driving me mad.

After a long attempt to install xampp and wordpress on ubunto, the latest following the HowTo of Petervk, I got the following error when I opened it in the browser (see IMG)

[IMG]http://www.superalb.com/Screenshot-Mozilla%20Firefox.png[/IMG]

How can I resolve the problem? 

Thank you in advance!

Banago

---

### Post by banago on 2008-02-05
Can anyone give me an answer please?

Banago

---

### Post by banago on 2008-02-06
No replay yet. :(

---

### Post by banago on 2008-02-06
PILIzzzzzzzzzzzzzzzz!

---

### Post by hnprashanth on 2008-02-07
Tanks buddy!
works perfectly in first shot!

---

### Post by techstop on 2008-02-11
The command in the first post doesn´t work to make the control panel. Correct command found in this post;

[http://ubuntuforums.org/showpost.php?p=3195778&postcount=130](http://ubuntuforums.org/showpost.php?p=3195778&postcount=130)

Can the OP please update their post to a working version? It seems like a lot of people have trouble adding the menu link to the control panel.

Cheers...

---

### Post by gally66 on 2008-02-15
Nice howto - I have used the XAMPP site a number of time but they are not as "direct" as you are, don't tell you about "Sweet" and of course you are specific to Ubuntu.  And the link idea is great, especially for folks like me who are not "real good" Linux users/dev.  Thanks, Graham

---

### Post by Dangerous2505 on 2008-02-17
Hi everyone.

I haven't seen anyone post with this problem so I'm going to ask.
Please note that I'm totally new to linux and Ubuntu.

I have downloaded the file to my desktop, but when I use terminal
to install it I keep getting an error.(See below)

I change to the Desktop directory, then type;

     sudo tar xvfz xampp-linux-1.6.6.tar.gz -c /opt

      (Latest version, As per the instructions.)

Then I get this message;

     tar: You may not specify more then one '-Acdtrux' option.


Does anyone know what is causing this, or what I'm doing wrong?
It seems to not like the "xvfz" part as far as I can tell.

Any help would be greatly useful as I have been trying for a couple
of days to get this installed. ](*,)

Thanks in advance for any help.

Dangerous Dan


PS:  Where in the heck is my spell checker? I can't type anything
       without it. :roll:

---

### Post by techstop on 2008-02-17
> **Dangerous2505 said:**
> Hi everyone.

I haven't seen anyone post with this problem so I'm going to ask.
Please note that I'm totally new to linux and Ubuntu.

I have downloaded the file to my desktop, but when I use terminal
to install it I keep getting an error.(See below)

I change to the Desktop directory, then type;

     sudo tar xvfz xampp-linux-1.6.6.tar.gz -c /opt

      (Latest version, As per the instructions.)

Then I get this message;

     tar: You may not specify more then one '-Acdtrux' option.


Does anyone know what is causing this, or what I'm doing wrong?
It seems to not like the "xvfz" part as far as I can tell.

Any help would be greatly useful as I have been trying for a couple
of days to get this installed. ](*,)

Thanks in advance for any help.

Dangerous Dan


PS:  Where in the heck is my spell checker? I can't type anything
       without it. :roll:

You should be using a capital C, not lower case in the command, eg

sudo tar zxvf archive.tar.gz -C /opt

A lower case tells to tar to create an archive, and you want to be extracting one.

---

### Post by Dangerous2505 on 2008-02-17
Thanks a bunch, techstop. *Smacks self on head.*

Maybe I need new glasses.

If I knew how, I'd give you an offical "Thanks"

Again, thanks.

Dangerous Dan

Edit: I found the thanks tag.

---

### Post by Krunktor on 2008-02-19
I've skimmed through all of the pages here, but it's a lot of posts so forgive me if this has been asked/solved before.

I've installed XAMPP 1.6.6 to Gutsy Gibbon, tested it by going to [http://localhost/](http://localhost/) and it works perfectly. I also made a folder in my home directory and successfully linked it into the htdocs folder. However, when I try to access [http://localhost/kent/](http://localhost/kent/) (my name being Kent, of course), I'm given this error:

```
Forbidden

You don't have permission to access /kent on this server.
Apache/2.2.8 (Unix) DAV/2 mod_ssl/2.2.8 OpenSSL/0.9.8e PHP/5.2.5 mod_apreq2-20051231/2.6.0 mod_perl/2.0.2 Perl/v5.10.0 Server at localhost Port 80
```

It's the same for any other folder I try to place either in my linked folder or directly in htdocs with *sudo mv*. I'm guessing it has something to do with file permissions, but I'm not positive how to edit them or what to edit them to. I've tried just right-clicking and going through the folder properties (classic Windows solution, I know), but that didn't help at all.

I really need to get XAMPP up and running soon so that I can complete a project  due next week, so any help would be greatly appreciated.

EDIT: I just tried the solution in [this thread](http://ubuntuforums.org/showthread.php?t=665487&page=4), but still am having no luck whatsoever. :(

EDIT Deux: I tried the "sudo gedit /opt/lampp/etc/httpd.conf" thing and it works now, and apparently didn't screw up the default XAMPP splash screen like it did for others. So... thanks... I guess?

---

### Post by abcprabhu on 2008-02-28
Actually i had installed the xammp in ubuntu. but i can't access the opt folder & also can not create any folder inside the htdoc & not able to save any file in htdoc.

pls help some one!!!

Lord_c

---

### Post by eheyl on 2008-03-19
The control panel blips in and out when I try to launch it. Does anyone have a workaround? I'm on ubuntu 7.10

---

### Post by eheyl on 2008-03-22
So I erased the first .desktop file I created as per instructions and did everything from the gui and pasted the commads in. It works! YAY!

---

### Post by cozmicharlie on 2008-03-22
> **abcprabhu said:**
> Actually i had installed the xammp in ubuntu. but i can't access the opt folder & also can not create any folder inside the htdoc & not able to save any file in htdoc.

pls help some one!!!

Lord_c

You need to be in nautilus as root.  Open a terminal and type or cut and paste the following 
```
sudo nautilus
```
 enter your password and now you are in Nautilus as root and you should be able to cut and paste or add folders to /opt/

---

### Post by sandclock on 2008-03-24
Hi
I read most of the posts in this thread and many other threads too. But couldnt find what i needed. 
Here is what i want to do.
1. I have small network on 4 pcs
2. 3 on ubuntu 1 on winxp
3. I want to setup another pc which will be host to all these pcs
4. I want to install xampp on 5th pc and i want other 4 pcs to use it as development server is it possible? 
Sorry if this is already covered and i missed something
Regards
NIk

---

### Post by slackmaster on 2008-03-25
Hello,

Thanks for the tutorial.  I got XAMPP up and working nicely.  So I see that I can access files through my browser.  Now how do I take it to the next step and permit other users with the right username and password to access my files from the internet?

Thanks for your help.

---

### Post by Geowilky on 2008-03-25
I finally got Xampp to load to the /opt directory, but when I went to start it I got this below:



XAMPP is currently only availably as 32 bit application. Please use a 32 bit compatibility library for your system.

Where and how can I get the compatibility library?

---

### Post by linuxtony on 2008-03-27
Nice tutorial.  On my Gutsy Gibbon setup the install went smoothly, but the script to set up a link to the python control panel produced an error message of file not found.

Anyhow, thanks for the quick install notes -- now to install Joomla

---

### Post by BlizzofOZ on 2008-03-31
I posted this over at Apache Friends forum, but thought I'd try here also, in case someone had encountered this before:

I had just got XAMPP to work... I had some problems accessing via the internet because I was trying to port forward the app. I found a thread here that showed the conf file to change (I have the link at home), where you would change the port. After doing that, it worked! 

This moring, after a reboot, I tried to stop and start XAMPP and recieved the following error: 

Error 1! Couldnt start Apache! 
Starting Diagnosis ... 
Sorry, Ive no idea whats wrong. 


Any idea what is causing this?

---

### Post by kemphp on 2008-04-02
Excellent instructions.  Worked perfect under ubuntu 7.10 with xampp 1.6.6.  One 'gotcha' for a noob (like me) might be that if you already have an apache service running, you need to shut it off before you can get the apache that is with xampp to start.

---

### Post by jlhaslip on 2008-04-17
New Ubuntu User. WUBI Ubuntu 8.04. Dual Booted with Window XP SP2
Used this Tutorial and have the LAMPP set up on my Laptop. Built the public_html folders and used the provided code to set them as user-level defaults (I think).
Admin level user can start/stop the Server okay, and phpinfo runs from the default Xampp start page for both an Admin user and a regular (non-admin user) using "localhost" in the Browser address bar, however, I can't get a php file in the public_html folder to operate properly in the Browser. If I ask for "file > open" and point to the php file in the public_html folder, it wants to download the file. If I click on the file directly, it opens in a text editor.
I have XAMPP on this Laptop under the Windoze XP, so I am cool with the operation of XAMPP, but this is likely a Linux (user) issue? Or it might be that the Terminal commands I issued were not recognized? How to tell? What to check for? Where is it located on the machine. Apache has been stopped/started several times, no change.
One method I attempted was to add the ApplicationType Handlers to the httpd file, but even the Admin level user was denied permissions, so any replies should consider that I am very new to Linux, although I have used Console-based O/S's in the past and am not totally green to them. Thanks.

*edit*

Not sure why, but it is all working well now. Thanks much for this informative Topic... I have learned lots...

---

### Post by neodare on 2008-04-19
thanks a lot man .....u write wat i need ..i was confusing how to save my file in xampp root ..u made it easy

---

### Post by bcnaat on 2008-04-22
THANKS! This worked great. I have a fresh install of Hardy and followed these instructions (used them for my install of Fiesty). The only difference this time is that I had to create the ./local/applications folder before it would add the file for the shortcut in the menu.

I also have a folder named WWW that I use instead of a Public_html folder. Same instructions, just different name. I did find that I had to change the permissions on my folder before it would allow me to view the files, but I think that may have been because I copied the file over from another drive. Seems to happen a lot to my folders when I store them on my MyBook drive.

Again, thank you so much for these instructions since I only wanted a local server to test my web pages on, and to do some ruby programming.

---

### Post by karq on 2008-04-24
So I installed xampp and got it running. I can see the test page, but when I try to run my own files, then it says 

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/opt/lampp/htdocs/proov/loops.php' (include_path='.:/opt/lampp/lib/php') in Unknown on line 0

---

### Post by rouge568 on 2008-05-02
Hello.

I am trying to set up lampp with htdocs as a symbolic link. It links to a copy of htdocs on a usb stick (which also has xampp on it so I can access my server on the go!). Anyways, it isn't liking my symbolic links, and keeps shooting me a 403 forbidden and this in the error log: ```
[Fri May 02 23:06:15 2008] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /opt/lampp/htdocs
``` I have allowed access to /opt/lampp and /media/disk/xampp and subfolders (chmod -R 777). I have also gone into httpd.conf and edited it to try and allow symbolic links. (attached)
Anybody have any clues as to what could be going on/ how to fix this? Thanks in advance.

---

### Post by ajboesch71 on 2008-05-03
awesome walkthrough, even I have it up and running...lol

---

### Post by drdanield@gmail.com on 2008-05-04
Excellent.  Thank you.  I made a quick svg icon using Incscape for the menu
[IMG]http://nohair.com/code/_media/computers:xamppicon.png?cache=cache[/IMG]
See quick notes and download the svg icon at: 
[http://nohair.com/code/computers:ubuntu_linux#use_xampp](http://nohair.com/code/computers:ubuntu_linux#use_xampp)
After clicking on above site, scroll down to see it.

---

### Post by LeeU on 2008-05-04
@Takster,

Sweet! Works just fine, and I don't have to follow a long path to get to my files. Thanks!

---

### Post by myharshdesigner on 2008-05-07
> **petervk said:**
> This is a how-to for setting up a web development environment easily. This guide will install the XAMPP lampp stack into /opt, setup an easy way to start it up and shut it down, and link a folder in your home directory to the webserver.

**WARNING**
This guide is aimed at a development environment only and should not be used as a public webserver. To setup a public webserver follow the directions on the Ubuntu wiki [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

As this is Ubuntu, all the major parts of a typical web server are included (in the main repo, or on the Ubuntu Server CD) and this is a great way to setup a server. The ubuntu developers have prepared a great web server and have made the process as seemless as possible. 

But what if even the official way is still to complicated? What if you just want a quick web server for development?

Fortunately there is the XAMPP project: [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html). The XAMPP project bundles Apache, PHP4 & 5, Perl, mySQL, and a bunch of other utilities/applications into an simple package for Mac OSX, Windows, Solaris, and Linux. Obviously this HOWTO only deals with the linux version.

For those of you with already existing Apache/mySQL/php installations it installs everything into /opt so it doesn't conflict with any other installation, and it is completely setup and ready to run.

[SIZE="3"]**_Install XAMPP_**[/SIZE]

Two easy steps:
[LIST=1]
[*]Download the most recent version of XAMPP: (at time of writing 1.5.3a)
[http://prdownloads.sourceforge.net/xampp/xampp-linux-1.5.3a.tar.gz?download](http://prdownloads.sourceforge.net/xampp/xampp-linux-1.5.3a.tar.gz?download)
(Source URL: [http://www.apachefriends.org/en/xampp-linux.html#374](http://www.apachefriends.org/en/xampp-linux.html#374))
[*]Extract the archive to /opt using sudo: (make sure you are in the directory that you downloaded the archive to) ```
sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt
```
[/LIST]

[SIZE="3"]**_Start XAMPP_**[/size]

To start it up, open a terminal and type this:
```
sudo /opt/lampp/lampp start
```

[SIZE="3"]**_Stop XAMPP_**[/size]

To stop it, open a terminal and type this:
```
sudo /opt/lampp/lampp stop
```

[SIZE="3"]**_Additional XAMPP commands_**[/size]

To see additional commands, open a terminal and type this:
```
sudo /opt/lampp/lampp
```

[SIZE="3"]**_Sweet XAMPP Control Panel_**[/size]

[img]http://img108.imageshack.us/img108/5647/screenshotxamppcontrolpanelfj6.png[/img]

To use the sweet gtk/python control panel:

Run in a terminal: ```
gedit ~/.local/share/applications/xampp-control-panel.desktop
```

Paste the following into the open file and save and exit.
```
[Desktop Entry]
Comment=Start/Stop XAMPP
Name=XAMPP Control Panel
Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
Icon[en_CA]=/usr/share/icons/Tango/scalable/devices/network-wired.svg
Encoding=UTF-8
Terminal=false
Name[en_CA]=XAMPP Control Panel
Comment[en_CA]=Start/Stop XAMPP
Type=Application
Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg
```
"XAMPP Control Panel" will show up in your applications menu under Internet. Use the Alacarte Menu Editor to move it around.

[SIZE="3"]**_Test to see if XAMPP is running_**[/size]

Once XAMPP is up and running open firefox and go to: [http://localhost/](http://localhost/)

You should see the XAMPP test page:

[IMG]http://static.apachefriends.org/images/380.jpg[/IMG]

[SIZE="3"]**_Location of files and uploading_**[/size]

XAMPP by default uses /opt/lampp/htdocs as the root web directory. The easiest way to start working on files is to link a folder in your home directory into this directory.
My user name is peter so I have /home/peter/public_html linked to /opt/lampp/htdocs/peter. So if I navigate to [http://localhost/peter/](http://localhost/peter/) I get a listing of all the files/folders in that directory. (As long is there isn't a index.php/html/etc file)
To set this up, run in a terminal:
[list=1]
[*]Make public_html directory in home directory: ```
mkdir ~/public_html
```
[*]Link to /opt/lampp/htdocs ```
sudo ln -s ~/public_html /opt/lampp/htdocs/$USER
```
[/list]
Now any files and folders you place in ~/public_html will be published to your personal webserver. 

Bookmark [http://localhost/username](http://localhost/username) to make this easy to access.

[SIZE="3"]**_WARNING - SECURITY_**[/size]
[http://www.apachefriends.org/en/xampp-linux.html#381](http://www.apachefriends.org/en/xampp-linux.html#381)
Open holes:
[list=1]
[*]The MySQL administrator (root) has no password.
[*]The MySQL daemon is accessible via network.
[*]ProFTPD uses the password "lampp" for user "nobody".
[*]PhpMyAdmin is accessible via network.
[*]Examples are accessible via network.
[*]MySQL and Apache running under the same user (nobody). 
[/list]
This doesn't leave your whole system wide open, but someone could hack your XAMPP installation, so be wary.
To fix most of the security weaknesses open a terminal and run: ```
sudo /opt/lampp/lampp security
```

[SIZE="3"]**_Feedback_**[/size]
Please read [ this post](http://www.ubuntuforums.org/showpost.php?p=1310039&postcount=5).

---- EDIT - July 28, 2006 ----
Minor Edits

---- EDIT - August 1, 2006 ----
Re-did xampp control panel shortcut to make it easier.

---- EDIT - August 16, 2006 ----
Added warning for public web servers and edited intro to make it more accurate.

---- EDIT - September 1, 2006 ----
Added sudo to security command.

i like it :)

---

### Post by bro on 2008-05-08
Howto make php email functions work? If I say, install wordpress and try to email via a form, it doesn't work. It is lacking or not finding sentmail?

---

### Post by bro on 2008-05-08
That was one of my smartest questions ever! I installed sendmail, problem solved.

---

### Post by eisenklopf on 2008-05-09
on mine mysql will not initiate. I am coming from a windows environment for using xampp so any pointers would be greatly appreciated. although not entirely ignorant to linux I am having some problems so treat me as if I am. when going to localhost I get an error of permission denied on line 2 of /opt/lampp/htdocs/xampp/index.php. If I comment out the if statement it then brings me to the splash screen asking me which language which then brings me to another error of permission denied and so on and so on. Thank you in advance.

---

### Post by bro on 2008-05-11
Okay, so actually installing sendmail gives many other problems. It is not really working and takes ages to start probably because my /etc/hosts is not what is should be (though I didn't touch it). 
How are you emailing from XAMPP powered apps/sites?

---

### Post by dwardwarbinx on 2008-05-21
> **gorilla_king said:**
> xampp installs the latest mysql version and gives you the option (after the install) about which version of php you would like run.

where do you get to choose which php version to use? im such a linux/ubuntu NOOB! :(

---

### Post by Lektorvis on 2008-05-29
**Xampp-control-panel doesn't show up in the menu.**

I followed this guide [http://http://ubuntuforums.org/showthread.php?t=223410]("http://http://ubuntuforums.org/showthread.php?t=223410") and everything went smudge but the control-panel. I did exactly like this:
> To use the sweet gtk/python control panel:

Run in a terminal:
Code:

gedit ~/.local/share/applications/xampp-control-panel.desktop

Paste the following into the open file and save and exit.
Code:

[Desktop Entry]
Comment=Start/Stop XAMPP
Name=XAMPP Control Panel
Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
Icon[en_CA]=/usr/share/icons/Tango/scalable/devices/network-wired.svg
Encoding=UTF-8
Terminal=false
Name[en_CA]=XAMPP Control Panel
Comment[en_CA]=Start/Stop XAMPP
Type=Application
Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg

"XAMPP Control Panel" will show up in your applications menu under Internet. Use the Alacarte Menu Editor to move it around.


I've tried to change the path of the icon, as it is in an other achive on my system, but that didn't solve the problem. 
Any suggestions are welcome.

---

### Post by moonshinerat on 2008-06-16
Okay, I read somewhere in this thread that to get rid of the Xampp test page I just had to remove the redirect from the index.html

So I've removed the redirect, I have written my own index.html and also tried index.php. I have tried removing the whole of the original index.html with the redirect in it. I have been up and down httpd.conf and checked DocumentRoot and everything. I even tried deleting the Xampp folder which results in a 404.

My Xampp keeps redirecting to [http://localhost/xampp/](http://localhost/xampp/) and giving me the test page.

How do I get this thing to see my own webpage. I have tried installing this on four different distro's now with the same problem. Nobody else seems to be suffering from it. I just want to put my pages in htdocs and have done.

Can someone please tell me what to do to get rid of the test page because writing this post without bad language was really, really hard.

Thank you so much in advance.

---

### Post by bro on 2008-06-17
Hi, 

> **moonshinerat said:**
> Okay, I read somewhere in this thread that to get rid of the Xampp test page I just had to remove the redirect from the index.html 
That is definitely not the easiest way.

> **moonshinerat said:**
> How do I get this thing to see my own webpage. I have tried installing this on four different distro's now with the same problem. Nobody else seems to be suffering from it. I just want to put my pages in htdocs and have done.
Can someone please tell me what to do to get rid of the test page because writing this post without bad language was really, really hard.


xampp has this nice orange screen for you when you go to [http://localhost/](http://localhost/) and you where redirected. ignore this. Think of a directory where you have easy access to. Say /home/moonshinerat/mySitesAreHere/

I assume you have installed xampp in /opt/lampp
On the commandline type: 
```
sudo ln -s /home/moonshinerat/mySitesAreHere/ /opt/lampp/htdocs/mysite
```

This will create a symbolic link (MS users say 'shortcut') in your htdocs that links to your 'mySitesAreHere' directory. place your .php 's and .html in that dir and go to [http://localhost/mysite](http://localhost/mysite). 

Good luck with your mental hygiene (keep out the bad words)

---

### Post by moonshinerat on 2008-06-17
Bro, you just made the last three weeks of my life worth it. Cheers fella.

I think maybe someone should try to produce a manual for Xampp to explain these things a bit better. A bunch of 'important' directory lists doesn't actually help that much.

It's great software and it doesn't need a 200 page manual but a few directions might be nice.

Once again, thanks.

---

### Post by bro on 2008-06-17
And the cool thing is, it'll work in all 4 distro's you tried in with. ;)

---

### Post by cleardensity on 2008-07-10
> **petervk said:**
> So far this post has just under 200 views, So great. If you read this and use it could you leave a reply saying if it was useful/useless? 

VERY Useful! Thanks alot for putting this together - took just under 2 minutes after the download and I'm up and running my development server... very cool.

You :guitar:

---

### Post by chipw on 2008-07-10
This is fantastic. Thanks. I've been doing it the hard way for years on various FreeBSD boxes. I'm really liking ubuntu and how easy everything works.

---

### Post by ruzt on 2008-07-14
Please help me..:confused:
when i'm extract xampp-linux.1.6.6.tar.gz with command line,

*sudo tar xvfz xampp-linux.1.6.6.tar.gz -C /opt*

request password..but, i have message error bellow :

[I]password for ruzt: 
tar: xampp-linux.1.6.6.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ruzt@ruzt:~$[/I]

Please, can give me any solution...thank!:confused:

---

### Post by sassur on 2008-07-14
You aren't in the same directory as the file "xampp-linux.1.6.6.tar.gz". Change directory to the directory where you downloaded the file and try the same command again.

---

### Post by ruzt on 2008-07-14
> **sassur said:**
> You aren't in the same directory as the file "xampp-linux.1.6.6.tar.gz". Change directory to the directory where you downloaded the file and try the same command again.
oke! thank:):):)
I'll try again!

---

### Post by Zogug on 2008-07-23
Ok here is my problem. Its about the default xampp page... I wan't to set up a dns from dyndns, but I keep getting the xampp page... I deleted the index.html in the htdocs and made a new one, but it keeps comming. Yes, I tried that sudo mysite link stuff. It does not accept IP/mysite. So I made a dns to the ip. And tried to use that one (eg. blabla.mine.nu/mysite), but dyndns does not accept that either. And it kinda sucks to have to tell people, hey go to blabla.mine.nu/mysite, when I could be telling them go to blabla.mine.nu. But as it is right now that takes us to the xampp default. The only way i want to access the xampp page is by typing blabla.mine.nu/xampp or localhost/xampp. How do I do this?? Please help.

Zogug

---

### Post by hezuo on 2008-07-28
great tutorial, thanks a lot!

---

### Post by itaworld on 2008-08-06
Very helpful tutorial, thanks a lot ):P

---

### Post by edmondt on 2008-08-21
To start xampp as a service just do the following:

sudo ln -s /opt/lampp/lampp /etc/init.d/lampp
sudo update-rc.d -f lampp defaults

---

### Post by powerof2 on 2008-08-31
When I copied and saved this code, the "executable" was in Applications/Other.

No big deal, but I panicked, as I often do with this new OS, when it didn't show up.

Thanks for the clear instructions.

j


Paste the following into the open file and save and exit.
Code:

[Desktop Entry]
Comment=Start/Stop XAMPP
Name=XAMPP Control Panel
Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
Icon[en_CA]=/usr/share/icons/Tango/scalable/devices/network-wired.svg
Encoding=UTF-8
Terminal=false
Name[en_CA]=XAMPP Control Panel
Comment[en_CA]=Start/Stop XAMPP
Type=Application
Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg

"XAMPP Control Panel"_ will show up in your applications menu under Internet_. Use the Alacarte Menu Editor to move it around.

---

### Post by DroBuddy on 2008-09-18
This is a great thread and it got me up and running in a matter of minutes.

The only problem I ran into was...

Run in a terminal:
Code:

gedit ~/.local/share/applications/xampp-control-panel.desktop

Paste the following into the open file and save and exit.
Code:

[Desktop Entry]
Comment=Start/Stop XAMPP
Name=XAMPP Control Panel
Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
Icon[en_CA]=/usr/share/icons/Tango/scalable/devices/network-wired.svg
Encoding=UTF-8
Terminal=false
Name[en_CA]=XAMPP Control Panel
Comment[en_CA]=Start/Stop XAMPP
Type=Application
Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg

Didn't work for me.... Here's the error mesg:

"Could not save the file /home/dro/.local/share/a…mpp-control-panel.desktop.

Unexpected error: File not found"

I'm running Hardy Heron and i386 (w/ a fresh install and all updates applied), so... I dunno, I'm not exactly sure why this isn't working. Any insight?

Also, what's the cmd to start XAMPP on startup? I'm always doing work, so it would be nice if it was waiting in the background for me. ;)

Once again, this is a great guide. Thanks for your help, man.


Peace,



Dro Buddy

---

### Post by techstop on 2008-09-18
> **DroBuddy said:**
> This is a great thread and it got me up and running in a matter of minutes.

<SNIP>

"Could not save the file /home/dro/.local/share/a…mpp-control-panel.desktop.

Unexpected error: File not found"

I'm running Hardy Heron and i386 (w/ a fresh install and all updates applied), so... I dunno, I'm not exactly sure why this isn't working. Any insight?

Also, what's the cmd to start XAMPP on startup? I'm always doing work, so it would be nice if it was waiting in the background for me. ;)

Once again, this is a great guide. Thanks for your help, man.

Peace,

Dro Buddy

This was posted a few pages back, have you tried it?

[http://ubuntuforums.org/showpost.php?p=3195778&postcount=130](http://ubuntuforums.org/showpost.php?p=3195778&postcount=130)

---

### Post by shcKr- on 2008-09-30
right.. im after some help please, i have xampp setup on my ubuntu machine, and can access it via typing localhost in the address bar, and on another computer typing the IP address of the computer running xampp to access it, but is there anyway, rather than typing '192.168.1.1' to type 'www' and it will go to the directory on the ubuntu computer 'localhost/intranet/'
thanks in advance

---

### Post by goldstar1 on 2008-10-08
Thank you very very much...This is just what the Doctor ordered!

---

### Post by ubuking on 2008-10-11
Works like a Charm, thank you!

---

### Post by effec on 2008-10-11
```
Starting XAMPP for Linux 1.6.8a...
XAMPP: Another web server daemon is already running.
XAMPP: Another MySQL daemon is already running.
XAMPP: Starting ProFTPD...
XAMPP:  - warning: unable to determine IP address of 'Mars'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/opt/lampp/etc/proftpd.conf'
XAMPP: Error 1! Couln't start ProFTPD!
XAMPP for Linux started.

```

I ran int this problem and dont know how to fix it. Any suggestions?

---

### Post by Wickd on 2008-10-11
Hi there thank you very much! This helped quite alot. I am new to this so gotta go study my sql and php, but this was great

Thanks

---

### Post by elfuegodiego on 2008-10-16
Thanks for the guide. 

Worked like a charm!

---

### Post by ramadha on 2008-11-06
thank you very much! 
:)

ramadha

---

### Post by mendozaro on 2008-11-07
Works perfectly.

I want to suggest [[COLOR="Red"]this icon[/COLOR]]("http://www.lestarte.com/blog/wp-content/uploads/2007/12/xampp-objectdock.png") for the XAMPP Control Panel.

---

### Post by CaseWestern on 2008-11-09
Any idea why I am unable to access mysql database from the terminal after installing xampp?

I can access the database using PHPMyAdmin, but somehow I cant see the databases from the terminal when I enter  mysql -u root


```
bash: mysql: command not found
```

What I supposed is, the process is looking for the mysql command in the PATH variable, but my /opt/lampp where the XAMPP is installed is not in the path.  Any idea how to do that? or Do you think there is a different approach for this.

---

### Post by Melindrea on 2008-11-13
And since I don't seem to be able to find how to do it... How do I setup so I can use CGI? I found a cgi-bin in the lampp folder, but can't seem to be able to access the ones in it. I'd prefer if the cgi-bin that is usable is the one in my public_html folder.

Thank you,
Marie

---

### Post by Melindrea on 2008-11-15
Just a quick bump, for me and the person posting right above me. =)

---

### Post by Suncoaster on 2008-11-27
Thanks for the instructions:KS.  It is working fine

Dave

---

### Post by Johnpeter on 2008-12-24
Good open-source web development environment?
I'm looking for a decent, open-source (read: free) web development environment that will make the development and maintenance of very basic websites easy, kind of like FrontPage (but hopefully standards-based). We're in a 32-bit XP environment.Does anyone have any suggestions?

---

### Post by Jodha on 2008-12-27
All in all very useful for setting up Xampp; had no problems at all through the entire process. However... (!)

I've run the security check and added passwords all over the place where is prompted.

Now I dont have "Create DataBase" privileges it seems.

I'm a bit new to Linux and Ubuntu, I've considered uninstalling Xampp and reinstalling it, but I cant find it in the add/remove programs section. And to be honest, I'd just like to turn that privilege back on so I can get on with stuff.

Any advice?

Thanks :)

---

### Post by Dssnz on 2009-01-06
Thank you,
You made a job I thought would be hard, easy!

---

### Post by javaman1909 on 2009-01-16
After I link my ~/public_html to /opt/lampp/htdocs/norton, I can't view my public_html on FF. It says that **"You don't have permission to access /norton on this server."**
What's wrong with this, anyone?
Thanks.

---

### Post by Cicer on 2009-01-18
> **javaman1909 said:**
> After I link my ~/public_html to /opt/lampp/htdocs/norton, I can't view my public_html on FF. It says that **"You don't have permission to access /norton on this server."**
What's wrong with this, anyone?
Thanks.

Did you check if the link you've made is broken? I don't know how to check it with Terminal, but if you go to the folder with nautilus it will tell you with the icon and under the "type" column. I had the same problem as you and was changing permissions left and right until I realized I had a miscapitalization between the ~/Public_html folder I had created and the ~/public_html folder I had addressed the link to.

---

### Post by PaulWhipp on 2009-01-18
Very handy.

Here is a little addition that might be useful:

Once you have lampp running on your system there will come a time when you want command line access to the mysql databases, for backup or perhaps for something that is too much trouble in phpmyadmin.

You can use synaptic package manager to install the mysql-client meta package.

Once installed, you can point it at your lampp mysql database by creating a .my.cnf file in your home directory and setting up its contents as follows (use your real username/password as appropriate):

```
[client]
user=root
password=secret
socket=/opt/lampp/var/mysql/mysql.sock

```

This allows you to use mysqldump etc. from the command line and have it act on your databases in lampp. For example:
```
$ mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 36
Server version: 5.0.67 Source distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> use test
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+----------------+
| Tables_in_test |
+----------------+
| names          | 
| orders         | 
+----------------+
2 rows in set (0.00 sec)

mysql> select * from names;
+-------+
| name  |
+-------+
| dick  | 
| harry | 
| tom   | 
+-------+
3 rows in set (0.00 sec)

mysql> quit
Bye


```

mysqldump is great for backups, mysqlimport is handy for large data imports and there are a number of other handy utilities in mysql-client just
```

apropos mysql

```
and use man to check them out.

---

### Post by xihad76 on 2009-01-23
Thank u very much bro.. it was really very very helpful :-) 

cheers!!

---

### Post by kodemind on 2009-01-29
> **petervk said:**
> ... If you read this and use it could you leave a reply saying if it was useful/useless? I'd like to keep improving this how-to, so feedback would be good.

Plus, replies bump it up the list.

Thank for the tut, very precise. I was wondering if you could add more info about running xampp as a single user...

Its default is to run as 'nobody'. Some users have had success by..

chown nobody:user *
chmod 0775 *

Possibly adding directions to run as single user so they can chmod files to 0755 or similar for better security.

Again great work!:)

---

### Post by jlhaslip on 2009-02-24
Thanks for the Tutorial on XAMPP. Worked great.

---

### Post by sitmex on 2009-03-25
Hi, first of all, thanks for posting this helpful guide.

How can I set it up so it start automatically when startup.

Using: Ubuntu 8.10
Experience: newbie.

I've tried to set it at: the sessions application but no luck.

---

### Post by PaulWhipp on 2009-03-27
To start lampp automatically when you start the session
```
gksudo gedit /etc/rc.local
```
Then add the following line somewhere after the comments and before
the exit 0 statement at the end of the file:

```
/opt/lampp/lampp start
```

Treat rc.local with care, all commands here executed as the super user and we need that to start lampp.

For normal automatic startup items you were right to look to the Administration > Services or Preferences > Sessions menu options.

---

### Post by duffboy on 2009-04-13
I went through this tutorial and do thank you, it is well done.

However, when I go to access my localhost/username folder I get a 403 forbidden error.

The link to the public_html folder in the /opt/lampp/htdocs folder is working.

I am not too sure how to handle this. I am a Ubuntu novice with some understanding, but that is about the extent of it. On the bright side, once I can figure this out, I will be one *major* step closer to leaving Windows behind me for good!

---

### Post by PaulWhipp on 2009-04-13
When you create local websites on your machine under the /opt/lampp/htdocs folder you need to set the file access permissions to be appropriate for general web access otherwise you may see permission errors such as 403.

You need to ensure that the file permissions on your website files allow the user 'nobody' access because this is the user that apache uses to access your web site files when it gets asked to serve up the page by your browser.

For this its probably easiest to give everyone ('others' in Unix speak) read and execute access on the directories and files as appropriate:

Change directory to the relevant website folder (~/websites/test for example) and execute the following:
```

~/websites/test $ find . -type d -exec chmod o+x {} \;
~/websites/test $ find . -type f -exec chmod o+r {} \;

```

The first command finds each file of type 'directory' and gives 'other' users the ability to execute (cd to) the directory.

The second command finds each file of type 'file' and gives 'other' users the ability to read the file.

Also, be sure to take the read access off any files that contain configuration information (such as usernames and passwords to access databases). For example:
```

~/websites/test $ chmod o-r configuration.php 

```

You might wonder how come you can take the read access off a file like configuration.php but can't take it off a file like index.php. I certainly did.

I believe that this is the reason:
When apache accesses the site file it does so as 'nobody'. However, when the php script executes to generate the html for the browser it executes as the php script owner. Thus configuration.php is protected against someone trying to directly access it but it can still be accessed by your php files.

---

### Post by duffboy on 2009-04-13
Thank you so very much. Worked like a charm.

That was my last major hurdle as I am now, effectively, Windows free!

---

### Post by PaulWhipp on 2009-04-19
Hi billyg,

AFAIK apache2triad is a windows product that does much the same thing as XAMPP so you can't install it in Linux.

Perhaps you could try XAMPP instead.

---

### Post by ReyPeste on 2009-04-25
I am having this problem with permissions (I create the symlinks but when I point the browser to [http://localhost/mysite](http://localhost/mysite) I get a 403 error).

I was using XAMPP on since Intrepid without problems (I did change the permissions to enable "others" to read the folders and files as explained). 

But now I just did a clean install of Jaunty. I reinstalled XAMPP the same as before, but it won't read anything that is not directly saved on /opt/lampp/htdocs and owned by root... any ideas?? has anything changed?
Any suggestions will be dearly appreciated.

---

### Post by PaulWhipp on 2009-04-25
Check and if necessary change the ownder of /opt/lampp/htdocs to be 'nobody' and ensure that any links in that folder or subfolders are readable and executable by anyone.

That's my best guess - I'm still on 8.10 Intrepid and wont be upgrading to 9.04 Jaunty for a few weeks yet.

---

### Post by ReyPeste on 2009-04-25
Yes thanks for you reply, I checked both things. I am not sure the problem is in the files permissions anymore.  If I write the full path to the files, using the symlink 'mysite' to point to the folder with my web pages, it works: 
> [file:///opt/lampp/htdocs/mysite/index.html](file:///opt/lampp/htdocs/mysite/index.html) 
But if I try to use localhost 
> [http://localhost/mysite/index.html](http://localhost/mysite/index.html)
it gives me the 403 forbidden access message.

I checked /opt/lampp/etc/httpd.conf and I have these settings

> <Directory "/opt/lampp/htdocs">
    Options Indexes FollowSymLinks ExecCGI Includes
    AllowOverride All
   Order allow,deny
    Allow from all
</Directory>


Permissions of source and target directories
Link in /opt/lampp/htdocs
> lrwxrwxrwx  1 root   root    47 2009-04-24 23:52 sistemas -> /home/robert/Documents/trabajo/sistem

Target folder /home/robert/Documents/trabajo/sistem
> drwxr-xr-x  7 robert robert   4096 2009-04-24 22:54 .
drwx-----x  9 robert robert   4096 2009-04-24 22:57 ..
drwxr-xr-x 12 robert robert   4096 2009-04-14 22:43 biblio_docs
drwxr-xr-x  2 robert robert   4096 2009-04-14 16:18 documentos
-rwxr-xr-x  1 robert robert   1150 2009-03-31 14:47 favicon.ico
drwxr-xr-x  2 robert robert   4096 2009-04-14 18:56 graficos
-rwxr-xr-x  1 robert robert   3003 2009-03-31 16:24 index.html
-rwxr-xr-x  1 robert robert   3092 2009-04-14 17:32 sistem.css

As I am not an expert on any of this, I really don't know where else to look.
Maybe somebody else is having this issue using XAMPP in Jaunty?

---

### Post by RachedTN on 2009-04-27
Really amazing explanation
I think that we should add a thanks button to the forum :)

---

### Post by ReyPeste on 2009-04-28
Ok, after my overly long and meandering explanation, I just wanted to say I finally figured out what was wrong. Obviously it was a very simple and kind of dumb thing, that goes to show I am just starting to understand all this stuff.  But maybe my experience can save some wasted hours to other newbies. Basically, if you are having trouble with the apache server accesing files elsewhere on your filesystem (via symlinks), you have to make sure that the whole path (all the directories) can be accessed by others.  
In my case, the folder 'Documents' was not readable and my web pages were inside a sub-sub-folder of that one. So even though I changed the permissions of all my webfiles and of the htdocs, and everything, I still got the 403 forbidden access error.
So I simply checked the permissions of my other folders from my home down to my webpages folder by right-clicking, and then selecting 
Properties > Permissions [tab] > and changing the third option "Others - 
Folder Access" to Access Files.
So you see it is a very basic mistake, but at the moment it was not so evident as it now seems.

---

### Post by PaulWhipp on 2009-04-28
Cool, thanks RayPeste - I should have noticed you weren't using a folder in your home directory. I was starting to feel a little nervous about upgrading to Jaunty because I rely heavily upon LAMPP ;)

FWIW:
[INDENT]Directory permissions are that way in Unix/Linux of necessity - the system has to search down the path its given to find the file and if the process doesn't have the right to read the directory along each step of the way, it can't get to the end of the path whatever permissions have been put there.

Complications with this are generally avoided because its unusual to not give execute and read permissions to others on directories. You would normally only do this if you **really** need to keep the directory content hidden. If you just want to suppress listing the files then take the read permission away but leave the execute. This tells the process that its allowed to get a file if it knows the name but its not allowed to get a list of the files.

Thus if you have a folder of sensitive files you can protect the individual files appropriately (chmod og-rwx <file>) and prevent anyone from listing the files (chmod og-x <dir>). That still allows an appropriately owned process to access the files. The final step would almost never be required - to keep all processes not owned by you out you could then take the final step of removing the read permission from the directory (chmod og-r <dir>).[/INDENT]

I'm considering not using LAMPP any more after I upgrade to Jaunty - In order to bring my development environment one step closer to the systems I deliver on I'm thinking I might install apache, mysql, and php separately (perl is in the standard distro). Has anyone else done this for desktop development?

It has the advantage that all the parts are supported ubuntu packages (which LAMPP is not).

---

### Post by tsdemented on 2009-05-07
Thanks!

This is exactly what I needed!

---

### Post by coolsiva on 2009-05-13
The Sweet XAMPP Control Panel did not work for me - so I got the information from this URL - [http://ubuntuforums.org/showthread.php?t=223410&page=13](http://ubuntuforums.org/showthread.php?t=223410&page=13) -- and at the bottom of this page, [christom]("http://ubuntuforums.org/member.php?u=342439") - has showed me how to do that. Thanks [christom]("http://ubuntuforums.org/member.php?u=342439").

---

### Post by rrll1977 on 2009-05-18
Hi,

Anybody has worked with mod_rewrite and mod_userdir?

mod_rewrite appears to work only for the localhost home pages located on /opt/lampp/htdocs and its subdirectories but not for the users's /home/user/public_html pages and its subdirectories

---

### Post by atariman5000 on 2009-05-19
I just wanted to say thank you. I have XAMPP up an running on my system. I did make a change to what version of XAMPP I am installing to the latest version (v1.7.1). The XAMPP Control Panel is great!

---

### Post by TideMan on 2009-05-19
I've just set up XAMPP, or rather lampp, on a Xubuntu machine following the instructions from here and had no trouble at all, especially when I found christom's post here: [http://ubuntuforums.org/showthread.php?t=223410&page=13](http://ubuntuforums.org/showthread.php?t=223410&page=13) on how to make the GUI work.

---

### Post by dipaish on 2009-05-19
why do you need to install xamp or wamp in linux? its very simple to setup a complete webserver in ubuntu . With 2 simple commands you can get a perfect lamp setup.

Step 1: sudo apt-get install tasksel
Note : tasksel is already installed in all versions of ubuntu 7.04 and later so far as i remember but you can check it....

Step 2: sudo tasksel install lamp-server

Your root directory is /var/www

The server is started by default whenever you boot your computer but if you wish to enable or disable then you can type the following commands 

sudo /etc/init.d/apache2 start
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 reload

---

### Post by TideMan on 2009-05-19
I have my public_html linked to htdocs and that works fine when I look for it in a browser.  But I cannot see it in gFTP from my Ubuntu machine, while from Win XP my ftp program shows a directory with my user name, but I cannot get into it.

What I want to do is to be able to ftp files from wherever in the LAN to public_html on the machine running lampp.  How can I set that up?

---

### Post by 34m0 on 2009-06-08
I was experiencing the same error as below until I realised my /etc/hostname was configured wrongly. 

> **dhani99 said:**
> sudo /opt/lampp/lampp start
/opt/lampp/lampp: line 74: arch: command not found
Starting XAMPP for Linux 1.6.4...
/opt/lampp/lampp: line 74: arch: command not found
/opt/lampp/lampp: line 74: arch: command not found
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Error 1! Couldn't start Apache!
XAMPP: Starting diagnose...
XAMPP: Sorry, I've no idea what's going wrong.
XAMPP: Please contact our forum [http://www.apachefriends.org/f/](http://www.apachefriends.org/f/)
/opt/lampp/lampp: line 74: arch: command not found
XAMPP: Starting MySQL...
/opt/lampp/lampp: line 74: arch: command not found
XAMPP: Starting ProFTPD...
XAMPP:  - warning: unable to determine IP address of 'desktop_ubuntu'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/opt/lampp/etc/proftpd.conf'
XAMPP: Error 1! Couln't start ProFTPD!
XAMPP for Linux started.
keval@desktop ubuntu:~$ test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator
test: 361: ubuntu.pid: unexpected operator

Apache couldn't start.. and gives me  this error.. any Idea...??

---

### Post by Pax-Man on 2009-06-15
I simply love the control panel!

---

### Post by patarnoster on 2009-06-15
“Hello Everyone

I have a project I am working on and one thing I need is an opinion/ideas of the wider community. Which is here this is my project;

I have client, she is an amateur photographer and designer. She is looking to expand; she would like to show case her ideas and projects on a website, and eventually hopefully be able to sell these items on her website. So far I have chosen Joomla as my program, and this website will have a database which will contain the photos and index of sort, the website has to be very appealing to viewers any ideas on that would be much appreciated. How could I improve the site? And what things could I add that would make it more appealing?

What I need help in is some ideas for the website, like what kind of php creation program to the actually design and set up of how it would work.  

A layman’s explanations would be welcome as I am only a secondary student with moderate computer knowledge.  

Thanks in advance
PatarNoster”

---

### Post by soultaker on 2009-06-17
Hello,
I am new to Linux and I installed the XAMPP and everything works fine with the commands lampp start/restart etc but I fail to create the cool control panel.
On the newly popped file: xampp-control-panel.desktop I can't save it after I copy/paste the needed code for the creation of the icon/control panel.
I get error inside the text file : 
Could not find the file /home/admin3/.local/shar&#8230;mpp-control-panel.desktop.

I am using XAMPP 1.7.1 for Linux under Ububtu 9.04.

Sorry for the newbish question I will apreciate if someone can ghelp.

---

### Post by MadL10n on 2009-06-30
I followed the installation instructions and everything went well until i linked the htdocs directory to $USER. I don't know what I did wrong but when I navigate to [http://localhost/username](http://localhost/username) its empty even though I put about four folders in it.

---

### Post by indianinside on 2009-07-22
very helpful :)

---

### Post by indianinside on 2009-07-22
Thats a problem with sourceforge, not a problem, if you go here.. you will get the latest version 

[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

---

### Post by Zsebyagain on 2009-08-19
> **petervk said:**
> So far this post has just under 200 views, So great. If you read this and use it could you leave a reply saying if it was useful/useless? I'd like to keep improving this how-to, so feedback would be good.

Thanks for this how-to. I am new in Ubuntu-world, so first I had to figure it out how to navigate to the downloaded file using terminal, but  except this I made XAMPP work in some minutes, and I linked my public_html folder succesfully to the htdocs. :)  great work.

---

### Post by PaulWhipp on 2009-08-19
I used xampp in 8.04 and 8.10 but after upgrading to 9.04 I switched to the native installation of apache2 making my desktop machine a 'real' server.

Following the [ubuntu guide]("https://help.ubuntu.com/9.04/serverguide/C/httpd.html") to do this took half an hour. This included setting up php and mysql which was surprisingly straightforward.

This approach has the benefit of getting all the usual updates etc. for the server and of being 'closer' to the likely deployment environment when testing web applications.

As you end up with a 'production quality' server you can also contemplate using it as an intranet or even allowing client access over the internet when demonstrating or testing features. All in all I would not go back to xampp.

---

### Post by sherwinraavi on 2009-08-30
Hi, I tried this but it does not work for me. I'm a Linux noob using Jaunty and have the xampp-linux-1.7.2.tar.gz downloaded to the desktop. I typed the following into the terminal and this is the response i've gotten:

> username-laptop:~$ sudo tar xvfz xampp-linux-1.7.2.tar.gz -C /opt
tar: xampp-linux-1.7.2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


I don't know what this means or what to do to get it installed from here. Can someone please help? (and yes, this is what I want to do; not to install them separately).

---

### Post by PaulWhipp on 2009-08-30
> Hi, I tried this but it does not work for me. I'm a Linux noob using Jaunty... 

See my reply earlier in this thread. As Ubuntu progresses every six months, things get better. It is now very easy to use the standard repositories to get your system perfectly set up for web development.

There is no point in using the xampp package for Ubuntu any more. Install apache2 (use synaptic), and follow [the guide]("https://help.ubuntu.com/9.04/serverguide/C/httpd.html") to add php, mysql and https as necessary for your purposes.

That way you have a good guide, regular security updates as necessary, and canonical support if you need it (although you may need to upgrade to a server support rather than desktop package if you have a lot of queries specific to apache2).

---

### Post by dondad on 2009-08-30
> **sherwinraavi said:**
> Hi, I tried this but it does not work for me. I'm a Linux noob using Jaunty and have the xampp-linux-1.7.2.tar.gz downloaded to the desktop. I typed the following into the terminal and this is the response i've gotten:



I don't know what this means or what to do to get it installed from here. Can someone please help? (and yes, this is what I want to do; not to install them separately).


You can probably use the repositories easier, but it looks like the reason the tar failed is that you are not on the desktop if the prompt is correct in your example. You have to be in the same directory as the file in order to tar it. (or include the full path.)

---

### Post by Prentice on 2009-09-01
And how do I remove it?

---

### Post by PaulWhipp on 2009-09-01
```
sudo rm -r /opt/lampp
```

from memory.

If you are auto starting the server you should remove the relevant start up commands too.

---

### Post by TomBrown2009 on 2009-09-03
Is your XAMPP symbolic link not working?

Thanks to ReyPeste's post in this thread I've got it working for me. I'm posting this because it has taken me 3 days to solve this issue and from reading this entire thread I see others have the same problem. I see some members have even compromised in putting their development files in /opt/lampp/htdocs/ which would mean they would be outside of the /home directory completely and so (in most cases) on the distro files partition rather than the /home partition. Also, I am using 64 bit Jaunty so it does definitely work on this distro. I am no expert but would like to share my solution.

I installed XAMPP and tried to create a symbolic link with the code below (as the tutorial at the start of this thread) which I have used successfully before on another Ubuntu box.

mkdir ~/public_html

sudo ln -s ~/public_html /opt/lampp/htdocs/$USER

However. I get an error message.

"Access forbidden! You don't have permission to access the requested directory. There is either no index document or the directory is read-protected."

The Cure:

When I installed my 64bit Jaunty I read somewhere on this Forum that it would be a good idea to set permissions for better security on my /home directory to 700 (rwx --- ---) . It was this that was preventing XAMPP/apache to allow me to use [http://localhost/tom/](http://localhost/tom/) and giving me the 403 error. I've now changed to 755 (rwx r-x r-x). Now the thing is I've searched to find what the default Ubuntu /home directory permissions are and I can't find a reference. All I can find is the advice to set it to 700 (which caused my particular problemo). 755 I think is the Ubuntu default setting will mean other users on my pc can see my files but that's not a problem.

Tom

---

### Post by marako on 2009-09-03
I really like the *AMPP softwares but ive never tried if for linux.  I guess its time to move on from windows...

---

### Post by PaulWhipp on 2009-09-03
> Is your XAMPP symbolic link not working?

If you bite the bullet and install apache2 normally into Ubuntu, following the instruction link in my earlier post, you will be taken through setting the document path to whatever you like. In my case I have it set to /home/paul/websites because its my personal development machine but you could add multiple virtual hosts on a multi user system so that each person can have their own local collection of websites.

Keeps it simple.

---

### Post by C. M .Hughes on 2009-09-15
Hi y'all,
I followed these instructions on Ubuntu 9.04, but still can't get a test page to work:

[http://localhost/](http://localhost/)

I get, 'Page Load Error'. 

Here is the output from the command:

$sudo /opt/lampp/lampp status
Version: XAMPP for Linux 1.5.3a
Apache is not running.
MySQL is running.
ProFTPD is running.

It seems to me that, 'Apache is not running' is the problem- my question is, how do I fix it?

Many thanks.

---

### Post by Marwy on 2009-09-17
Works great on Ubuntu 9.04, thanks a lot! :).

---

### Post by EvolutionFallen on 2009-09-19
Hello,
I tried installing XAMPP via the instructions on the first page of this thread. All was going well, until I tried actually running it:
```

~/Desktop$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.5.3a...                    
XAMPP: Starting Apache with SSL (and PHP5)...         
XAMPP: Starting MySQL...                              
/opt/lampp/bin/mysql.server: 84: source: not found    
XAMPP: Starting ProFTPD...                            
XAMPP for Linux started.                              
~/Desktop$ /opt/lampp/bin/mysql.server: 334: log_success_msg: not found
```At this point I tried going to [http://localhost/](http://localhost/) and got a "Failed to Connect to Server" error.
I ran the command to stop the server anyway... The command prompt didn't come back up after "log_success_msg: not found" above -- I don't know if that matters:

```

sudo /opt/lampp/lampp stop
Stopping XAMPP for Linux 1.5.3a...
XAMPP: XAMPP-Apache is not running.
XAMPP: Stopping MySQL...           
XAMPP: Stopping ProFTPD...         
XAMPP stopped.   
```Anyone have an idea what the problem might be? I also tried going to the directory "~/.local/share/applications/xampp-control-panel.desktop" to set up the GUI interface as mentioned, but there was no "applications" folder in my "share" directory...

Thanks for any help in advance. I'm a bit of a newbie to this, but I'm trying to learn to do things from the command line instead of relying on GUIs.

---

### Post by agilius on 2009-09-20
I seem to have the same problem as EvolutionFallen. Restarting xampp didn't work. Additionally I sometimes get this when restarting:

```
Stopping XAMPP for Linux 1.5.3a...
XAMPP: XAMPP-Apache is not running.
XAMPP: Stopping MySQL...
XAMPP: Stopping ProFTPD...
XAMPP stopped.
Starting XAMPP for Linux 1.5.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
**/opt/lampp/bin/mysql.server: 84: source: not found**
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

root@agilius-laptop:~#** /opt/lampp/bin/mysql.server: 334: log_success_msg: not found**

```

I installed exactly as this guide described, I saw no error or anything during the installation. Might it be because I used root for this? 

Thanks in advance!

---

### Post by seuzo on 2009-09-21
Hi,

i got this error after install xampp and start xampp.

create a folder in home folder and link to /opt/lampp/htdocs/

when access [http://localhost/username/drupal-6.14/install.php](http://localhost/username/drupal-6.14/install.php)


Deprecated: Function ereg() is deprecated in /home/aik/public_html/drupal-6.14/includes/file.inc on line 902

Warning: Cannot modify header information - headers already sent by (output started at /home/aik/public_html/drupal-6.14/includes/file.inc:902) in /home/aik/public_html/drupal-6.14/includes/install.inc on line 618

Warning: Cannot modify header information - headers already sent by (output started at /home/aik/public_html/drupal-6.14/includes/file.inc:902) in /home/aik/public_html/drupal-6.14/includes/install.inc on line 619


anyone can advise on this?
i am lost
cannot reach the drupal/install.php

---

### Post by EvolutionFallen on 2009-09-21
> **seuzo said:**
> 
Warning: Cannot modify header information - headers already sent by (output started at /home/aik/public_html/drupal-6.14/includes/file.inc:902) in /home/aik/public_html/drupal-6.14/includes/install.inc on line 618

Warning: Cannot modify header information - headers already sent by (output started at /home/aik/public_html/drupal-6.14/includes/file.inc:902) in /home/aik/public_html/drupal-6.14/includes/install.inc on line 619


That warning happens when PHP tries to send header information to the browser after output has already been sent to it. Sometimes it's caused by extra whitespace at the end of a file. Other times it can be that some code was sent to output before whatever header function is being called. Usually you can fix it by finding the whitespace and deleting it, or by using PHP's output buffering fcns, I think.
Alas, I've never used Drupal so I don't know how exactly to solve the problem. But if you know PHP you might be able to figure it out. A search on Google may help too.

---

### Post by seuzo on 2009-09-22
> **EvolutionFallen said:**
> That warning happens when PHP tries to send header information to the browser after output has already been sent to it. Sometimes it's caused by extra whitespace at the end of a file. Other times it can be that some code was sent to output before whatever header function is being called. Usually you can fix it by finding the whitespace and deleting it, or by using PHP's output buffering fcns, I think.
Alas, I've never used Drupal so I don't know how exactly to solve the problem. But if you know PHP you might be able to figure it out. A search on Google may help too.

But i did not try to edited anything. is a new installation. possible to happen?

---

### Post by RachedTN on 2009-09-23
> **seuzo said:**
> Hi,

i got this error after install xampp and start xampp.

create a folder in home folder and link to /opt/lampp/htdocs/

when access [http://localhost/username/drupal-6.14/install.php](http://localhost/username/drupal-6.14/install.php)


Deprecated: Function ereg() is deprecated in /home/aik/public_html/drupal-6.14/includes/file.inc on line 902

Warning: Cannot modify header information - headers already sent by (output started at /home/aik/public_html/drupal-6.14/includes/file.inc:902) in /home/aik/public_html/drupal-6.14/includes/install.inc on line 618

Warning: Cannot modify header information - headers already sent by (output started at /home/aik/public_html/drupal-6.14/includes/file.inc:902) in /home/aik/public_html/drupal-6.14/includes/install.inc on line 619


It seems that XAMP 1.7.2 and drupal 6.13 and earlier have this problem, because I tried with XAMP 1.7.1 and drupal 6.12 and all it's OK, but when trying with XAMP 1.7.2 and Drupal 6.13 I encountred the same probleme as you.
I advise you to install LAMP : sudo tasksel
then choose LAMP, hit OK
after the istallation is done you can create a folder in home folder and link to /opt/lampp/www/
Good luck :)

---

### Post by seuzo on 2009-09-23
oh. What is LAMP? 

LAMP is a software ? is will install Apache? (web server)

does it include MySQL?
because i wanted to install drupal CMS to try out.

sorry that i am nob on ubuntu but interested to know all this knowledge.

Any info link i can read up on LAMP?

---

### Post by RachedTN on 2009-09-23
LAMP : Linux/Apache/MySQL/PHP
as you are a newbie (and me too ;) ) here is a useful link : [http://www.howtoforge.com/ubuntu_lamp_for_newbies]("http://www.howtoforge.com/ubuntu_lamp_for_newbies")
Enjoy it :)

---

### Post by aditya.t on 2009-10-09
In trying to activate the desktop panel for XAMPP, i save unable to save the file

Could not find the file /home/aditya/.local/shar…mpp-control-panel.desktop.
Please check that you typed the location correctly and try again.

---

### Post by Amethyst05 on 2009-10-18
> **aditya.t said:**
> In trying to activate the desktop panel for XAMPP, i save unable to save the file

Could not find the file /home/aditya/.local/shar…mpp-control-panel.desktop.
Please check that you typed the location correctly and try again.

When I did this on one of my computers I found that I didn't have an applications folder. Check that all your folders are there. If they are not, you will have to create them and then this line will work:


```
gedit ~/.local/share/applications/xampp-control-panel.desktop
```

---

### Post by Amethyst05 on 2009-10-18
Thank you for these instructions. I am a complete newcomer to Linux so appreciate everything I have learned via this forum and I'm having great fun with Ubuntu. No computer is safe from me installing Ubuntu on it! :)

I now have a problem with my testing server and I cannot seem to find an answer. 

The root of my site seems to be /myname/mysite/. Is there anyway to make the root start after /mysite/ the way it would in a live environment on the internet? 

I need to do this as many files have include files with links such as /includes/header.php and this does not work in the testing environment.

I would be grateful for any help or pointers in the right direction. Thanks.

By the way, I have edited the DocumentRoot in httpd.conf file but this will only work for one site and I have several sites I need to test. Is there any way to do this?

---

### Post by Amethyst05 on 2009-10-19
OK, I've solved my problem by setting up virtual hosts.

In case anyone is interested in this sort of set up, this is what I did.

1. First of all enable virtual hosts by editing httpd.conf:

```

sudo gedit /opt/lampp/etc/httpd.conf

```Find #Include etc/extra/httpd-vhosts.conf and remove the # so it looks like:

```

Include etc/extra/httpd-vhosts.conf

```Save and close.

2. Now add the virtual host:

```

sudo gedit /opt/lampp/etc/extra/httpd-vhosts.conf

```You will find two virtual hosts set up as examples. Remove or edit these with your own details.

```

<VirtualHost *:80>
    ServerAdmin webmaster@mysite.com
    DocumentRoot /opt/lampp/htdocs/myname/mysite
    ServerName mysite.com
    ErrorLog logs/mysite.com-error_log
    CustomLog logs/mysite.com-access_log common
</VirtualHost>

```Save and close the file.

3. Now tell Xampp where to find this site:

```

sudo gedit /etc/hosts

```Add this:

```

127.0.0.1    mysite.com

```Save and close the file.

4. Restart xampp server

```

sudo /opt/lampp/lampp restart

```5. Now you can point your browser to [http://mysite.com](http://mysite.com) and it should fetch your site.


These are my instructions and I am a beginner so please let me know if there is anything not correct in this. Thanks.

---

### Post by johanbove on 2009-10-22
Response to 			#[**280**]("http://ubuntuforums.org/showpost.php?p=7892714&postcount=280")

Hello Tom,

I'm having exact the same issue as you have described in this post;

Does you error_log contain the message that symbolic links cannot be used? Do you have your /home on an extra mounted drive ? I have my /home folder mounted through fstab with these options:  "defaults,rw,nodev"

I'm kind stuck here...

Regards,
Johan

---

### Post by PaganDruid on 2009-11-04
Hello all, not sure if this is the right place to post...

almost a complete newbie.

For the past few years i have been using wamp for web development.  
The only reason i havent got xampp running in ubuntu is because it just damn well doesn't work!  I have followed EVERY SINGLE one of the almost identical tedious tutorial(s) which each start with 'simply download and extract',bah!

I have downloaded xampp, following the instructions, extracting the file from the downloads file in terminal, but the terminal returns 'no file or directory', and im looking at the directory that apparently doesn't exist. Is my syntax wrong...help!

Why isnt there a .deb bundled with apache,mysql,php?

I love almost everything about Ubuntu, but i mean, wamp, i double click the installer app, and its done...xampp/ubuntu, well its been almost 4 years and i stil havent managed to get it working properly

any assistance would be very much appreciated

---

### Post by Mickser_52 on 2009-11-04
Hi, I just installed xampp in ubuntu 9.10 following instructions from this site [http://www.officeray.com/?blog:how-to-install-xampp-on-ubuntu-jaunty-9.04:4ZXD1405V0]("http://www.officeray.com/?blog:how-to-install-xampp-on-ubuntu-jaunty-9.04:4ZXD1405V0") and it appears to be working. I haven't had time to test it yet though

---

### Post by PaulWhipp on 2009-11-04
As a professional web application developer, building the lamp stack on ubuntu using xampp seems a waste of effort to me.

I was doing it up until 8.04 but these days Ubuntu is very good at setting up the stack directly. Just do the following:

```

sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server

```

Make sure you remember the password for mysql!

You should then have a working server serving pages from /var/www

From there, there are lots of ways you can go. [http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html](http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html) has details.

Personally, I develop web sites and web applications using this scheme locally.

I also use ssmtp so that sending mail from the sites under development works well enough for testing (if you are developing something that processes incoming email this wont do though).

```

sudo rm /etc/ssmtp/ssmtp.conf

```
Follow the instructions at [http://www.nixtutor.com/linux/send-mail-with-gmail-and-ssmtp/](http://www.nixtutor.com/linux/send-mail-with-gmail-and-ssmtp/) to set this up to send via a gmail account.

If you don't want to open your machine up to the world, you can repeat this on an EC2 Ubuntu instance to for testing or (with appropriate modifications for persistence and security) to deploy the live websites too!

---

### Post by PaganDruid on 2009-11-05
Thank you very much for the assistance :) 


I dont suppose you could suggest a nice Linux app to replace dreamweaver?

Once again thanks :)

---

### Post by PaulWhipp on 2009-11-05
off topic a bit but for Dreamweaver just get a second monitor and run with what you've got :)

Really though - You can use just about any decent editor in one window and just save then reload the page in your browser in another window. Its not quite wysiwyg but its accurate and fast.

I use vim for general editing, Zend Studio for php and vim + tidy to keep my html neat and accurate.

Always having the browser looking at your work and reloading frequently to check it is the key to getting stuff done.

---

### Post by PaganDruid on 2009-11-05
Thank you very much for the help!

If i could be a further bother...

Is it entirely necessary to paste my existing HTML/PHP projects into the /www with the command line terminal (root user bs). I am dealing with a lot of imported PHP/AJAX/Java/HTML content from my windows local web development server and i would really like to just copy paste them into my localhost like i do in windows. Security is not an issue to me, I really just want to replace my wamp5/dreamweaver platform for development :( .

Also i must admit i am really confused as to what packages i need to continue from here.  What application do i use for viewing my own php projects on the firefox browser,and how do i get them there? 

how does one setup mysql and ms access connections (product catalogs etc)

And of course what dreamweaver substitutes are there?

Sorry about the noob questions :P

once again, thank you very very much so far :)

---

### Post by PaulWhipp on 2009-11-05
> Is it entirely necessary to paste my existing HTML/PHP projects into the /www with the command line terminal (root user bs). I am dealing with a lot of imported PHP/AJAX/Java/HTML content from my windows local web development server and i would really like to just copy paste them into my localhost like i do in windows. Security is not an issue to me, I really just want to replace my wamp5/dreamweaver platform for development

I am not sure what you mean by this. You can use subfolders under www for each project and just refer to them in the url as [http://localhost/project1](http://localhost/project1) etc.

Firefox will work with php from the outset so should be fine. If its not being served php files, try restarting apache (sudo /etc/init.d/apache2 restart).

Mysql should all be there and working as normal. If you are importing existing websites you need to create and populate the matching databases and users so that your configuration matches up. I've no idea about hooking up MS Access because that is in windows.

If you really want a dreamweaver substitute, try [bluefish]("http://bluefish.openoffice.nl/").

---

### Post by PaganDruid on 2009-11-05
Hi,thanks again

Sorry, i meant to say is there a way to paste php/html projects into the /www WITHOUT using the command line as root.  Which is to say is there some way of using the gnome desktop explorer to paste the projects as the root user.

again sorry for the newbie question(s)

---

### Post by PaulWhipp on 2009-11-06
If its your own machine and secure you can change the permissions on the www folder:
```

sudo chmod go+w /var/www

```

Alternatively you can put your projects in your home folder eg ~/websites/project1 etc. and either change the apache configuration to point there or put a link to that folder in /var/www.

---

### Post by coldkreap on 2009-11-10
Thank you for this. It worked perfectly for me. I saved my php files to the public_html directory and they showed up on localhost and ran as I expected. THANKS!!

---

### Post by DominaDoom on 2009-11-11
> **PaulWhipp said:**
> If its your own machine and secure you can change the permissions on the www folder:
```

sudo chmod go+w /var/www

```

Alternatively you can put your projects in your home folder eg ~/websites/project1 etc. and either change the apache configuration to point there or put a link to that folder in /var/www.

I think I am getting closer to being on the right track.  I get a link at [http://localhost/](http://localhost/) to the Index.html file found in /var/www which reads "It Works" instead of the XAMPP test page.  There is also a strange locked lampp file in my Home folder.  I know the issue could involve changing modes of this mystery lampp file and/or linking the appropriate directory to var/www.  Any help from anyone would be appreciated.  Thank You.

---

### Post by PaulWhipp on 2009-11-11
> There is also a strange locked lampp file in my Home folder. I know the issue could involve changing modes of this mystery lampp file and/or linking the appropriate directory to var/www. Any help from anyone would be appreciated.

There are two setups being covered here now (my fault really) - xampp and a real apache2 web server. I think you may be confusing the two. They both ultimately do the same thing. xampp was much better when it used to be a pain configuring your own machine to be a server because it set up the whole lamp stack and gave you a control panel to manage it. These days, setting up a real server is so easy, I recommend you leave xampp alone unless you are working in Windows (where its still very handy).

/var/www is the default location for a real apache2 server. Its started up and stopped by using ```
sudo /etc/init.d/apache2 restart
```.

xampp (from memory) uses /opt/lampp/htdocs by default for its web documents. I can't remember how you start and stop it but it will have ..lampp.. in the path to the apache2 command somewhere.

I think, from your note, that you have a real server working and some xampp stuff hanging over. I recommend you clean out the xampp stuff completely to remove the confusion. xampp is a great package for systems that can't easily support the lamp stack but Ubuntu can these days - its used on a lot of professional web servers and can be set up really easily for developers or content creators on local systems too.

---

### Post by rocklee on 2009-11-12
Hey guys, I tried installing XAMPP in Ubuntu 9.10 following some of the instructions here and had somehow got it to work.  I used the virtual host to relocate my working web files instead of using Xampp's htdoc directory.

Now my query is trying to access the site on my other PCs on the same network.  I can ping my web server IP and can even see the default directory on the server that points to XAMPP index page (using [http://192.168.0.4](http://192.168.0.4)), but I can't seem to connect to my own directories using the host name created (ie. localhost.ajax.com).

I tried to link 192.168.0.4 to a hostname but that doesn't work.

Can anyone advice what I need to setup on the web server or client PCs?

---

### Post by sitex on 2009-11-13
If someone want to help to install Xampp on Ubuntu. You can get help with related screen shots with the site [Solutionz click here to go the site]("http://solutionz.yolasite.com/")

---

### Post by milos037 on 2009-11-14
Hi everybody,
I have copied all my projects from wamp/windows into
~/public_htmland I can list all of them  in browser with http://localhost/$user/
project1
project2
...

but in all files (.tpl, .html, .php ...) I used absolute path to link pages and it works fine on windows. But not on Ubuntu. 
example:
httpd://localhost/milos/project1/index.php
(critical part of file)
                    <div id="navigation"> 
                        <ul> 
                            <li class="active"><a href="/">HOME</a></li> 
                            <li><a href="/services/">SERVICES</a></li> 
                            <li><a href="/clients/">CLIENTS</a></li> 
                            <li><a href="/prices/">PRICES</a></li> 
                            <li><a href="/about/">ABOUT US</a></li> 
                            <li><a href="/contact/">CONTACT</a></li> 
                        </ul> 
                    </div>
PROBLEM: 
my home page link [http://localhost/](http://localhost/)  instead [http://localhost/milos/project1/](http://localhost/milos/project1/)

"/services/"  link to [http://localhost/services](http://localhost/services) instead [http://localhost/milos/project1/sevices/](http://localhost/milos/project1/sevices/) 
How can I fix this, without change all my files?
Thanks

---

### Post by Jaysn on 2010-01-01
omg thats basic html...
well a link using "/something/" withouth "http://www.somedomain.tld/somethingelse/something/" is a relative path, so the link starting with / is relative to the domain root, wich is "localhost/" so href="/" goes to http://www.domain.tld/" and href="/lol/" goes to "http://www.domain.tld/lol/" to fix this relatively you just need to delete the first "/" so it would add the foldername/directoryname to the current one. or you could try href="/milos/project1/" and
href="/milos/project1/service/" 
sry for the bad english and description, i hope you know what i mean :D
*edit*
<div id="navigation"> 
                        <ul> 
                            <li class="active"><a href="/milos/project1/">HOME</a></li> 
                            <li><a href="/milos/project1/services/">SERVICES</a></li> 
                            <li><a href="/milos/project1/clients/">CLIENTS</a></li> 
                            <li><a href="/milos/project1/prices/">PRICES</a></li> 
                            <li><a href="/milos/project1/about/">ABOUT US</a></li> 
                            <li><a href="/milos/project1/contact/">CONTACT</a></li> 
                        </ul> 
                    </div>
this should help ;)

@topic
i would prefer to create a user folder in htdocs instead of a public_html folder in the user folder and link from the home directory to the htdocs/$USER folder because that way you can administrate the files via FTP otherwise i cant go into my folder remotely :/
again sry for bad en.

---

### Post by The Other Steve on 2010-01-07
> **TeaSwigger said:**
> XAMPP has a .gif icon in /opt/lampp/htdocs that you could use, or if it has to be .xpm or .png format it should be a snap to convert it in GIMP or some such.
It is.  

For my preferences, the icon at 48x48 was a little too large and obtrusive, so I resized it on a transparent background.

[[IMG]http://img509.imageshack.us/img509/7729/xamppsm.png[/IMG]]("http://img509.imageshack.us/i/xamppsm.png/")
If you'd like it, it's here:

[http://img509.imageshack.us/img509/7729/xamppsm.png](http://img509.imageshack.us/img509/7729/xamppsm.png)

To change the icon in the Applications Menu:
right click on Applications
select Edit Menus
navigate to XAMPP Control Panel and select it
select Properties
click on the existing icon 
navigate to the location of the XAMPP icon you downloaded and select it
[[IMG]http://img63.imageshack.us/img63/4873/xamppiconscreen2.th.jpg[/IMG]]("http://img63.imageshack.us/i/xamppiconscreen2.jpg/")

To change the icon on the Desktop:
right click on the icon
select Properties
click on the existing icon
navigate to the location of the XAMPP icon you downloaded and select it
[[IMG]http://img63.imageshack.us/img63/2381/xamppiconscreen1.th.jpg[/IMG]]("http://img63.imageshack.us/i/xamppiconscreen1.jpg/")

---

### Post by ginost7 on 2010-01-08
Hello i followed the above commands as root 


 sudo mkdir /opt/lampp/htdocs/homefiles/

Then made the equivilant directory in our home directory.

    mkdir ~/public_html/

And finally link them together.

    sudo ln -S ~/public_html/ /opt/lampp/htdocs/homefiles/

well on mozilla 

[http://localhost/xampp/homefiles](http://localhost/xampp/homefiles)

does not exist.  The error is "object not found" All my php files are in public_html directory.

Can anybody help????

Gino

---

### Post by ginost7 on 2010-01-08
I was under the impression that all my php files in /home/gino/homefiles will be shown in 

/opt/lampp/htdocs/webapps

AND 

when i open a browser :

[http://localhost/xampp/webapps](http://localhost/xampp/webapps)

USING THE ABOVE COMMANDS

---

### Post by Dragonbite on 2010-01-22
When trying to start Drupal, I got the following errors (duplicated multipel times) > Deprecated: Function ereg() is deprecated in /opt/lampp/htdocs/includes/file.inc on line 902

Warning: Cannot modify header information - headers already sent by (output started at /opt/lampp/htdocs/includes/file.inc:902) in /opt/lampp/htdocs/includes/install.inc on line 618

The solution I found was found here :
[http://drupal.org/node/586416]("http://drupal.org/node/586416")
> go to your drupal directory..
you hav to edit drupal\includes\file.inc file a little bit..
open file .inc
search for elseif ($depth >= $min_depth && ereg($mask, $file)) line in that file
edit the above line by
elseif ($depth >= $min_depth && mb_ereg($mask, $file))

your problem is solved..


It worked for me like a charm. It just took me a long time to re-find this solution.

---

### Post by Billsputters on 2010-01-28
I've followed the installation to the letter, trying to setup a server for home use/testing.

PHP is running and security has been set as advised. However, if I try to login the SQL
```
mysql -u root

```

I get 
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

I've searched and read for the last two days on and off in attempy to solve it, but alas am getting nowhere. Any ideas?

---

### Post by PaulWhipp on 2010-01-28
Hi Billsputters,

/var/run/mysqld/mysqld.sock is the right socket for the default mysql-server installation. Check mysql server is running as it should be:

```

~$ sudo /etc/init.d/mysql status
 * /usr/bin/mysqladmin  Ver 8.41 Distrib 5.0.75, for debian-linux-gnu on i486
Copyright (C) 2000-2006 MySQL AB
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license

Server version		5.0.75-0ubuntu10.2
Protocol version	10
Connection		Localhost via UNIX socket
UNIX socket		/var/run/mysqld/mysqld.sock
Uptime:			11 hours 31 min 3 sec

Threads: 1  Questions: 12068  Slow queries: 0  Opens: 1643  Flush tables: 3  Open tables: 64  Queries per second avg: 0.291

```

You can start it with "sudo /etc/init.d/mysql start" if its not running although it should start automatically after a normal installation.

Pretty much whatever the problem, it may be easiest to purge and reinstall it since you presumably don't yet have any mysql content.

---

### Post by Billsputters on 2010-01-29
I found part of the problem, as you suspected, mysql was not running, which doesn't help things. So I tried to start it, and it came up with a simple fail.

So, I purged out mysql and then tried to reinstall.

But now I get 

```
Couldn't find package mysql
```

Think I've done some serious damage here!

Help!

Sorted. It installed OK during the last update

---

### Post by PaulWhipp on 2010-01-29
Try
```

~ $ sudo aptitude purge php5-mysql libapache2-mod-php5 mysql-server mysql-client
~ $ sudo dpkg -a --configure
~ $ sudo aptitude install php5-mysql libapache2-mod-php5 mysql-server mysql-client

```

That should have you started back from scratch.

---

### Post by n0v1c3n00b on 2010-02-05
Could not find the file /home/ayyub/.local/share…mpp-control-panel.desktop.

that's the error I'm getting when I attempt to save the copied text to allow the control panel

---

### Post by a_rojilla on 2010-02-20
> **n0v1c3n00b said:**
> Could not find the file /home/ayyub/.local/share…mpp-control-panel.desktop.

that's the error I'm getting when I attempt to save the copied text to allow the control panel

Same here.

Months and even years ago I had no problems with this applet with different versions of Ubuntu. In fact, only some days ago I had no problems in a new laptop with Karmic (9.10) but **now** I'm getting this error in a new PC where I also installed Karmic...

The difference? That this time I installed Ubuntu with a **separated /home partition**.

I guess that's what's causing the problem because it is, well, the only difference. Any ideas on how to solve this?

Regards.

---

### Post by a_rojilla on 2010-02-20
Ok, it seems that the folder applications (in ~/.local/share/) was not created, so just create it or do the following to get the applet:

1 - Right-click on Ubuntu's logo in the main menu bar.
2 - Select "Edit menus" and a window called "Main Menu" will appear.
3 - In this window, from the list on the left pick the menu where you want the applet to be placed in (I picked "Programming").
4 - Press the "New Item" button on the right.
5 - In the new window (called "Create Launcher"):
    - Type: "Application".
    - Name: "XAMPP Control Panel" (or whatever you want to call it).
    - Command: gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
    - Comment: any comment you wish about the applet or what it is for or it does or just let it blank.
    - Now click on the big icon at the left (in this same "Create Launcher" window) and pick an icon.
    - Click "OK"
6 - Click "Close" in the "Main Menu" window. Done.

I hope this helps.

Regards.

---

### Post by carpman on 2010-03-22
Hello, ok set this up and all was working till set security, now under status everything is deactivated?

Tried restarting but still the same?

That said php must be running as i can load myphpadmin fine!

any ideas?

cheers

---

### Post by beachbuggy on 2010-04-05
Hi There,

I have setup LAMP and the test page on localhost works

I have then followed the code but when I go to localhost/bart I get an error saying "Not Found

The requested URL /bart was not found on this server."

I'm not sure what to do next :(

My folders are there in opt/lamp/htdocs and these were put there via my linked folder in home/bart/public_html

This was what the instructions said to do.

Any ideas.. Thanks

Collin

---

### Post by MMosley on 2010-04-07
> **beachbuggy said:**
> Hi There,

I have setup LAMP and the test page on localhost works

I have then followed the code but when I go to localhost/bart I get an error saying "Not Found

The requested URL /bart was not found on this server."

I'm not sure what to do next :(

My folders are there in opt/lamp/htdocs and these were put there via my linked folder in home/bart/public_html

This was what the instructions said to do.

Any ideas.. Thanks

Collin

Hi Collin, 

I had the same problem.  This is what worked for me:

[http://localhost/public_html](http://localhost/public_html) 
 
(instead of [http://localhost/user](http://localhost/user))

Hope that might help you!

---

### Post by damnated on 2010-04-10
Excellent tutorial, worked like a charm.

---

### Post by windphere on 2010-04-17
> **petervk said:**
> This is a how-to for setting up a web development environment easily. This guide will install the XAMPP lampp stack into /opt, setup an easy way to start it up and shut it down, and link a folder in your home directory to the webserver.

**WARNING**
This guide is aimed at a development environment only and should not be used as a public webserver. To setup a public webserver follow the directions on the Ubuntu wiki [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

As this is Ubuntu, all the major parts of a typical web server are included (in the main repo, or on the Ubuntu Server CD) and this is a great way to setup a server. The ubuntu developers have prepared a great web server and have made the process as seemless as possible. 

But what if even the official way is still to complicated? What if you just want a quick web server for development?

Fortunately there is the XAMPP project: [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html). The XAMPP project bundles Apache, PHP4 & 5, Perl, mySQL, and a bunch of other utilities/applications into an simple package for Mac OSX, Windows, Solaris, and Linux. Obviously this HOWTO only deals with the linux version.

For those of you with already existing Apache/mySQL/php installations it installs everything into /opt so it doesn't conflict with any other installation, and it is completely setup and ready to run.

[SIZE=3]**_Install XAMPP_**[/SIZE]

Two easy steps:
[LIST=1]
[*]Download the most recent version of XAMPP: (at time of writing 1.5.3a)
[http://prdownloads.sourceforge.net/xampp/xampp-linux-1.5.3a.tar.gz?download](http://prdownloads.sourceforge.net/xampp/xampp-linux-1.5.3a.tar.gz?download)
(Source URL: [http://www.apachefriends.org/en/xampp-linux.html#374](http://www.apachefriends.org/en/xampp-linux.html#374))
[*]Extract the archive to /opt using sudo: (make sure you are in the directory that you downloaded the archive to) ```
sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt
```
[/LIST]

[SIZE=3]**_Start XAMPP_**[/SIZE]

To start it up, open a terminal and type this:
```
sudo /opt/lampp/lampp start
```[SIZE=3]**_Stop XAMPP_**[/SIZE]

To stop it, open a terminal and type this:
```
sudo /opt/lampp/lampp stop
```[SIZE=3]**_Additional XAMPP commands_**[/SIZE]

To see additional commands, open a terminal and type this:
```
sudo /opt/lampp/lampp
```[SIZE=3]**_Sweet XAMPP Control Panel_**[/SIZE]

[IMG]http://img108.imageshack.us/img108/5647/screenshotxamppcontrolpanelfj6.png[/IMG]

To use the sweet gtk/python control panel:

Run in a terminal: ```
 sudo gedit ~/.local/share/applications/xampp-control-
panel.desktop
```Paste the following into the open file and save and exit.
```
[Desktop Entry]
Comment=Start/Stop XAMPP
Name=XAMPP Control Panel
Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
Icon[en_CA]=/usr/share/icons/Tango/scalable/devices/network-wired.svg
Encoding=UTF-8
Terminal=false
Name[en_CA]=XAMPP Control Panel
Comment[en_CA]=Start/Stop XAMPP
Type=Application
Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg
```"XAMPP Control Panel" will show up in your applications menu under Internet. Use the Alacarte Menu Editor to move it around.

[SIZE=3]**_Test to see if XAMPP is running_**[/SIZE]

Once XAMPP is up and running open firefox and go to: [http://localhost/](http://localhost/)

You should see the XAMPP test page:

[IMG]http://static.apachefriends.org/images/380.jpg[/IMG]

[SIZE=3]**_Location of files and uploading_**[/SIZE]

XAMPP by default uses /opt/lampp/htdocs as the root web directory. The easiest way to start working on files is to link a folder in your home directory into this directory.
My user name is peter so I have /home/peter/public_html linked to /opt/lampp/htdocs/peter. So if I navigate to [http://localhost/peter/](http://localhost/peter/) I get a listing of all the files/folders in that directory. (As long is there isn't a index.php/html/etc file)
To set this up, run in a terminal:
[LIST=1]
[*]Make public_html directory in home directory: ```
mkdir ~/public_html
```
[*]Link to /opt/lampp/htdocs ```
sudo ln -s ~/public_html /opt/lampp/htdocs/$USER
```
[/LIST]
Now any files and folders you place in ~/public_html will be published to your personal webserver. 

Bookmark [http://localhost/username](http://localhost/username) to make this easy to access.

[SIZE=3]**_WARNING - SECURITY_**[/SIZE]
[http://www.apachefriends.org/en/xampp-linux.html#381](http://www.apachefriends.org/en/xampp-linux.html#381)
Open holes:
[LIST=1]
[*]The MySQL administrator (root) has no password.
[*]The MySQL daemon is accessible via network.
[*]ProFTPD uses the password "lampp" for user "nobody".
[*]PhpMyAdmin is accessible via network.
[*]Examples are accessible via network.
[*]MySQL and Apache running under the same user (nobody).
[/LIST]
This doesn't leave your whole system wide open, but someone could hack your XAMPP installation, so be wary.
To fix most of the security weaknesses open a terminal and run: ```
sudo /opt/lampp/lampp security
```[SIZE=3]**_Feedback_**[/SIZE]
Please read [ this post]("http://www.ubuntuforums.org/showpost.php?p=1310039&postcount=5").

---- EDIT - July 28, 2006 ----
Minor Edits

---- EDIT - August 1, 2006 ----
Re-did xampp control panel shortcut to make it easier.

---- EDIT - August 16, 2006 ----
Added warning for public web servers and edited intro to make it more accurate.

---- EDIT - September 1, 2006 ----
Added sudo to security command.

--- EDIT sudo to 
gedit ~/.local/share/applications/xampp-control-panel.desktop

---

### Post by windphere on 2010-04-17
> **petervk said:**
> This is a how-to for setting up a web development environment easily. This guide will install the XAMPP lampp stack into /opt, setup an easy way to start it up and shut it down, and link a folder in your home directory to the webserver.

**WARNING**
This guide is aimed at a development environment only and should not be used as a public webserver. To setup a public webserver follow the directions on the Ubuntu wiki [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

As this is Ubuntu, all the major parts of a typical web server are included (in the main repo, or on the Ubuntu Server CD) and this is a great way to setup a server. The ubuntu developers have prepared a great web server and have made the process as seemless as possible. 

But what if even the official way is still to complicated? What if you just want a quick web server for development?

Fortunately there is the XAMPP project: [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html). The XAMPP project bundles Apache, PHP4 & 5, Perl, mySQL, and a bunch of other utilities/applications into an simple package for Mac OSX, Windows, Solaris, and Linux. Obviously this HOWTO only deals with the linux version.

For those of you with already existing Apache/mySQL/php installations it installs everything into /opt so it doesn't conflict with any other installation, and it is completely setup and ready to run.

[SIZE=3]**_Install XAMPP_**[/SIZE]

Two easy steps:
[LIST=1]
[*]Download the most recent version of XAMPP: (at time of writing 1.5.3a)
[http://prdownloads.sourceforge.net/xampp/xampp-linux-1.5.3a.tar.gz?download](http://prdownloads.sourceforge.net/xampp/xampp-linux-1.5.3a.tar.gz?download)
(Source URL: [http://www.apachefriends.org/en/xampp-linux.html#374](http://www.apachefriends.org/en/xampp-linux.html#374))
[*]Extract the archive to /opt using sudo: (make sure you are in the directory that you downloaded the archive to) ```
sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt
```
[/LIST]

[SIZE=3]**_Start XAMPP_**[/SIZE]

To start it up, open a terminal and type this:
```
sudo /opt/lampp/lampp start
```[SIZE=3]**_Stop XAMPP_**[/SIZE]

To stop it, open a terminal and type this:
```
sudo /opt/lampp/lampp stop
```[SIZE=3]**_Additional XAMPP commands_**[/SIZE]

To see additional commands, open a terminal and type this:
```
sudo /opt/lampp/lampp
```[SIZE=3]**_Sweet XAMPP Control Panel_**[/SIZE]

[IMG]http://img108.imageshack.us/img108/5647/screenshotxamppcontrolpanelfj6.png[/IMG]

To use the sweet gtk/python control panel:

Run in a terminal: ```
sudo gedit /usr/share/applications/xampp-control-panel.desktop panel.desktop
```Paste the following into the open file and save and exit.
```
[Desktop Entry]
Comment=Start/Stop XAMPP
Name=XAMPP Control Panel
Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
Icon[en_CA]=/usr/share/icons/Tango/scalable/devices/network-wired.svg
Encoding=UTF-8
Terminal=false
Name[en_CA]=XAMPP Control Panel
Comment[en_CA]=Start/Stop XAMPP
Type=Application
Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg
```"XAMPP Control Panel" will show up in your applications menu under Internet. Use the Alacarte Menu Editor to move it around.

Control Panel will be located under Applications-Other-XAMPP Control Panel

[SIZE=3]**_Test to see if XAMPP is running_**[/SIZE]

Once XAMPP is up and running open firefox and go to: [http://localhost/](http://localhost/)

You should see the XAMPP test page:

[IMG]http://static.apachefriends.org/images/380.jpg[/IMG]

[SIZE=3]**_Location of files and uploading_**[/SIZE]

XAMPP by default uses /opt/lampp/htdocs as the root web directory. The easiest way to start working on files is to link a folder in your home directory into this directory.
My user name is peter so I have /home/peter/public_html linked to /opt/lampp/htdocs/peter. So if I navigate to [http://localhost/peter/](http://localhost/peter/) I get a listing of all the files/folders in that directory. (As long is there isn't a index.php/html/etc file)
To set this up, run in a terminal:
[LIST=1]
[*]Make public_html directory in home directory: ```
mkdir ~/public_html
```
[*]Link to /opt/lampp/htdocs ```
sudo ln -s ~/public_html /opt/lampp/htdocs/$USER
```
[/LIST]
Now any files and folders you place in ~/public_html will be published to your personal webserver. 

Bookmark [http://localhost/username](http://localhost/username) to make this easy to access.

[SIZE=3]**_WARNING - SECURITY_**[/SIZE]
[http://www.apachefriends.org/en/xampp-linux.html#381](http://www.apachefriends.org/en/xampp-linux.html#381)
Open holes:
[LIST=1]
[*]The MySQL administrator (root) has no password.
[*]The MySQL daemon is accessible via network.
[*]ProFTPD uses the password "lampp" for user "nobody".
[*]PhpMyAdmin is accessible via network.
[*]Examples are accessible via network.
[*]MySQL and Apache running under the same user (nobody).
[/LIST]
This doesn't leave your whole system wide open, but someone could hack your XAMPP installation, so be wary.
To fix most of the security weaknesses open a terminal and run: ```
sudo /opt/lampp/lampp security
```[SIZE=3]**_Feedback_**[/SIZE]
Please read [ this post]("http://www.ubuntuforums.org/showpost.php?p=1310039&postcount=5").

---- EDIT - July 28, 2006 ----
Minor Edits

---- EDIT - August 1, 2006 ----
Re-did xampp control panel shortcut to make it easier.

---- EDIT - August 16, 2006 ----
Added warning for public web servers and edited intro to make it more accurate.

---- EDIT - September 1, 2006 ----
Added sudo to security command.

--- Edit - April 17, 2010
Replace code Ubuntu 9.04
sudo gedit /usr/share/applications/xampp-control-panel.desktop

---

### Post by EJI on 2010-04-20
Hi Guys,

I am unable to get apache to start using Xampp Control Panel or cli

1st problem:
mysql  stopped
apache stopped

using webmin 1.5 stopped mysql server. stopped apache server.

used xampp control panel.

mysgl RUNNING
apache STOPPED

Start Apache via webmin, still no luck

Here is my installed packages of apache on my sys:

Installed packages for apache:
libapache2-mod-php5, apache2-mpm-prefork,apache2-utils,
apache2.2-bin,apache2.2-common

Am I missing a package?

When I run [http://localhost](http://localhost)  i get message It Works!

Thanks
EJI

---

### Post by bb93 on 2010-04-20
I only unknowned Sweet XAMPP Control Panel.

Thanks for the Tuto :)

---

### Post by diabolicalspooz on 2010-04-25
You can not have 2 different instances of Apache running like this it appears as though you install the synaptic package for apache somewhere along the line either through apt-get install apache2 or used the GUI... which has seem to have broken your xampp the reasons why you are able to browse to the [http://localhost/](http://localhost/) and get a message saying it works is because your ubuntu is directly running apache not XAMPP.... this is why your xampp applet is saying that it is not running. Furthermore Xampp will not work since your xampp install is self contained with the apache,mysql,phpadmin etc... and the instance of apache that is the webserver is on it own. 

if you drop down to a shell and type "sudo /opt/lampp/lampp start" if it is not started already or if it is started "sudo /opt/lampp/lampp restart"  and watch the screen it will first say the Apache is not running when it goes to shut down the program then once it does it will not allow it to start because another Apache Server is already running. Which is the other install... 

Simple fix get rid of the synaptic repo's for Apache and once you do so things should be A ok...

> **EJI said:**
> Hi Guys,

I am unable to get apache to start using Xampp Control Panel or cli

1st problem:
mysql  stopped
apache stopped

using webmin 1.5 stopped mysql server. stopped apache server.

used xampp control panel.

mysgl RUNNING
apache STOPPED

Start Apache via webmin, still no luck

Here is my installed packages of apache on my sys:

Installed packages for apache:
libapache2-mod-php5, apache2-mpm-prefork,apache2-utils,
apache2.2-bin,apache2.2-common

Am I missing a package?

When I run [http://localhost](http://localhost)  i get message It Works!

Thanks
EJI

---

### Post by honnour on 2010-05-03
Hello;

First of all thank you for your tutorial.

I installed the xampp just fine and its working. Then I tried to make a shorcut to /applications/internet as you told.

I wrote the code, then i copy and paste the other code to empty page. When i tried to save it I have a problem.
It says;

"Could not find the file /home/onur/.local/share/&#8230;mpp-control-panel.desktop."
"Please check that you typed the location correctly and try again."

What should i do to fix this?

Edit: i solved my problem. Dont answer this.

Thank you

---

### Post by zakeen on 2010-05-04
> **diabolicalspooz said:**
> 
Simple fix get rid of the synaptic repo's for Apache and once you do so things should be A ok...


This is my problem also, if I get this right:

system
admin
synaptic
status
installed
quick search "apache"

then uninstall all ?

---

### Post by avengerxp on 2010-05-23
when i tried the code (downloaded xampp latest version) the terminal spits back at me saying 

tar: you may not specify more than one "-acdtrux" option....

what am i supposed to do?

---

### Post by craig0927 on 2010-05-25
> **ReyPeste said:**
> Ok, after my overly long and meandering explanation, I just wanted to say I finally figured out what was wrong. Obviously it was a very simple and kind of dumb thing, that goes to show I am just starting to understand all this stuff.  But maybe my experience can save some wasted hours to other newbies. Basically, if you are having trouble with the apache server accesing files elsewhere on your filesystem (via symlinks), you have to make sure that the whole path (all the directories) can be accessed by others.  
In my case, the folder 'Documents' was not readable and my web pages were inside a sub-sub-folder of that one. So even though I changed the permissions of all my webfiles and of the htdocs, and everything, I still got the 403 forbidden access error.
So I simply checked the permissions of my other folders from my home down to my webpages folder by right-clicking, and then selecting 
Properties > Permissions [tab] > and changing the third option "Others - 
Folder Access" to Access Files.
So you see it is a very basic mistake, but at the moment it was not so evident as it now seems.

Thank you very much for posting this.  I'm just starting out myself, and I got tripped up by this same issue.  You probably saved me several hours of frustration. :-)

---

### Post by abedepaul81 on 2010-05-27
> **craig0927 said:**
>  I got tripped up by this same issue. . :-)

I have the same issue but when I go to the permission tab it wont let me choose anything.  I think it has to do with....is that the files for xampp are on my main file system which is a non-writable file and anything on it cant be altered without super user powers.

can someone tell me how to make a file writable in non-writable main file????? I guess single it out somehow

I am running Ubuntu 9......whatever

I was trying to save a file in the XAMPP file and it wont let me!!!!!

thank u

---

### Post by waspinator on 2010-06-02
Hi,

I'm using Ubuntu 10.04 and XAMPP installed fine, and I can access the sample screen fine, but when I ran sudo ```
ln -s ~/projects/test /opt/lampp/htdocs/test

```

and try to access localhost/test I get

```
Access forbidden!
You don't have permission to access the requested object. It is either read-protected or not readable by the server. 
```

in my error_log I get

```
[error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /opt/lampp/htdocs/test 
```


How do I change permissions so that I can access the link?


SOLVED:

Instead of using the command line to create the link, I right clicked on my test folder, selected "make link", and then copied it to /opt/lampp/htdocs

the command to create the link must be broken

---

### Post by walt11 on 2010-06-25
> **petervk said:**
> This is a how-to for setting up a web development environment easily. This guide will install the XAMPP lampp stack into /opt, setup an easy way to start it up and shut it down, and link a folder in your home directory to the webserver.
[B]. . .

[/B] [SIZE=3]**_Location of files and uploading_**[/SIZE]

XAMPP by default uses /opt/lampp/htdocs as the root web directory. The easiest way to start working on files is to link a folder in your home directory into this directory.
My user name is peter so I have /home/peter/public_html linked to /opt/lampp/htdocs/peter. So if I navigate to [http://localhost/peter/](http://localhost/peter/) I get a listing of all the files/folders in that directory. (As long is there isn't a index.php/html/etc file)
To set this up, run in a terminal:
[LIST=1]
[*]Make public_html directory in home directory: ```
mkdir ~/public_html
```
[*]Link to /opt/lampp/htdocs ```
sudo ln -s ~/public_html /opt/lampp/htdocs/$USER
```
[/LIST]
Now any files and folders you place in ~/public_html will be published to your personal webserver.

I've done this, and it works, but relative URLs to sub-folders are not working. E.g.,
```
href="Styles/docStyles4.css"

background-image:url('images/shore.jpg');
```*Styles* and *images* are sub-folders in my public_html folder, and they are evidently not found, since the styles and image are not used.
What must I do to get this to work?

Thanks

Added on 07-03-10:
Problem solved. It was not due to the link. I had some permission issues, and also relative URLs seem to work differently than I've encountered before. Instead of
```
href="Styles/docStyles4.css"
``` I've had to use an address starting at the server root, htdocs:
```
href="/walt/Styles/docStyles4.css"
``` where "walt" is my home directory (and the name of the link in htdocs).

---

### Post by syed.rakib.al.hasan on 2010-07-15
this is a great tutorial on how to install XAMPP on Linux.
i have followed the steps mentioned here and XAMPP works fine.

nonetheless, anyone has an idea how to configure the XAMPP for using Joomla CMS.......
copy pasting the Joomla Files into the htdocs folder of XAMPP (like the way it's described for installing jommla on XAMPP in Windows) does not seem to work out.

---

### Post by PaulWhipp on 2010-07-15
syed.rakib.al.hasan, you really don't need XAMPP on Ubuntu these days. It was great when apache, mysql and php needed lots of configuration and fiddling to get working but that has not been the case, at least since 8.04.

I develop using Joomla all the time and I've just installed apache2, mysql etc. straight from the repositories as per the instructions on the Ubuntu help guides (or elsewhere on this thread). It works out of the box and you can have as many joomla sites as you like in subfolders of your web root (either by copying the files, creating the database and user and editing the configuration.php appropriately or by doing the standard joomla installation).

---

### Post by walt11 on 2010-07-15
syed.rakib.al.hasan, I did use XAMPP, because it was so easy to install, and before I saw PaulWhipp's forum post. I've finally got Joomla working on it - after considerable effort (and much help from forums). Here's what worked for me.

I had to modify the php.ini file, and it's best to do that to begin with. You can find it in /opt/lampp/etc. I changed the line ```
error_reporting = E_ALL | E_STRICT
``` to ```
error_reporting = E_ALL & ~E_STRICT
```I also changed the line ```
display_errors = On
``` to ```
display_errors = Off
```(You have to call your editor from the command line using sudo to modify this file.)

Next, with the Joomla web install I ran into some serious errors, so I used the manual install. You can find a very good set of instructions for that at [http://help.joomla.org/content/view/1944/302/](http://help.joomla.org/content/view/1944/302/). Be sure to install it WITHOUT filling in the $ftp_ variables in the configuration.php file (except set $ftp_enable = '0'). I tried using the ftp layer, and ran into innumerable problems. It works without it.

Once you complete the installation and have logged in as admin, choose Help > System Info > Directory Permissions. All the directories will probably show their status in red as Unwritable. At command level using sudo, you will need to change the owner of each of those directories to **nobody**. E.g.,
```
sudo chown -v nobody directoryname
``` making sure you're located in the proper containing directory when you issue the command. After changing them, reload the current page in your browser, and they should now all show the status Writable in green. In the same way, change the owner of the file configuration.php to **nobody**. It's located in the directory in which you installed Joomla.

Hope that works for you.

---

### Post by suzenon on 2010-08-15
does anybody know, how to make it psosible to create database? i've just installed xampp on my 10.4
but when i want to login as root in phpmyadmin i get
```
 #1045 - Access denied for user 'root'@'localhost' (using password: YES)
```i've set up password in config.inc.php file
and if i log in with pma i can't create database, it says i have no privilege

any help please?

UPDATE

ok after struggling with this damn problem i've managed to get privileges to create mysql database
here's what i did

after failures with  changing config files and so on i've just reinstalled xampp
just tar xzvf xampp* -C /opt
above replaced all previous files with default ones

after this i've started xamp for first time with lampp start

now what worked out
BEFORE using any "lampp security" script and BEFORE changing any passwords i've opened localhost, and clicked phpmyadmin
by default you can login with root without any password, just open phpmyadmin login page, make sure user is root and click GO without any password
then i went to privileges tab, i've added EVERYTHING to pma user

closed all webpages that had anything to do with xampp including phpmyadmin panel
now started xampp secruity script, wrote passwords
logged in as pma with my previously set password to phpmyadmin
privileges tab
and CREATED NEW user with privileges as pma
it can be done by clicking edit icon for account pma, scrolling down the page and using create new user option and just leave old one

now finally after i log in with new user i can create mysql databases...

what a hell...

---

### Post by LinLou on 2010-10-08
okay.. all this is really good.. especially the first time i used it.. 

BUT, i cant make it work now.. the only way i have made it work is by running nautilus..

i have tried this "sudo ln -s ~/public_html /opt/lampp/htdocs/$USER" but the link that it creates is broken..

Can some one help me on this? 

Thanks in advance.

PS: Once i make the link and i try to see the page ive made on firefox, i get an "Access Forbiden" warning..

what is that?

---

### Post by LinLou on 2010-10-08
> **LinLou said:**
> okay.. all this is really good.. especially the first time i used it.. 

BUT, i cant make it work now.. the only way i have made it work is by running nautilus..

i have tried this "sudo ln -s ~/public_html /opt/lampp/htdocs/$USER" but the link that it creates is broken..

Can some one help me on this? 

Thanks in advance.

PS: Once i make the link and i try to see the page ive made on firefox, i get an "Access Forbiden" warning..

what is that?


Ok my fault..

If you guys want to link any file, where your html or php files are located, you have to do it like this..

"  ln -s /home/$USER/foldername/ /opt/lampp/htdocs/$USER  "

it worked prefect for me.. 

+  you do not have to create a new file.. you simply use the one you already have..

---

### Post by berlinblue on 2010-10-24
If anyone keeps having trouble, maybe [this tutorial]("http://www.codetorment.com/2009/10/20/guide-install-xampp-on-ubuntu") could help you further.

It worked for me, with the following version code:

```
tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt
```

Good luck!

---

### Post by PaulWhipp on 2010-10-24
And remember that xampp is really pretty redundant considering how easily you can now install the stack directly to make a 'real' server (see earlier posts in this thread).

---

### Post by baffodoro on 2010-11-14
> **petervk said:**
> So far this post has just under 200 views, So great. If you read this and use it could you leave a reply saying if it was useful/useless? I'd like to keep improving this how-to, so feedback would be good.

Plus, replies bump it up the list.

Hello,
I am just a newbie and I will make a newbie question: to start, how do I make sure i am in the right directory? (this is what you wrote at the veru beginning).
This because I downloaded xampp and entered terminal but the system said it couldn't find any such file in the directory.

Thank you 

ps

sorry for my english

---

### Post by killboymota on 2010-12-08
hey, thanks for your tutorial but this is not working for me.

> Starting XAMPP for Linux 1.5.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
/opt/lampp/bin/mysql.server: 84: source: not found
XAMPP: Another FTP daemon is already running.
XAMPP for Linux started.
motz@motz-Aspire-5735:~$ /opt/lampp/bin/mysql.server: 334: log_success_msg: not found

cya

---

### Post by Godspell on 2010-12-28
Hi there,

I followed your instructions using Xampp 1.7.3a on two of my laptops.

On one of my laptops, I cannot access the folder (where I keep ALL my html, php files) from Firefox address bar i.e. [http://localhost/USER](http://localhost/USER)

I've already uninstalled and reinstalled everything but it still doesn't work.
It keeps saying > Access forbidden!            You don't have permission to access the requested object.     It is either read-protected or not readable by the server.      
  If you think this is a server error, please contact the [EMAIL="you@example.com"]webmaster[/EMAIL].  


It's even more frustrating that on the other laptop, it works straight away after creating the shortcut.

So, any idea on how to get around this???

Thank you.

Regards,
GS

---

### Post by Charlie78 on 2011-05-22
Hello, when i try an install lampp/xampp ii keep getting this error when i try to access phpmyadmin:

#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)

I've tried, removing it, reinstalling it, a couple of commands but nothing seems to be working! if anyone can help it would be highly appreciated.

---

### Post by fchartier on 2011-09-23
Hi all
I am trying to make xamp work on ubuntu 11 to use joomla ultimately.  I installed it, and i could load up the '' ''localhost / xamp '' page. but i could not access a web site locally constructed.
I don t know why, i taught that I had to reinstall apache2, mysql, php etc seperaly. which i did. and i removed them afterwards when i realised that xamp install everything.  problem now i can start xamp but it says that everything is run by another application... 
see below:

/opt/lampp/lampp start
Starting XAMPP for Linux 1.5.3a...
XAMPP: Another web server daemon is already running.
XAMPP: Another MySQL daemon is already running.
XAMPP: Another FTP daemon is already running.
XAMPP for Linux started.

now i dont know what to do...
thanks
f

---

### Post by davidw1957 on 2011-10-08
> **petervk said:**
> This is a how-to for setting up a web development  environment easily. This guide will install the XAMPP lampp stack into  /opt, setup an easy way to start it up and shut it down, and link a  folder in your home directory to the webserver.

**WARNING**
This guide is aimed at a development environment only and should not be  used as a public webserver. To setup a public webserver follow the  directions on the Ubuntu wiki [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

As this is Ubuntu, all the major parts of a typical web server are  included (in the main repo, or on the Ubuntu Server CD) and this is a  great way to setup a server. The ubuntu developers have prepared a great  web server and have made the process as seemless as possible. 

But what if even the official way is still to complicated? What if you just want a quick web server for development?

Fortunately there is the XAMPP project: [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html).  The XAMPP project bundles Apache, PHP4 & 5, Perl, mySQL, and a  bunch of other utilities/applications into an simple package for Mac  OSX, Windows, Solaris, and Linux. Obviously this HOWTO only deals with  the linux version.

For those of you with already existing Apache/mySQL/php installations it  installs everything into /opt so it doesn't conflict with any other  installation, and it is completely setup and ready to run.

[SIZE=3]**_Install XAMPP_**[/SIZE]

Two easy steps:
[LIST=1]
[*]Download the most recent version of XAMPP: (at time of writing 1.5.3a)
[http://prdownloads.sourceforge.net/xampp/xampp-linux-1.5.3a.tar.gz?download](http://prdownloads.sourceforge.net/xampp/xampp-linux-1.5.3a.tar.gz?download)
(Source URL: [http://www.apachefriends.org/en/xampp-linux.html#374](http://www.apachefriends.org/en/xampp-linux.html#374))
[*]Extract  the archive to /opt using sudo: (make sure you are in the directory  that you downloaded the archive to) ```
sudo tar xvfz  xampp-linux-1.5.3a.tar.gz -C /opt
```
[/LIST]

[SIZE=3]**_Start XAMPP_**[/SIZE]

To start it up, open a terminal and type this:
```
sudo /opt/lampp/lampp start
```[SIZE=3]**_Stop XAMPP_**[/SIZE]

To stop it, open a terminal and type this:
```
sudo /opt/lampp/lampp stop
```[SIZE=3]**_Additional XAMPP commands_**[/SIZE]

To see additional commands, open a terminal and type this:
```
sudo /opt/lampp/lampp
```[SIZE=3]**_Sweet XAMPP Control Panel_**[/SIZE]

[IMG]http://img108.imageshack.us/img108/5647/screenshotxamppcontrolpanelfj6.png[/IMG]

To use the sweet gtk/python control panel:

Run in a terminal: ```
gedit  ~/.local/share/applications/xampp-control-panel.desktop
```Paste the  following into the open file and save and exit.
```
[Desktop Entry]
Comment=Start/Stop XAMPP
Name=XAMPP Control Panel
Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
Icon[en_CA]=/usr/share/icons/Tango/scalable/devices/network-wired.svg
Encoding=UTF-8
Terminal=false
Name[en_CA]=XAMPP Control Panel
Comment[en_CA]=Start/Stop XAMPP
Type=Application
Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg
```"XAMPP  Control Panel" will show up in your applications menu under Internet.  Use the Alacarte Menu Editor to move it around.

[SIZE=3]**_Test to see if XAMPP is running_**[/SIZE]

Once XAMPP is up and running open firefox and go to: [http://localhost/](http://localhost/)

You should see the XAMPP test page:

[IMG]http://static.apachefriends.org/images/380.jpg[/IMG]

[SIZE=3]**_Location of files and uploading_**[/SIZE]

XAMPP by default uses /opt/lampp/htdocs as the root web directory. The  easiest way to start working on files is to link a folder in your home  directory into this directory.
My user name is peter so I have /home/peter/public_html linked to /opt/lampp/htdocs/peter. So if I navigate to [http://localhost/peter/](http://localhost/peter/) I get a listing of all the files/folders in that directory. (As long is there isn't a index.php/html/etc file)
To set this up, run in a terminal:
[LIST=1]
[*]Make public_html directory in home directory: ```
mkdir ~/public_html
```
[*]Link to /opt/lampp/htdocs ```
sudo ln -s ~/public_html /opt/lampp/htdocs/$USER
```
[/LIST]
Now any files and folders you place in ~/public_html will be published to your personal webserver. 

Bookmark [http://localhost/username](http://localhost/username) to make this easy to access.

[SIZE=3]**_WARNING - SECURITY_**[/SIZE]
[http://www.apachefriends.org/en/xampp-linux.html#381](http://www.apachefriends.org/en/xampp-linux.html#381)
Open holes:
[LIST=1]
[*]The MySQL administrator (root) has no password.
[*]The MySQL daemon is accessible via network.
[*]ProFTPD uses the password "lampp" for user "nobody".
[*]PhpMyAdmin is accessible via network.
[*]Examples are accessible via network.
[*]MySQL and Apache running under the same user (nobody).
[/LIST]
This doesn't leave your whole system wide open, but someone could hack your XAMPP installation, so be wary.
To fix most of the security weaknesses open a terminal and run: ```
sudo /opt/lampp/lampp security
```[SIZE=3]**_Feedback_**[/SIZE]
Please read [ this post]("http://www.ubuntuforums.org/showpost.php?p=1310039&postcount=5").

--------------------------------------------------------------------------------------------------------------------
Xampp and Ubuntu/Kubuntu/Xubuntu 11.04 have changed... but the Xampp installation is the same.

Make sure your config files are accurately configured

IMPORTANT FILES AND DIRECTORIES
/opt/lampp/bin/     The XAMPP commands home. /opt/lampp/bin/mysql calls for example the MySQL monitor.
/opt/lampp/htdocs/     The Apache DocumentRoot directory.
/opt/lampp/etc/httpd.conf     The Apache configuration file.
/opt/lampp/etc/my.cnf     The MySQL configuration file.
/opt/lampp/etc/php.ini     The PHP configuration file.
/opt/lampp/etc/proftpd.conf     The ProFTPD configuration file. (since 0.9.5)
/opt/lampp/phpmyadmin/config.inc.php     The phpMyAdmin configuration file.
-------------------------------------------------------------------------------------------
To stop MySql already running
sudo /etc/init.d/mysql stop

To stop Apache already running
sudo /etc/init.d/apache2 stop

To start XAMPP simply call this command:
sudo /opt/lampp/lampp start

To stop XAMPP simply call this command:
sudo /opt/lampp/lampp stop

Download and use Filezilla to upload your web files to localhost

---

### Post by fchartier on 2011-10-08
thanks it worked

---

### Post by brahmfrie on 2011-11-19
I'm a first time participant in this forum.  I just installed xampp or lampp since I'm in linux.  I wanted to use the xampp control panel but was not able to install it.  Is this because of the linux system? Is there a lampp control panel?

---

### Post by mick8985 on 2011-11-24
This thread is retarded.
```
sudo tasksel install lamp-server
```

---

### Post by Dragonbite on 2011-11-24
> **mick8985 said:**
> This thread is retarded.
```
sudo tasksel install lamp-server
```

I'm sure with over 350 posts, some people found benefit in this thread.  Not everybody wants to run the full-blown LAMP server directly on their system, and Xampp is a viable alternative.

---

### Post by jasonhotham on 2012-01-18
Hi,

Assuming for personal use only.
I was able to setup using these easy steps:

Put archive on desktop or directory you can get access to.

1. on first line:
username@username:~$ sudo -s
[sudo] password for username:
'enter password'

2. Select desktop:
root@username:~# cd Desktop

3. Extract archive:
root@username:~# sudo tar xvfz xampp-linux-1.7.7.tar.gz -C /opt

4. Start lampp:
root@username:~# /opt/lampp/lampp start

5. Change ownership:
root@username:~# sudo chown -R username:username /opt/lampp

6. Change permissions:
root@username:~# chmod -R 755 /opt/lampp

7. Test file in browser after creating file in htdocs folder:
[http://localhost/test/testing.html](http://localhost/test/testing.html)
(should display file)

8. Test directory to show listed files:
[http://localhost/test/](http://localhost/test/)

9. Test permissions and default file using 'right click' on file 'rename':
rename file name 'testing.html' to 'index.html'

10. Any issues with the above and there's no other solution uninstall and try again :
root@username:~# rm -rf /opt/lampp

Resources:
* [http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)
* [http://zorinlinux.cyacomputerblog.com/2011/01/16/watch-how-to-install-xampp-1-7-2-for-linux-ubuntu-9-04/](http://zorinlinux.cyacomputerblog.com/2011/01/16/watch-how-to-install-xampp-1-7-2-for-linux-ubuntu-9-04/)
* [http://kb.liquidweb.com/new-user-tutorial-basic-file-permissions/](http://kb.liquidweb.com/new-user-tutorial-basic-file-permissions/)
* [http://hiox.org/1763-stopping-and-uninstalling-xampp.php](http://hiox.org/1763-stopping-and-uninstalling-xampp.php)

---

### Post by Rugby2 on 2012-03-28
Excellent tutorial - had xampp up and running in no time! Thanks

---

### Post by dingd0ng on 2012-03-29
Great post! Oddly, I never knew there was a GUI version for XAMPP! Thanks!

---

### Post by calydon on 2012-06-19
update: I figured out I needed to manually create the applications folder. I'm not used to being unable to see hidden folders.

However XAMPP is not showing up under 'internet' in my applications folder. How do I reach the GUI control panel?


*******************]]

I'm trying to install the GUI control panel but when I try to create the .dekstop file I get an error.

> To use the sweet gtk/python control panel:

Run in a terminal

```
gedit ~/.local/share/applications/xampp-control-panel.desktop
```

The error is: "Could not find the file /home/cal/.local/a...mpp-control-panel.desktop"

It's saying it can't find the file it's trying to save??

---

### Post by grollsta on 2012-06-24
> **petervk said:**
> So far this post has just under 200 views, So great. If you read this and use it could you leave a reply saying if it was useful/useless? I'd like to keep improving this how-to, so feedback would be good.

Plus, replies bump it up the list.

This was pretty helpful thanks. I am struggling a bit still tho. I got xampp installed in /opt, but when I run the GUI admin you showed i can't get Mysql or Apache2 to start...

I had another instance of mysql and apache installed but i have stopped both of those manually at the command line...

any idea how to start up the /opt version of mysql and apache?

thanks in advance!

---

### Post by calydon on 2012-06-24
For anyone else struggling to find the GUI panel it is under 'other' in the main app menu.

Thanks for this article.

---

### Post by Suncoaster on 2012-07-06
Great tutorial, up and operational in next to no time.  Thanks heaps.:guitar:

---

### Post by ItyImean on 2012-07-23
Good Tut, I love it. It help me so much.

---

### Post by Lektorvis on 2012-10-24
For those who are having troubles with the Xampp control panel, try to update python-gtk2. 
You can use Synaptic.

---

### Post by Dragonbite on 2012-10-24
> **Lektorvis said:**
> For those who are having troubles with the Xampp control panel, try to update python-gtk2. 
You can use Synaptic.

Does the control panel include any means of handling their closing phpMyAdmin for security reasons?

---

### Post by glenndr15 on 2012-12-26
Try manual installation [https://glenndr15.wordpress.com/xampp-installation-on-linux-mint-14-and-ubuntu-12-10-32bit64bit](https://glenndr15.wordpress.com/xampp-installation-on-linux-mint-14-and-ubuntu-12-10-32bit64bit)* install Xampp on Ubuntu 12.10 32bit/64bit or Ubuntu web server 32bit/64bit *     :D

---

### Post by wanthai on 2013-02-12
> **petervk said:**
> I don't think it is possible to create a soft link to a fat32 drive. I'm pretty sure its a ext2/3 only thing and cannot span different filesystems.

What you can do is change the "DocumentRoot" in the httpd.conf file for XAMPP.

Open a terminal:
```

sudo cp /opt/lampp/etc/httpd.conf /opt/lampp/etc/httpd.conf.backup
sudo gedit /opt/lampp/etc/httpd.conf

```Now Scroll down to the line:
```
DocumentRoot "/opt/lampp/htdocs"
```and change it to point to your fat32 drive. (? "/media/fat32/" ?) 

I'd suggest to point it only to a web subdirectory on the drive as serving up the root of the drive will put all of the files on it onto the webserver and allowing anyone to view them.

Changing this will make the fancy [http://localhost/xampp](http://localhost/xampp) test stuff stop working. (It is installed into /opt/lampp/htdocs/) Everything else should work.

Hope that helps.

Hi Peter ):P
Can use the same command if I as an example want to place my doc-root in / ?

  /lamp/WWW/

is hwat I mean, like it is in Wamp under windows

---

### Post by tobiz on 2013-02-22
Very useful tutorial, got it up and running nearly first time, problems were mostly my fault!

---

### Post by mcondon on 2013-02-22
Everything seems to go fine until I try to start XAMPP.  Then I get:
[INDENT]test-Dimension-8400 Downloads # sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.8.1...
XAMPP: Another web server daemon is already running.
XAMPP: XAMPP-MySQL is already running.
XAMPP: XAMPP-ProFTPD is already running.
XAMPP for Linux started.
[/INDENT]Its seems like there may be another web server running?  (I am new to Linux.....since yesterday.  Just trying to get a developmental web server up and running.)

I noticed the other posts are a few years old.  Is there somewhere else I should go for help on this?

Thanks

---

### Post by Ubucket on 2013-03-26
> **jasonhotham said:**
> Hi,

Assuming for personal use only.
I was able to setup using these easy steps:

Put archive on desktop or directory you can get access to.

1. on first line:
username@username:~$ sudo -s
[sudo] password for username:
'enter password'

2. Select desktop:
root@username:~# cd Desktop

3. Extract archive:
root@username:~# sudo tar xvfz xampp-linux-1.7.7.tar.gz -C /opt

4. Start lampp:
root@username:~# /opt/lampp/lampp start

5. Change ownership:
root@username:~# sudo chown -R username:username /opt/lampp

6. Change permissions:
root@username:~# chmod -R 755 /opt/lampp

7. Test file in browser after creating file in htdocs folder:
[http://localhost/test/testing.html](http://localhost/test/testing.html)
(should display file)

8. Test directory to show listed files:
[http://localhost/test/](http://localhost/test/)

9. Test permissions and default file using 'right click' on file 'rename':
rename file name 'testing.html' to 'index.html'

10. Any issues with the above and there's no other solution uninstall and try again :
root@username:~# rm -rf /opt/lampp

Resources:
* [http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)
* [http://zorinlinux.cyacomputerblog.com/2011/01/16/watch-how-to-install-xampp-1-7-2-for-linux-ubuntu-9-04/](http://zorinlinux.cyacomputerblog.com/2011/01/16/watch-how-to-install-xampp-1-7-2-for-linux-ubuntu-9-04/)
* [http://kb.liquidweb.com/new-user-tutorial-basic-file-permissions/](http://kb.liquidweb.com/new-user-tutorial-basic-file-permissions/)
* [http://hiox.org/1763-stopping-and-uninstalling-xampp.php](http://hiox.org/1763-stopping-and-uninstalling-xampp.php)


Yes!!!

This did it for me!

PeterVK & Jasonhotham, if you were girls....

---

### Post by pragnesh89 on 2013-04-07
I am having troubles with the xampp control panel. I am using Ubuntu 12.10. When I go into dash, and click on xampp control panel, it asks me for the root password and then I enter it and nothing happens.

---

### Post by sensama on 2013-05-27
Installing Wampp seems now very easy! Thank you.

Sensama
EeePC Xubuntu Wordpress

---

### Post by nishoba on 2013-06-06
> **pragnesh89 said:**
> I am having troubles with the xampp control panel. I am using Ubuntu 12.10. When I go into dash, and click on xampp control panel, it asks me for the root password and then I enter it and nothing happens.

Try installing glade python with:
```
sudo apt-get install python-glade2
```

---

### Post by anumaz on 2014-04-14
Apache doesn't start. Any clue?

---

