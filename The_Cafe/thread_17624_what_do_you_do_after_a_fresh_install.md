---
title: "what do you do after a fresh install"
date: 2005-03-01
forum: The Cafe
---

### Post by monkeymartin on 2005-03-01
these are the things that I would like to do 

-burn cds/dvds (k3b?)
-watch movies (mplayer xine) 
-play mp3's (XMMS)
-play dvd's 
-p2p (azureus)
-firefox plugins 

I am a gentoo user giving ubuntu a try.  I don't know much about apt/synaptic

what repositories should I add if any?

I know about this guide [http://ubuntuguide.org/](http://ubuntuguide.org/) I am just wondering what you do to tweak your Ubuntu install 

thakns Ubuntu looks great

---

### Post by jdong on 2005-03-01
Make sure you enable Universe to get K3b -- still the best, most mature burning application. It runs beautifully from GNOME.

Add debian-marillat repositories (in the guide). These get you decent multimedia support - libdvdcss[2], w32codecs.

Add Ubuntu Backports (backports.ubuntuforums.org) repositories to your sources -- you'll find lots of nice updates and such.


Azureus.... Hoary now comes with GNOME Bittorrent, but it's still not as good as azureus.

You first need to install Java. You need to grab the updated java-package from Ubuntu Backports. Then, you can directly turn a Sun .bin package into a Ubuntu .deb package and install it.

Azureus will need to be manually unzipped to some central location, like /opt or /usr/bin. I've yet to find a Debian package, and in Hoary I'll work on a package to be included with Ubuntu Backports.

---

### Post by jdodson on 2005-03-01
i do it in waves.  first off add all the repositories: universe, security, multiverse, mailrat(get repo list via [http://www.ubuntuguide.org)](http://www.ubuntuguide.org)).  update the repos then do any security patches.  that usually tides me over for the time being. 

the other waves are generally for what i want to do at the time.  when i want to play a video, i get the w32codecs and then mplayer.  i might change totem to totem-xine too.  dvd playback, then i install libdecss.  rinse, repeat as needed.  

the base ubuntu install takes care of 90% of my daily needs.  firefox, console, ryhtmbox and gaim and gnome games being what i use most often.

"generally" the only repos i add are mailrat.  but sometimes mailrat stuff wont install without a debian repo, so i use those when i need them.  i was not able to get transcode and a few other packages to make dvds without adding the debian repos.

---

### Post by landotter on 2005-03-01
[http://www.ubuntulinux.org/wiki/RestrictedFormats/view?searchterm=mp3](http://www.ubuntulinux.org/wiki/RestrictedFormats/view?searchterm=mp3)

is a good place to start.

I usually just add flash, java, realplayer, gstreamer-mad, xmms, win32 codecs, and totem-xine first thing after an install.

---

### Post by poofyhairguy on 2005-03-01
[QUOTE=monkeymartin]these are the things that I would like to do 

-burn cds/dvds (k3b?)
-watch movies (mplayer xine) 
-play mp3's (XMMS)
-play dvd's 
-p2p (azureus)
-firefox plugins 

I am a gentoo user giving ubuntu a try.  I don't know much about apt/synaptic

what repositories should I add if any?

I know about this guide [http://ubuntuguide.org/](http://ubuntuguide.org/) I am just wondering what you do to tweak your Ubuntu install 

thakns Ubuntu looks great[/QUOTE]

After I install, I whip out the guide and install Java, media codecs, and firefox plugins just like the guide says. But instead of installing Mplayer or Xine-ui I install Gxine (try it, its works great). Make sure you you copy the sources.list from the guide first.

Then I disable IPv6 as it says here:

[http://www.osnews.com/story.php?news_id=9650](http://www.osnews.com/story.php?news_id=9650)

Then I install zsnes, and K3b. In order to run K3B, you must use this command:

gksudo k3b

and it works like a charm.

Then I disable Spatial Nautilus, and I replace the Gnome Foot with the Ubuntu Icon I posted here:

[http://www.ubuntuforums.org/showthread.php?t=6457&highlight=gnome+foot](http://www.ubuntuforums.org/showthread.php?t=6457&highlight=gnome+foot)

Finally, I prelink everything to make it go faster. Directions here:

[http://www.ubuntuforums.org/showpost.php?p=9864&postcount=80](http://www.ubuntuforums.org/showpost.php?p=9864&postcount=80)

EDIT: I forgot to add that I also add the backport repo. New apps rock!

---

