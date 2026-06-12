---
title: "weird apt errors on a clean install."
date: 2010-01-01
forum: System76 Support
---

### Post by xakh on 2010-01-01
```
xakh@WarMachine:~$ sudo apt-get install memaker
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nvidia-185-libvdpau
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgtksourceview-common
  libgtksourceview1.0-0 libnautilus-burn4 python-bugbuddy python-evince
  python-evolution python-gnome2-desktop python-gnomedesktop python-gnomeprint
  python-gtksourceview python-gtop python-mediaprofiles python-metacity
  python-nautilusburn python-totem-plparser python-wnck
Suggested packages:
  gnome-mount bug-buddy python-gnome2-desktop-doc python-gnome2-desktop-dbg
The following NEW packages will be installed:
  libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgtksourceview-common
  libgtksourceview1.0-0 libnautilus-burn4 memaker python-bugbuddy
  python-evince python-evolution python-gnome2-desktop python-gnomedesktop
  python-gnomeprint python-gtksourceview python-gtop python-mediaprofiles
  python-metacity python-nautilusburn python-totem-plparser python-wnck
0 upgraded, 22 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1,849kB of archives.
After this operation, 15.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic/main libgnomecups1.0-1 0.2.3-3build1 [32.4kB]
Get:2 http://us.archive.ubuntu.com karmic/main libgnomeprint2.2-data 2.18.6-1build1 [46.9kB]
Get:3 http://us.archive.ubuntu.com karmic/main libgnomeprint2.2-0 2.18.6-1build1 [237kB]
Get:4 http://us.archive.ubuntu.com karmic/main libgnomeprintui2.2-common 2.18.4-1 [7,372B]
Get:5 http://us.archive.ubuntu.com karmic/main libgnomeprintui2.2-0 2.18.4-1 [118kB]
Get:6 http://us.archive.ubuntu.com karmic/main libgtksourceview-common 1.8.5-2 [60.4kB]
Get:7 http://us.archive.ubuntu.com karmic/main libgtksourceview1.0-0 1.8.5-2 [95.3kB]
Get:8 http://us.archive.ubuntu.com karmic/main libnautilus-burn4 2.25.3-0ubuntu3 [51.4kB]
Get:9 http://us.archive.ubuntu.com karmic/main python-bugbuddy 2.28.0-0ubuntu1 [30.2kB]
Get:10 http://us.archive.ubuntu.com karmic/main python-evince 2.28.0-0ubuntu1 [55.0kB]
Get:11 http://us.archive.ubuntu.com karmic/main python-evolution 2.28.0-0ubuntu1 [95.4kB]
Get:12 http://us.archive.ubuntu.com karmic/main python-gnomedesktop 2.28.0-0ubuntu1 [50.3kB]
Get:13 http://us.archive.ubuntu.com karmic/main python-gnomeprint 2.28.0-0ubuntu1 [114kB]
Get:14 http://us.archive.ubuntu.com karmic/main python-gtksourceview 2.28.0-0ubuntu1 [81.4kB]
Get:15 http://us.archive.ubuntu.com karmic/main python-gtop 2.28.0-0ubuntu1 [52.3kB]
Get:16 http://us.archive.ubuntu.com karmic/main python-mediaprofiles 2.28.0-0ubuntu1 [36.6kB]
Get:17 http://us.archive.ubuntu.com karmic/main python-metacity 2.28.0-0ubuntu1 [52.9kB]
Get:18 http://us.archive.ubuntu.com karmic/main python-nautilusburn 2.28.0-0ubuntu1 [54.0kB]
Get:19 http://us.archive.ubuntu.com karmic/main python-totem-plparser 2.28.0-0ubuntu1 [38.6kB]
Get:20 http://us.archive.ubuntu.com karmic/main python-wnck 2.28.0-0ubuntu1 [69.7kB]
Get:21 http://us.archive.ubuntu.com karmic/main python-gnome2-desktop 2.28.0-0ubuntu1 [29.5kB]
Get:22 http://us.archive.ubuntu.com karmic/universe memaker 1.5-0ubuntu4 [441kB]
Fetched 1,849kB in 4s (415kB/s)  
Selecting previously deselected package libgnomecups1.0-1.
(Reading database ... 274373 files and directories currently installed.)
Unpacking libgnomecups1.0-1 (from .../libgnomecups1.0-1_0.2.3-3build1_amd64.deb) ...
Selecting previously deselected package libgnomeprint2.2-data.
Unpacking libgnomeprint2.2-data (from .../libgnomeprint2.2-data_2.18.6-1build1_all.deb) ...
Selecting previously deselected package libgnomeprint2.2-0.
Unpacking libgnomeprint2.2-0 (from .../libgnomeprint2.2-0_2.18.6-1build1_amd64.deb) ...
Selecting previously deselected package libgnomeprintui2.2-common.
Unpacking libgnomeprintui2.2-common (from .../libgnomeprintui2.2-common_2.18.4-1_all.deb) ...
Selecting previously deselected package libgnomeprintui2.2-0.
Unpacking libgnomeprintui2.2-0 (from .../libgnomeprintui2.2-0_2.18.4-1_amd64.deb) ...
Selecting previously deselected package libgtksourceview-common.
Unpacking libgtksourceview-common (from .../libgtksourceview-common_1.8.5-2_all.deb) ...
Selecting previously deselected package libgtksourceview1.0-0.
Unpacking libgtksourceview1.0-0 (from .../libgtksourceview1.0-0_1.8.5-2_amd64.deb) ...
Selecting previously deselected package libnautilus-burn4.
Unpacking libnautilus-burn4 (from .../libnautilus-burn4_2.25.3-0ubuntu3_amd64.deb) ...
Selecting previously deselected package python-bugbuddy.
Unpacking python-bugbuddy (from .../python-bugbuddy_2.28.0-0ubuntu1_all.deb) ...
Selecting previously deselected package python-evince.
Unpacking python-evince (from .../python-evince_2.28.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package python-evolution.
Unpacking python-evolution (from .../python-evolution_2.28.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package python-gnomedesktop.
Unpacking python-gnomedesktop (from .../python-gnomedesktop_2.28.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package python-gnomeprint.
Unpacking python-gnomeprint (from .../python-gnomeprint_2.28.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package python-gtksourceview.
Unpacking python-gtksourceview (from .../python-gtksourceview_2.28.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package python-gtop.
Unpacking python-gtop (from .../python-gtop_2.28.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package python-mediaprofiles.
Unpacking python-mediaprofiles (from .../python-mediaprofiles_2.28.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package python-metacity.
Unpacking python-metacity (from .../python-metacity_2.28.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package python-nautilusburn.
Unpacking python-nautilusburn (from .../python-nautilusburn_2.28.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package python-totem-plparser.
Unpacking python-totem-plparser (from .../python-totem-plparser_2.28.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package python-wnck.
Unpacking python-wnck (from .../python-wnck_2.28.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package python-gnome2-desktop.
Unpacking python-gnome2-desktop (from .../python-gnome2-desktop_2.28.0-0ubuntu1_all.deb) ...
Selecting previously deselected package memaker.
Unpacking memaker (from .../memaker_1.5-0ubuntu4_all.deb) ...
Processing triggers for desktop-file-utils ...
Setting up yiff-server (2.14.5-5.1) ...
Starting Y Sound Server: invoke-rc.d: initscript yiff-server, action "start" failed.
dpkg: error processing yiff-server (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libgnomecups1.0-1 (0.2.3-3build1) ...

Setting up libgnomeprint2.2-data (2.18.6-1build1) ...
Setting up libgnomeprint2.2-0 (2.18.6-1build1) ...

Setting up libgnomeprintui2.2-common (2.18.4-1) ...
Setting up libgnomeprintui2.2-0 (2.18.4-1) ...

Setting up libgtksourceview-common (1.8.5-2) ...
Setting up libgtksourceview1.0-0 (1.8.5-2) ...

Setting up libnautilus-burn4 (2.25.3-0ubuntu3) ...

Setting up python-bugbuddy (2.28.0-0ubuntu1) ...

Setting up python-evince (2.28.0-0ubuntu1) ...

Setting up python-evolution (2.28.0-0ubuntu1) ...

Setting up python-gnomedesktop (2.28.0-0ubuntu1) ...

Setting up python-gnomeprint (2.28.0-0ubuntu1) ...

Setting up python-gtksourceview (2.28.0-0ubuntu1) ...

Setting up python-gtop (2.28.0-0ubuntu1) ...

Setting up python-mediaprofiles (2.28.0-0ubuntu1) ...

Setting up python-metacity (2.28.0-0ubuntu1) ...

Setting up python-nautilusburn (2.28.0-0ubuntu1) ...

Setting up python-totem-plparser (2.28.0-0ubuntu1) ...

Setting up python-wnck (2.28.0-0ubuntu1) ...

Setting up python-gnome2-desktop (2.28.0-0ubuntu1) ...
Setting up memaker (1.5-0ubuntu4) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Errors were encountered while processing:
 yiff-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
I tried to install memaker, a program that makes little faces for use as avatars as an example. It says those errors, and ten it just dies, any ideas on what causes this? I clean installed yesterday, I've moved my old home folder over, but I never got these errors on my machine before.

---

### Post by MelDJ on 2010-01-01
tried sudo dpkg --configure -a?

---

### Post by xakh on 2010-01-01
```
xakh@WarMachine:~$ sudo dpkg --configure -a
Setting up yiff-server (2.14.5-5.1) ...
Starting Y Sound Server: invoke-rc.d: initscript yiff-server, action "start" failed.
dpkg: error processing yiff-server (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 yiff-server

``` That happened.
Edit: I'd like to point out that the install succeeds, but the errors still concern me.

---

### Post by thomasaaron on 2010-01-04
That means that yiff-server (The Y Sound 3D server) didn't install. It would seem that it is a very buggy program...

[http://www.google.com/search?q=Errors+were+encountered+while+processing%3A++yiff-server&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=Errors+were+encountered+while+processing%3A++yiff-server&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

You might try just deleting it altogether with...

sudo apt-get --purge remove yiff-server
sudo apt-get clean
sudo apt-get auto-clean

It doesn't come installed on Ubuntu, so I assume either you installed it, or it was a dependency for some other program you installed.

---

### Post by xakh on 2010-01-04
wonder what depended on it.

---

