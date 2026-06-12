---
title: "Finally took the plunge"
date: 2004-12-22
forum: The Cafe
---

### Post by jakeslife on 2004-12-22
Sorta anyways. 

So tonight while I was packing up my non-essential computer equiptment (like there is such a thing) I found an old 6.4 gig hard drive. I figured I was tired of packing for my move, and I was just going to install Ubuntu on that hard drive and play for a bit. 

For starters, my machine is a 2 GHz Intel Celeron, MSI (don't remember the exact model) motherboard, nVidia GeForce 4 128 MB video card, CD-RW and DVD-ROM, with a MS wireless keyboard and mouse. Misc. peripherals are a bluetooth dongle, MS sidewinder gamepad, Creative webcam Pro (x2), USB web cam of non-descript make. I unplugged the bluetooth dongle, but left everything else connected.

I was excited. I had a 12-pack of soda next to my desk and ready to roll. From the time I rebooted to the time I was in Gnome was about 28 minutes (I chose a default install to the entire hard drive, and chose to update all of the packages online--this alone took a few minutes). 

Before it started Gnome, it asked me which monitor resolutions I wanted it to display at. I chose 1600x1200 (which is what I run in XP on my 21" Viewsonic flat screen) and thought it would be a pain because all of the linux distros I have tried in the past can never get higher than 1024x768 for osme reason, even with the proper drivers installed. Amazing, it's at 1600x1200.

The first thing I did was change the background to the Apple wallpaper I posted a few days ago, and started going through the Ubuntu User's Guide and installing media codecs, DVD compatability, etc. I have not run into one problem, and everything seems to be working fine.

I think that once I move into my new place next week, I've found my new OS, and I think it's all because of one hyphenated word..."apt-get." ;-)

---

### Post by jakeslife on 2004-12-22
Okay, so maybe I lied. My Soundblaster card isn't working. I'm currently searching the forums to work on it.

Disabled onboard sound from BIOS. Working now. Yay!

---

### Post by cacofonix on 2004-12-22
Thats good news jake :D Enjoy ubuntu  8) 


cacofonix

---

### Post by ubuntu_demon on 2004-12-22
good :)
Does that mean more wallpapers from you ?   :-D

---

### Post by crun on 2004-12-22
[IMG]http://imageafter.com/temp/lex/images/forums/welcome_to_ubuntu.jpg[/IMG]

---

### Post by Quest-Master on 2004-12-22
Awesome :)

It always seems like you won't have much fun with Ubuntu at first since you think it'll be like all of the other distros, but once you try it, you can't leave. Just as that great image crun posted says so ;)

---

### Post by jakeslife on 2004-12-22
Well I have run into a few minor annoyances...nothing huge, just things that are working right I'm sure but I don't understand...

In the repository the only version of Thunderbird I've found was .9. I downloaded and installed Thunderbird 1.0 from Mozilla.org and can't find where it installed to. I've used Lost & Found but whenever I try to search it doesn't search. Hmph.

I've also downloaded some stuff (Quake 2, some other little games and stuff) through Synaptic that won't work. I okayed all of the dependancies to be installed along with them, but (although it took me a while before I found where they installed) they still won't work. I open up the System Manager and their process starts, but stops a few seconds later.

I haven't found a doc on the file structure of Ubuntu, and I know most distros loosely follow the same one, but some distros do things differently. Can someone give me a quick breakdown?

And yes, more wallpapers are sure to come. :-)

---

### Post by jakeslife on 2004-12-22
FYI...more wallpapers at [http://ubuntu.jakeslife.net](http://ubuntu.jakeslife.net)

Just finished uploading them.

---

### Post by crun on 2004-12-22
nice collection of wallpapers jakeslife

* Firefox 1.0 isn't in Warty yet, but it is in Hoary
* Firefox is usually installed in /usr/lib, probably /usr/lib/mozilla-firefox
* if it isn't there, try
```
find / | grep firefox 
```
(takes some time as it searches all your partitions)
or
```
whereis firefox
```
* Quake 2 is still a commercial game and as such can't be placed totally in the repositories (correct me if I'm wrong though) - what you installed will probably be the Linux environment, but you'll still need that original (.wad ?) files from the commercial game

---

### Post by jakeslife on 2004-12-22
Thanks for the advice crun, but Firefox is in /usr/lib, but Thunderbird isn't.

---

### Post by jakeslife on 2004-12-22
Okay, so I think I found it. When I downloaded the package from Mozilla.org it downloaded to my Home directory, and when I ran the installation script, that's where it installed.

---

### Post by jdodson on 2004-12-22
i am running those wallpapers on my machine now, they are great!

---

### Post by jakeslife on 2004-12-22
Which ones do you like?

---

### Post by matt on 2004-12-22
Jake: love the wallpapers! The Christmas ornament will be a fixture for the next few days, but my favourites are Coffee Candy and Buddha! Great work.

---

### Post by jakeslife on 2004-12-22
Thanks Matt! I'm glad that you enjoy them! I'm partial to the Buddha one myself *glances at statue*, but the one I'm using right now is the nutcracker one. I was looking at it later on, and I don't know why, but it's hilarious!

I like minimalistic, smooth wallpapers, and I always prefer photographs of simplicity over anything rendered.

Current screenie: [http://ubuntu.jakeslife.net/screenie.png](http://ubuntu.jakeslife.net/screenie.png)

---

### Post by mark on 2004-12-22
[QUOTE=jakeslife]FYI...more wallpapers at [http://ubuntu.jakeslife.net](http://ubuntu.jakeslife.net)

Just finished uploading them.[/QUOTE]
Jake - nice job with the wallpapers (I like the Buddha, too).  And congratulations on a *relatively* painless first Ubuntu install.  I empathize with your comment (elsewhere) re: apt-get - I was a long-time user of Red Hat/Fedora Core distros (which served me well) but the ease & speed of apt vs. up2date/yum won me over.

Mark

---

### Post by jakeslife on 2004-12-22
Thanks Mark. The only issue I have run into with apt-get is trying to install xfce. I was following the directions on a web site, so they may or may not be correct for Ubuntu specifically (the docs were for Debian) and they sent me into a spiral of dependency blibber. Overall, I do love apt-get though.

---

### Post by jakeslife on 2004-12-22
I've run into an odd situation...gnome is gone. There was an error, and it disappeared, so I restarted the X server and it was still coming up with no panels or anything, so I rebooted the machine and it's the same thing again. Any suggestions?

---

### Post by cacofonix on 2004-12-22
Thunderbird doesnt install itself at all where ever you downloaded and untared it, is where you will most likely to find it. By the way excellent wallpapers jake :D


cacofonix

---

### Post by jakeslife on 2004-12-22
Well I've learned something...always check dependancies when you uninstall something! Uninstalling Evolution also uninstalls gnome-panel. Muey muey!

---

### Post by jobezone on 2004-12-22
If you delete the .gnome, .gnome2 and .gconf and .gconf.d directories on your homedir, it will completely delete the configuration you've done in gnome, (panel configs, desktop wallpaper, etc. BUT not your files and configuration for aplications which lie outside of these directories) and give you back the default Gnome state again. Perhaps there's no need to delete all of these, but it has worked for me when something like what you explained happened to me.

To do this, at GDM do:

CTRL+ALT+F1 (which will open Virtual Terminal 1)
log in with your username and type:
rm -r .gnome
rm -r .gnome2

etc,

They're hidden, since they have a .(dot) before their name. To list all the files and dirs, including hidden ones, type:

ls -al

---

### Post by jakeslife on 2004-12-22
Thanks, but I think I got it figured out. I searched for it on the forum, and one fix said to start gnome, then open a terminal and start "gnome-panel." When I tried to do this, it said that it didn't exist, so I tinkered around for a few minutes looking at other fixes, then went into Synaptic and searched for Gnome, and sure enough when I uninstalled Evolution, it took gnome-panel and a bunch of other stuff with it, so I just reinstalled it and everything else.

Thanks though!

---

### Post by Hikaru79 on 2004-12-23
Just a note -- you can safely uninstall Evolution without touching gnome-panels, it's the package called evolution-data-server which causes problems. That's the one that takes GNOME with it. On my box, I removed every part of evolution except for that one, and it's all been good :)

BTW, Jake, the photos used on your wallpapers, do you take them yourself or are they just pilfered from the net? :) I like all the candy ones! You must have quite a sweet tooth ;)

---

### Post by jakeslife on 2004-12-23
Some of them I take myself, some of them are part of stock photo collections I've purchased, and some are from sxc.hu (great site by the way). 

I love candy! Even though I have to be fit and everything, I like to stash a few things here and there for those stressful moments...

---

### Post by crun on 2004-12-23
jakeslife: now seems as good a time as any to plug my own stockphoto site: [http://www.imageafter.com](http://www.imageafter.com) (we're in the link section of sxc.hu). We haven't got as many photos as them, but we still have a good collection and it's growing fast. Everything is (copyright-) free ofcourse.

---

### Post by jakeslife on 2004-12-23
sa-weet!

---

### Post by gbusse on 2005-03-16
[QUOTE=jakeslife]Sorta anyways. 

So tonight while I was packing up my non-essential computer equiptment (like there is such a thing) I found an old 6.4 gig hard drive. I figured I was tired of packing for my move, and I was just going to install Ubuntu on that hard drive and play for a bit. 

For starters, my machine is a 2 GHz Intel Celeron, MSI (don't remember the exact model) motherboard, nVidia GeForce 4 128 MB video card, CD-RW and DVD-ROM, with a MS wireless keyboard and mouse. Misc. peripherals are a bluetooth dongle, MS sidewinder gamepad, Creative webcam Pro (x2), USB web cam of non-descript make. I unplugged the bluetooth dongle, but left everything else connected.

I was excited. I had a 12-pack of soda next to my desk and ready to roll. From the time I rebooted to the time I was in Gnome was about 28 minutes (I chose a default install to the entire hard drive, and chose to update all of the packages online--this alone took a few minutes). 

Before it started Gnome, it asked me which monitor resolutions I wanted it to display at. I chose 1600x1200 (which is what I run in XP on my 21" Viewsonic flat screen) and thought it would be a pain because all of the linux distros I have tried in the past can never get higher than 1024x768 for osme reason, even with the proper drivers installed. Amazing, it's at 1600x1200.

The first thing I did was change the background to the Apple wallpaper I posted a few days ago, and started going through the Ubuntu User's Guide and installing media codecs, DVD compatability, etc. I have not run into one problem, and everything seems to be working fine.

I think that once I move into my new place next week, I've found my new OS, and I think it's all because of one hyphenated word..."apt-get." ;-)[/QUOTE]
 Jake,

I noticed that you have a Creative Webcam Pro. I also have one of those webcams. My question is have you been able to get it to work well with Gnomemeeting? Mine worked with Gnomemeeting right out of the box but the picture is extremely dark and seems to be cut off (ie not showing the whole image). Just curious as so far this is the only thing that is giving me some issues with Ubuntu. Other than that the experience has been very liberating.

I have searched througout these forums and google and have yet to find any solutions to the my webcam woes. I did find a bit of info on the Gnomemeeting site:

----

8.1.2. GnomeMeeting only displays a part of the real picture in the video window, what can I do?

Are u sure that your driver support 176x144 (QCIF) or 352x288 (CIF) as capture size? Try to look at the documentation of your driver. 

----

This sounds like the size issue but I really have no idea where to check this? I have still not been able to find anything related to the dark picture. Even playing with the video controls in Gnomemeeting doesn't help much at all.

The cam works perfectly fine under XP, so I am pretty sure it is not a hardware issue.

Thanks in advance to anyone who can point me in the right direction...

Gord

Oh and by the way, very cool wallpapers!

---

### Post by Dragonfly_X on 2005-03-17
Nice Backgrounds! I decided to go with the apple background! =P~

---

