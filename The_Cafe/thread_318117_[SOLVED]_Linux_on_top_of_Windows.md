---
title: "[SOLVED] Linux on top of Windows"
date: 2006-12-13
forum: The Cafe
---

### Post by victorbrca on 2006-12-13
Hi all,

  Anyone has any experience on Linux running on top of Windows?

  Found a couple of softwares but not sure which one to go for. It can't be bootOS/liveCD as I need Windows to be running....


[coLinux]("http://www.colinux.org/?section=home")
[Topologilinux]("http://topologi-linux.sourceforge.net/index.php?menu=2")
[Linux Inside Windows]("http://dev.mainsoft.com/Default.aspx?tabid=49")


Appreciate any input!!!


Vic.

---

### Post by yabbadabbadont on 2006-12-13
Back in the day (1996ish), I used to use ZipSlack (Slackware on top of UMSDOS filesystem).  [http://www.slackware.com/zipslack/](http://www.slackware.com/zipslack/)

---

### Post by mjm115 on 2006-12-13
> **victorbrca said:**
> Hi all,

  Anyone has any experience on Linux running on top of Windows?

  Found a couple of softwares but not sure which one to go for. It can't be bootOS/liveCD as I need Windows to be running....


[coLinux]("http://www.colinux.org/?section=home")
[Topologilinux]("http://topologi-linux.sourceforge.net/index.php?menu=2")
[Linux Inside Windows]("http://dev.mainsoft.com/Default.aspx?tabid=49")


Appreciate any input!!!


Vic.

topologilinux is probably what you are looking for.

---

### Post by victorbrca on 2006-12-13
Thanks!!!!  :D

---

### Post by ago on 2006-12-13
AndLinux is also very interesting.

[http://wiki.gp2x.org/wiki/AndLinux](http://wiki.gp2x.org/wiki/AndLinux)

It uses coLinux and it is based on top of Ubuntu. It basically simplifies (A LOT) a coLinux installation of Ubuntu. Solutions based on QEmu perform too poorly to be useful IMO (but DSL embedded is cool nevertheless). 

At the moment my favourite is topologi-linux. In fact I think that Ubuntu should provide a one-click installer that sets-up Ubuntu inside a windows folder without CD-roms, ISOs and repartitioning. Something that can be used in dual-boot, inside an emulator, or dumped into its own dedicated partition. IMO having a simple one click installer would make the use of Ubuntu skyrocket... A mix of andlinux and topologilinux is the way to go to get rid of the ISOs for windows users...

---

### Post by victorbrca on 2006-12-13
Now, just to confirm:

1- AndLinux runs mixed with Windows right? Looks like there's no separation between Windows and Linux programs....

2- The other 4 versions (coLinux, Topologilinux, Linux Inside Windows and ZipSlack) you need to modify boot files right? Also seems that some configuration (like network) are a little complicated...

I ask this because the computer I'll be installing this Linux version is not mine, so I don't wanna screw around with it too much...

It may be better to use VMware.. Not sure..


Vic.

---

### Post by ago on 2006-12-13
> **victorbrca said:**
> 1- AndLinux runs mixed with Windows right? Looks like there's no separation between Windows and Linux programs....
AndLinux uses coLinux. Think of coLinux as an emulator (which is not correct, but will do for now), wich in practice means that it runs the other OS inside a windowed application within windows. The advantage being that you do not have to install Ubuntu from scratch inside coLinux (which is not trivial). You have a nice image created for you and most of the problems associated with coLinux (X server on windows) are solved.

> 2- The other 4 versions (coLinux, Topologilinux, Linux Inside Windows and ZipSlack) you need to modify boot files right?
There is no difference between coLinux and AndLinux (except that with andlinux you are up and running with far less hassle). Linux Inside Windows is based on QEmu so same thing. Topologilinux can be started in dual boot (which requires a modification of the bootloader) or from coLinux (without any need to change the bootloade).

I believe that even with Topologilinux the main bootloader is still the windows one, but Topologilinux modifies boot.ini to add an option to chainload grub-for-windows that in turns loopmounts the linux image file (I might be wrong).

> Also seems that some configuration (like network) are a little complicated...
Qemu networking is simpler but qemu is slower. Colinux is a bit more complicated, that is why you may want to try andlinux, it will get you up and running with far less hassle.

> It may be better to use VMware.. Not sure..
That is also a nice approach, but coLinux is still faster (and completely open source). Make sure to use one of the pre-made images for VMWare

---

### Post by victorbrca on 2006-12-13
Ok you convinced me!! :p   I'll give AndLinux a try!!!


Thanks for the inputs!!! :)


Vic.

---

### Post by ago on 2006-12-13
If you also want to try QEMU the quickest way is to extract DSL-embedded 

[ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/dsl-3.1-embedded.zip](ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/dsl-3.1-embedded.zip) (50MB)

and execute dsl-windows. if you do not like it, just delete the extracted folder.

---

### Post by crispingatiesa on 2006-12-13
U can use MS Virtual PC + any distro. In my case I'm running MSVPc plus DSLinux. I tried Ubuntu instead of DSLinux and althoug runs, is does so using to many resources.

---

### Post by BetaguyGZT on 2006-12-30
After some tinkering around with andLinux (along with a LOT of trial-and-error), I've gotten everything basic working. Full KDE, Gnome, and XFCE happiness. I haven't tried Beryl yet, but I'm pretty hopeful that it **can** be made to work also.

What you need to do is update to the **latest** version of XMing ([found here](http://www.straightrunning.com/XmingNotes/release.php)), change the startup.bat options to -fullscreen rather than -multiwindow, and then you can start whichever window manager you want (after you've installed it in Synaptic). 

I'm still figuring out how to manually change the startup stuff in the Linux side since using the Sessions stuff won't do it (if someone could point me to the file I need to modify that would be great), but in the meantime your desired wm can be started manually using xfrun4. I'm currently using Kwin (since KDE is my environment of choice) -- and other than Styleclock not working (causes a nasty problem with Xming) -- I've had no trouble. I have gotten Gnome working perfectly using XFWM4 as well.

Anyway, lets keep this one alive. I understand that a new version of andLinux is in the works, and hopefully it brings more to the table as far as default settings go.

8)

---

