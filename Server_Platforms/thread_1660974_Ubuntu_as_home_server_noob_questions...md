---
title: "Ubuntu as home server noob questions.."
date: 2011-01-06
forum: Server Platforms
---

### Post by benjio123 on 2011-01-06
Well here's my dilemma: I just bought a very cheap atom-based board and have a few huge usb hard drives lying around. I am planning on using this for just a few simple tasks, but I am a linux noob and I was hoping someone could point me to some guides to help me with some of this stuff..

First of all, I have a monitor, mouse, and keyboard that I can use for setup, but will not be there permanently, so I'll need a good VNC server that I can control from my mac. I usually use LogMeIn, but it doesn't look like there's a linux version..

Since I'll use it as a file server between multiple macs and PCs I'm hoping AFP and Samba are simple to set up, but apparently Samba is pretty tough, and I can't find a thing on AFP/Bonjour.. My network is locked down tight, and all of the computers on it are trusted, so I want the password settings to be wide-open (not even ask for one).

Stream media files to my ps3 via DLNA.. This one I've found a guide for.. But it involved compiling minidlna from scratch and I really don't think I'm qualified for that.. any easier way than that?

Possibly setting up a password-protected FTP site that can be accessed over internets thru dyndns.

If possible, I'd like my usb drives to show up on other devices as one mega drive, if this is even possible..

Run transmission, but I think I can figure this one out..

Also, is any of this built into ubuntu server, desktop, or any of the builds??? Might explain my inability to find guides on my own..

I don't have ubuntu installed on it yet, but I'd like to make sure it's easy enough before I take the plunge (If not, I'll spring for a windows home server license, although I don't really want to). I have used ubuntu before on some desktops, so I know my way around, but messing with config files and stuff is a bit over my head unless theres an extremely simple guide to follow.

Anyway, sorry for the noob questions and thanks in advance for any help!!

---

### Post by Skadork on 2011-01-06
Sounds like you are wanting an all in one solution.  I would suggest something like OpenFiler ([http://openfiler.com](http://openfiler.com)) or FreeNAS ([http://freenas.org](http://freenas.org)).  These are both complete systems that have an extremely small foot print and offer lots of features including everything that you have mentioned.  All administration is done through a website on the server.  Its very intuitive and easy to navigate.

If you are wanting to set it up yourself, I would suggest using a server management software like Webmin which will make it easy to set up a webserver, ftp server, and other maintenance tasks.

---

### Post by elico on 2011-01-06
well you dont realy need vnc to manage the server..
you can use wither SSH or WEBMIN.
in case you want only storage then ok it's fine to use freenas and openfiler.
freenas is much more simple to understand (my opinion) then open filer.
but if you want to make something else more then just nas you should consider ubuntu server.
for me it takes between 1.5 GB to 2GB the whole os files(basic stuff + servers + packages of other things).
im using my server as a NAS + Bit-torrent client + mail server (couple domains of some business ).


if you ask me it will be a waste of your money to buy windows server licensee for your needs.
ubuntu is one of best Linux servers the i now of and can do so much for you.

in any case you will use ubuntu server you will read manuals and guides so take a cup of tea or something relaxing   to have clear mind about it.

---

### Post by benjio123 on 2011-01-10
Hey thanks a TON for the help guys..  freenas looks pretty ok but not tweakable enough for me lol...
Anyway, I installed a fedora-based home server called Amahi, and it was awesome except for a few things that bugged me. It ran on an older fedora that couldn't intall the latest transmission, and couldn't use remotegui with it. Also, the disk-pooling feature didn't work with AFP.. It was definitely a learning experience!!
Now that I know what I need I think I've got a solution that only involves minimal cli work.

Installing ubuntu server, pooling the storage disks with LVM, installing minidlna, webmin, and following [This Guide]("http://missingreadme.wordpress.com/2010/05/08/how-to-set-up-afp-filesharing-on-ubuntu/") for getting AFP running.

I also managed to use mac's built in screen sharing for my vnc using some info here:[http://wiki.amahi.org/index.php/AFP](http://wiki.amahi.org/index.php/AFP)

---

