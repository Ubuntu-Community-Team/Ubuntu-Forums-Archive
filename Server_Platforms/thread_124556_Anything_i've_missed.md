---
title: "Anything i've missed?"
date: 2006-02-01
forum: Server Platforms
---

### Post by Tripmonkey_uk on 2006-02-01
Even though i'm still pretty new at Linux in general I used Ubuntu server install to set up my first home server without gnome etc. last week using the different forum topics & howto's that I came across.
Everything worked great until the old crappy 40GB hard drive that I was using died a horrible death.
I'm getting a new HD in a couple of days & I thought it might be a good idea to go through how I did my last installation & see if I can rectify any mistakes that I made the first time, & to see if the installation can be improved upon.

Would it be possible for someone to have a quick read through my list & see if there is anything that i've missed, or if there's any way to do it better?
I'd rearly like to get it right for the new hard drive :) 
This is what I can remember doing off the top of my head & from the very scrappy notes I took:

Put the (K)Ubuntu cd into the cdrom drive. 
When prompted on what kind of install you want to do type: server & press enter to start
Proceed with the installation (I.E. Set up the language, hostname, username, etc.)
After it's finished installing log into the CLI (command prompt) to make sure it works
To shutdown computer type: sudo shutdown -h now
Before booting up the operating system, make sure that the computers bios is set to boot from hard drive first for security (& so u can leave the (K)Ubuntu cd in without it booting straight to the cd).


Type: sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup - backs up the source list
sudo vi /etc/apt/sources.list
# Find this section & remove the # before it to enable
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

# Find this section & remove the # before it to enable
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse


sudo apt-get update - updates the package list
sudo apt-get upgrade - updates all installed programs to the latest versions
sudo apt-get install openbox - light weight & fast desktop
sudo apt-get install irssi-text - can be used to get help
sudo apt-get install elinks - a very helpful text browser
sudo apt-get install x-window-system-core - might not need it if it's installed with openbox
sudo apt-get install xbase-clients - might not need it if it's installed with openbox
sudo apt-get install xserver-xorg - might not need it if it's installed with openbox
sudo apt-get install openbox obconf - openbox preferences manager
sudo apt-get install xfce4-terminal - looks nice, easy to read & light on resources
sudo apt-get install firefox - installs the default stable version (not always the latest & greatest)

Type: updatedb - updates your computers search database
Type: locate menu.xml & cd to the location
sudo vi menu.xml
# Find this section
<item label="Terminal">
<action name="Execute"><execute>x-terminal-emulator</execute></action>
</item>
Change to:
<item label="Terminal">
<action name="Execute"><execute>xfce4-terminal</execute></action>
</item>

# Find this section
<item label="Web browser">
<action name="Execute"><execute>x-webrowser</execute></action>
</item>
Change to:
<item label="Web browser">
<action name="Execute"><execute>/home/name_of_user/firefox/firefox/./firefox</execute></action> (needs full execute path)
</item>

Type: startx - Starts your desktop (openbox in this case)
If it starts up ok then now would be a good time to shutdown the computer & make sure that it all boots up again as it should. 
Right click on the desktop & choose exit from the menu to shutdown the desktop to the CLI again
Type: sudo apt-get clean - cleans out the temp folders to save from crashing 
Type: sudo shutdown -h now

Turn on the computer again & login with your user name & password
Type: startx to start the desktop again
Now u can right click on the desktop & choose terminal
sudo apt-get update - update the package list again
sudo apt-get upgrade - update to the latest versions again
mkdir /home/name_of_user/www - place to hold the web site
mkdir /home/name_of_user/media - place to put your media files for gnump3d

Install these:
sudo apt-get install gedit - installs gedit for editing text files (vi's already installed if needed)
sudo apt-get install unzip - let's u unzip compressed zip files e.g unzip /location of file/name of file
sudo apt-get install rox-filer - gives u a basic desktop with icons, basic windowed file manager etc
sudo apt-get install apache2 - installs the HTTP web server ([http://localhost](http://localhost) - to test it)
sudo apt-get install mysql-server - installs latest mysql server
sudo apt-get install php5 - installs php5
sudo /etc/init.d/apache2 restart - restarts the apache2 install to allow changes
sudo apt-get install libapache2-mod-auth-mysql - installs MYSQL for Apache2 HTTM web server
sudo apt-get install php5-mysql - installs php5 for Apache2 HTTM web server
sudo /etc/init.d/apache2 restart - restart the apache2 to allow changes again
sudo apt-get install gnump3d - installs GNUMP3d for a Streaming Media Server ([http://localhost:8888](http://localhost:8888) - to test it)
sudo apt-get install ssh - installs SSH Server for remote administration
sudo apt-get build-essential - if u want to build programs from source
sudo apt-get install checkinstall -if u want to check the installs
sudo apt-get clean - cleans out the temp folders to save from crashing


Edit these:

***Clean /tmp/ folder contents on shutdown*** - I've had 2 systems refuse to start up because of the full/corrupt? temp folders
sudo cp /etc/init.d/sysklogd /etc/init.d/sysklogd_backup - backs up file incase of errors
sudo gedit /etc/init.d/sysklogd
# Find this section
...
  stop)
    log_begin_msg "Stopping system log daemon..."
    start-stop-daemon --stop --quiet --oknodo --exec $binpath --pidfile $pidfile
    log_end_msg $?
...
# Add the following line below it
rm -fr /tmp/* /tmp/.??*
# save and exit

***Map web site URLs to folders outside /var/www/***
sudo gedit /etc/apache2/conf.d/alias - no need to backup as file doesn't exist yet
# Insert the following lines into the new file
Alias /home  /home/name_of_user/www

<Directory /location_of_folder/>
   Options Indexes FollowSymLinks
   AllowOverride All
   Order allow,deny
   Allow from all
</Directory>
# save and exit
sudo /etc/init.d/apache2 restart - restarts the apache2 to allow changes

***Change the default port number for Apache HTTP Server***
sudo gedit /etc/apache2/ports.conf
# Find this line
Listen 80
# Replace with the following line
Listen 78
# save and exit
sudo /etc/init.d/apache2 restart - restarts the apache2 to allow changes
([http://localhost:78](http://localhost:78) - to test it)

***Change the default directory containing multimedia files for GNUMP3d & change port***
sudo cp /etc/gnump3d/gnump3d.conf /etc/gnump3d/gnump3d.conf_backup - backs up file in case of errors
sudo gedit /etc/gnump3d/gnump3d.conf
# Find this line
root = /var/music
# Replace with the following line
root = /home/name_of_user/media
# Find this line
user = gnump3d
# Replace with the following line
user = root
# Find this line
port = 8888
# Replace with the following line
port = 7878
# save and exit
sudo /etc/init.d/gnump3d restart - restarts the gnump3d to allow changes
([http://localhost:7878](http://localhost:7878) - to test it)

As rox-filer was installed, it should show up when the desktop is reloaded
To do this just right click on the desktop & exit to get to the CLI again
Type: startx - loads the desktop with rox-filer active
Unfortunatly if u right click on the desktop now, the openbox menu has been replaced with rox-filer's own menu
Go into ROX-Filer/Options in the menu & navigate to Compatibility at the bottom of the list
Check the option for Pass all backdrop mouse clicks to window manager 
Now the openbox menu should be back when theres a right click anywhere on the desktop


Setup mysql:
sudo gedit /etc/mysql/my.cnf
# Find this section
bind-address = 127.0.0.1
# Replace with the following line
# bind-address = 127.0.0.1 - same line but # on the front so it isn't read by the system
# save and exit

mysqladmin -u root password db_user_password - set's up mysql with root user & password db_user_password
# create a database
mysql -u root -p 
Enter Password: db_user_password
mysql> create database mysite; - in this case mysite as it's the name of site
mysql> show databases; - shows the database


Setup antivirus:
sudo apt-get install clamav
sudo apt-get install clamav-base
sudo apt-get install clamav-daemon
sudo apt-get install clamav-freshclam

***Automatically scan files/folders for viruses at midnight everyday***
sudo gedit /etc/crontab
# Add the following line to the end of the file
00 00 * * * sudo clamscan --bell --mbox -i /home/name_of_user/www/* - scans the users entire website folder at midnight everyday
This is needed as the php-fusion CMS for the site will allow users to upload files/photo's etc. & u don't want to be passing virus's from user to user.


Download these as they are needed:
[http://www.php-fusion.co.uk/news.php](http://www.php-fusion.co.uk/news.php) - CMS software to make a website
[http://www.simplemachines.org/](http://www.simplemachines.org/) - software to make a forum
[http://wordpress.org/](http://wordpress.org/) - software to host a blog/blogs
[http://www.mediawiki.org/wiki/MediaWiki](http://www.mediawiki.org/wiki/MediaWiki) - software to make a user editable wiki
[http://www.goteamspeak.com/](http://www.goteamspeak.com/) - voice server & client


***Install php-fusion***
cd /home/name_of_user/Desktop - changes to the desktop directory
ls - lists files in desktop directory
unzip name_of_file /home/name_of_user/Desktop/php-fusion - extracts name_of_file to a folder on the desktop called php-fusion
# Upload the contents of the php-files folder to your site folder
cd php-fusion/php-files - navigates to php-files folder within php-fusion
cp * /home/name_of_user/www - copies (*)all the files within the folder to the sites main folder

chmod the following files & folders to 777 - changes permissions of file/folder to be written by anyone
sudo chmod 777 administration/db_backups/
sudo chmod 777 images/
sudo chmod 777 images/imagelist.js
sudo chmod 777 images/articles/
sudo chmod 777 images/avatars/
sudo chmod 777 images/news/
sudo chmod 777 images/news_cats/
sudo chmod 777 images/photoalbum/
sudo chmod 777 forum/attachments/
sudo chmod 777 config.php

Go to your website and run setup.php e.g. [http://localhost:78/home/setup.php](http://localhost:78/home/setup.php)
Complete the setup process by following all on-screen prompts until finished
address = localhost
user = root
password = db_user_password
database = mysite (or whatever's been used)
table = _fusion

cd /home/name_of_user/www - navigate back to the sites main folder
chmod the config.php file back to 644 (more secure) - e.g sudo chmod 644 config.php
delete setup.php from the folder (won't be needed again) - e.g sudo rm setup.php

[http://localhost:78/home/](http://localhost:78/home/) - to start using the site


Thanx for looking & any help that u can give me :)

---

### Post by Tripmonkey_uk on 2006-02-08
As there was no replies for 4 days on this I took it that there was no critical mistakes, so I went ahead & followed the list to install on a new 30GB hard drive.
I corrected some minor errors as I went but it mostly went unchanged.
Just started to transfer a couple of MP3 albums over to my Gnump3d server & once again I got the Xsession: warning: unable to write to /tmp error.
This is a 30GB hard drive with nearly a clean install.
As this is an install for a minimum desktop server, how is this happening?
I've checked the /tmp file & it's clean.
I've done sudo apt-get clean & it's clean.
df reports that the hard drive is 100% in use.

Anyone got any ideas? this is the 3rd install on two different hard drives that this has happened on & it's rearly starting to annoy me.

Cheers for any help..

---

### Post by Glut on 2006-02-08
If df reports that the HDD is 100% in use, you have 0% left over...
I suppose this to be a typo. What are the permissions on /tmp?
If you could check your /tmp line in /etc/fstab, it may give clues.
BTW I (& others I suppose) baulked at replying to the first post, it's a lot to look over & I don't have time to do that. I'd be more surprised if someone checked it for you.

---

### Post by LordHunter317 on 2006-02-08
> **Tripmonkey_uk]
I'm getting a new HD in a couple of days & I thought it might be a good idea to go through how I did my last installation & see if I can rectify any mistakes that I made the first time, & to see if the installation can be improved upon.[/quote]Yes, a whole list of things.

> sudo apt-get install openbox - light weight & fast desktop
sudo apt-get install irssi-text - can be used to get help
sudo apt-get install elinks - a very helpful text browser
sudo apt-get install x-window-system-core - might not need it if it's installed with openbox
sudo apt-get install xbase-clients - might not need it if it's installed with openbox
sudo apt-get install xserver-xorg - might not need it if it's installed with openbox
sudo apt-get install openbox obconf - openbox preferences manager
sudo apt-get install xfce4-terminal - looks nice, easy to read & light on resources
sudo apt-get install firefox - installs the default stable version (not always the latest & greatest)These all can be done in one command, and x-window-system-core depends on xbase-clients and xserver-xorg.  

> Type: updatedb - updates your computers search databaseUnless you have some reason for needing locate right away, a cron job will update this automatically.

> Type: locate menu.xml & cd to the location
sudo vi menu.xml
# Find this section
<item label="Terminal">
<action name="Execute"><execute>x-terminal-emulator</execute></action>
</item>
Change to:
<item label="Terminal">
<action name="Execute"><execute>xfce4-terminal</execute></action>
</item>Don't hack up the menu.  Do "sudo update-alternatives --config x-terminal-emulator" instead.  The same applies to x-webrowser as well.

> Type: sudo apt-get clean - cleans out the temp folders to save from crashing There's no need to do this unless you're low on disk-space.  

> Type: sudo shutdown -h nowThere's no need to do this I'm aware of, either, unless libc6 was upgraded.  Even then, it's not a requirement before proceeding.

> sudo apt-get update - update the package list again
sudo apt-get upgrade - update to the latest versions againNo need do this again, it shouldn't find anything.

> mkdir /home/name_of_user/www - place to hold the web siteYou can use this, but public_html is the Ubuntu default.

> Install these:
sudo apt-get install gedit - installs gedit for editing text files (vi's already installed if needed)
sudo apt-get install unzip - let's u unzip compressed zip files e.g unzip /location of file/name of file
sudo apt-get install rox-filer - gives u a basic desktop with icons, basic windowed file manager etc
sudo apt-get install apache2 - installs the HTTP web server ([http://localhost](http://localhost) - to test it)
sudo apt-get install mysql-server - installs latest mysql server
sudo apt-get install php5 - installs php5
sudo /etc/init.d/apache2 restart - restarts the apache2 install to allow changes
sudo apt-get install libapache2-mod-auth-mysql - installs MYSQL for Apache2 HTTM web server
sudo apt-get install php5-mysql - installs php5 for Apache2 HTTM web server
sudo /etc/init.d/apache2 restart - restart the apache2 to allow changes again
sudo apt-get install gnump3d - installs GNUMP3d for a Streaming Media Server ([http://localhost:8888](http://localhost:8888) - to test it)
sudo apt-get install ssh - installs SSH Server for remote administration
sudo apt-get build-essential - if u want to build programs from source
sudo apt-get install checkinstall -if u want to check the installsYou should install everything at once, in one go.  There's no need to restart Apache in the middle either said:**
> sudo apt-get clean - cleans out the temp folders to save from crashingAgain, see above. This won't cause crashing of any sort.


> ***Clean /tmp/ folder contents on shutdown*** - I've had 2 systems refuse to start up because of the full/corrupt? temp foldersThat's impossible.  It's cleaned automatically on bootup.

Moreover, **editing an existing init script to do it is a terrible idea.  Create a new one instead.**

> ***Map web site URLs to folders outside /var/www/***
sudo gedit /etc/apache2/conf.d/alias - no need to backup as file doesn't exist yet
# Insert the following lines into the new file
Alias /home  /home/name_of_user/www

<Directory /location_of_folder/>
   Options Indexes FollowSymLinks
   AllowOverride All
   Order allow,deny
   Allow from all
</Directory>
# save and exitDon't do it this way.  Either use mod_userdir or include Aliases on a per user, per-directory basis.  And they belong in sites-available/default, under the proper virtual host entry.  They shouldn't be global to the server configuration.

> ***Change the default port number for Apache HTTP Server***
sudo gedit /etc/apache2/ports.conf
# Find this line
Listen 80
# Replace with the following line
Listen 78
# save and exit
sudo /etc/init.d/apache2 restart - restarts the apache2 to allow changes
([http://localhost:78](http://localhost:78) - to test it)Why?  There's no reason to do this, and it shouldn't be done.

> Setup mysql:
sudo gedit /etc/mysql/my.cnf
# Find this section
bind-address = 127.0.0.1
# Replace with the following line
# bind-address = 127.0.0.1 - same line but # on the front so it isn't read by the system
# save and exitAgain, why?  Unless you need MySQL to listen to non-local TCP (you probably don't), you shouldn't do this.

> Setup antivirus:
sudo apt-get install clamav
sudo apt-get install clamav-base
sudo apt-get install clamav-daemon
sudo apt-get install clamav-freshclamAgain, install everything at once.

> ***Automatically scan files/folders for viruses at midnight everyday***
sudo gedit /etc/crontab
# Add the following line to the end of the file
00 00 * * * sudo clamscan --bell --mbox -i /home/name_of_user/www/* - A better idea is to put a new file in /etc/cron.daily to run this, so it runs with the rest of the nightly jobs and doesn't effect other jobs if it takes too long.

> ***Install php-fusion***
cd /home/name_of_user/Desktop - changes to the desktop directory
ls - lists files in desktop directory
unzip name_of_file /home/name_of_user/Desktop/php-fusion - extracts name_of_file to a folder on the desktop called php-fusion
# Upload the contents of the php-files folder to your site folder
cd php-fusion/php-files - navigates to php-files folder within php-fusion
cp * /home/name_of_user/www - copies (*)all the files within the folder to the sites main folderDon't install it inside the user's directory, install it inside the webroot: /var/www.  It's there for a reason, don't pervert it.

> chmod the following files & folders to 777 - changes permissions of file/folder to be written by anyone**No, No No.  If your solution involves 777 it's instantly wrong.**

The correct solution in this case is to given ownership to the Apache user (www-data) and give it write access.  And I'm pretty sure that db_backups and config.php shouldn't be world-writeable in any case.  In fact, I'm positive.  

config.php probably shouldn't even be left writable after you include the inital setup.

> Complete the setup process by following all on-screen prompts until finished
address = localhost
user = root
password = db_user_password
database = mysite (or whatever's been used)
table = _fusionNo.  Don't access the database as root for a web-application.  Create a MySQL database user with the appropriate permissions, and use that.  **This is very dangerous.**

---

### Post by Tripmonkey_uk on 2006-02-09
@Glut - here's my fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

& a copy of the df report
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             28692180  28676500         0 100% /
tmpfs                   128396         0    128396   0% /dev/shm
tmpfs                   128396     12588    115808  10% /lib/modules/2.6.12-9-386/volatile

drwxrwxrwt  4 root root 4096 2006-02-09 13:12 /tmp is the permissions on the temp folder. I havn't touched the temp folder at all so if this is different than what it should be, I don't know how??

I know it was a lot for someone to read through, but I figured I could get lucky & someone who was rearly bored would stumble across it ;)
Cheers for looking anyway.

@LordHunter - cheers for all the tips. I'll have to have a proper sift through the list & make the changes before I try another install.
Whats kinda worrying is that a lot of the mistakes u've mentioned are straight from howto's that a lot of people use.

[http://ubuntuguide.org/](http://ubuntuguide.org/) - is where I got the infomation on changing the Apache port etc. & the cleaning of tmp on exit.

[http://www.ubuntuforums.org/showthread.php?t=103806&highlight=openbox](http://www.ubuntuforums.org/showthread.php?t=103806&highlight=openbox) - Is where I got the info on installing openbox.

And the most worrying of all is when u said... No, No No. If your solution involves 777 it's instantly wrong.
That part of the list was taken from the official install notes of PHP-Fusion, so I wouldn't have ever tried to second guess that.
Maybe someone at php-fusion just made a mistake with the permissions?

Cheers for the feed back. I'm gunna keep trying at this until I get it right, or at least until I go completely mad & need to be locked up ;)

---

### Post by LordHunter317 on 2006-02-09
[QUOTE=Tripmonkey_uk][http://ubuntuguide.org/](http://ubuntuguide.org/) - is where I got the infomation on changing the Apache port etc. & the cleaning of tmp on exit.[/quote]The guide is wrong.  It's wrong on lots of things.  It doesn't come up so much anymore, but I used to actively point out it's errors here.  I've mostly stopped bothering.

Ignoring the errors, it doesn't explain why one should do things one way over another, which is dangerous.  There's no need to change the port number unless you have a reason to do so.

> And the most worrying of all is when u said... No, No No. If your solution involves 777 it's instantly wrong.
That part of the list was taken from the official install notes of PHP-Fusion, so I wouldn't have ever tried to second guess that.
Maybe someone at php-fusion just made a mistake with the permissions?Yes, it's a security issue.  Uploads from the web will occur as www-data, so only www-data needs write access to those areas.

The issue is that on break-in or compromise from another account, the compromiser can now attack that directory.  This may allow them to execute a compromise that would not otherwise be possible (e.g., if it filters on upload but not when it goes to use the uploaded files).

---

