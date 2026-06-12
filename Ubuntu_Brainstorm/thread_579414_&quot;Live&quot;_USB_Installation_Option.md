---
title: "&quot;Live&quot; USB Installation Option"
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by Ceemee on 2007-10-18
And by the I mean the ability to install a "LIVE" Ubuntu installation on a thumb drive or USB Hard drive, that will retain changes in GUI configuration, etc.   but will still detect hardware and install correct drivers on boot.

While this option will not be for everyone, it would make it much easier to install to a USB device and get to keep your work and settings across many computers.

Addition-  Maybe during boot-up it would try a "Last Known good Config" before doing a standard detection.  If it works, it continues bootup, if not, it falls back to a hardware-detection scheme. This way if your re-booting on the same hardware, you will have a quicker boot time -VS- re-detecting EVERY single time.

---

### Post by Taku on 2007-10-18
yes, yes, yes and still yes !

I've been asking for this for 2 years !

we MUST be able to have a carriable version of Ubuntu. And with all advantages of USB HDD device : 
- Profiles
- Auto-adaptation of the distro to the host

It's time to do this, the major problem we had for this problem was Xorg, which was making difficult the "in the flight" configuration of the display driver and display configuration : now we can do that !

More, the possibility to "encrypt"  the filesystem is a great thing that could be used here.

More, the USB "Live" Ubuntu would be just AS a standard install, since the cdrom device is not occupied.

USB flash and USB HDD are faster than cdroms, and, more, they leave the computer just as if you were running a "standard" ubuntu installed version, except for one usb slot.
This is just a must-have !

---

### Post by X-dark on 2007-10-18
Good idea but it may be slow if it runs from the key.

---

### Post by Taku on 2007-10-18
Can't be as slow as a cdrom :)

---

### Post by X-dark on 2007-10-18
Yes that's true.

But what I meant is I used firefox and thunderbird installed in my usb key (for windows) and that was really slow to read all the data and to write them. So it was not very usable.
But on the other hand today USB Key become faster and more reliable so this can be feasible.

---

### Post by ankursethi on 2007-10-18
I've used PCLinuxOS on a USB. Trust me, it feels just like a normal system.

---

### Post by smartboyathome on 2007-10-18
I wouldn't say it would be a high priority, but I would like it.

---

### Post by Awalton on 2007-10-18
File a Blueprint, then attach this:
[http://git.fedoraproject.org/?p=hosted/livecd](http://git.fedoraproject.org/?p=hosted/livecd)

Fedora's and Ubuntu's LiveCD format (are/should be/might be) similar enough to use their tools as-is, but in case they're not it might need a few touchups. The particular one you're looking for, if you want to test this yourself, is "creator-isotostick.sh". The major requirement is a thumbdrive with the amount of space required (a 1GB drive or better).

---

### Post by notna01 on 2007-10-18
Ive had it on my usb drives for ages.... all you have to do is installl it on it, then restart your pc and go into the bios and set it so usb disks are counted as bootable harddisks.

Also: It takes about 3mins to boot, but otherwise it is fast......

---

### Post by Zdravko on 2007-10-18
Nice idea.

---

### Post by DizzyTech on 2007-10-18
The only problem with slowness would be using a system with USB 1.0 instead of 2.0, but V2 is commonplace now.

---

### Post by bethaviv on 2007-10-18
I'm all for a USB Ubuntu =)

It would save me a bunch of time when I work on my friend's computers.

---

### Post by Ceemee on 2007-10-19
> **notna01 said:**
> Ive had it on my usb drives for ages.... all you have to do is installl it on it, then restart your pc and go into the bios and set it so usb disks are counted as bootable harddisks.

Also: It takes about 3mins to boot, but otherwise it is fast......

Yes, that is currently what I do as well.  

The difference between what that and this idea is this -

Try and plug your USB drive with Ubuntu installed into any other computer, it will not work.  The installation expects certain hardware to be there, so it doenst detect hardware, it just loads drivers for what it expects to be there.

This idea would allow you to select a "LIVE" installation, that would change the way the USB Ubuntu would boot to have it Auto-Detect the hardware every time on boot-up.  This way you can use it on multiple computers with different hardware configs, while still keeping your GUI settings, files, and everything with you.

---

### Post by Ceemee on 2007-10-19
Expanded idea for using a "last known good config" before auto-detection of hardware.

---

### Post by carac on 2007-10-19
> **Ceemee said:**
> And by the I mean the ability to install a "LIVE" Ubuntu installation on a thumb drive or USB Hard drive, that will retain changes in GUI configuration, etc.   but will still detect hardware and install correct drivers on boot.

While this option will not be for everyone, it would make it much easier to install to a USB device and get to keep your work and settings across many computers.

Addition-  Maybe during boot-up it would try a "Last Known good Config" before doing a standard detection.  If it works, it continues bootup, if not, it falls back to a hardware-detection scheme. This way if your re-booting on the same hardware, you will have a quicker boot time -VS- re-detecting EVERY single time.



I subscribe to this !!!

---

### Post by Zdravko on 2007-10-19
Nice idea.

---

### Post by aamukahvi on 2007-10-20
Here's the script with touchups:
[http://janimo.blogspot.com/2007/10/live-cd-on-usb-key.html](http://janimo.blogspot.com/2007/10/live-cd-on-usb-key.html)

EDIT: I just tried it, works like a charm! :) I had a Mandriva LiveUSB stick (2GB) lying around. I partitioned it 700MiB/1.24GiB (both FAT32), formatted the partitions and used the script.
EDIT2: No persistence though...

---

### Post by kurrier on 2007-10-20
Best way for Live USB: [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/")

On USB 2.0 runs fast enough to run as normal os, or could simply do a quick install to the hd. Ubuntu should really adopt those directions and just sell the distro on flash drives.

---

### Post by Zdravko on 2007-10-20
It would be cool to see it working!

---

### Post by Joshua R. on 2007-10-31
I tried to install ubuntu on my 2 gig thumb drive, and it stopped during the partitioning stage and I think that it ran out of room. but now I cannot use the thumbdrive. I have deleted the partitions, and now it wont even "mount" the drive (says something about not having the media in the drive [which is valid for an optical drive or a card reader, but not a thumbdrive like mine]). is there any way of making my drive usable again?

---

### Post by smartboyathome on 2007-10-31
> **Joshua R. said:**
> I tried to install ubuntu on my 2 gig thumb drive, and it stopped during the partitioning stage and I think that it ran out of room. but now I cannot use the thumbdrive. I have deleted the partitions, and now it wont even "mount" the drive (says something about not having the media in the drive [which is valid for an optical drive or a card reader, but not a thumbdrive like mine]). is there any way of making my drive usable again?

You have to make a new partition on the drive (i use gparted for this) and then it will mount. Btw, try [pendrivelinux's]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") guide to installing Gutsy on a usb drive. Worked for me! :)

---

### Post by Joshua R. on 2007-11-03
> **smartboyathome said:**
> You have to make a new partition on the drive (i use gparted for this) and then it will mount. Btw, try [pendrivelinux's]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") guide to installing Gutsy on a usb drive. Worked for me! :)

thanks! it worked great! (I used the disk manager in windows vista)

---

### Post by spanella47 on 2007-12-06
Ubuntu should offer a convenient way to install Ubuntu to a USB drive and from a USB drive.

To avoid burning a cd every time i upgrade Ubuntu (prefer clean installs, everything runs so much smoother) I found a tutorial and installed onto a USB stick in persistent mode, booted from USB, and re-installed Ubuntu.  However it was a hell of an operation and it took me forever to figure out why my usb drive wouldnt mount anymore after the upgrade...had to do with ubuntu treating it as a cd during install.

have heard of a netboot install but it looked just as hassle filled.  Since more small computers are coming without cd drives, alternate install methods are becoming more crucial.

Ubuntu should create an installer for USB drives that will also cleanly install the other way OR an installer for an easy netboot.

---

### Post by smartboyathome on 2007-12-07
> **spanella47 said:**
> Ubuntu should offer a convenient way to install Ubuntu to a USB drive and from a USB drive.

To avoid burning a cd every time i upgrade Ubuntu (prefer clean installs, everything runs so much smoother) I found a tutorial and installed onto a USB stick in persistent mode, booted from USB, and re-installed Ubuntu.  However it was a hell of an operation and it took me forever to figure out why my usb drive wouldnt mount anymore after the upgrade...had to do with ubuntu treating it as a cd during install.

have heard of a netboot install but it looked just as hassle filled.  Since more small computers are coming without cd drives, alternate install methods are becoming more crucial.

Ubuntu should create an installer for USB drives that will also cleanly install the other way OR an installer for an easy netboot.

Is this really necessary? The 1GB usb drive is still the most abundant, so it wouldn't work very well (trust me, I tried...).

---

### Post by ppibburr on 2007-12-07
Tool to practically automatically partition, format, install, make bootable a usb flash disk

can help detect the device if needed

from running the live cd 
         - or - 
a local iso file


Command Line and Graphical User, Interfaces

Gui is simple, effective, clean

[http://belemu.netfirms.com/ubuntu_pen.tar](http://belemu.netfirms.com/ubuntu_pen.tar)
[http://belemu.netfirms.com/readme](http://belemu.netfirms.com/readme)
[http://belemu.netfirms.com/snapshot6.png](http://belemu.netfirms.com/snapshot6.png)

---

### Post by ppibburr on 2007-12-07
The above post:

use this link instead of what is posted

[http://belemu.netfirms.com/ubuntu_pen.html](http://belemu.netfirms.com/ubuntu_pen.html)

---

### Post by smartboyathome on 2007-12-07
> **ppibburr said:**
> The above post:

use this link instead of what is posted

[http://belemu.netfirms.com/ubuntu_pen.html](http://belemu.netfirms.com/ubuntu_pen.html)

NICE! Now if only there was a live version of Ubuntu-minimal so I could install that + e17 on it. :)

---

### Post by ppibburr on 2007-12-08
my greater aim is a app that makes a live image of your hosted enviroment, then use the above app to put it on a usb key

---

### Post by YoDaddeh on 2007-12-08
Do you suppose instead of sending out Cd's as install or Live media, you could end up sending branded Ubuntu Thumbdrives?

Just another Idea that goes along with it. (sorry if its already been said. Didn't really skim the topic for that long before posting)

---

### Post by smartboyathome on 2007-12-08
> **ppibburr said:**
> my greater aim is a app that makes a live image of your hosted enviroment, then use the above app to put it on a usb key

The two pieces for this puzzle are already in place (remastersys 2 and this). You should be able to make an image of your environment and then use that image to make a livecd. :)

> **YoDaddeh said:**
> Do you suppose instead of sending out Cd's as install or Live media, you could end up sending branded Ubuntu Thumbdrives?

Just another Idea that goes along with it. (sorry if its already been said. Didn't really skim the topic for that long before posting)

This could be done (possibly even by canonical) to raise money for Ubuntu, and LiveUSBs becoming even bigger will let people install more on it while saving their prefs.

---

### Post by YoDaddeh on 2007-12-08
> **smartboyathome said:**
> 
This could be done (possibly even by canonical) to raise money for Ubuntu, and LiveUSBs becoming even bigger will let people install more on it while saving their prefs.

That's what I figured. The only thing that kind of threw me off about the whole idea was the overall cost. I know canonical holds the license to Ubuntu but I'm not totally sure where the money comes from.

But it is a good idea :)

---

### Post by ppibburr on 2007-12-08
The app does make a persistent enviroment, tho usb keys are subject to get scrambled when you shutdown, specially kdm settings and X. i think its a mix of hardware/software in this problem.

I note that most of my work is done from a usb key.

Plus, a build of your system as a liveUSB is a great way to work abroad, perform multiple installs already set up, quickly. as well as a great back-up, with the install to disk app.

As to selling branded tumbdrives, they do sell.

---

### Post by smartboyathome on 2007-12-08
> **YoDaddeh said:**
> That's what I figured. The only thing that kind of threw me off about the whole idea was the overall cost. I know canonical holds the license to Ubuntu but I'm not totally sure where the money comes from.

But it is a good idea :)

I was thinking that Canonical could sell it through their store. It shouldn't cost *too* much. ;)

> **ppibburr said:**
> The app does make a persistent enviroment, tho usb keys are subject to get scrambled when you shutdown, specially kdm settings and X. i think its a mix of hardware/software in this problem.

I note that most of my work is done from a usb key.

Plus, a build of your system as a liveUSB is a great way to work abroad, perform multiple installs already set up, quickly. as well as a great back-up, with the install to disk app.

As to selling branded tumbdrives, they do sell.

I haven't seen a USB drive in Canonical's store, can you give me a link? :)

---

### Post by YoDaddeh on 2007-12-08
[Ubuntu Branded Thumbdrive](https://shop.canonical.com/product_info.php?products_id=110&osCsid=3a9d5c941e8acede1273dd1fc3cdb4aa)

:KS

(I don't know why it always defaults to pounds but its about 25 bucks US)

---

### Post by smartboyathome on 2007-12-08
> **YoDaddeh said:**
> [Ubuntu Branded Thumbdrive](https://shop.canonical.com/product_info.php?products_id=110&osCsid=3a9d5c941e8acede1273dd1fc3cdb4aa)

:KS

(I don't know why it always defaults to pounds but its about 25 bucks US)

Thanks, and they probably have the default as pounds since one of their offices is in England. ;)

---

### Post by IanW on 2007-12-09
> **smartboyathome said:**
> I was thinking that Canonical could sell it through their store. It shouldn't cost *too* much. ;))

I've suggested via the store's "contact us" page, and pointed out that Mandriva already do this.

(Edit) I believe Canonical's UK office is on the Isle of Man (Tax Haven!)

---

### Post by spanella47 on 2007-12-09
> **smartboyathome said:**
> Is this really necessary? The 1GB usb drive is still the most abundant, so it wouldn't work very well (trust me, I tried...).

1GB is all you need for a liveusb...cd's only hold 750-800MB

thanks for the link ppibburr.  thats exactly what i'm talking about, except officially supported of course.  Now would only have to fix the install issues from the usb to a computer.  I think my problem stemmed from the installer treating the usb as if it were a cd.

---

### Post by smartboyathome on 2007-12-09
> **spanella47 said:**
> 1GB is all you need for a liveusb...cd's only hold 750-800MB

thanks for the link ppibburr.  thats exactly what i'm talking about, except officially supported of course.  Now would only have to fix the install issues from the usb to a computer.  I think my problem stemmed from the installer treating the usb as if it were a cd.

Yes, but that leaves 200-300 mbs of space left for persistance. I would say it would be better to wait until 2 GB becomes more abundant. :)

---

### Post by spanella47 on 2007-12-09
> **smartboyathome said:**
> Yes, but that leaves 200-300 mbs of space left for persistance. I would say it would be better to wait until 2 GB becomes more abundant. :)

all i want it for is a medium to install ubuntu or recover from a failed system, so for me 1GB is plenty.  Maybe I didnt need persistence for that but thats what the guides described.

on Amazon you can get 2GB usb drives for only $15-20.  Wouldnt really call that a lack of abundance....

---

### Post by ppibburr on 2007-12-09
> **spanella47 said:**
> 1GB is all you need for a liveusb...cd's only hold 750-800MB

thanks for the link ppibburr.  thats exactly what i'm talking about, except officially supported of course.  Now would only have to fix the install issues from the usb to a computer.  I think my problem stemmed from the installer treating the usb as if it were a cd.

What was the problem with the install? I have installed many times from a usb.

---

### Post by spanella47 on 2007-12-09
> **ppibburr said:**
> What was the problem with the install? I have installed many times from a usb.

had problems with USB drives not automounting...fix i used is at the bottom of this bug:
[https://bugs.launchpad.net/ubuntu/+bug/129581](https://bugs.launchpad.net/ubuntu/+bug/129581)
installation had set up an fstab entry for 2 cdrom drives (i have one), one for /media/cdrom1 and another using /dev/sdb1 which is used for automounting external drives.

Figured it was an artifact from using the usb key for installation.

---

### Post by Lorenz on 2007-12-14
+1

I think that would be very useful.
Probably possible now already, but it would be cool to have it as a extra download, next to live CD, alternate CD, etc.

---

### Post by desperado666 on 2007-12-14
German Loco already have a nice working Wiki article ;)

[http://wiki.ubuntuusers.de/Live-USB](http://wiki.ubuntuusers.de/Live-USB)

Dont see the problem to release an iso which can be extracted to an usb pen drive.

---

### Post by Shin_Gouki2501 on 2007-12-15
is this request to install FROM USB Media or TO USB Media?

From is no problem imo... TO an USB stick or external USB hdd is more a problem imo.
And it would be absolutly great if such an option would exist!

---

### Post by smartboyathome on 2007-12-15
> **Shin_Gouki2501 said:**
> is this request to install FROM USB Media or TO USB Media?

From is no problem imo... TO an USB stick or external USB hdd is more a problem imo.
And it would be absolutly great if such an option would exist!

An option does exist, just not graphically.

---

### Post by Shin_Gouki2501 on 2007-12-16
ithx for or answer but...
of COURSE i know that via CLI and config files  *_* ANYTHING COULD be doen , but thats not my question.
My question was: is this thread request for a GUI option for installing FROM USB MEdia or TO USB MEDIA.

---

### Post by meborc on 2007-12-17
i don't know if that is the point of this thread, but it would be supercool to be able to download a rar file, extract it to USB stick, insert the USB stick to another computer, boot ubuntu from stick and install it like this...

i know we can already do it... i mean it would be supercool, if there were official rar files for every new release :)

---

### Post by smartboyathome on 2007-12-17
The only problem with that theory is that instead of a rar file, it would be a tarball (rar is a proprietary format). Also, the image for installing everything would have to be small so it could fit into someone's RAM, since you can't partition a USB drive while it is in use.

---

### Post by meborc on 2007-12-18
> **smartboyathome said:**
> The only problem with that theory is that instead of a rar file, it would be a tarball (rar is a proprietary format). Also, the image for installing everything would have to be small so it could fit into someone's RAM, since you can't partition a USB drive while it is in use.

yes :) tar was what i was thinking ... stupid me

well... i am not talking about installing ON the usb... so no partitioning of the USB stick... just use the USB stick as a MEDIUM instead of the cd

first we used floppies... then we moved to cd... then to dvd... i think it is time to move to usb... i don't have enough money to buy new cd-w's all the time :) and no, cd-rw is not an option (loss of quality after extensive use)

my idea is just to use the USB stick as we are used to using the live-cd installer

---

### Post by IanW on 2007-12-18
The new "EeeXubuntu" distro (Xubuntu compiled for the Asus EeePC) has an option to create a bootable USB stick from the Live CD session.

ie. Boot the Live CD and one of the menu options is to create a "Live USB".

Is that the kind of thing you mean?

---

### Post by Moezzie on 2007-12-20
> **IanW said:**
> The new "EeeXubuntu" distro (Xubuntu compiled for the Asus EeePC) has an option to create a bootable USB stick from the Live CD session.

ie. Boot the Live CD and one of the menu options is to create a "Live USB".

Is that the kind of thing you mean?

That sounds like a really cool deal. Is it presistant?

---

### Post by spanella47 on 2007-12-20
> **IanW said:**
> The new "EeeXubuntu" distro (Xubuntu compiled for the Asus EeePC) has an option to create a bootable USB stick from the Live CD session.

ie. Boot the Live CD and one of the menu options is to create a "Live USB".

Is that the kind of thing you mean?

kinda like that, except forgoing the Live CD all together.  I'm trying to avoid making a cd when making a Live USB.  Is a step in the right direction though.

---

### Post by meborc on 2007-12-20
> **spanella47 said:**
> kinda like that, except forgoing the Live CD all together.  I'm trying to avoid making a cd when making a Live USB.  Is a step in the right direction though.

YES +1

i want to get a file from official ubuntu homepage, copy it on my usb, and use it as livecd

is that so hard to do? ;)

---

### Post by smartboyathome on 2007-12-20
> **meborc said:**
> YES +1

i want to get a file from official ubuntu homepage, copy it on my usb, and use it as livecd

is that so hard to do? ;)

You can extract the files from a livecd image onto your USB drive formatted to FAT16 and made bootable (can be done with the latest gparted). If you want it persistant, though, it takes a little more work. ;)

---

### Post by spanella47 on 2007-12-20
> **smartboyathome said:**
> You can extract the files from a livecd image onto your USB drive formatted to EXT2 and made bootable (can be done with the latest gparted). If you want it persistant, though, it takes a little more work. ;)

ha, yes you make it sound so simple... point is to make that whole process graphical and/or extractable

---

### Post by smartboyathome on 2007-12-21
It is graphical. Just install GParted from getdeb,net, open it, unmount your USB drive, then format your partition to fat16. Right click the partition before you partition it, and check the checkbox next to boot. Now partition it. When done, extract the contents of the livecd (you can do this by right clicking the ISO and opening it with archive manager), then push extract. Make sure the radio button by all files is selected. Now, extract it to your USB. You have officially made a LiveUSB using only the GUI. Restart your computer and enjoy.

---

### Post by IanW on 2007-12-22
I used the instructions from here (with modifications):- [Pendrive Linux.com]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/")

The change I made was simply to loop mount the Live CD iso image instead of burning it to CD, thusly:-

```
sudo mkdir /mnt/iso
sudo mount -o loop -t iso9660 filename.iso /mnt/iso
```

As long as you start with a 1GB or better pendrive, it works fine. (I needed this to install Ubuntu on my new Asus EeePC.)

---

### Post by joecr on 2007-12-22
One thing that I'd like to work in the USB live version is a way to get it to update as I have yet to figure out how to do that.  I've got Kubuntu 7.10 on a 4 GB drive.

---

### Post by smartboyathome on 2007-12-22
> **joecr said:**
> One thing that I'd like to work in the USB live version is a way to get it to update as I have yet to figure out how to do that.  I've got Kubuntu 7.10 on a 4 GB drive.

You have to use persistance for it to update and stay updated.

---

### Post by pavel989 on 2007-12-27
Well how big woud it have to be? i mean, you not gonna fit that on a 512mb. but maybe a gig isn't enough with drivers and apps?

---

### Post by smartboyathome on 2007-12-27
At least 2 GB for anything decent. Using 1GB gives you barely 100-200MBs of space for persistance (which doesn't get you far). With Xubuntu, you can get it to 300MBs, but that is still not much.

---

### Post by aselya1 on 2008-01-16
I agree that 2GB is really the minimum for Persistent LiveUSB *Ubuntu if you use a 'stock' livecd. You can remaster the livecds using this process: [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) to give yourself more room. Also, since I didn't see it mentioned, the wiki has the full process outlined here: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) for making LiveUSB, not installing to a USB stick. The 'Alternate Partition Layout' is great if you want to keep using the stick to shuttle files with non-Linux OS's.

---

### Post by phoenix81000 on 2008-01-16
Once again this has turned into a typical Linux idea project :D

cmon people get some GUI app into the repos =]

Main aim: Install Ubuntu to a USB Flash Drive
Possible Options: 
Clean Full Install
Dirty Full install (keep setting + programs + copy home dir 2 USB)
Minimal install (aka alternative)
Recover install (for rescueing PC's, maby contain script for resetting GRUB GDM Partioner and other tools)

Hell why not make USBuntu sound catchy doesnt it? Just have something like the above installer application but give a choice of window manager to be installed on the USB-Drive. How hard (size) would it be to have both GNOME and something light installed (FluxBox?) It would be best if this USBInstaller was a per default installed app w. ubuntu or atleast be in the repos. The thing is it all should be very easy to install to a USB and be done via a GUI. Now the nice thing is that installing to a USB stick is always the exact same. Just pick the USBDevice and run a resize/format on it and install the OS.


Anyway i havnt been asleep in a while and been studying so it might just be talking loads of ******** :P But why doesnt someone just setup a seperate forum / clean thread and take controll of this project. Make some clear objectives organize poeple and manage things propperly.

just my 2pence

---

### Post by smartboyathome on 2008-01-16
The problem with choosing the window manager is that you would have to remaster an ISO image to include the Window Manager and THEN put it on the USB drive.

---

### Post by phoenix81000 on 2008-01-16
> **smartboyathome said:**
> The problem with choosing the window manager is that you would have to remaster an ISO image to include the Window Manager and THEN put it on the USB drive.
cant u have an iso with both a heavy and a light window manager installed? for example USB1.0 would really run well with gnome. And rember public PCs or onces available at colleges arnt processor beasts.
And someone should really steup and take charge of this.. Smartboyathome u sound like a fit manager for this project.. 

This is an Awsome idea

---

### Post by smartboyathome on 2008-01-16
> **phoenix81000 said:**
> cant u have an iso with both a heavy and a light window manager installed? for example USB1.0 would really run well with gnome. And rember public PCs or onces available at colleges arnt processor beasts.
And someone should really steup and take charge of this.. Smartboyathome u sound like a fit manager for this project.. 

This is an Awsome idea

You can, but it would take up more space on the LiveUSB and would also require GDM to be used instead of how it is currently used now (it logs in automatically).

I could do this, but the problem is that I don't know how to program very well, and don't know any GTK yet.

---

### Post by phoenix81000 on 2008-01-16
> **smartboyathome said:**
> You can, but it would take up more space on the LiveUSB and would also require GDM to be used instead of how it is currently used now (it logs in automatically).

I could do this, but the problem is that I don't know how to program very well, and don't know any GTK yet.
well.. i have no clue where we can find some devs .. but maby on IRC or in the forums? iam currently at union.. burried in a 650page book which i need to recite by hart tommorow.. so i shouldnt even be typing here..

---

### Post by Huss on 2008-01-17
¨And by the I mean the ability to install a "LIVE" Ubuntu installation on a thumb drive or USB Hard drive, that will retain changes in GUI configuration, etc. but will still detect hardware and install correct drivers on boot.¨

Great idea!

---

### Post by belovedmonster on 2008-02-01
I've just wasted two days of my life trying to get Xubuntu on a USB pen, completely screwing up the USB pen in the process.

A noob friendly graphical way of doing this would be an amazing feature and one I would love to see. Other distros are starting to do it so why cant Ubuntu?

In fact part of the reason I screwed up my USB stick is because I tried to repartition it using the terminal when I should have just used Gparted. GUI is just better for average users!

---

### Post by smartboyathome on 2008-02-01
> **belovedmonster said:**
> I've just wasted two days of my life trying to get Xubuntu on a USB pen, completely screwing up the USB pen in the process.

A noob friendly graphical way of doing this would be an amazing feature and one I would love to see. Other distros are starting to do it so why cant Ubuntu?

In fact part of the reason I screwed up my USB stick is because I tried to repartition it using the terminal when I should have just used Gparted. GUI is just better for average users!

I am trying to put together a guide which does all this graphically, but I still need to find a way to rename partitions. Once I do find a way, though, I think I will be able to make it so that you can create a live usb (with persistance!) graphically.

---

### Post by belovedmonster on 2008-02-01
That would be really awesome. :biggrin:

---

### Post by smartboyathome on 2008-02-01
It is done, check it out [here]("http://ubuntuforums.org/showthread.php?t=647587").

---

### Post by probono on 2008-05-22
Hi all, I am working on a GUI to make things really simple. This tool creates a bootable Live USB medium from a running Ubuntu Live CD. It was made in response to Ubuntu Brainstorm idea #16.

[IMG]http://klik.atekon.de/liveusb/screenshot.png[/IMG]

It performs the following actions:

    * Detects available USB sticks (using HAL)
    * Partitions USB stick with 1 partition
    * Sets partition bootable
    * Writes MBR to USB stick
    * Formats partition FAT16
    * Installs bootloader (syslinux) to partition
    * Writes bootloader configuration file
    * Copies necessary files from running Live CD to USB stick
    * Sets language and keyboard of USB Live system to match running Live CD
    * Optionally: Downloads and integrates Adobe Flash Player

[https://launchpad.net/liveusb](https://launchpad.net/liveusb)
#liveusb on freenode

---

### Post by smartboyathome on 2008-05-22
Why not format the usb to fat32? That works the same, but has some additional support.

---

