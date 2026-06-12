---
title: "Unetbootin NEVER works"
date: 2017-02-25
forum: The Cafe
---

### Post by guinea2 on 2017-02-25
Every time I decide to give a bistro of linux a try, I always try Unetbootin to create a bootable USB (I have a Mac), but it NEVER works when I try it, it won't work on my MacBook nor will it work on my windows computer... It says it was successful in creating the USB from the ISO but it won't boot from the menu in Mac and it won't boot from either Legacy or UEFI mode on my windows computer. Does anyone have this issue?

Note: For now I am just using the built in command for making a bootable USB on a Mac.

---

### Post by poorguy on 2017-02-25
I still use version 585 as I also have not had any good luck using any newer version of Unetbootin.
Unetbootin 585 has never failed to work on any computer I have used it on and don't understand why the newer versions fail to work.

Give these a try.

Rufus.
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

LinuxLive USB Creator
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

I don't know if they will work on Apple Mac based computers.

Hope this helps.

---

### Post by bearlake on 2017-02-25
Been using [mkusb]("https://help.ubuntu.com/community/mkusb") since it was introduced.

It never failed me yet. ;)

---

### Post by kurt18947 on 2017-02-26
The trick is to find a USB creator that work in Linux. Unetbootin worked fine in Windows the last time I used it (couple years ago). Unetbootin from the 16.04 repository? Not so much; it opened a blank window and that was it. I've been using the "Disks" app then "Restore Partition Image". Be sure to restore to the correct device or partition! This does not support persistence.

---

### Post by uNoubu8a on 2017-02-27
On a tangent but for those wanting to "burn" iso's to discs or thumb-drives rufus is brilliant :KS

---

### Post by sudodus on 2017-02-27
You can get a small linux system with [***mkusb-dus*** alias ***guidus***](https://help.ubuntu.com/community/mkusb) if you download a file according to the following link

[Small 9w iso file with guidus and gparted installed](https://help.ubuntu.com/community/9w#Small_9w_iso_file_with_guidus_and_gparted_installed)

You get a complete and new persistent live system with Lubuntu 16.04.2 LTS according to the following link

[Lubuntu 16.04.2 LTS (32 bit and 64 bit) with mkusb version 12.0.4](https://help.ubuntu.com/community/mkusb/persistent#Lubuntu_16.04.2_LTS_.2832_bit_and_64_bit.29_with_mkusb_version_12.0.4)

and create a USB boot drive according to the following link [https://wiki.ubuntu.com/Win32DiskImager]() (in Windows).

Use a cloning tool in MacOS. It is best with a GUI tool with some built-in security. (Otherwise, if no other alternative is found, you can use the dangerous ***dd*** and double-check that everything is correct before you press the Enter key).

---

### Post by HermanAB on 2017-02-27
Well, the main reason why unetbootin etc don't work is because you don't need it.

For the last several years, the Ubuntu ISO files are dual mode.  All you need to do is write the ISO file to the USB thingy using dd.

It took the Ubuntu maintainers many years to catch up with the rest of the Linux world, but they eventually got it right and unfortunately there are now bazillions of erroneous and unhelpful guides and utilities out there confusing the matter.

---

### Post by kurt18947 on 2017-02-27
> **HermanAB said:**
> Well, the main reason why unetbootin etc don't work is because you don't need it.

For the last several years, the Ubuntu ISO files are dual mode.  All you need to do is write the ISO file to the USB thingy using dd.

It took the Ubuntu maintainers many years to catch up with the rest of the Linux world, but they eventually got it right and unfortunately there are now bazillions of erroneous and unhelpful guides and utilities out there confusing the matter.

Unless you want persistence. I know it's possible to create a persistent partition but isn't there more to having a persistent partition recognized than simply naming it casper-rw?

Personally, with the advent of cheap high capacity USB drives If I want storage I just install a full version. That might not be most peoples' first choice though.

---

### Post by sudodus on 2017-02-27
I think the main problem with ***dd*** is that it does what you tell it to do without questions. There is 'no final checkpoint'. So if you tell it to wipe the family pictures ...

I have seen too many cases, where important data have been overwritten because of a typing error, when using dd. ***mkusb*** wraps a safety belt around dd. It helps you identify the target drive, select it, and check it again, when making live-only boot drives with the cloning method.

But this does not work with a persistent live drive, because the ISO file system (and partition structure) is read-only, so there is no way to add a partition or file for persistence in that drive. Instead you should use an extracting method. So mkusb switches method when creating a persistent live drive.

---

### Post by yoshii on 2017-02-28
Some of the Ubuntu guides and other sites now say to avoid uNetBootIn.  
I used to use it, but I switched to YUMI (for Windows).  
For Linux, I haven't decided yet, but there are lists of alternatives.  
Even Gnome-Disks (installed by default in Lubuntu) can allegedly write ISOs to USB drive.

---

### Post by wildmanne39 on 2017-02-28
Rufus is very easy to use and works great.

---

### Post by HermanAB on 2017-02-28
"Even Gnome-Disks (installed by default in Lubuntu) can allegedly write ISOs to USB drive. "
Everyone and his dog always moans about 'dd' being too complicated for n00bs, but even 'cat' can write an ISO to a USB drive.

---

### Post by DuckHook on 2017-02-28
> **HermanAB said:**
> …Everyone and his dog always moans about 'dd' being too complicated for n00bs…Not "too complicated" perhaps, but certainly "very dangerous". Confusing *if* with *of* will really ruin your day.

---

### Post by kurt18947 on 2017-03-01
> **yoshii said:**
> Some of the Ubuntu guides and other sites now say to avoid uNetBootIn.  
I used to use it, but I switched to YUMI (for Windows).  
For Linux, I haven't decided yet, but there are lists of alternatives.  
Even Gnome-Disks (installed by default in Lubuntu) can allegedly write ISOs to USB drive.

Gnome-Disks can certainly write ISOs to a flash drive. Use the restore partition function I think. Gnome-Disks doesn't help with persistence if that's desired though.

---

### Post by RobertoRecordo on 2017-03-24
This week I used unetbootin to make a bootable freedos flash drive so I could update my BIOS. My first attempt was using an SD card ( I can boot my system from SD) It failed "probably" a problem with the card, but successful with USB stick.

---

### Post by night_sky2 on 2017-03-26
Unetbootin works well you just have to format the USB drive properly beforehand.

I use this little tool called ''Disk'' for that purpose, which is installed by default on many distros.

---

### Post by g33zr on 2017-03-27
You might want to try [Etcher]("https://etcher.io/"), which is cross-platform and very easy to use.

---

### Post by kazakore on 2017-09-17
Just tried to create a bootable drive for upgrading SSD firmware using Unetbootin. It wouldn't work on multiple devices which I had previously used and knew to work on my system! After a bit of head-scratching, many attempts and even trying formatting on multiple machines (I've had weird results formatting with GParted in the past for some reason) but it wouldn't even work when formatted from Windows (which didn't recognise it at all, another pointer of GParted not doing things correctly when doing MBR partition table and FAT32 file system!)

In the end I checked the supposedly installed device in GParted and noticed it didn't have the Boot Flag set. Setting the correct (only) partition to be have the Boot flag within GParted did the job.

You really shouldn't have to do that though!!

---

### Post by yoshii on 2017-09-18
Yeah, I switched to gnome-disks and rufus portable.  They both work well.  
I still keep unetbootin around for some windows oses as a backup though.

---

### Post by C.S.Cameron on 2017-09-19
Persistent installs are quick to do and fit onto a small drive, but they always go corrupt within about six months.
I have had Full installs to USB last years, they are also updateable and upgradeable, but the drive can not be used as an installer.

---

### Post by su:bhatta on 2017-09-27
+1 for [Etcher]("https://etcher.io/")

---

### Post by kurt18947 on 2017-09-27
> **C.S.Cameron said:**
> Persistent installs are quick to do and fit onto a small drive, but they always go corrupt within about six months.
I have had Full installs to USB last years, they are also updateable and upgradeable, but the drive can not be used as an installer.

Perhaps part of the trouble with live USBs is that they can't be updated or at least I've never had success with it. For simple stuff at least doing a full install to a good sized (16 GB+)USB flash drive works pretty well in my experience. True you can't do an install from a full install but smaller flash drives are pretty cheap. It can be useful to have a live session with its severe case of amnesia, such as connecting to a dicy public wifi connection.

---

### Post by sudodus on 2017-09-27
It is possible to create a live-only (or simple persistent live) system according to this link, ['Do it yourself'](https://help.ubuntu.com/community/Installation/iso2usb/diy)

or a persistent live system according with [mkusb - Compressed image file ...](https://help.ubuntu.com/community/mkusb/persistent#Compressed_image_file_with_a_persistent_live_system)

and 'behind' it install an Ubuntu or Ubuntu community flavour (for example light-weight Lubuntu, which works well from a USB drive). I mean install it into the latter part of the USB drive like it were installed into an internal drive.

If you install the bootloader to the partition, you will still boot via the live system, and you can copy the menyentries from the installed system to the live system's **/boot/grub/grub.cfg** and get it into the live system's grub menu.

Or you let the installer write the bootloader to the head of the drive if BIOS mode, copy the live system's menuentries to the installed system's **/etc/grub.d/40_custom** file, run sudo update-grub and get it into the installed system's grub menu.

[hr][/hr]
There will be plenty of space for this in a USB 3 pendrive of 32 GB or more.

[hr][/hr]
A rather convenient way to get an installed system that boots in both UEFI and BIOS mode (but not in old 32-bit computers) is to clone/extract the system from a compressed image file according to the following link, [help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS).

---

### Post by yoshii on 2017-09-28
Thanks for the link to Etcher.  
I recently tried the gnome-disks technique on a flash drive and it looked like it worked, but in actuality it created an unreadable partition on part of the drive and it didn't boot.  Etcher looks promising.

---

### Post by sudodus on 2017-09-28
Disks alias gnome-disks works, when you clone from an Ubuntu iso file to the whole drive /dev/sdx but not when you clone to a partition, for example /dev/sdx1. Disks uses the term 'restore' for this action (cloning from an image to a drive).

All cloning tools work, when you clone from an Ubuntu iso file to the whole drive /dev/sdx

*Edit:* Cloning works with hybrid iso files (that are/were treated with the linux program isohybrid), which makes them good for burning CD/DVD disks as well as cloning USB pendrives and memory cards. *Most but not all linux distros provide hybrid iso files.* The current Windows iso files are *not* hybrid iso files.

---

### Post by su:bhatta on 2017-09-28
> **yoshii said:**
> Thanks for the link to Etcher.  


You are welcome. 
I had difficult times with Unetbootin.
So bad that I had to use my windows partition just to get Rufus to write the ISO/dd.

Might I add, since then 'dd' is the best way i found.

Another option is [Gnome Multiwriter.]("https://wiki.gnome.org/Apps/MultiWriter")

It has worked conveniently for me.

---

### Post by sudodus on 2017-09-28
> **su:bhatta said:**
> 
Might I add, since then 'dd' is the best way i found.


You are brave :-P

I think 'dd' deserves the nickname 'Data Destroyer' because it does what you tell it to do without questions. I prefer tools with a final checkpoint and some output that helps you identify the target drive, so that you will write to the correct one, and not overwrite another drive with important and not yet backed up data.

I have seen too many threads here at the Ubuntu Forums and also at AskUbuntu, where people ask for help to recover data after 'dd' has gone bärsärk.

-o-

I must admit, that sometimes I use 'dd' too, but only when no other tool can do the job, and I double-check and triple-check that there is no typing error or other mistake, or I use it via a shellscript. (mkusb is a shellscript, and I have some other and simpler shellscripts too. These shellscripts wrap a safety belt around dd.)

---

### Post by su:bhatta on 2017-09-28
> **sudodus said:**
> You are brave :-P


Not as brave as I would like to believe sudodus ;)

Thats why I searched out Etcher and Multiwriter :)

---

### Post by yoshii on 2017-09-29
> **sudodus said:**
> Disks alias gnome-disks works, when you clone from an Ubuntu iso file to the whole drive /dev/sdx but not when you clone to a partition, for example /dev/sdx1. Disks uses the term 'restore' for this action (cloning from an image to a drive).

All cloning tools work, when you clone from an Ubuntu iso file to the whole drive /dev/sdx

That was not the case with me.  
I'm glad it worked for you.  For me, I tried to restore a downloaded Lubuntu .ISO to a flash drive (without any special partitions, just a typical FAT32 formatted flash drive) and gnome-disks looked like it worked, but upon closer inspection in gParted and when trying to boot from it, it had failed.  

It left the flash drive with an incomplete format, non-filesystem partition which wouldn't boot of course.  I didn't do any special commands and I wasn't trying to clone anything, just transfer an .ISO to a flash drive... pretty common these days like I've done with RufusP and even occasionally uNetBootIn from Windows.  

Anyways, Etcher worked just fine instead.  I'm not trying to start (or continue) a flame war, I'm just saying that it didn't work for me and what actually did.  
Honest anecdotes aren't exactly proof, but they do imply that what works for one system might not work for another.  Blanket generalizations aren't really effective descriptions of computer science reality in my educated experiential opinion.  

But I'm just glad to have something native that works.  The interface of Etcher is nice and simple too.  No wierd menus, just pretty much click and go.

---

### Post by cariboo on 2017-09-29
> **sudodus said:**
> Disks alias gnome-disks works, when you clone from an Ubuntu iso file to the whole drive /dev/sdx but not when you clone to a partition, for example /dev/sdx1. Disks uses the term 'restore' for this action (cloning from an image to a drive).

All cloning tools work, when you clone from an Ubuntu iso file to the whole drive /dev/sdx

I've found that gnome-disks works with iso's other than Ubuntu. I've been using it to created sd boot disks for various debian based raspberry pi distributions.

---

### Post by sudodus on 2017-09-29
> **cariboo said:**
> I've found that gnome-disks works with iso's other than Ubuntu. I've been using it to created sd boot disks for various debian based raspberry pi distributions.

You are right. I mentioned Ubuntu, but *cloning works with all hybrid iso files* (that are/were treated with the linux program isohybrid), which makes them good for burning CD/DVD disks as well as cloning USB pendrives and memory cards.

I will also edit my previous post to make this clear, and yes, **gnome-disks** can perform this operation in a good way.

Edit:

And yes, cloning from other image (img) files and even expanding and cloning from compressed image files, for example installed systems (typical for Raspberry Pi) will also work with gnome-disks.

---

### Post by sudodus on 2017-09-29
> **yoshii said:**
> That was not the case with me.  
I'm glad it worked for you.  For me, I tried to restore a downloaded Lubuntu .ISO to a flash drive (without any special partitions, just a typical FAT32 formatted flash drive) and gnome-disks looked like it worked, but upon closer inspection in gParted and when trying to boot from it, it had failed.  

It left the flash drive with an incomplete format, non-filesystem partition which wouldn't boot of course.  I didn't do any special commands and I wasn't trying to clone anything, just transfer an .ISO to a flash drive... pretty common these days like I've done with RufusP and even occasionally uNetBootIn from Windows.  

Anyways, Etcher worked just fine instead.  I'm not trying to start (or continue) a flame war, I'm just saying that it didn't work for me and what actually did.  
Honest anecdotes aren't exactly proof, but they do imply that what works for one system might not work for another.  Blanket generalizations aren't really effective descriptions of computer science reality in my educated experiential opinion.  

But I'm just glad to have something native that works.  The interface of Etcher is nice and simple too.  No wierd menus, just pretty much click and go.

I know that Etcher has a good reputation, and I can understand that you like it. But I want to show, how to use Disks for this purpose. It could be useful also for other readers of this thread.

I respect your experience, but I thought and think that you 'restored' (cloned) to a partition, the FAT32 partition, in the USB flash drive, when you should instead 'restore' (clone) to the device (drive) itself (to the head of the device).

The first time you use Disks for this purpose it is easy to make this mistake because of the interface (of Disks). In order to select the whole device, you should first remove the partition table (if it exists), otherwise Disks will prompt you to select a partition (which will not 'restore' (clone) to a working USB drive).

See the attached screenshots made in a recent version of Lubuntu Artful (soon released as 17.10).

[hr][/hr]
But if you *extract* the content from an Ubuntu 64-bit iso file to a FAT32 partition, you will get a USB drive, that is bootable in UEFI mode. If a grub bootloader is installed for BIOS mode, it will be bootable both in UEFI mode and BIOS mode. See these links,

[help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

[help.ubuntu.com/community/Installation/iso2usb/diy](https://help.ubuntu.com/community/Installation/iso2usb/diy)

---

### Post by emilyjane2 on 2018-04-24
I have had problems with the newest version of UNetbootin myself, and I am looking for answers as to why!

For example, why would an older version (see @poorguy's comments on [p.1]("https://ubuntuforums.org/showthread.php?t=2353856")) work but the newer one doesn't? 

I'm also confounded because I've had such a mix of different results using UNetbootin. I've had it work perfectly, for example when I used it to create a live USB for Ubuntu 14.04 with persistence on a grungy old flash drive. This was done using a Mac.

I've also had it fail miserably, like when I tried to make a live USB for 16.04, both with and without persistence, both on a Mac (OSX10) and on a PC (Ubuntu 16.04).

And I should note that once when I used UNetbootin on my Mac and it failed to create the live USB, it corrupted a brand new flash drive almost beyond repair. I couldn't use Mac's Disk Utility to fix it. I also couldn't use Disks (Ubuntu), gparted, fdisk, gdisk, or EVEN mkusb, which has an option that is usually a failsafe (restore to usable storage drive or something like that). None of the dd commands worked either, which are usually another kind of failsafe method if you don't have any data you need to rescue.

WTF.

In that case, the only thing that worked was getting to a Windows machine and using chkdsk to repair and then formatting the drive. But, seriously. Why?

---

### Post by monkeybrain20122 on 2018-04-24
On Ubuntu I use [multisystem]("http://liveusb.info/dotclear/index.php?pages/install"), works for many distros and can create multiboot usbs (with several live systems packed into one usb) . I don't know what they use in Windows these days, haven't touched Windows since 2011 except at work and in VM. When I started I used [LILI]("https://www.linuxliveusb.com/"). I have only made a live usb on a Mac once about 2 years ago, I used the [Mac-Linux-USB-loader]("https://github.com/SevenBits/Mac-Linux-USB-Loader"), it worked. I have tried unetbootin only once or twice long time ago, never really used it.

---

### Post by sudodus on 2018-04-25
> **emilyjane2 said:**
> I have had problems with the newest version of UNetbootin myself, and I am looking for answers as to why!

For example, why would an older version (see @poorguy's comments on [p.1]("https://ubuntuforums.org/showthread.php?t=2353856")) work but the newer one doesn't? 

I'm also confounded because I've had such a mix of different results using UNetbootin. I've had it work perfectly, for example when I used it to create a live USB for Ubuntu 14.04 with persistence on a grungy old flash drive. This was done using a Mac.

I've also had it fail miserably, like when I tried to make a live USB for 16.04, both with and without persistence, both on a Mac (OSX10) and on a PC (Ubuntu 16.04).

And I should note that once when I used UNetbootin on my Mac and it failed to create the live USB, it corrupted a brand new flash drive almost beyond repair. I couldn't use Mac's Disk Utility to fix it. I also couldn't use Disks (Ubuntu), gparted, fdisk, gdisk, or EVEN mkusb, which has an option that is usually a failsafe (restore to usable storage drive or something like that). None of the dd commands worked either, which are usually another kind of failsafe method if you don't have any data you need to rescue.

WTF.

In that case, the only thing that worked was getting to a Windows machine and using chkdsk to repair and then formatting the drive. But, seriously. Why?

Your experience is telling us to avoid Unetbootin. My experience is somewhat better. If you use the version from this link, it is likely to work,but there is no guarantee:

[https://unetbootin.github.io/](https://unetbootin.github.io/)

Unetbootin is an extracting tool. See this link: [help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

I think the main problem with extracting tools (in contrast to cloning tools) is that they are sensitive to changes in the boot structure and versions used in new versions of iso files. The extraction process must 'understand' what it should find and how to treat it, and this must be updated to work when something important for booting is changed in a new version of a linux distro.

[hr][/hr]
Cloning tools simply copy the whole content of the iso file to a USB pendrive (or memory card). And if the iso file is a hybrid iso file (treated with the program isohybrid), it will make a bootable USB pendrive.

Cloning tools in Ubuntu:

- The **Startup Disk Creator** in Ubuntu 16.04 LTS and newer versions
- **Disks** alias gnome-disks in Ubuntu 14.04 LTS and newer versions
- [**mkusb**](https://help.ubuntu.com/community/mkusb) in in Ubuntu 12.04 LTS and newer versions (can also extract in order to create a persistent live drive)

Cloning tool in Windows:

[**Win32 Disk Imager**](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

Cloning tool in MacOS:

**dd** (but it is dangerous, so check and double-check, that everything is OK, before you run it. Otherwise you might overwrite valuable data).

---

### Post by aktiwers on 2018-05-09
I also started using [https://etcher.io/](https://etcher.io/) 
Github: [https://github.com/resin-io/etcher](https://github.com/resin-io/etcher)

It works very well.

---

