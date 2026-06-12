---
title: "DLNA for Headless Ubuntu Server"
date: 2011-10-14
forum: Server Platforms
---

### Post by damo12 on 2011-10-14
Hi,

I have a server running Ubuntu Server 10.04 64 bit.  This server is mainly used as a file server for my computers and laptop.  I store all of my music, films pictures etc on the server and each computer accesses them through samba shares.

I have recently bought an LG HX806SH Blu-ray player which is DNLA compliant.  Although I have a networked media streamer connected to my TV, I would like to do away with that and use the Blu-ray player to view my media.

The server is a headless one, controlled through Webmin and Putty when necessary.

Can anyone advise of a suitable DNLA program that I can use to stream my media?

I have tried Mediatomb which just did not seem to work at all.  It added the files to its database but on restarting the server or even the program, it either lost all of the files in the database or refused to restart.  Even before restarting, the Blu-ray player could not see the server at all.

I then tried Minidlna which worked a little bit.  The player would see the server and would see a few folders of the video files but did not see all of the folders and did not see most of the video files.  When it came to my pictures and music, it did not see any of the files or folders at all.

I should stress that I am not overly confident with Linux so ideally I would be looking for a site which has straight forward instructions (not just “download and compile program x then run it”) and a healthy support / forum network should I run into any problems.

I have also posted this question in the “Multimedia and Video” forum at [http://ubuntuforums.org/showthread.php?p=11342111#post11342111](http://ubuntuforums.org/showthread.php?p=11342111#post11342111).

Thanks in advance for your help.

---

### Post by cariboo on 2011-10-14
I use [minidlna]("http://sourceforge.net/projects/minidlna/"), and I used [this]("http://blog.homelinux.org/?p=198") howto, to set it up.

This is what my minidlna.conf looks like:

> cat minidlna.conf
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
#media_dir=/opt
media_dir=V,/media/green
media_dir=A,/media/music
media_dir=V,/media/tv1
media_dir=V,/media/tv2

# set this if you want to customize the name that shows up on your clients
friendly_name=Willy DLNA Server

# set this if you would like to specify the directory where you want MiniDLNA to store its database and album art cache
db_dir=/var/cache/minidlna

# set this if you would like to specify the directory where you want MiniDLNA to store its log file
log_dir=/var/log

# this should be a list of file names to check for when searching for album art
# note: names should be delimited with a forward slash ("/")
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg/Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg

# set this to no to disable inotify monitoring to automatically discover new files
# note: the default is yes
inotify=yes

# set this to yes to enable support for streaming .jpg and .mp3 files to a TiVo supporting HMO
enable_tivo=no

I use a Samsung BD-B5300 as a client. The one thing I've noticed so far, is that I use vobcopy to rip my dvds, and It will only play the first 50 minutes of the files. Whether this is a problem with the dvd player or something else, I haven't had time to track it down.

---

### Post by myusernameisnotvalid on 2011-10-15
I have server for same use at the time. I used to use minidlna too, but since it won't support FLAC (as far as I know, correct me if I'm wrong) I have change to serviio. If your interested in you can check the [link]("http://www.serviio.org/").

---

### Post by damo12 on 2011-10-17
Hi,

Thanks for the help and advice.  For some reason I could not get minidlna to work at all so I uninstalled it and after reading what you posted I tried re-installing it.  This time it seems to be working pretty well but I'm still having a few problems with it.

It won't stream photos which to be honest, I'm not bothered about, I can view my recordings and listen to my music (all in mp3 format) so there's no issues there.  The problem seems to be getting it to recognise new files or folders that I've added and still shows deleted files as being present.

Since re-installing, I have added a few sub-folders to the folders already listed in my minidlna.conf file and have added a new folder to the minidlna.conf file.

I have tried stopping and restarting minidlna using the commands:

```
sudo /etc/init.d/minidlna stop
sudo /etc/init.d/minidlna start
```

and reloading the database using the command:

```
sudo /etc/init.d/minidlna reload
```

When that did not work, I tried rebooting the server and then carrying out the same commands with no joy.

I changed the name of the server and the Blu-ray picks that up fine so I think it is something with minidlna rather than the Blu-ray.

Is there any way to resolve this without re-installing minidlna every time I add or remove files?

My minidlna.conf file is:

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
friendly_name=My DLNA Server

# set this if you would like to specify the directory where you want MiniDLNA to store its 

database and album art cache
db_dir=/media/server/server/Backup/Server/MiniDLNA

# set this if you would like to specify the directory where you want MiniDLNA to store its 

log file
#log_dir=/var/log

# this should be a list of file names to check for when searching for album art
# note: names should be delimited with a forward slash ("/")
album_art_names=Front.jpg/front.jpg/Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/

AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg/Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg

# set this to no to disable inotify monitoring to automatically discover new files
# note: the default is yes
inotify=yes

# set this to yes to enable support for streaming .jpg and .mp3 files to a TiVo supporting 

HMO
enable_tivo=no

# set this to strictly adhere to DLNA standards.
# * This will allow server-side downscaling of very large JPEG images,
#   which may hurt JPEG serving performance on (at least) Sony DLNA products.
strict_dlna=no

# default presentation url is http address on port 80
presentation_url=http://server/index.php

# notify interval in seconds. default is 895 seconds.
notify_interval=900

# serial and model number the daemon will report to clients
# in its XML description
serial=12345678
model_number=1

```


Many thanks

---

### Post by Gyokuro on 2011-10-17
Hi,

there is no need to restart your server in such a case - kill minidlna and force a rescan of your medialib

minidlna -R

---

### Post by damo12 on 2011-10-17
Hi Gyokuro,

I have set a new scan with the command minidlna -R which so far does not seem to have made any difference (new files are still missing and old ones which have been deleted are still showing as being present).

Looking through the log (minidlna.log) I receive messages such as:

```
[2011/10/17 19:31:23] scanner.c:726: warn: Scanning /media/server/server/Music/Videos
[2011/10/17 19:31:32] scanner.c:798: warn: Scanning /media/server/server/Music/Videos finished (1369 files)!

```

However, this folder (which I added to the minidlna.conf today) is still missing.

Further on I get messages such as:

```
[2011/10/17 20:13:17] upnphttp.c:1795: error: Error opening /media/server/server/Media/TV/Test/xvid.avi

```

xvid.avi is one of the files I have deleted however it still shows up on the Blu-ray player.

I have tried looking using a Windows computer to access the stream as it sees the minidlna server as a streaming device.  This has the same problems as the Blu-ray in that it still sees files that have been deleted and it does not see new files.

Thanks for your help

---

### Post by damo12 on 2011-10-21
Thanks for all of your help.

After some looking around, I found a Webmin module for MiniDLNA at [https://sourceforge.net/projects/minidlnawebmin/]("https://sourceforge.net/projects/minidlnawebmin/").

Once that was installed, there is a button "Rescan" which automatically erases the database and re-scans the folders.  This removes all deleted files and folders and adds any new ones.  It took less than 10 minutes for it to scan about 12,000 files.

The only problem I found with this module was that the "Restart" button does not work properly.  It stops MiniDLNA but will not restart it and the using the command *sudo /etc/init.d/minidlna start* fails.  The only way round that was to restart the entire server.

After my trials and tests, I have produced a step by step guide at [http://ubuntuforums.org/showthread.php?t=1866520]("http://ubuntuforums.org/showthread.php?t=1866520") which will hopefully help other people trying to install and configure MiniDLNA.

Thanks again for all of your help and support.

---

### Post by shirike on 2012-09-06
Apologies for the thread necromancy but this seemed the most appropriate existing thread for ym query.

I'm running minidlna on a semi-headless ubuntu setup.

minidlna works fine until I perform a rescan in webmin - the rescan always deletes the minidlna folder I have created to hold the album art and file.db.

To resolve the problem I simply re-create the directory via tight vnc then run 


sudo /etc/init.d/minidlna start

then

sudo chown -R minidlna:minidlna /media/Main/minidlna

Starting minidlna gets it all working again.

Knowing how to fix it is all well and good but I'd quite like to know why it breaks.

---

### Post by damo12 on 2012-09-07
Hi shirike,

As far as I can tell from my experience with miniDLNA, this is the normal procedure the rescan function.  On my system at least when I perform a rescan through the Webmin module, miniDLNA deletes its database and album art file and creates a new one.

With video clips (films etc) it does this quite quickly although I have noticed that with pictures this can take some time.  I must admit that I have not checked to see how long it takes to do this with music.

I believe it does this as there is no way to manually remove files from its database and so the only way it can do this is to wipe everything and start from scratch again.

With regards to album art, when it carries out the rescan it will re-create the art based on the art encoded into the file.

I hope that this answers your question but if you are still having problems and you do not get a suitable reply on this thread, you could try asking at [http://ubuntuforums.org/showthread.php?t=1866520]("http://ubuntuforums.org/showthread.php?t=1866520") which is a guide I wrote on miniDLNA and there are quite a few miniDLNA experts on there.

Good luck,

Damian

---

