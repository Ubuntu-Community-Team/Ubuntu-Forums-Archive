---
title: "Guide to Installing and Running MiniDLNA on an Ubuntu Server"
date: 2011-10-21
forum: Server Platforms
---

### Post by damo12 on 2011-10-21
I have recently been experimenting with running MiniDLNA on a headless Ubuntu Server and have hit a few snags.  After a lot of search and a few pointers from this and other forums I have finally managed to get it running fine.  In case anyone else has this problem I have written this guide to hopefully take some of the pain out of installing and configuring an amazing program.


**The Hardware**

My server is a headless HP Microserver running Ubuntu 10.04.3 LTS 64 bit edition accessed through Putty and Webmin ([www.webmin.com]("http://www.webmin.com/")).  I have also tried this using a virtual setup using Virtual Box and that also worked fine.

As a receiver, I am using an LG HX806SH Blu-ray player connected to my LAN by a Homeplug adapter.  I have also tried using Windows Media Player and they both work fine.  I would like to try this with VLC to test it on a Linux desktop but configuring VLC to receive streaming media from a server is beyond me right now.


**The Server Setup**

The server has a standard headless setup including Samba installed (a combination of Windows and Linux machines share files stored on it).  If you need any help installing and using Webmin, I suggest you have a look at the excellent guide at [http://www.kelvinwong.ca/2010/05/22/installing-webmin-on-ubuntu-server-10-04-lts-lucid/]("http://www.kelvinwong.ca/2010/05/22/installing-webmin-on-ubuntu-server-10-04-lts-lucid/").


**Installing and Configuring MiniDLNA**

For some reason, when I tried to install MiniDLNA, through Putty I received error messages.  From reading around, it turns out that this is a common problem as some repositories are missing.

In the end, these commands installed the package:

```
sudo apt-get install --reinstall python-software-properties && sudo dpkg-reconfigure python-software-properties

sudo add-apt-repository ppa:stedy6/stedy-minidna
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install minidlna
```

I would also recommend installing the Webmin MiniDLNA module from [https://sourceforge.net/projects/minidlnawebmin/]("https://sourceforge.net/projects/minidlnawebmin/")

If you are accessing the server through Webmin and are not sure how to install the module, save it to a local location (such as your desktop on your computer).  Select the "Webmin Configuration" module which is under the "Webmin" tab.  Select the "Webmin Modules" and choose to load the module “From uploaded file".  Once the module has been installed it will be automatically be configured and it will be available under the "Servers" tab.

Once this is installed, you need to configure the MiniDLNA conf file located at /etc/minidlna.conf.

You can use your favourite text editor or if you are accessing this through Webmin, you can use the "Edit" option in "File Manager".  If you have installed the Webmin module, you can also change all of the settings from there.

My minidlna.conf file reads as follows:

```
# port for HTTP (descriptions, SOAP, media transfer) traffic
port=8200

# network interface to bind to (this is the only interface that will serve files)
#network_interface=eth0

# set this to the directory you want scanned.
# * if have multiple directories, you can have multiple media_dir= lines
# * if you want to restrict a media_dir to a specific content type, you
#   can prepend the type, followed by a comma, to the directory:
#   + "A" for audio  (eg. media_dir=A,/home/jmaggard/Music)
#   + "V" for video  (eg. media_dir=V,/home/jmaggard/Videos)
#   + "P" for images (eg. media_dir=P,/home/jmaggard/Pictures)

media_dir=V,/media/server/server/Media/Films
media_dir=V,/media/server/server/Media/TV
media_dir=V,/media/server/server/Media/Commedy
media_dir=V,/media/server/server/Music/Videos
media_dir=A,/media/server/server/Music/Music
media_dir=P,/media/server/server/Stuff/Pictures

# set this if you want to customize the name that shows up on your clients
friendly_name=MiniDLNA Server

# set this if you would like to specify the directory where you want MiniDLNA to store its database and album art cache
db_dir=/media/server/server/Backup/Server/MiniDLNA

# set this if you would like to specify the directory where you want MiniDLNA to store its log file
#log_dir=/var/log

# this should be a list of file names to check for when searching for album art
# note: names should be delimited with a forward slash ("/")
album_art_names=Front.jpg/front.jpg/Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg/Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg

# set this to no to disable inotify monitoring to automatically discover new files
# note: the default is yes
inotify=yes

# set this to yes to enable support for streaming .jpg and .mp3 files to a TiVo supporting HMO
enable_tivo=no

# set this to strictly adhere to DLNA standards.
# * This will allow server-side downscaling of very large JPEG images,
#   which may hurt JPEG serving performance on (at least) Sony DLNA products.
strict_dlna=no

# default presentation url is http address on port 80
presentation_url=http://minidlna/index.php

# notify interval in seconds. default is 895 seconds.
notify_interval=895

# serial and model number the daemon will report to clients
# in its XML description
serial=12345678
model_number=1

```

As you can see, I've made a few changes to the standard file:

[INDENT][LIST]
[*]I have added various sources of videos
[*]I have changed the name of the server so I can recognise it easily on the network
[*]I have moved the location of the database to a location that I backup each day and is shared by Samba (this is for my personal benefit only)
[*]I have added extra filenames to the "AlbulmArt" section as I usually call the front cover of an album "Front"
[/LIST][/INDENT]

Despite the line “*# default presentation url is http address on port 80*” MiniDLNA does not have a webpage that it can be controlled from.  From what I can gather, this was going to be a future feature that was not completed for whatever reason.  However, the Webmin module takes care of everything that you need.

From the "Command Shell" in Webmin or through an SSH session using Putty, you can control MiniDLNA using the commands:

```
sudo /etc/init.d/minidlna stop
sudo /etc/init.d/minidlna start
```

At first run, MiniDLNA will scan all of the folders (and their sub-folders) it has been pointed at and make all of these files available.  The scan is extremely quick (less than 10 minutes to scan about 12,000 files).

The Webmin module has a "Restart" button but for some reason (on my set-ups) it does not work properly.  It will stop MiniDLNA but when it tries to restart it, it fails.  Trying to manually start it using the command "*sudo /etc/init.d/minidlna start*" after using this "Restart" does not seem to work and the only way I have found to resolve this is to restart the whole server.


**Adding or Removing Files of Folders from the Database**

In my experience, MiniDLNA tends not to notice if a file has been added or removed from the folders so the database does not update and new files are not shown on your device and old files are still shown even though they have been removed.  This seems to be a problem with MiniDLNA and not the receiving soft/hardware.  If you change the name of the server, the soft/hardware picks that up fine.

Some people have had success with the command:

```
minidlna -R
```

or by removing the file */tmp/minidlna/files.db* and restarting the server using the command:

```
rm -rf /tmp/minidlna
```

Someone else suggested using the command:

```
minidlna -R -f /tmp/minidlna.conf
```

However, I have found the easiest and most successful method is to use the "Rescan" button in the Webmin interface.  This button deletes the MiniDLNA database and rescans from scratch.  On my system, this new scan took less than 10 minutes to scan about 12,000 files.  After the scan, any new files appear in the database and any deleted files are removed.


**Outstanding Problems**

The only thing I have not been able to get MiniDLNA to do so far is display my photos properly on the Blu-ray player even though they display fine on Windows Media Player.  On the Blu-ray, it shows all of the folders where my pictures are stored and even gives me the option to search by camera but when I try to view the pictures or look into the folders, the folders are all empty.  This suggests it is something to do with the Blu-ray player and not MiniDLNA however, to be honest this is not an issue for me as my main aim was to stream videos and music and it works perfectly for that.

If anyone can point me to a walkthrough of how to receive streamed videos and music on VLC I would be grateful so I can test this set-up on that and add it to this guide.

I hope you find this guide useful and it takes away some of the headaches I've had with setting up this excellent program.

---

### Post by craigchambers on 2011-10-24
> If anyone can point me to a walkthrough of how to receive streamed videos and music on VLC I would be grateful so I can test this set-up on that and add it to this guide.

To view the server on a Linux desktop, you can use Totem (IIRC it's the default media player on Ubuntu) with the Coherence plugin enabled.  
Coherence is a UPnP/DLNA controller which allows Totem to play the content served by miniDLNA.
It's pretty easy to use - available UPnP and DLNA servers are displayed in the sidebar and media is browseable via the tree.

> MiniDLNA tends not to notice if a file has been added or removed from the folders so the database does not update and new files are not shown on your device and old files are still shown even though they have been removed

The problem of files not being added to the database without a rescan is due to Samba shares not creating an inotify event.  The issue does not exist when other methods are used (e.g. NFS shares or local access).  To save yourself a rescan for an individual file you can 'touch' the file from a terminal on the server (e.g. an ssh/putty session or your webmin terminal) which inotify will pick up, and therefore so will miniDLNA.

e.g. ```
touch /media/server/server/films/S-T/Three_Musketeers.mpg
```

Obviously, for a lot of files this can be more hassle than a rescan.
I'm not certain, but to remove files from the DB it may be a case of 'touching' the parent folder.

/Craig

---

### Post by damo12 on 2011-10-24
Hi Craig,

For some reason my version of Totem (which does indeed come as standard on Ubuntu 11.10 32 Bit) will not see the Coherence plugin.  When I used the Ubuntu Software Centre and searched for Coherence, I was shown two options: the extra plugins for totem and UPnP Inspector.  When they did not work, I removed both and tried to install Coherence using the command:
```
sudo apt-get install python-coherence
```
This seemed to install coherence with the latest version but it still does not show up in Totem.

The extras plugin appears to have other plugins but there is no mention of Coherence.  I tried activating all of the plugins but this did not show me a DLNA option in the drop-down.  There is a “Python Console” plugin.  When this plugin is activated, there is a new menu item of “Python” which opens a console which appears to be very similar to a text editor.  As I do not know anything about Python, I stayed well clear of that one.

UPnP inspector will see the MiniDLNA server but I cannot find any way to get it to play the files it finds.

Thanks for your advice.  I tried to add a file using the "*touch*" command.  Unfortunately this did not work.  I think it may have something to do with the there being a space in the name.  I tried the commands:

[INDENT]*touch /media/server/server/films/S-T/New Film.mpg*[/INDENT]
and
[INDENT]*touch "/media/server/server/films/S-T/New Film.mpg"*[/INDENT]

but neither worked.

Thanks for the thought though.

Damian

---

### Post by sloopjonb on 2011-10-27
Don't get caught out with minidlna apparently not starting automatically.........

When you use apt-get to install minidlna on Ubuntu Server it installs the start and stop scripts in the /etc/rcN.d folders with the minidlna server starting almost immediately in the boot process. This is too early! Things like RAID partitions might not be ready to be probed by minidlna at this point, so you need to delay it to later..... read on.....

I'm running 11.10 (oneiric) and got minidlna to start automatically upon booting, with the following instructions:

> sudo apt-get minidlna install

edit minidlna.conf to point towards the path for your video/audio etc.

> sudo update-rc.d -f minidlna remove 
this removes the incorrectly numbered start up scripts.

> sudo update-rc.d minidna defaults 99 01 
creates new start up scripts which will start near the end of the boot process

All is now good in the world......

---

### Post by latimerio on 2011-11-17
Thank you for your very concise guide to minidlna.
 I needed a dlna server to connect my Raidsonic MB3011 to my Philips TV. 
 So I mounted the NAS to my Ubuntu Box and stream it with minidlna. 
 As the MB3011 is not always on I disabled autostart and everything works  fine. 
 A strange thing I noticed is that the default database location is in /tmp  and not in /var/cache as the config file suggests. 
 Thus I uncommented the database line to get the database into the place where  it should go. 
 Strange enough the server log file gets then into that location too. 
 As minidlna does not install a logrotate script it might be necessary to add  it manually to /etc/logrotate.d if log files grow large. 
 BTW: I have app. 500 videos and no music on my NAS and building the database  takes about 2 hours so I do not regard this as fast ;-( I guess this has to do  with the Wifi connection I have to my NAS and I further guess that the file size  matters at scanning. 
 As a result to my setup it can be very annoying to get new movies into the  database if the auto recognition of new movies does not work properly.
 **Update:**
 After re-starting the service I found that the database was going to be  rebuilt from scratch.
 This means that whenever I start minidlna to stream something I need to wait for 2  hours before the database gets ready.
 This is a no go, so I uninstalled minidlna.as it seems to be useless to me in  its current state

---

### Post by reddevil2064 on 2011-11-17
> **latimerio said:**
> Thank you for your very concise guide to minidlna.
 I needed a dlna server to connect my Raidsonic MB3011 to my Philips TV. 
 So I mounted the NAS to my Ubuntu Box and stream it with minidlna. 
 As the MB3011 is not always on I disabled autostart and everything works  fine. 
 A strange thing I noticed is that the default database location is in /tmp  and not in /var/cache as the config file suggests. 
 Thus I uncommented the database line to get the database into the place where  it should go. 
 Strange enough the server log file gets then into that location too. 
 As minidlna does not install a logrotate script it might be necessary to add  it manually to /etc/logrotate.d if log files grow large. 
 BTW: I have app. 500 videos and no music on my NAS and building the database  takes about 2 hours so I do not regard this as fast ;-( I guess this has to do  with the Wifi connection I have to my NAS and I further guess that the file size  matters at scanning. 
 As a result to my setup it can be very annoying to get new movies into the  database if the auto recognition of new movies does not work properly.
 **Update:**
 After re-starting the service I found that the database was going to be  rebuilt from scratch.
 This means that whenever I start minidlna to stream something I need to wait for 2  hours before the database gets ready.
 This is a no go, so I uninstalled minidlna.as it seems to be useless to me in  its current state

FUPPES is quite a bit faster (from most other streamers), and the documentation has improved tremendously. I haven't had any issues downloading and compiling the latest version (691 IIRC) from the repos. 

[http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Main_Page]("http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Main_Page")

---

### Post by damo12 on 2011-11-18
Hi latimerio,

I'm so pleased that you found the guide easy to use even if it ended up not being suitable for your needs.

With regards to the scan time, I can only guess that the problem is (like you say) related to the fact that the connection is a wireless one and the files are not always there for the database meaning that sometimes it scans and there are no files and then it scans and has to add the files from the NAS.

My media files are held on a drive in the server so my scans are much quicker.  I have around 1,800 video files of varying sizes, 2,800 music files and 300 pictures (which are now showing on my blu-ray player).  A complete rescan of the database takes around 9 minutes which is a lot quicker than yours.

Good luck with trying other programs and please let me know if you find a one that works.  I'm always up for trying new programs to see how they compare.

Damian

---

### Post by susja on 2012-05-10
hi damo12,
maybe you could help me with this ... it's kind of new territory for me.
1. I installed minidlna. After that I installed  webmin.
2. minidlna starts automatically after reboot and I also could access webmin .
Two issues I have:
1. when I login to webmin ... I don't know what to do next  :smile: i.e. I don't see dlna module. Could it be because I didn't install it as a module of webmin? How could I re-do it?
2. when I try to access dlna server from my smartphone it get connected  to my server i.e. Ubuntu but it shows only 2 folders and it can't see  any folders were actually my pictures and video were stored. FYI: I have  samba installed and my home directory is shared so I'd expect to see  all folders but I don't. Actually when I try to open e.g. Video folder  it states: 'No files to display'. Maybe I should configure some files?  BTW I could access my Linux home directory from iPad.
Could you pls answer my question and explain how you practically are  using it? I mean currently I'm playing with my smart-phone but the goal  is to use dlna client on my TV. Could/should I delete both dlna and webmin and do it again?
Thanks

Thanks

---

### Post by damo12 on 2012-05-10
Hi susja,

I'll do my best to help you through the problems as best I can.

**1.** You need to ensure that you install the minidlna webmin module.  You can find the latest version at [http://sourceforge.net/projects/minidlnawebmin/files/Webmin%20alpha1.12%20svn26/minidlnawebmin_alpha1_12.wbm/download]("http://sourceforge.net/projects/minidlnawebmin/files/Webmin%20alpha1.12%20svn26/minidlnawebmin_alpha1_12.wbm/download").  Save the file to a local location (such as your desktop on your computer). Log into Webmin and select the "Webmin Configuration" module which is under the "Webmin" tab. Select the "Webmin Modules" and choose to load the module "From uploaded file". Once the module has been installed it will be automatically be configured and it will be available under the "Servers" tab.  If you can't see it there, it might have placed itself in the "Un-used Modules" tab.

**2.** I have never tried accessing my media through a smart phone only my Blu-ray player and Windows computers.  From the description of your problems, it sounds like you have not configured the MiniDLNA conf file correctly.  The file is located at /etc/minidlna.conf.  Ensure that your locations are correct remembering that Linux filenames are case sensitive.  Once you have configured this file to point at your media files tell minidlna to rescan your files using the *"Rescan"* button in the Webmin module. Do not try using the *"Restart"* button as in my experience this just stops the program from working.

My Blu-ray player, scans the network and sees the server as miniDLNA server.  Once I open that, I can see the files and then can select which one I want to view / listen to.

My current minidlna.conf file is:

```
# port for HTTP (descriptions, SOAP, media transfer) traffic
port=8200


# network interface to bind to (this is the only interface that will 
#serve files) network_interface=eth0


# set this to the directory you want scanned. * if have multiple 
# directories, you can have multiple media_dir= lines * if you want to 
# restrict a media_dir to a specific content type, you
#   can prepend the type, followed by a comma, to the directory: + "A" 
#   for audio (eg. media_dir=A,/home/jmaggard/Music) + "V" for video 
#   (eg. media_dir=V,/home/jmaggard/Videos) + "P" for images (eg. 
#   media_dir=P,/home/jmaggard/Pictures)

media_dir=V,/media/media/Films
media_dir=V,/media/media/TV
media_dir=V,/media/media/Comedy
media_dir=V,/media/media/Daft
media_dir=V,/media/media/F1
media_dir=V,/media/server/server/Music/Music Videos
media_dir=V,/media/media/Magic
media_dir=V,/media/media/Stop and Think 
media_dir=A,/media/server/server/Music/Music/iTunes 
media_dir=P,/media/server/server/Pictures


# set this if you want to customize the name that shows up on your 
# clients
friendly_name=MiniDLNA Server


# set this if you would like to specify the directory where you want 
# MiniDLNA to store its database and album art cache
db_dir=/media/server/server/Backup/Server/MiniDLNA


# set this if you would like to specify the directory where you want 
#MiniDLNA to store its log file log_dir=/var/log


# this should be a list of file names to check for when searching for 
# album art note: names should be delimited with a forward slash ("/")
album_art_names=Front.jpg/front.jpg/Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg/Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg


# set this to no to disable inotify monitoring to automatically discover 
# new files note: the default is yes
inotify=yes


# set this to yes to enable support for streaming .jpg and .mp3 files to 
# a TiVo supporting HMO
enable_tivo=no


# set this to strictly adhere to DLNA standards. * This will allow 
# server-side downscaling of very large JPEG images,
#   which may hurt JPEG serving performance on (at least) Sony DLNA 
#   products.
strict_dlna=no


# default presentation url is http address on port 80
presentation_url=http://minidlna/index.php


# notify interval in seconds. default is 895 seconds.
notify_interval=895


# serial and model number the daemon will report to clients in its XML 
# description
serial=12345678 model_number=1
```

I hope this is of use to you.

---

### Post by susja on 2012-05-10
-damo12
thanks so much for speedy reply.
**1.** I was able to do 1. from your note and now I could see minidlna from webmin
**2.** That sounds reasonable and I'll modify  minidlna.conf file  when I'll be at home
**3.** After that I'll rescan it and home to access server from both my iPad and TV.
Thanks again and I'll update you when I try.
P.S. Since you are familiar with this stuff maybe you could explain me the difference between DLNA and Plex Media Server? I know that my TV supports both  but I just don't know which one is better ;)
Thanks again

---

### Post by susja on 2012-05-10
-damo12
Unfortunately it still doesn't work.
I modified minidlna.conf file and provide the path to my media sources like this:
media_dir=/home/me/Downloads
media_dir=/home/me/Music
media_dir=/home/me/Videos
media_dir=/home/me/Pictures 
but it didn't have any effect. The only effect it took was that now server is displayed as MiniDLNA Server. I rescanned, restarted and even rebooted PC but it still does not recognize none of those folders.
Any idea?
Thanks

---

### Post by shz1 on 2012-05-10
> **susja said:**
> -damo12
Unfortunately it still doesn't work.
I modified minidlna.conf file and provide the path to my media sources like this:
media_dir=/home/me/Downloads
media_dir=/home/me/Music
media_dir=/home/me/Videos
media_dir=/home/me/Pictures 
but it didn't have any effect. The only effect it took was that now server is displayed as MiniDLNA Server. I rescanned, restarted and even rebooted PC but it still does not recognize none of those folders.
Any idea?
Thanks

try 

media_dir=A,/home/me/Music
media_dir=V,/home/me/Videos
media_dir=P,/home/me/Pictures

---

### Post by susja on 2012-05-10
well ... I modified as you recommended but nothing has changed.
To be honest I'm not positive how to check that it works :)
Here's how I'm doing it: 
1. on my Smartphone ( Droid X) I installed DLNA client
2. on my iPad I installed DLNA client
I start client either on phone or iPad and in both cases it recognized my DLNA server as MiniDLNA Server and it lists 4 folders:
'Browse Folders', 'Music', 'Pictures' and 'Video'.
When I open all those folders they are empty.
What could be wrong?
Thanks

---

### Post by shz1 on 2012-05-10
give your server a reboot, or restart the machine, not sure if itll work but its worth a try

---

### Post by susja on 2012-05-10
restart of machine didn't make a difference
Thanks

---

### Post by damo12 on 2012-05-11
Hi susja,

I'm afraid to say that I do not know the difference between a DLNA and Plex Media Server in fact to be honest I've never even heard of a Plex Media Server.  The only reason I wrote this post was to hopefully make life easier for anyone else trying to set up miniDLNA server.

With regards to your set-up, if you can see the 4 folders, I think that you have everything set-up right.  The only thing I can think of is that for some reason, the files in your home folder are being blocked.  If that is the case, you could try creating a new folder in /media and move your media to that folder.  Amend your minidlna.conf file and rescan.

Fingers crossed,

Damian

---

### Post by susja on 2012-05-11
Well I have no clue what's  going on.
I created a new folder under /media folder.  Copied a video file there and rescan.
Nothing has changed. It looks that whatever I do in minidlna.conf file take effect  accept the name of my server. Looks like I hit the wall.
Thanks

---

### Post by damo12 on 2012-05-11
Hi susja,

I'm stumped but why don't you put a copy of your minidlna.conf file on here.  You never know, someone might be able to see what's causing the problem.

Damian

---

### Post by susja on 2012-05-11
-damo12
I do appreciate your help. I spent some my time and used your time to set it up. Well it's really frustrated.
Meanwhile I just googled and I found another media server running on Linux i.e. Media Tomb. I installed and configured it and it working fine between my TV and iPad.
I hate to say that ... but I'm going to uninstall minidlna since it's not working for me. After all it doesn't much matter which tool/app you are using as long as it works for you, right?
So I'm giving up and thank you again.
I hope that uninstalling minidlna and webmin from my Ubuntu won't discontinue media sharing.
Best regards.

---

### Post by damo12 on 2012-05-12
Hi susja,

I'm sorry to hear that you couldn't get miniDLNA to work properly but am pleased that you have managed to find something that works for you.  Ironically, I came across miniDLNA when I couldn't get Media Tomb to work for me but like you say, the important thing is finding something that works for you.

Damian

---

### Post by styelz on 2012-05-20
My minidlna wouldn't update anymore, even if i did a rescan.

After looking at the logs i noticed the SQL DB (/var/cache/minidlna/files.db) was corrupt/read only. I had to  manually delete the db file to get it working again.

Here is a sample of the errors I saw:
```
[2012/05/19 21:02:01] sql.c:40: error: SQL ERROR 8 [attempt to write a readonly database]
INSERT into DETAILS (PATH, SIZE, TIMESTAMP, DURATION, DATE, CHANNELS, BITRATE, SAMPLERATE, RESOLUTION,  TITLE, CREATOR, ARTIST, GENRE, COMMENT, DLNA_PN, MIME, ALBUM_ART) VALUES ('/var/lib/storage/recordings/1012_20120519202800.mpg', 3356234468, 1337425320, '0:34:00.420', '2012-05-19T21:02:00', '5', '1644874', '48000', '1440x1080', '1012_20120519202800', NULL, NULL, NULL, NULL, 'MPEG_TS_HD_NA_ISO;DLNA.ORG_OP=01;DLNA.ORG_CI=0', 'video/mpeg', 0);
[2012/05/19 21:02:01] scanner.c:498: warn: Unsuccessful getting details for /var/lib/storage/recordings/1012_20120519202800.mpg!
[2012/05/19 21:22:12] sql.c:40: error: SQL ERROR 8 [attempt to write a readonly database]
DELETE from DETAILS where ID = 32
[2012/05/19 21:22:12] sql.c:40: error: SQL ERROR 8 [attempt to write a readonly database]
DELETE from OBJECTS where DETAIL_ID = 32

```

---

### Post by Buggrit on 2012-05-20
Great guide - thanks for all the effort. I have a query that I'm hoping may be within your expertise to answer....

I had been using Minidlna for about a year with great success. I use the wonderful 'get-iplayer' app to download shows from the BBC over night during my ISPs free period. Minidlna picks these up when I get 'crontab' to rescan the library (sudo minidlna -R) and then restart the minidlna server (sudo /etc/initial.d/minidlna restart). This allows me to stream the shows to the Sony tv or to my Android mobile using 'upnp', at leisure - all good so far. But...

During an upgrade to Precise Pangolin last week, the Linux OS install failed! All was not lost as I had a backup of my home folder but I had to reinstall all my software - including minidlna. I re configured the minidlna.conf file in a similar way to yours but now find the shows have no proper titles - dates and thumbnail yes - titles no. Any thoughts would be appreciated as I'm at a bit of a loss as to what has changed.

Many thanks 

JB

---

### Post by damo12 on 2012-05-20
Hi JS,

I'm afraid I have not come across this problem before although someone else in the forums might have.  My first thought would be to check that the files themselves have not become corrupt (ie can you play the files when you copy them onto another computer and not streamed).

If you can play the files without problems then I would suggest following styelz's solution to replace the database in case that is corrupt.  The guide can be found at [http://ubuntuforums.org/showpost.php?p=11951530&postcount=21]("http://ubuntuforums.org/showpost.php?p=11951530&postcount=21").

I hope one of these solutions helps you,

Damian

---

### Post by skyrail02 on 2012-06-05
Hi,
I don't know if it can help. I am experiencing a similar issue.
I am using minidlana, the last version on debian with plugcomputer Dockstar.
I have a samsung smarttv browsing folders through minidlna from my dockstar.
I can see videos thumbnails, as well as music album covers (folder.jpg for both) But I cannot see pictures thumbnails in any folder. theses pictures may be photos or simple image illustrations of any size and dimensions.
In two case only, I can see picture thumbnails.
First, when the picture come from a camera ans is untouched. If a alter it from photoshop, it's ok, but alter from office picture manager, I loose the thumbnail.
If I open an untouched camera picture in photoshop, paste any image into, resize, or alter contrast, color ... and save as jpg (not save for web), the new picture supposedly keep exif, ipc.
And this new picture, i can see its thumbnail on my TV.

I Guess there is some missing info minidlna as to send to my smart tv. But I don't know what.

I also noticed, any picture that is not necessarily a camera picture, shw thumbnail on tv, when I browse windows7 dlna store.
So the problem come from minidlna

Hope some dev encountered this issue before I switch to mediatomb or other friendly dlna server for smarttv ;)

---

### Post by shirike on 2012-09-08
Hi damo

bit of crossover post from the other thread:


> **damo12 said:**
> Hi shirike,

As far as I can tell from my experience with miniDLNA, this is the normal procedure the rescan function.  On my system at least when I perform a rescan through the Webmin module, miniDLNA deletes its database and album art file and creates a new one.

With video clips (films etc) it does this quite quickly although I have noticed that with pictures this can take some time.  I must admit that I have not checked to see how long it takes to do this with music.

I believe it does this as there is no way to manually remove files from its database and so the only way it can do this is to wipe everything and start from scratch again.

With regards to album art, when it carries out the rescan it will re-create the art based on the art encoded into the file.

I hope that this answers your question but if you are still having problems and you do not get a suitable reply on this thread, you could try asking at [http://ubuntuforums.org/showthread.php?t=1866520]("http://ubuntuforums.org/showthread.php?t=1866520") which is a guide I wrote on miniDLNA and there are quite a few miniDLNA experts on there.

Good luck,

Damian


The issue I'm having is that rescan deletes the folder rather than just the art cache/files.db.

I imagine this is due to giving the user/group too high a permission?

---

### Post by damo12 on 2012-09-09
Hi shirike,

Sorry, I misunderstood your original post.  I have never heard of the rescan deleting the actual folder.  On my system (now running Ubuntu 12.04.1), I have noticed that restarting the server seems to forces MiniDLNA to perform a re-scan without being told to.  It could be worth seeing if that works.

Failing that, you could try seeing what happens when you force a re-scan through the command prompt.  Although it did not work for me, some people have achieved this using the commands:

```
minidlna -R
```
or
```
minidlna -R -f /tmp/minidlna.conf
```

Hopefully one of these will resolve this problem for you.

---

### Post by craigchambers on 2012-10-03
> **shirike said:**
> Hi damo

bit of crossover post from the other thread:

The issue I'm having is that rescan deletes the folder rather than just the art cache/files.db.

I imagine this is due to giving the user/group too high a permission?

This sounds familiar, and if it's the same problem it is quite an old bug.  The problem arises when your media is in the same location as your database etc.

It's been fixed for quite some time... What version are you using?

/Craig

---

### Post by ssreesanth on 2012-11-07
i am using 10.10 and have configured minidlna. my problem is that my tv is showing my server and the audio video and pictures option. and only video files are getting listed. the audio files and pictures are not showing up on my tv.
any ideas???

media_dir=V,/home/sree/Media/server
media_dir=P,/home/sree/Media/Pictures
media_dir=A,/home/sree/Media/Music

---

### Post by damo12 on 2012-11-07
Hi ssreesanth,

I also have this problem after performing a rescan.  For some reason it can take days (or even a week or so) for the pictures and music to show up.

This has always baffled me as the audio and pictures folders are much smaller in size than the video folder.  The only thing I can think of is that MiniDLNA caches thumbnails of the album art and pictures which takes some time to do this.

Hopefully someone with more knowledge on this matter will be able to confirm this or provide a work around for you.

Damian

---

### Post by cariboo on 2012-11-08
> **ssreesanth said:**
> i am using 10.10 and have configured minidlna. my problem is that my tv is showing my server and the audio video and pictures option. and only video files are getting listed. the audio files and pictures are not showing up on my tv.
any ideas???

media_dir=V,/home/sree/Media/server
media_dir=P,/home/sree/Media/Pictures
media_dir=A,/home/sree/Media/Music

10.10, eol'd in April 2012, I'd suggest updating/fresh installing 12.04, as minidlna is in the repositories. My music library is updated fairly quickly, I've never actually timed it, but if I restart the minidlna service, it takes about 5 minutes for new titles to show up on screen.

---

### Post by ssreesanth on 2012-11-11
well the thing is i am pretty much set with my 10.10
i tried upgrading to 11 and 12.10 also. but my system turns out to be comparatively slow.so decided to stick on with 10.10.

there has to be some solution as videos are showing up fine. 
i tried changing the directories of audio and pictures but no luck.
any solutions...:confused:

p.s is there anything similar to minidlna which i can try?

---

### Post by cariboo on 2012-11-11
If you have logging enabled, have you checked the logs for any errors.

I'm using 12.04 server on an atom 230 based system, 1.6Ghz, 1GiB of ram. I don't use a gui, so the system runs really well, mind you all it is, is a minidlna server.

---

### Post by ssreesanth on 2012-11-12
okay now i have a new symptom...
 
media_dir=V,/home/sree/Media/server
media_dir=P,/home/sree/Media/Pictures
media_dir=A,/home/sree/Media/Music

my audio and pictures were not displayed in the dlna client..

the issue is that there are many subfolders under /home/sree/Media/Music..like the artist and then their respective albums...

i tried moving some audio files to the main /home/sree/Media/Music directory and then they were getting displayed.. 
they r not geting displayed if they r under the sub folder in the music folder.

i dont want to open up all my music files and put it under the music folder.

does anyone know why minidlna is not able to scan the subfolders under music.

---

### Post by donniezazen on 2012-11-12
```
sudo /etc/init.d/minidlna restart
[sudo] password for donnie: 
 * Restarting DLNA/UPnP-AV media server minidlna                                                                                                  [2012/11/11 23:12:56] utils.c:282: warn: make_dir: cannot create directory '/var/lib/minidlna'
[2012/11/11 23:12:56] minidlna.c:527: fatal: Database path not accessible! [/var/lib/minidlna]
```

```
# port for HTTP (descriptions, SOAP, media transfer) traffic
port=8200

# network interfaces to serve, comma delimited
#network_interface=eth0

# set this to the directory you want scanned.
# * if have multiple directories, you can have multiple media_dir= lines
# * if you want to restrict a media_dir to a specific content type, you
#   can prepend the type, followed by a comma, to the directory:
#   + "A" for audio  (eg. media_dir=A,/home/jmaggard/Music)
#   + "V" for video  (eg. media_dir=V,/home/jmaggard/Videos)
#   + "P" for images (eg. media_dir=P,/home/jmaggard/Pictures)
media_dir=V,/mnt/wd/Videos

# set this if you want to customize the name that shows up on your clients
friendly_name=Ubuntu Server

# set this if you would like to specify the directory where you want MiniDLNA to store its database and album art cache
db_dir=/var/lib/minidlna

# set this if you would like to specify the directory where you want MiniDLNA to store its log file
log_dir=/var/lib/minidlna/log

# set this to change the verbosity of the information that is logged
# each section can use a different level: off, fatal, error, warn, info, or debug
#log_level=general,artwork,database,inotify,scanner,metadata,http,ssdp,tivo=warn

# this should be a list of file names to check for when searching for album art
# note: names should be delimited with a forward slash ("/")
album_art_names=art.jpg/Art.jpg/front.jpg/Front.jpg/Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg/Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg

# set this to no to disable inotify monitoring to automatically di# set this to strictly adhere to DLNA standards.
# * This will allow server-side downscaling of very large JPEG images,
#   which may hurt JPEG serving performance on (at least) Sony DLNA products.
strict_dlna=no

# default presentation url is http address on port 80
#presentation_url=http://www.mylan/index.php

# notify interval in seconds. default is 895 seconds.
notify_interval=900

# serial and model number the daemon will report to clients
# in its XML description
serial=12345678
model_number=1

# specify the path to the MiniSSDPd socket
#minissdpdsocket=/var/run/minissdpd.sock

# use different container as root of the tree
# possible values:
#   + "." - use standard container (this is the default)
#   + "B" - "Browse Directory"
#   + "M" - "Music"
#   + "V" - "Video"
#   + "P" - "Pictures"
# if you specify "B" and client device is audio-only then "Music/Folders" will be used as root
#root_container=.
scover new files
# note: the default is yes
inotify=yes

# set this to yes to enable support for streaming .jpg and .mp3 files to a TiVo supporting HMO
enable_tivo=no


```

UPDATE:- Okay it seems to work now. I had to sudo minidlan once to be able to create folders in root filesystem.

---

### Post by ssreesanth on 2012-11-12
i checked the log.. minidlna is trying to scan the desired audio folders but the permission is getting denied..


[COLOR="DarkSlateBlue"]2012/11/12 11:14:38] upnpsoap.c:1748: warn: Returning UPnPError 402: Invalid Args
[2012/11/12 11:31:10] inotify.c:434: warn: Could not access /home/sree/Media/Music/Hindi [Permission denied]
[2012/11/12 11:31:10] inotify.c:434: warn: Could not access /home/sree/Media/Music/Amma [Permission denied]
[2012/11/12 11:31:10] inotify.c:434: warn: Could not access /home/sree/Media/Music/Ludovico Einaudi - Discografia [Permission denied]
[2012/11/12 11:31:10] inotify.c:434: warn: Could not access /home/sree/Media/Music/Malayalam [Permission denied]
[2012/11/12 11:31:10] inotify.c:434: warn: Could not access /home/sree/Media/Music/newsic [Permission denied]
[2012/11/12 11:31:10] inotify.c:434: warn: Could not access /home/sree/Media/Music/English [Permission denied]
[2012/11/12 11:31:10] inotify.c:434: warn: Could not access /home/sree/Media/Music/Hindustani [Permission denied][/COLOR]


any ideas??

---

### Post by craigchambers on 2012-11-12
> **ssreesanth said:**
> i am using 10.10 and have configured minidlna. my problem is that my tv is showing my server and the audio video and pictures option. and only video files are getting listed. the audio files and pictures are not showing up on my tv.
any ideas???

media_dir=V,/home/sree/Media/server
media_dir=P,/home/sree/Media/Pictures
media_dir=A,/home/sree/Media/Music

This may not be your problem, but in my early days of usage on my Sony TV, I sometimes made the mistake (and occasionally still do) of going into Video in the XMB, then selecting Music or Pictures in the tree within Video...

If you have a Sony (possibly other devices also have this issue??) make sure that you select Pictures or Music at the top level of the XMB.  
I have discussed this with Justin Maggard (the dev) and this is because my Sony TVs never tell the server what sort of media each XMB option is looking for, so the server sends all 3 types and this is then filtered by the TV to the type that it is expecting.  

HTH,
Craig

---

### Post by craigchambers on 2012-11-12
> **ssreesanth said:**
> i checked the log.. minidlna is trying to scan the desired audio folders but the permission is getting denied..


[COLOR="DarkSlateBlue"]2012/11/12 11:14:38] upnpsoap.c:1748: warn: Returning UPnPError 402: Invalid Args
[2012/11/12 11:31:10] inotify.c:434: warn: Could not access /home/sree/Media/Music/Hindi [Permission denied]
[2012/11/12 11:31:10] inotify.c:434: warn: Could not access /home/sree/Media/Music/Amma [Permission denied]
[2012/11/12 11:31:10] inotify.c:434: warn: Could not access /home/sree/Media/Music/Ludovico Einaudi - Discografia [Permission denied]
[2012/11/12 11:31:10] inotify.c:434: warn: Could not access /home/sree/Media/Music/Malayalam [Permission denied]
[2012/11/12 11:31:10] inotify.c:434: warn: Could not access /home/sree/Media/Music/newsic [Permission denied]
[2012/11/12 11:31:10] inotify.c:434: warn: Could not access /home/sree/Media/Music/English [Permission denied]
[2012/11/12 11:31:10] inotify.c:434: warn: Could not access /home/sree/Media/Music/Hindustani [Permission denied][/COLOR]


any ideas??

It seems obvious, but have you checked the permissions on the folders and files?  
I'm guessing minidlna is running as a user who does not have read/execute permissions on those folders.

/Craig

---

### Post by ssreesanth on 2012-11-12
> **craigchambers said:**
> It seems obvious, but have you checked the permissions on the folders and files?  
I'm guessing minidlna is running as a user who does not have read/execute permissions on those folders.

/Craig


thanks man. i think i solved it.. minidlna was unablee to read from the default "music" "pictures" "Video" folder in ubuntu.

so i made new folders and shifted all the media.. now all the media is getting listed...
 

cheers:popcorn:

---

### Post by ssreesanth on 2012-11-12
one more thing.... anyone knows step by step process how to autostart minidlna at laptop startup.
will appreciate any help..

---

### Post by cariboo on 2012-11-12
This is the script that starts minidlna as a service on my 12.04 server.

```
#!/bin/sh
#
# MiniDLNA initscript
#
# Based on the mediatomb debian package.
# Original authors: Tor Krill <tor@excito.com>
#                   Leonhard Wimmer <leo@mediatomb.cc>
#                   Andres Mejia <mcitadel@gmail.com>
#
# Modified by: Benoît Knecht <benoit.knecht@fsfe.org>
#
### BEGIN INIT INFO
# Provides:          minidlna
# Required-Start:    $network $local_fs $remote_fs
# Required-Stop::    $network $local_fs $remote_fs
# Should-Start:      $all
# Should-Stop:       $all
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: DLNA/UPnP-AV media server
### END INIT INFO

unset USER

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/sbin:/usr/sbin:/bin:/usr/bin
DESC="DLNA/UPnP-AV media server"
NAME=minidlna
DAEMON=/usr/bin/minidlna
PIDDIR=/var/run/$NAME
PIDFILE=$PIDDIR/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME
DEFAULT=/etc/default/$NAME

# Exit if the package is not installed
[ -x $DAEMON ] || exit 0

# Read configuration variable file if it is present
[ -r $DEFAULT ] && . $DEFAULT

# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

# Do not start the daemon if NO_START is enabled in DEFAULT
if [ "$START_DAEMON" != "yes" ] && [ "$1" != "stop" ]; then
	log_warning_msg "$NAME: Not starting $DESC."
	log_warning_msg "$NAME: Disabled in $DEFAULT."
	exit 0
fi

# Set the default configuration file
if [ -z $CONFIGFILE ]; then
	CONFIGFILE=/etc/minidlna.conf
fi

# Set the default log file
if [ -z $LOGFILE ]; then
	LOGFILE=/var/log/minidlna.log
fi

# Run as `minidlna' if USER is not specified or is `root'
if [ -z $USER ]; then
	USER=minidlna
fi

# If no group is specified, use USER
if [ -z $GROUP ]; then
	GROUP=$USER
fi

DAEMON_ARGS="-f $CONFIGFILE -P $PIDFILE $DAEMON_OPTS"

#
# Function that starts the daemon/service
#
do_start()
{
	# Return
	#   0 if daemon has been started
	#   1 if daemon was already running
	#   2 if daemon could not be started
	touch $LOGFILE && chown $USER:$GROUP $LOGFILE || return 2
	if [ ! -d $PIDDIR ]; then
	    mkdir $PIDDIR || return 2
	fi
	chown $USER:$GROUP $PIDDIR || return 2

	start-stop-daemon --start --quiet --pidfile $PIDFILE \
		--chuid $USER:$GROUP --exec $DAEMON --test > /dev/null \
		|| return 1
	start-stop-daemon --start --quiet --pidfile $PIDFILE \
		--chuid $USER:$GROUP --exec $DAEMON -- \
		$DAEMON_ARGS \
		|| return 2
}

#
# Function that stops the daemon/service
#
do_stop()
{
	# Return
	#   0 if daemon has been stopped
	#   1 if daemon was already stopped
	#   2 if daemon could not be stopped
	#   other if a failure occurred
	start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
	RETVAL="$?"
	[ "$RETVAL" = 2 ] && return 2
	# Wait for children to finish too if this is a daemon that forks
	# and if the daemon is only ever run from this initscript.
	start-stop-daemon --stop --quiet --oknodo --retry=0/30/KILL/5 --exec $DAEMON
	[ "$?" = 2 ] && return 2
	# Many daemons don't delete their pidfiles when they exit.
	rm -rf $PIDDIR
	return "$RETVAL"
}

case "$1" in
  start)
    [ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC " "$NAME"
    do_start
    case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
  ;;
  stop)
	[ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
	do_stop
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  status)
       status_of_proc "$DAEMON" "$NAME" && exit 0 || exit $?
       ;;
  restart|force-reload)
	log_daemon_msg "Restarting $DESC" "$NAME"
	do_stop
	case "$?" in
	  0|1)
		if [ "$1" = "force-reload" ]; then
			# Rescan the collection
			DAEMON_ARGS="$DAEMON_ARGS -R"
		fi
		do_start
		case "$?" in
			0) log_end_msg 0 ;;
			1) log_end_msg 1 ;; # Old process is still running
			*) log_end_msg 1 ;; # Failed to start
		esac
		;;
	  *)
	  	# Failed to stop
		log_end_msg 1
		;;
	esac
	;;
  *)
	echo "Usage: $SCRIPTNAME {start|stop|status|restart|force-reload}" >&2
	exit 3
	;;
esac

:
```

If I remember correctly 10.10 uses upstart, so the script should work for you, although you may have to check paths.

---

### Post by ssreesanth on 2012-11-13
stupid question...

what to do with this code. lol...
an u plzzz tell me step by step process.

---

### Post by craigchambers on 2012-11-16
> **ssreesanth said:**
> stupid question...

what to do with this code. lol...
an u plzzz tell me step by step process.

That's a sysvinit script by the look of it, so you can do the following...

1) Put the contents into a file /etc/init.d/minidlna
e.g. if you like a GUI text editor... ```
gksu gedit /etc/init.d/minidlna
```

2) Run the following
```
sudo update-rc.d minidlna defaults 91
```

HTH,
Craig

---

### Post by donniezazen on 2012-11-19
It doesn't do on-the-fly-transcode. Does it?

I see there is a [minidlna-trancode]("https://bitbucket.org/stativ/minidlna-transcode/overview") which is work in progress but no easy to stable install.

---

### Post by cariboo on 2012-11-19
> **donniezazen said:**
> It doesn't do on-the-fly-transcode. Does it?

I see there is a [minidlna-trancode]("https://bitbucket.org/stativ/minidlna-transcode/overview") which is work in progress but no easy to stable install.

That utility looks like it only transcodes raw photo images.

---

### Post by craigchambers on 2012-11-19
> **cariboo907 said:**
> That utility looks like it only transcodes raw photo images.

As stated on the linked site, it's a selection of parts of Hieroun's transcode patch.  The original was linked on the page...
[http://sourceforge.net/tracker/index.php?func=detail&aid=3193201&group_id=243163&atid=1121518](http://sourceforge.net/tracker/index.php?func=detail&aid=3193201&group_id=243163&atid=1121518)

The readme from Hiroun's patch starts with 
> Note for transcode patch

1. Options

This patch supports transcoding for both Video and Audio using mencoder/ffmpeg as transcoder.
Also other encoders can be used using shell script.

I've never used it as I started with miniDLNA at the same time as I started ripping my DVDs for my TV, so I simply used a supported format, but I've read that it works.

/Craig

---

### Post by neuman1812 on 2012-12-02
Im hoping someone here can help as I';ve been reading this thread to get minidlna started.   

I installed with the ppa  on ubuntu 12.04  This is what I get on startup in the log

```
[2012/12/02 17:58:49] minidlna.c:888: warn: Starting MiniDLNA version 1.24.1-stedy [SQLite 3.7.9].
[2012/12/02 17:58:49] sql.c:41: error: SQL ERROR 8 [attempt to write a readonly database]
pragma default_cache_size = 8192;
[2012/12/02 17:58:49] minidlna.c:989: warn: HTTP listening on port 8200
[2012/12/02 17:58:49] inotify.c:91: error: inotify_add_watch(/media/Storage/movies) [Permission denied]
[2012/12/02 17:58:49] inotify.c:91: error: inotify_add_watch(/media/Storage/tvshows) [Permission denied]
[2012/12/02 17:58:49] minidlna.c:1199: debug: HTTP connection from 192.168.1.104:65147
[2012/12/02 17:58:50] minidlna.c:1199: debug: HTTP connection from 192.168.1.104:13722
[2012/12/02 17:58:51] minidlna.c:1199: debug: HTTP connection from 192.168.1.104:31834
```


I checked the permissions on the folders and they open  but to double check I ran  
```
sudo 777 /media/Storage/tvshows
sudo 777 /media/Storage/movies

```

Im at a loss here.  any suggestions?

---

### Post by craigchambers on 2012-12-03
> **neuman1812 said:**
> This is what I get on startup in the log

```

[2012/12/02 17:58:49] sql.c:41: error: SQL ERROR 8 [attempt to write a readonly database]
```

I checked the permissions on the folders and they open  but to double check I ran  
```
sudo 777 /media/Storage/tvshows

```


I presume that you mean 'sudo chmod 777'.

Are you running miniDLNA manually?  You are getting permission problems which suggests that this is the case.

MiniDLNA is designed to be run as a daemon (like, for example, the Apache web server), which means that it is usually run with escalated permissions by a startup script.
Running it as a manual process is more of a debug usage, as running any server manually is.

In your case the database is causing an error, as is adding an inotify watch (not reading the folders).  The DB is not generally stored in the media location, but it seems to default on the Ubuntu package to /var/lib/minidlna/files.db (or it could be /var/cache/minidlna/files.db as this is the config file suggestion).  

Can you see if the database file exists and what the permissions are on the file?

The start-up script forces the user to minidlna, and that is the owner and group on my file.

If you want to run manually or without the escalated permissions required to write to the standard locations, you will have to configure the db to a writeable directory either in your config file, or as a command line parameter.

HTH,
Craig

---

### Post by Tosh78 on 2013-01-13
Hi all, maybe someone of you can help me out.

I've installed minidlna and was using it without any issues until a couple of days ago. 
Everything seems to work fine except two things:
1) if I want to watch a video that has subtitles inserted directly in the file (not as separate file), the subtitles don't show at all in the TV. Because of this problem I ran it manually and I found that I get an error, which takes me to the next point
2) I get a parsing error in line 1, which is the port. I didn't touch anything here and it's all default. However I don't know what the problem could be or how to check it. 

I'm running Minidlna version 1.0.25

The only thing that I installed a couple of days ago was Webmin and the minidlna module. 

Can anybody help?

---

### Post by craigchambers on 2013-01-14
> **Tosh78 said:**
> 
I've installed minidlna and was using it without any issues until a couple of days ago. 
1) Embedded subtitles don't show at all in the TV. 
Is this a new problem since you upgraded?  Subtitle support is generally client side.  My Sonys don't support them at all (embedded or in an SRT file).

> 2) I ran it manually and I get a parsing error in line 1, which is the port.  Did you stop the existing minidlna daemon?

> The only thing that I installed a couple of days ago was Webmin and the minidlna module. 
I found webmin a lot more trouble than it was worth in time saving (YMMV).  Did the minidlna module also pull in a repository version of minidlna that up/downgraded your existing install?
Did it overwrite your existing config file.  Did it change the init script?

HTH,
Craig

---

### Post by jimbean on 2013-01-22
ubuntu 12.10

Used sudo service minidlna force-reload

parsing error :

parsing error file /etc/minidlna.conf line 34 : /home/***/.minidlna/cache

Also the streaming device smp-n200 sony is saying a whole bunch of directories that arent there
eg: music album,allmusic,artist,genre,playlists

Used// tail -20f /var/log/minidlna.log and got

[2013/01/22 15:54:50] scanner.c:727: warn: Scanning /home/***/Pictures
[2013/01/22 15:54:50] scanner.c:798: warn: Scanning /home/***/Pictures finished (16 files)!
[2013/01/22 15:54:50] playlist.c:125: warn: Parsing playlists...
[2013/01/22 15:58:28] minidlna.c:155: warn: received signal 15, good-bye
[2013/01/22 16:06:34] minidlna.c:898: warn: Starting MiniDLNA version 1.0.24 [SQLite 3.7.13].
[2013/01/22 16:06:34] minidlna.c:926: warn: Creating new database...
[2013/01/22 16:06:34] scanner.c:727: warn: Scanning /home/***/Music
[2013/01/22 16:06:34] scanner.c:798: warn: Scanning /home/***/Music finished (0 files)!
[2013/01/22 16:06:34] scanner.c:727: warn: Scanning /home/***/Pictures
[2013/01/22 16:06:34] minidlna.c:1006: warn: HTTP listening on port 8200
[2013/01/22 16:06:34] scanner.c:798: warn: Scanning /home/***/Pictures finished (8 files)!
[2013/01/22 16:06:34] scanner.c:727: warn: Scanning /home/***/Videos
[2013/01/22 16:06:34] scanner.c:798: warn: Scanning /home/***/Videos finished (8 files)!
[2013/01/22 16:06:34] scanner.c:727: warn: Scanning /home/***/Pictures
[2013/01/22 16:06:34] scanner.c:798: warn: Scanning /home/***/Pictures finished (16 files)!
[2013/01/22 16:06:34] playlist.c:125: warn: Parsing playlists...
[2013/01/22 16:08:58] minidlna.c:155: warn: received signal 15, good-bye
[2013/01/22 16:08:59] minidlna.c:898: warn: Starting MiniDLNA version 1.0.24 [SQLite 3.7.13].
[2013/01/22 16:08:59] minidlna.c:1006: warn: HTTP listening on port 8200
[2013/01/22 16:11:39] minidlna.c:155: warn: received signal 15, good-bye

---

### Post by Martin_Davies on 2013-10-16
> **sloopjonb said:**
> Don't get caught out with minidlna apparently not starting automatically.........

When you use apt-get to install minidlna on Ubuntu Server it installs the start and stop scripts in the /etc/rcN.d folders with the minidlna server starting almost immediately in the boot process. This is too early! Things like RAID partitions might not be ready to be probed by minidlna at this point, so you need to delay it to later..... read on.....

I'm running 11.10 (oneiric) and got minidlna to start automatically upon booting, with the following instructions:



edit minidlna.conf to point towards the path for your video/audio etc.

 
this removes the incorrectly numbered start up scripts.

 
creates new start up scripts which will start near the end of the boot process

All is now good in the world......


All would be good if there wasn't a tiny, tiny typo in your code...

The last code snippet should read
```
sudo update-rc.d minidlna defaults 99 01
```


Great guide, by the way.  Just need to fix my CRON jobs to re-run the scan at midnight and I'll be done.

Savcom

---

### Post by Martin_Davies on 2014-01-08
> **Martin_Davies said:**
> Just need to fix my CRON jobs to re-run the scan at midnight and I'll be done.

Well it took a while, but if you want to automatically re-scan the media on your system then you should:

[LIST]
[*]Choose or set up a user with a valid login account (don't use minidlna as it does not have a shell in which to run Cron tasks) 
[*]Under that user's Crontab enter the Cron task 
[/LIST]
```

#
# Sudo command at 04:00 and 16:00 every day to re-scan the media directories for miniDLNA
0 04,16 * * * minidlna -R -f /etc/minidlna.conf > /dev/null
#
```

[LIST]
[*]Make sure that /etc/default/minidlna is set up with that username and group too. 
[/LIST]
```

# User and group the daemon should run as
USER="martin"
GROUP="martin"
```

---

### Post by Urgrok on 2014-02-01
> **donniezazen said:**
> 

```
# 
# set this if you want to customize the name that shows up on your clients
friendly_name=Ubuntu Server
 
```


 I think you are supposed  NOT to use  " " within the Friendly name ?!

---

