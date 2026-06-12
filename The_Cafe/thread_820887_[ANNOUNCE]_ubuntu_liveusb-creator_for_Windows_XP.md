---
title: "[ANNOUNCE] ubuntu liveusb-creator for Windows XP"
date: 2008-06-06
forum: The Cafe
---

### Post by hjt4vdr on 2008-06-06
hi,

i created a sidux liveusb-creator fork which also works with ubuntu,
based on the very good work from Luke Macken, Kushal Das (Red Hat/Fedora)
Luke and Kushal thank you very much!
[https://fedorahosted.org/liveusb-creator](https://fedorahosted.org/liveusb-creator) 

You can install both iso's, ubuntu and sidux, if you have a pen >= 2GB, but if you will do this, the first iso must be ubuntu, the second sidux.

read more here:
[http://sidux.com/PNphpBB2-viewtopic-t-10929.html](http://sidux.com/PNphpBB2-viewtopic-t-10929.html)

[IMG]http://maledivenhilfe.com/liveusb-creator/screenshot/create%20new.jpg[/IMG]

Have fun!
Horst

---

### Post by fatality_uk on 2008-06-06
If I had a machine running Windows in the house, or at work, might be useful :D

---

### Post by JT9161 on 2008-06-06
*Looks at the Live USB drive that I made a couple hours ago using Pen Drive Linux instructions*  
Once again my luck proves itself.

I'll give this a try latter and see how it works.

---

### Post by JT9161 on 2008-06-08
Tried it on my dads XP home machine, Both the fedora and Sidux creator  gave me a "couldn't find Live OS " error message after ISO extraction with a Ubuntu 8.04 ISO

---

### Post by hjt4vdr on 2008-06-09
> **JT9161 said:**
> Tried it on my dads XP home machine, Both the fedora and Sidux creator  gave me a "couldn't find Live OS " error message after ISO extraction with a Ubuntu 8.04 ISO

hi,

you tried version 003?

can you post syslinux.cfg pls.
```
default vesamenu.c32
timeout 150

menu background splash.jpg
menu title Welcome to sidux!
menu color border 0 #ffffffff #00000000
menu color sel 7 #ffffffff #ff777777
menu color title 0 #ffffffff #00000000
menu color tabmsg 0 #ffffffff #00000000
menu color unsel 0 #ffffffff #00000000
menu color hotsel 0 #ff000000 #ffffffff
menu color hotkey 7 #ffffffff #ff000000
menu color timeout_msg 0 #ffffffff #00000000
menu color timeout 0 #ffffffff #00000000
menu color cmdline 0 #ffffffff #00000000

label sidux i686
  menu label sidux i686
  menu default
  kernel boot/vmlinuz0
  append initrd=boot/initrd0.img boot=fll quiet vga=791 fromiso=sidux/sidux.iso persist=sidux/sidux.img nointro 
```

which files are in the boot and sidux folder?

```
E:\boot
09.06.2008  13:39    <DIR>          .
09.06.2008  13:39    <DIR>          ..
04.06.2008  00:35         7.202.459 initrd0.img
04.06.2008  00:35         1.791.520 vmlinuz0
```

```
E:\sidux

09.06.2008  13:39    <DIR>          .
09.06.2008  13:39    <DIR>          ..
09.06.2008  13:40       469.266.432 sidux.iso
09.06.2008  13:40       113.246.208 sidux.img
```

---

### Post by splitsch on 2008-06-15
Hello !
Could you tell us if you're planning on doing this tools for linux ?
Like a *.sh or somthing...because, uunfortunately, I don't have windows ;)

Or, could you tell what change you made to the original sources, so I could build something for linux.
I'm not really good at this, but I'd really like to give it a shot !

Thanks !

Splitsch

---

### Post by hjt4vdr on 2008-06-16
> **splitsch said:**
> Hello !
Could you tell us if you're planning on doing this tools for linux ?
Like a *.sh or somthing...because, uunfortunately, I don't have windows ;)

Or, could you tell what change you made to the original sources, so I could build something for linux.
I'm not really good at this, but I'd really like to give it a shot !

Thanks !

Splitsch

hi,

download last sidux, start the livecd and use
**install-usb-gui.bash**  for gui installation or
**fll-iso2usb** for terminal
[http://svn.berlios.de/wsvn/fullstory/fll-installer/trunk/fll-iso2usb](http://svn.berlios.de/wsvn/fullstory/fll-installer/trunk/fll-iso2usb)
#--------------------------------------------------------------
# functions
#--------------------------------------------------------------
usage()
{
        echo ""
        echo "Create an fromiso (frugal) installation on a USB drive"
        echo ""
        echo "-d|--debug                     debug sh code execution"
        echo "-D|--drive </dev/sdX>          name of device where to install the \"fromiso\""
        echo "-n|--noformat                  do not format partition"
        echo "-f|--format vfat|ext2|ext3     format partition with given filesystem"
        echo "-p|--persist                   use cheatcode persist"
        echo "-h|--help                      print this help"
        echo "-I|--iso   <iso_file>          iso file name to be installed"
        echo "-t|--test                      copy everything but do not copy the iso"
        echo ""
        echo "Everything after -- will be appended to the kernel cmdline of grub menu.lst"
        echo ""
        echo "Use it at your own risk, it comes without any warranty."
        echo ""

---

### Post by tuxcantfly on 2008-06-24
> **splitsch said:**
> Hello !
Could you tell us if you're planning on doing this tools for linux ?
Like a *.sh or somthing...because, uunfortunately, I don't have windows ;)

Or, could you tell what change you made to the original sources, so I could build something for linux.
I'm not really good at this, but I'd really like to give it a shot !

Thanks !

Splitsch

My own, earlier tool, [UNetbootin](http://unetbootin.sourceforge.net/), can create liveUSB installs for Ubuntu and most other mainstream distros. It can run from both Windows or Linux. You can obtain it at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) I have a guide here on the forums at [http://ubuntuforums.org/showthread.php?t=811397](http://ubuntuforums.org/showthread.php?t=811397) and an earlier one at [http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)

To anyone interested, here's a screenshot of [UNetbootin](http://unetbootin.sourceforge.net/) running on Ubuntu (Fedora and other Linux distributions are supported as well):

[img]http://sourceforge.net/dbimage.php?id=173791[/img]

And a screenshot of [UNetbootin](http://unetbootin.sourceforge.net/) on Windows Vista (Windows 2000, XP, and newer are also supported)

[img]http://sourceforge.net/dbimage.php?id=167328[/img]

By the way, looking at that liveusb-creator screenshot, the user interface looks remarkably similar to some earlier versions of my own application. The toolkit (Qt4) and approach used (bundled in 7-zip and syslinux via QResource to extract ISO and install bootloader) are also the same; disregarding syntactical differences between Python (liveusb-creator) and C++ (UNetbootin), even the code looks similar. Looking at the git history logs, it appears that the first commit was made in February, shortly after UNetbootin made the frontpage of Linux.com, Digg, and a variety of other tech sites in January. Just wondering (not pointing fingers or anything; I'm fully aware that the GPL allows for nearly unrestricted forking; just curious), does anyone close with the liveusb-creator project know whether liveusb-creator was forked from or based on UNetbootin, because it certainly appears to be, though I didn't find any info saying so?

---

### Post by sharks on 2008-06-24
its not useful for me as i dont have windows.

---

### Post by papsynot on 2008-08-07
> **tuxcantfly said:**
> 
By the way, looking at that liveusb-creator screenshot, the user interface looks remarkably similar to some earlier versions of my own application. The toolkit (Qt4) and approach used (bundled in 7-zip and syslinux via QResource to extract ISO and install bootloader) are also the same; disregarding syntactical differences between Python (liveusb-creator) and C++ (UNetbootin), even the code looks similar. Looking at the git history logs, it appears that the first commit was made in February, shortly after UNetbootin made the frontpage of Linux.com, Digg, and a variety of other tech sites in January. Just wondering (not pointing fingers or anything; I'm fully aware that the GPL allows for nearly unrestricted forking; just curious), does anyone close with the liveusb-creator project know whether liveusb-creator was forked from or based on UNetbootin, because it certainly appears to be, though I didn't find any info saying so?

No, the liveusb-creator is not a fork of UNetbootin.  The code is much better.

---

### Post by moycano on 2008-08-21
I test the liveusb-creator fork posted by **hjt4vdr**, and must say I finally got a persistent GNU/linux distro running from my flash drive after days of line commands and even others graphical assistants!

It work both with *Xubuntu Hardy *and *sidux erebos *but since I cant get a custom desktop environment (honestly, the default *xfce *setup isn't much practical) I may prefer stick to *Xubuntu*.

And is refreshing to see a distro with that much documentation _included_ (because I first try in a laptop without web connection). This debian brad worth to keep an eye on.

UPDATE: **The program can't complete the process if the folder has a long name.**

---

