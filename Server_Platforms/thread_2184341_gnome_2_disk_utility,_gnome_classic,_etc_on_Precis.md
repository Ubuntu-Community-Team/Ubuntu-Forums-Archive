---
title: "gnome 2 disk utility, gnome classic, etc on Precise server (12.04 LTS)"
date: 2013-10-28
forum: Server Platforms
---

### Post by bradn on 2013-10-28
BACKGROUND
I started my home media server on Ubuntu 10.04 (file and video sharing to macs, pcs, tivo, Apple TV running xbmc, Time Machine and PC backups).  built out a couple of raid arrays and got everything working smoothly (netatalk, smbd, avahi, rsync, ffmpeg, mysql, etc).  I also installed gnome-desktop so I could use nautilus, palimpsest (Gnome Disk), handbrake gui, grsync and kmttg (tivo download manager).  palimpsest was particularly awesome because if had some really nice raid support support.

[IMG]https://dl.dropboxusercontent.com/u/783836/gnome2%20raid%20disk%20utily%20and%20server%20UI.png[/IMG]

CURRENT SITUATION
I upgraded to 12.04 LTS a few months back.  Unfortunately I lost some functionality in the process.  I was particularly disappointed in the functionality regression with gnome disk as all of the raid monitoring bits had been dropped.  So I've been trying to setup a gnome desktop environment that is compatible with the gnome 2 disk utility.    I tried getting basic gnome shell running with [these instructions.]("http://linux-software-news-tutorials.blogspot.com.es/2012/04/totally-remove-unity-from-ubuntu-1204.html")  Unfortunately gdm segfaults during startup and the desktop never comes up.  I've worked around it for now by reinstalling lightdm and some basic unity bits.  I really can't stand Unity though, and this is a server.

MY QUESTION
Anyone have any suggestions on which path I should take until gnome-disk releases a feature complete version with all the raid functionality?  I assume I can't run the gnome 2 'raid capable' version of palimpsest / gnome disk with gnome 3 and gnome classic.  but maybe I'm wrong.

---

### Post by tgalati4 on 2013-10-28
Linux Mint Mate is a fork of Gnome2 so presumably gnome2 utilities should run.  It is definitely a pain when you upgrade and lose functionality at the same time.

It sounds like you had a decent home media setup.  Let us know what works and what doesn't under 12.04.  Do you have a link for AppleTV running XBMC?

---

### Post by bradn on 2013-10-28
> **tgalati4 said:**
> Linux Mint Mate is a fork of Gnome2 so presumably gnome2 utilities should run.  It is definitely a pain when you upgrade and lose functionality at the same time.

Interesting.  I love Mint on the Desktop!  didn't realize they'd forked Gnome2.  So looks like I'll need to do some more digging there about running Gnome2 apps with a Gnome3 setup.  If it works I'll switch to Gnome 3..

> **tgalati4 said:**
> It sounds like you had a decent home media setup.  Let us know what works and what doesn't under 12.04.  Do you have a link for AppleTV running XBMC?

XBMC on ATV2 ran really well with the old AppleTV UI (AppleTV 4.4 and earlier).  You can centralize all the library data on a mysql server which is just great.  You can still jailbreak to AppleTV 5.3 as of this writing (though not much longer I suspect).  Unfortunately the new release 12 of XBMC (Frodo) doesn't work well.  If you like a nice UI you will definitely be disappointed.  Trying to figure out how to run the earlier release on 5.3 now.

---

