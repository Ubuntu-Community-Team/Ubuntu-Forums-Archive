---
title: "Xubuntu 8.10 Tascam US122L Install help!!!"
date: 2009-04-25
forum: Ubuntu Studio
---

### Post by mistercreamer on 2009-04-25
Hello All,

I normally dont "ever" have the need to start a thread to get help on any topic, because I normally just google the crap out of what ever I need to know, BUT it seems that I have finally hit that brickwall where I cant make heads or tails of the situation(Label me a NOOB). 

I have a HP Pavilion zd8000 Labtop that I used for music creation and engineering (in windows), I started saving up to by a MacBook Pro because windows is just horriable. I tried out Xubuntu and the look and feel it wonderfull. I have installed Audour2 and it works great with my Labtop's built-in card, but for the life of me I cant get it to even see that my Mbox 2 Pro or my Tascam US122L is plugged in.

The green light is on and I have tried a crap load of walk thru's to install but Jack never see's it.

I have tried
[http://alsa.opensrc.org/Tascam_US-122](http://alsa.opensrc.org/Tascam_US-122)
[http://ubuntuforums.org/showthread.php?t=431066](http://ubuntuforums.org/showthread.php?t=431066)
and lastly
[http://ubuntuforums.org/showthread.php?t=1030139](http://ubuntuforums.org/showthread.php?t=1030139)

I dont want to pay over $2,000 for a new computer and I certainly dont want to go back to Windows. PLEASE HELP:confused:

---

### Post by mistercreamer on 2009-04-25
while following the AlsaProject walk thru

I got the error

root@BlueDemonLinux:/home/mistercreamer# aplay -D default test.wav
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
aplay: main:583: audio open error: Device or resource busy

and now I am even more confused

---

### Post by mistercreamer on 2009-04-25
root@BlueDemonLinux:/home/mistercreamer# apt-get install alsa-firmware alsa-firmware-loaders
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsa-firmware

am I looking for the wrong filename?

---

### Post by mistercreamer on 2009-04-25
from [http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux)
from the install kernel part.
sudo apt-get install build-essential debhelper kernel-package libncurses5-dev fakeroot linux-headers-2.6.27 linux-source-2.6.27
is actually 
sudo apt-get install linux-source <press enter>

otherwise you get

root@BlueDemonLinux:/usr/src# apt-get install build-essential debhelper kernel-package libncurses5-dev fakeroot linux-headers-2.6.27 linux-source-2.6.27
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
debhelper is already the newest version.
kernel-package is already the newest version.
libncurses5-dev is already the newest version.
fakeroot is already the newest version.
E: Couldn't find package linux-headers-2.6.27

rather than 

root@BlueDemonLinux:/usr/src# apt-get install linux-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  quilt libasound2-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-source-2.6.27
Suggested packages:
  libqt3-dev
The following NEW packages will be installed:
  linux-source linux-source-2.6.27
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 52.0MB of archives.
After this operation, 52.2MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main linux-source-2.6.27 2.6.27-11.31 [52.0MB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main linux-source 2.6.27.11.14 [2876B]
Fetched 52.0MB in 12min24s (69.9kB/s)                                                 
Selecting previously deselected package linux-source-2.6.27.
(Reading database ... 118921 files and directories currently installed.)
Unpacking linux-source-2.6.27 (from .../linux-source-2.6.27_2.6.27-11.31_all.deb) ...
Selecting previously deselected package linux-source.
Unpacking linux-source (from .../linux-source_2.6.27.11.14_all.deb) ...
Setting up linux-source-2.6.27 (2.6.27-11.31) ...
Setting up linux-source (2.6.27.11.14) ...

---

### Post by mistercreamer on 2009-04-25
Okay now I am stuck again.....


here is the Terminal command
sudo patch -p1 < ../us122l-patches_2.6.27/ehci-hcd_2.6.27.patch

here is the error

ls
arch     debian         include  kernel-versions  modules         samples   usr
block    Documentation  init     lib              net             scripts   virt
COPYING  drivers        ipc      MAINTAINERS      package-list    security
CREDITS  firmware       Kbuild   Makefile         README          sound
crypto   fs             kernel   mm               REPORTING-BUGS  ubuntu
root@BlueDemonLinux:/usr/src/linux# sudo patch -p1 < ../us122l-patches_2.6.27/ehci-hcd_2.6.27.patch
bash: ../us122l-patches_2.6.27/ehci-hcd_2.6.27.patch: No such file or directory
root@BlueDemonLinux:/usr/src/linux# 

what does -pl do?
and whats with the "<../" before the "/us122l-patches_2.6.27/ehci-hcd_2.6.27.patch"
I am not sure if I should manually try to download the us122l patches and created these folders or should they already be there?

IF THERE IS A GOD SOMEONE PLEASE HELP

---

### Post by mistercreamer on 2009-04-25
so I have made some progress but now when I use the command

root@BlueDemonLinux:/usr/src/us122l-patches_2.6.27# sudo patch -p1 < ../us122l-patches_2.6.27/ehci-hcd_2.6.27.patch

I get:

root@BlueDemonLinux:/usr/src/us122l-patches_2.6.27# sudo patch -p1 < ../us122l-patches_2.6.27/ehci-hcd_2.6.27.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -uNrp kernel-2.6.27.old/drivers/usb/host/ehci.h kernel-2.6.27.new/drivers/usb/host/ehci.h
|--- kernel-2.6.27.old/drivers/usb/host/ehci.h    2008-11-15 21:00:58.000000000 +0100
|+++ kernel-2.6.27.new/drivers/usb/host/ehci.h    2008-11-15 21:02:51.000000000 +0100
--------------------------
File to patch:

ummmmm where did I go wrong?

---

### Post by mistercreamer on 2009-04-25
okay so I think I was just using the wrong dir

but after I put in the command: "sudo make menuconfig" and follow the steps to get to the tascam usb driver install part and I try to change it from "M" to yes

" .config - Linux Kernel v2.6.27.10 Configuration
 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; USB sound devices &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
  &#9474;  Arrow keys navigate the menu.  <Enter> selects submenus --->.          &#9474;  
  &#9474;  Highlighted letters are hotkeys.  Pressing <Y> includes, <N> excludes, &#9474;  
  &#9474;  <M> modularizes features.  Press <Esc><Esc> to exit, <?> for Help, </> &#9474;  
  &#9474;  for Search.  Legend: 
[*] built-in  [ ] excluded  <M> module  < >       &#9474;  
  &#9474; &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488; &#9474;  
  &#9474; &#9474;    --- USB sound devices                                            &#9474; &#9474;  
  &#9474; &#9474;    <M>   USB Audio/MIDI driver                                      &#9474; &#9474;  
  &#9474; &#9474;    <M>   Tascam US-122, US-224 and US-428 USB driver                &#9474; &#9474;  
  &#9474; &#9474;    <M>   Native Instruments USB audio devices                       &#9474; &#9474;  
  &#9474; &#9474;    
[*]     enable input device for controllers                      &#9474; &#9474;  
  &#9474; &#9474;    < >   Tascam US-122L USB driver (NEW)    "

I get the error of 
This feature depends on another which has been configured as a module. &#9474;  
   &#9474; As a result, this feature will be built as a module.                   &#9474;  
   &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;(100%)&#9472;&#9472;&#9508;  
   &#9474;                                < Exit >      
 

so what do I do need?

---

### Post by federicobriata on 2009-10-23
Hi!

try to follow my note here [http://wiki.briata.org](http://wiki.briata.org)

you need to follow in total 4 step for
patching, compiling and file editing.

The Step2 differ from kernel/distribution version, there you have to
make a choise and do one of this case explained in step 2.
Please look at the menu on top of the page, it should show you the way
how to do.


If you have problem with step2, as i
wrote in [http://wiki.briata.org/doku.php#ubuntu](http://wiki.briata.org/doku.php#ubuntu) you can decide to just install all package located here [http://pub.briata.org/us-122l/](http://pub.briata.org/us-122l/) for 8.10 look in intrepid-2.6.27

or

another alternative is to install latest ubuntu stable version, now is 9.04, or try the new 9.10 beta, I think this should be the best for you.

Once more, from Ubuntu 9.04 you don't need any external package, because everything has been integrated

Anyway, if you decide to use my package or upgrade to more fresh
ubuntu, you can skip only step3 on note.

Hope to be helpful,
please let me know your progress.

federico

---

