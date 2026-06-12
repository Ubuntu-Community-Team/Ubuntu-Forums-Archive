---
title: "Stuck on boot: Syslinux Problem"
date: 2012-07-08
forum: Ubuntu Studio
---

### Post by Alecossy on 2012-07-08
Hello there, I'm Alecossy.
I've been using linux distros for over 4 years now, going from Fedora to Chakra, passing through ubuntu, knoppix and another couple of minor forks.
Just yesterday I decided to remove my chakra copy to try out Ubuntu Studio 12.04 on an Acer Aspire 5742ZG laptop.
I went straight to making the flash USB just to find that it gets systematically stuck on SYSLINUX.
The exact message says: 
"Syslinux 4.03 2010-10-22 EDD Copyright (C) 1994-2010 H. Peter Anvin et al"
Used to this kind of problems from other distros i tried to browse your forum looking for a solution.
Of the few I tried none worked.
I'm sure my computer supports USB boots because all other distros have been installed using this very USB Drive i'm using now (Including a version of Android x86) and I made the flash drive both using LiLi and Unetbootin.
I'm now wondering, what might the problem be?

---

### Post by Cheesehead on 2012-07-08
There are usually three possibilites:

1) The syslinux bootloader was corrupted and needs to be reinstalled.
2) syslinux.cfg is pointing to the wrong kernel
3) syslinux.cfg is pointing to the wrong initrd (root system)

Take a look at the .cfg file and try to eliminate some possibilities.

If you don't know how to read it, post it here.

---

### Post by Alecossy on 2012-07-08
Here's the content of my syslinux.cfg:
Note that I never used syslinux before so I'm completly new to the whole thing.
```

default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntustudio.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu Studio without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntustudio.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu Studio
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntustudio.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu Studio without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntustudio.seed boot=casper quiet splash --

label ubnentry7
menu label Install Ubuntu Studio
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntustudio.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --


```

---

### Post by Cheesehead on 2012-07-08
Looks like the install is set up for a LiveCD instead of a LiveUSB environment. Perhaps you simply copied it over? If so, that won't work; it needs to be installed properly - the CD and USB environments are a bit different.

How, exactly, did you create the bootable USB?
What program did you use to create it?

For example, take a look at this line from the syslinux.cfg:
> append initrd=/ubninit **file=/cdrom/preseed/ubuntustudio.seed** boot=casper quiet splash --
See how the system is looking for a preseed file on the CDROM instead of the USB?

Are you really trying to install Ubuntu Studio? Is the preseed file on your USB stick? 
If so, simply fix the string(s) to reflect the correct location.

---

### Post by Alecossy on 2012-07-08
As I said, I used Unetbootin - 575, Windows version.
I simply downloaded ubuntustudio-12.04-dvd-amd64.iso from the ubuntu studio site and ran a checksum to be sure, then I opened Unetbootin and selected "ubuntu" and the 12.04_live_x64 version.
I then selected the drive and hit the okay button.
The result is what you see before us.
Did I do something wrong? 
I also tried to use LiLi (which is a windows application called LinuxLive USB Creator) but the result was the same.

---

### Post by Cheesehead on 2012-07-08
Perhaps you did something wrong. Or perhaps you have discovered a bug with the way unetbootin handles preseed files.

Doesn't seem relevant to your problem right now. We know what the problem seems to be in the syslinux.cfg file.
Do you understand how to fix it?

---

### Post by Alecossy on 2012-07-09
I'm not quite sure about it...
I'm pretty sure I simply have to redirect the string you highlighter but I'm sure how to call the usb drive.
Do I have to do something like:
```
append initrd=/ubninit file=/dev/sdb/preseed/ubuntustudio.seed boot=casper quiet splash --
```
provided that the folder structure is the right one?

---

### Post by Cheesehead on 2012-07-09
Close. For the base path, use the root level of the stick, not the root filesystem. GRUB uses these before the root filesystem is loaded, so the only filesyste it know is the stick. init hasn't created  /dev yet.

For example, the initrd (ubninit) isn't at /dev/sdb/ubninit, for GRUB purposes it's at  /ubninit (you can see it there at the top level of the stick).

Similarly, the preseed file should be at /preseed/ubuntusutdio.seed

---

### Post by Alecossy on 2012-07-09
Okay, this is strange...
I accidentally left the stick plugged in my PC and the system started without a problem...
I will try changing it to what you said and test it on the laptop anyway.
Edit:
the newly made syslinux.cfg
> 
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/preseed/ubuntustudio.seed boot=casper quiet splash --

has no effect. still stuck at the same screen

---

### Post by Cheesehead on 2012-07-09
> **Alecossy said:**
> Okay, this is strange...
I accidentally left the stick plugged in my PC and the system started without a problem...

Wait a second! You never mentioned that you used the stick to install, and that it's the *installed system* that won't boot!

I've been trying to diagnose why your USB stick won't boot...which apparently it does perfectly well. I've been working on the wrong problem entirely.

Question: Did you really **install** Ubuntu Studio onto the laptop, or did you merely copy over a live environment? Normally, if you really install, you would be using GRUB instead of Syslinux. Syslinux doesn't work on ext2/3/4, which is what Ubuntu prefers; it's meant for ms-dos formatted media. Did you really install, but somehow manually change bootloaders?

If you simply copied over a live environment, then needing the stick to boot makes more sense. Some path in the syslinux.cfg is still pointing to the stick.

---

### Post by Alecossy on 2012-07-09
First of all, sorry, my bad about the description but I've been preparing an exam till today (which I passed, btw).
All I'm trying to do is use the stick instead of a CD to "burn" in the iso (in order to boot the live DVD and try the distro and, eventually, install it on the laptop HDD).
I'm using both lili and unetbootin because it's the way I've always done that in order to get bootable live sticks (worked with chakra and with android x86, just to mention the latest two I tried).
I'm now feeling that it's not the right procedure to follow in order to obtain an ubuntu studio live stick, am I right?

Okay... this is somewhat strange... 
On the PC it works extremely well, on the laptop it doesn't even goes on to loading the menus we're trying to edit...
May it be my laptop, then? 
It's not the first time I use a live stick, though

---

### Post by Cheesehead on 2012-07-10
> **Alecossy said:**
> preparing an exam till today (which I passed, btw) Congratulations! Always a good feeling.

If the USB-stick works properly in the PC but not in the Laptop, then there's nothing wrong with the way you made the USB-stick version. Your description (using unebootin) is the same way I make them.

This laptop has worked with USB-Stick boots in the past?

Laptop BIOS permits booting to USB? (Very old systems may support only USB-ZIP instead of USB-HDD, and we must use a workaround)

Problem with the laptop USB port?

---

### Post by Alecossy on 2012-07-11
Laptop has worked with USB sticks before (I installed chakra via USB and, just 3 days ago, booted and then installed an android x86 distro)
I'm pretty sure there's nothing wrong with the bios either, since i've been able to do these steps before.
Port's okay, i've been trying on three different ones to be sure and i've been using the one i'm using now before... 
any other idea?

---

### Post by Cheesehead on 2012-07-11
Let's see. LiveUSB works on System A but not System B. Other LiveUSBs work on System B. Same method of creating all LiveUSBs.

Assuming all hardware is working properly, and I see you tested, then I'm out of ideas, sorry.

I was going to suggest trying a couple things, but upon reflection I won't - they're just grasping for more data.

---

### Post by Alecossy on 2012-07-11
Which steps does loading syslinux take? We might try debugging if we follow it step by step...
Also, i'm thinking it might be a problem with the resources, cuz syslinux isn't even loading the cfg file (you know, you don't even get to pick one of the choices handled by that file...)
If anything else fails, i'm going to buy a dvd and try burning it on a phisical support

---

### Post by Cheesehead on 2012-07-11
The MBR points to syslinux as the first program to execute.
Syslinux itself, once it starts, loads it's own .cfg files.

So this points to a corrupt syslinux file, or a bad install...but does not explain why the same install works fine on another system.

Debugging syslinux is described at [http://www.syslinux.org/wiki/index.php/Development/Debugging](http://www.syslinux.org/wiki/index.php/Development/Debugging) , but effective debugging (if I recall correctly) requires recompiling it to add the debug hooks.

---

### Post by Alecossy on 2012-07-19
seems like i can't get anything out of it... do you think it might work if I burned it on DVD?

---

### Post by Alecossy on 2012-07-22
Solved... thanks for the assistance, man!

---

### Post by Cheesehead on 2012-07-22
Don't keep us in suspense! Please tell us what the problem was, and how you solved it....

---

### Post by Alecossy on 2012-07-25
that's quite a question... i simply went to the nearest store, bought a virgin dvd and burnt the iso over it and it worked. 
I'm guessing my system had problems finding the files on the stick and simply kept hanging at the point I've shown you.
I'm now experiencing some minor problems but the overall stability and functionality of the system's good, even better than I could imagine.

---

### Post by mikemastercorp on 2012-10-03
Alessossy and the others that are wondering why SysLinux boot from USB might be caused - I have found the reason long long time ago (for my case), however I did forgot about it since today when I have met the same problem.

I do not know in particular why this is happening, however the problem is related to the partitioning of the hard drive. I will explain what I mean in details:

I have started testing BackTrack to test my WAN vulnerability. It booted well but had problems with X server which seemed awkward and strange as the image is 100% perfect and MD5 verified.

Tried to boot Fedora 17 which I "burned" to my USB stick with PowerISO (under Windows) and UnetBootIn as well as Universall-Boot-Installer . All caused exactly the same problem - SYSLINUX 4.06 EDD 4.06-pre1 Copyright (C) 1994-2011 H. Peter Anvin et al (the cursor is flashing on the next row and nothing happens even after 10 minutes of waiting).

I have remembered about the problem and formated the drive with Part Magic which meant in particularly to delete all the partitions, create one NTFS Active and to format it. After that - voila, the system is booting and now I have my Pepermint 3 Linux installed and booting fine on Acer Aspire ZG5 (AOA 150)

Bonne chance everyone and I hope this will enlighten you about another approach to try to fix such problem.

---

### Post by mikemastercorp on 2012-10-03
Well, I guess my digging deeper came back to me with some better suggestions and an idea why this is happening. Actually I shall correct myself as it was not a fix-up if somebody formats his drive. The problem is caused by the records in MBR (Master Boot Records) so if anybody have such problem might try Parted Magic which is a perfect hard drive partitioning linux distro (based on Fedora LXDE - if I am not wrong).

Writing zeros to MBR fixed the booting and now it is all up. Probably the last time I have formated the hard drive I did a whole disk wipening and repartitioning which have also recreated the proper MBR records.

Well good luck and for me now the topic is really closed ;)

---

### Post by guritaburongo on 2013-04-18
hi, first of all sorry for my english, not my native language, i have  made some research with the info posted here, and made some tests, i had  the same problem running any distro: i've tried ubuntu, linux mint, and  wifiway, and made tests with yumi and unetbootin, and tested it on 2  laptops, the first one (sony vaio) booted the livecd on the usb stick  normally with no problems (any distro, with unetbootin or yumi) the  other one (lenovo g475), didnt run any of them, no matter the distro, no  matter the software used. 
but if i use wifiway with unetbootin and then i run \boot\bootinst.bat
this script primarily what it does is to run this command
\boot\syslinux\syslinux.exe -maf -d \boot\syslinux %DISK%
(being %DISK% the letter of our usb stick)
the problem is solved and now i can boot wifiway on the lenovo g475
this didnt worked on yumi because i think is a multiboot software and things arent that simple (at least for me)
so i made some comparisons with winmerge (file comparison tool)   comparing the "before command" stick and the "after command" stick, and  the only thing that changed was this file:
\boot\syslinux\ldlinux.sys
and it was only one line of the file, saddly a text editor is not a propper tool to see that file so i didnt understand what info changed...
 so now its you turn gurus to tell  me how i apply this solution to yumi, so i can have my multiboot usb  stick working on any computer hehe... well, i hope i have contributed on  something...

---

### Post by Divergence on 2013-04-21
I am having the very same problem with my HP Mini. The only distro I could boot so far is DamnSmallLinux, which does not recognize its wireless card anyway. I have spent the last 6/7 hours trying to boot Lubuntu on it, without any luck. The drive is fine (I am typing from Lubuntu live on my Pavilion dv5 right now) as it would boot on three other terminals BUT on the HP mini. I will try to change the values of the MBR if I somehow manage to manipulate it, and let you know if it is resolutive once and for all.

---

### Post by charl135m1th on 2013-10-31
I'm having the same issue, I'm familiar with syslinux from old days setting up pxe boot, but this is driving me a little nuts. 

I know this threads a bit old but did you guys have a Solid state drive or a Bios with EFI?

---

### Post by LentoMan on 2014-06-09
I had this issue today when trying to install xubuntu on my old Acer netbook using unetbootin.

Eventually I found out that the problem was that the 1 GB USB-stick was detected as USB-FDD, 
I tried with another newer 4GB USB-stick and it was detected as USB-HDD instead.

After switching to the 4GB USB-HDD stick, I had no problems booting and installing xubuntu with unetbootin.

---

