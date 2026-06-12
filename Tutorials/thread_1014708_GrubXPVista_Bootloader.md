---
title: "Grub/XP/Vista Bootloader"
date: 2008-12-18
forum: Tutorials
---

### Post by talsemgeest on 2008-12-18
The information in this thread has been moved to 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?t=2012409](http://ubuntuforums.org/showthread.php?t=2012409)

Thread closed.


**[SIZE=6][COLOR=blue]How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 11.10)[/COLOR][/SIZE]**

This How-to is for windows dual booters who reinstall an operating system only to find that it has taken away access to their other operating system. 
Whether you want to restore the XP, Vista, 7 or Ubuntu (Grub) bootloader, this guide will walk you through it.

All three parts of this tutorial require that you boot from a cd. If you don't know how to do this, check [here.]("http://www.hiren.info/pages/bios-boot-cdrom")

If you have made a mistake and want to revert the changes, simply follow the instructions for reinstalling the previous bootloader. For example, if you have installed vista over ubuntu, try to get the ubuntu bootloader back, but want to get the vista bootloader back, simply follow my instructions for installing the vista bootloader.


[SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.10 and beyond)[/COLOR][/SIZE]

First you need to find out what your drives are called. You can do this by going to a terminal and typing: ```
sudo fdisk -l
```

From that you need to find the device name of your Ubuntu drive, something like &#8220;/dev/sda5&#8243;.
 So, still in the terminal, type:
```

sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
```And then, to reinstall the grub: ```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```Push enter and you&#8217;re done! Of course you need to replace &#8220;/dev/sda5&#8243; and &#8220;/dev/sda&#8221; with what you found in the fdisk output.

[SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.04 and older)[/COLOR][/SIZE]

First of all, all credit for this part of the tutorial goes to [catlet]("http://ubuntuforums.org/showpost.php?p=1308395&postcount=1"). I am simply rewriting his tutorial to have all three bootloaders in this tutorial.

So, lets begin. To restore the grub, you must boot off the ubuntu live cd. Any ubuntu live cd will do.

Once there, open a terminal (Applications>Accessories>Terminal) and type this:

```
sudo grub
```Next, you need to find which hard drive ubuntu and the grub is installed to. You do this by running this command:

```
find /boot/grub/stage1
```Take note of what it returns (something like (hd0,1).)

Now you need to tell Grub where it is installed. Using the output of the last command, change this one and run it:

```
root (hd<a>,<b>)
```Replacing <a> and <b> with what you got back before. For example, if "find /boot/grub/stage1" gave me "(hd0,1)", you would run "root (hd0,1)"

Ok, so thats the configuration over and done with. Now we just need to run one command to install the Grub to your hard drive:

```
setup (hd0)
```Now to quit and check if it has worked:

```
quit
``````
sudo reboot
```Make sure you have taken the live cd out of your disc tray. All going well, you should start back up and see the grub once again.

 
[SIZE=5][COLOR=red]How to restore the Windows XP bootloader[/COLOR][/SIZE]

For this you will need your Windows XP installation CD. Boot into it now.

You will get to a part where it asks if you want to repair or recover. To do so, press "r".

If prompted, enter your Windows XP administrator password. This will leave you at at a command line, so type in the following two commands:

```
fixboot
``````
fixmbr
```Then type ```
exit
``` then remove your XP cd. If everything has gone well, you should come to your XP bootloader.


[SIZE=5][COLOR=red]How to restore the Windows Vista or 7 bootloader[/COLOR][/SIZE]

To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download for [Vista]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download") or [Win 7](http://neosmart.net/blog/2009/windows-7-system-repair-discs/).
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

```
bootrec.exe /fixboot
``````
bootrec.exe /fixmbr
```Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader.

---

### Post by maxideci on 2009-07-06
Hi, 

Nice tutorial there, I will work on it, but, I am not sure if the situation I find myself is same or not.

I have Dell Studio with preinstalled Vista Home SP1.
I made a 20 GB raw partion and installed Linux with Grub Bootloader.

On the initial boot screen (Grub), I see option of selecting Linux or Windows.

Next, using EasyBCD, I configured the Vista bootloader to show boot option of Microsoft Vista and Linux.

Currently, this is how the boot sequence is on my notebook.
->Initial boot screen : Grub (1-Linux, 2-Windows Vista)
->Once I select Windows, I get is another boot selection option 1-Microsoft Vista, 2-Linux.

What I prefer is to have only one boot option screen that is second one (Which i suppose is Windows Vista's bootloader), at the same time I want to keep Linux partition intact.

Simply putting it, I want to get rid of Grub bootloader, without getting rid of Linux partition.

If I follow your tutorial will I be able to achieve it ???

What is the standard procedure to install Linux, on a system with MS Vista, without disturbing the bootloader?

thanks in advance.

cheers!!

---

### Post by talsemgeest on 2009-07-06
> **maxideci said:**
> Hi, 

Nice tutorial there, I will work on it, but, I am not sure if the situation I find myself is same or not.

I have Dell Studio with preinstalled Vista Home SP1.
I made a 20 GB raw partion and installed Linux with Grub Bootloader.

On the initial boot screen (Grub), I see option of selecting Linux or Windows.

Next, using EasyBCD, I configured the Vista bootloader to show boot option of Microsoft Vista and Linux.

Currently, this is how the boot sequence is on my notebook.
->Initial boot screen : Grub (1-Linux, 2-Windows Vista)
->Once I select Windows, I get is another boot selection option 1-Microsoft Vista, 2-Linux.

What I prefer is to have only one boot option screen that is second one (Which i suppose is Windows Vista's bootloader), at the same time I want to keep Linux partition intact.

Simply putting it, I want to get rid of Grub bootloader, without getting rid of Linux partition.

If I follow your tutorial will I be able to achieve it ???

What is the standard procedure to install Linux, on a system with MS Vista, without disturbing the bootloader?

thanks in advance.

cheers!!
Ok, the easiest thing to do is to use easybcd to remove the option of linux, then to reinstall the grub bootloader, which should give you your one bootloader screen, and still allow you to access both ubuntu and windows.

Your other option is to reinstall the vista bootloader, and edit the grub so it only has one option.

It is up to you :)

---

### Post by Diamond.Dave on 2009-08-30
Ok, so I hosed something up...
System: Dell D820, 2 GB RAM, 80GB HD, T5500 processor
I've been playing with both XP and Ubuntu, and finally settled on a dual boot.  So, I read through all the threads and it seemed to say that it was best to start with WinXP and then boot up in to ubuntu and tell it to do a side by side install>
Put in the WinXP disk, had it wipe all the partitions (there were many) back to 1 big partition.  Got XP set up.  Then put in the Ubuntu disk, told it to side by side install - it did, then said it needed to reboot...
 
now I get GRUB Loading stage1.5.  
GRUB loading, please wait...
Error 22
 
I tried the above thread to reload the Ubuntu grub - no joy, still get the Error 22.  So I loaded the Ubuntu CD and ran fdisk -l:
 
[EMAIL="ubuntu@ubuntu"]ubuntu@ubuntu[/EMAIL]: ~$ sudo fdisk -l
 
Disk /dev/sda:80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316
 
    Device    Boot      Start         End            Blocks      Id    System
/dev/sda1    *             1            9729      78148161    7       HPFS/NTFS
 
I'm not an expert, but to me, I don't see where there's a Ubuntu partition here...am I missing something?

---

### Post by Diamond.Dave on 2009-08-30
Ok, might have solved my own problem.  I ran the above WinXP recovery, including fixboot and fixmbr, and it booted fine.  Then, in Computer Management, I looked at Disk Management, and it ONLY shows the C: partition...guess I messed up the Ubuntu load...will let you know after I try again!
Thanks!

---

### Post by Diamond.Dave on 2009-08-30
Yeah!  So it worked - actually followed the dual-boot instructions and setup the partitions ahead of time...all is well now!  Thanks for the thread.

---

### Post by talsemgeest on 2009-08-31
No problem, always glad to help! :)

---

### Post by emeraldgirl08 on 2009-09-26
Hey member me??!!!

Good to know I bookmarked this as reference! Needed it this evening :)

---

### Post by talsemgeest on 2009-09-26
> **emeraldgirl08 said:**
> Hey member me??!!!

Good to know I bookmarked this as reference! Needed it this evening :)
Haha, cool, happy to help again. I will be making a few screencasts to accompany this post, so that should be done in a few days.

---

### Post by bresdog on 2009-09-27
Put xp on an old laptop of mines that already had ubuntu, and obviously the GRUB menu has gone. Followed these steps and i've gotten this error message-

 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

Tried the suggestions here aswell-
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Any thoughts? Im still learning this stuff, any help is greatly appreciated. Soon i'll hopefully be giving advice back! Thanks

---

### Post by talsemgeest on 2009-09-27
> **bresdog said:**
> Put xp on an old laptop of mines that already had ubuntu, and obviously the GRUB menu has gone. Followed these steps and i've gotten this error message-

 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

Tried the suggestions here aswell-
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Any thoughts? Im still learning this stuff, any help is greatly appreciated. Soon i'll hopefully be giving advice back! Thanks
Have you made sure you have followed the instructions perfectly? Please post what you get when you run the ```
sudo grub
find /boot/grub/stage1
```
Also, while you are on the live cd, give us the output of ```
sudo fdisk -l
```

---

### Post by markuspxpx on 2009-09-28
How can I repair the Vista boot without dvd and from Ubuntu LIVECD ?
because my vista is updated do SP2 and the dvd is SP1 ....

so I can't use repair by the prompt option ...

I'm trying do by the ubuntu console this...

sudo apt-get install update - Ok done.
sudo apt-get install ms-sys - error: E: could not find the package ms-sys 

someone can help me ?

---

### Post by bresdog on 2009-09-28
> **talsemgeest said:**
> Have you made sure you have followed the instructions perfectly? Please post what you get when you run the ```
sudo grub
find /boot/grub/stage1
```
Also, while you are on the live cd, give us the output of ```
sudo fdisk -l
```

Yep followed the steps exactly. Heres the output-

```
grub> find /boot/grub/stage1

 (hd0,5)
```

```
ubuntu@ubuntu:~$ sudo fdisk -l

omitting empty partition (5)



Disk /dev/sda: 320.0 GB, 320072933376 bytes

255 heads, 63 sectors/track, 38913 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x80d2f3ee



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        5187    41664546    7  HPFS/NTFS

/dev/sda2            5188       38913   270904095    5  Extended

/dev/sda3           37880       38913     8305573+  82  Linux swap / Solaris

/dev/sda5            5188       37075   256140297   83  Linux

/dev/sda6           37076       37879     6458098+  82  Linux swap / Solaris
```

Any ideas?

---

### Post by talsemgeest on 2009-09-28
> **markuspxpx said:**
> How can I repair the Vista boot without dvd and from Ubuntu LIVECD ?
because my vista is updated do SP2 and the dvd is SP1 ....

so I can't use repair by the prompt option ...

I'm trying do by the ubuntu console this...

sudo apt-get install update - Ok done.
sudo apt-get install ms-sys - error: E: could not find the package ms-sys 

someone can help me ?
As far as I know there is no way to restore the vista bootloader from the Ubuntu Live CD. However, there is a free download of the vista recovery disk which should do the same thing as the vista installation dvd. Download it from [here](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/) and follow my instructions for the reinstallation of the vista bootloader.

---

### Post by talsemgeest on 2009-09-28
> **bresdog said:**
> Yep followed the steps exactly. Heres the output-

```
grub> find /boot/grub/stage1

 (hd0,5)
```

```
ubuntu@ubuntu:~$ sudo fdisk -l

omitting empty partition (5)



Disk /dev/sda: 320.0 GB, 320072933376 bytes

255 heads, 63 sectors/track, 38913 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x80d2f3ee



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        5187    41664546    7  HPFS/NTFS

/dev/sda2            5188       38913   270904095    5  Extended

/dev/sda3           37880       38913     8305573+  82  Linux swap / Solaris

/dev/sda5            5188       37075   256140297   83  Linux

/dev/sda6           37076       37879     6458098+  82  Linux swap / Solaris
```

Any ideas?
So running ```
sudo grub
root (hd0,5)
setup (hd0)
``` gives you the above error?

---

### Post by bresdog on 2009-09-29
It did yeah. After follwoing some steps in a couple of other threads I ended up getting Error 17: Cannot Mount Partition. Gave up there for a couple of hours as i had other stuff to do, when i came back and tried to sort that error it had magically become Error 15: File not Found (along those lines). Turns out my entire hard drive was wiped, and both partitions deleted. Not sure how that happened. Quite a pain in the ***:frown:

---

### Post by talsemgeest on 2009-09-29
> **bresdog said:**
> It did yeah. After follwoing some steps in a couple of other threads I ended up getting Error 17: Cannot Mount Partition. Gave up there for a couple of hours as i had other stuff to do, when i came back and tried to sort that error it had magically become Error 15: File not Found (along those lines). Turns out my entire hard drive was wiped, and both partitions deleted. Not sure how that happened. Quite a pain in the ***:frown:
Ouch, I'm sorry to hear that. Have you tried recovery tools like testdisk?

---

### Post by bresdog on 2009-09-29
I'll try that when i get back home, in work at the minute. I need xp for some work stuff that was why i was installing it, tried to do a clean install of that on the whole hard drive and its bringing up  Non System Disk error. Tried fixmbr and that didn't work. I'll probably just stick Ubuntu on it again. Thanks for the help anyway!

---

### Post by markuspxpx on 2009-09-29
> **talsemgeest said:**
> as far as i know there is no way to restore the vista bootloader from the ubuntu live cd. However, there is a free download of the vista recovery disk which should do the same thing as the vista installation dvd. Download it from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and follow my instructions for the reinstallation of the vista bootloader.


thank you alot !

---

### Post by talsemgeest on 2009-09-29
> **bresdog said:**
> I'll try that when i get back home, in work at the minute. I need xp for some work stuff that was why i was installing it, tried to do a clean install of that on the whole hard drive and its bringing up  Non System Disk error. Tried fixmbr and that didn't work. I'll probably just stick Ubuntu on it again. Thanks for the help anyway!

Ok, hope it all works out for you :)

> **markuspxpx said:**
> thank you alot !
Not a problem, always happy to help.

---

### Post by shadowhawk2008 on 2009-11-08
Tried to update grub to grub 2 in karmic koala. Chainloader worked fine so I update from grub legacy.  So far when I start the computer I get error 15. I've followed the instructions to reinstall grub bootloader for ubuntu 9.10 but when I enter sudo grub-install –root-directory=/media/sda5 /dev/sda I get a message saying "Unrecognised option -root-directory=media/sda5 and a  load of different options like type h for help and v for version number etc. No installations take place though (BTW, my ubuntu is on /dev/sda5 aswell). I'm running a dual boot between Win Vista and Ubuntu 9.10. 

Photos:
[http://www.flickr.com/photos/35581816@N03/4086419946/](http://www.flickr.com/photos/35581816@N03/4086419946/) what appears after running sudo fdisk -l

[http://www.flickr.com/photos/35581816@N03/4085659385/](http://www.flickr.com/photos/35581816@N03/4085659385/) Unrecognised option message when running sudo grub-install

[http://www.flickr.com/photos/35581816@N03/4085657751/in/photostream/](http://www.flickr.com/photos/35581816@N03/4085657751/in/photostream/) grub error 15

---

### Post by talsemgeest on 2009-11-08
> **shadowhawk2008 said:**
> Tried to update grub to grub 2 in karmic koala. Chainloader worked fine so I update from grub legacy.  So far when I start the computer I get error 15. I've followed the instructions to reinstall grub bootloader for ubuntu 9.10 but when I enter sudo grub-install &#8211;root-directory=/media/sda5 /dev/sda I get a message saying "Unrecognised option -root-directory=media/sda5 and a  load of different options like type h for help and v for version number etc. No installations take place though (BTW, my ubuntu is on /dev/sda5 aswell). I'm running a dual boot between Win Vista and Ubuntu 9.10. 

Photos:
[http://www.flickr.com/photos/35581816@N03/4086419946/](http://www.flickr.com/photos/35581816@N03/4086419946/) what appears after running sudo fdisk -l

[http://www.flickr.com/photos/35581816@N03/4085659385/](http://www.flickr.com/photos/35581816@N03/4085659385/) Unrecognised option message when running sudo grub-install

[http://www.flickr.com/photos/35581816@N03/4085657751/in/photostream/](http://www.flickr.com/photos/35581816@N03/4085657751/in/photostream/) grub error 15
Thank you for that, it seems I made a typo in my post. There should be an extra dash in the command, this: ```
sudo grub-install --root-directory=/media/sda5 /dev/sda
``` instead of this: ```
sudo grub-install -root-directory=/media/sda5 /dev/sda
```Hope I havent caused you too much inconvenience. :)

---

### Post by shadowhawk2008 on 2009-11-11
Thank you. Will try it again when I get back to my ubuntu box. 

:)

---

### Post by von Stalhein on 2009-11-13
After following oyur clear and easy directions I got this output in the LiveCD terminal: -
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3f79c20

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       14593   117210240    f  W95 Ext'd (LBA)
/dev/sda5               2       14593   117210208+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x960c960c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf66fc667

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       18705   150247881   83  Linux
/dev/sdc2           18706       19457     6040440    5  Extended
/dev/sdc5           18706       19457     6040408+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mkdir /media/sdc1
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /media/sdc1
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sdc1 /dev/sdc1
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator
Installing GRUB to /dev/sdc1 as (hd2,0)...
Installation finished. No error reported.
This is the contents of the device map /media/sdc1/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
```

However, when I try reboot I get the "Error 15" I notice it's still trying to load GRUB stage1.5 - could that be the problem??

This is after a clean install using the alternate CD on a machine that used to boot XP & 9.04. I can still boot XP by changing the boot order in BIOS.

TIA

---

### Post by talsemgeest on 2009-11-13
> **von Stalhein said:**
> After following oyur clear and easy directions I got this output in the LiveCD terminal: -
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3f79c20

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       14593   117210240    f  W95 Ext'd (LBA)
/dev/sda5               2       14593   117210208+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x960c960c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf66fc667

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       18705   150247881   83  Linux
/dev/sdc2           18706       19457     6040440    5  Extended
/dev/sdc5           18706       19457     6040408+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mkdir /media/sdc1
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /media/sdc1
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sdc1 /dev/sdc1
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator
Installing GRUB to /dev/sdc1 as (hd2,0)...
Installation finished. No error reported.
This is the contents of the device map /media/sdc1/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
```

However, when I try reboot I get the "Error 15" I notice it's still trying to load GRUB stage1.5 - could that be the problem??

This is after a clean install using the alternate CD on a machine that used to boot XP & 9.04. I can still boot XP by changing the boot order in BIOS.

TIA
Which Live CD are you using? I am pretty sure it needs to be a 9.10 Live CD for it to work, as every previous release only has support for Grub 1.5.

---

### Post by shadowhawk2008 on 2009-11-14
Yep the change worked, it installed without a hitch and there's no more error 15 on boot! Thank you!

---

### Post by talsemgeest on 2009-11-14
> **shadowhawk2008 said:**
> Yep the change worked, it installed without a hitch and there's no more error 15 on boot! Thank you!
Excellent, I'm glad it worked. :)

---

### Post by von Stalhein on 2009-11-14
> **talsemgeest said:**
> Which Live CD are you using? I am pretty sure it needs to be a 9.10 Live CD for it to work, as every previous release only has support for Grub 1.5.

I used the Alternate, and from the cli. I can't get it to a GUI from the 9.10 CD, it gives "Cannot display this video mode".

I might try another reinstall, it should work "out of the box" with a clean drive!!

I thought it might have been an MBR issue. I booted from an XP disk to do a fixboot etc, but couldn't get into the ecovery console.

When it rebooted, I had forgotten to take the CD from the drive, and it it went to the GRUB2 screen, I thought that the fix had worked. I selected 9.10 it started to load, but again went to the video message as above. 

Ignoring that issue at the time, I rebooted sans XP CD, but the same Error 15 and the GRUB 1.5 dialogue reappeared. Back to square one :-)

4 hrs later: - I've reinstalled again, and run the code again - success!!! It goes to the GRUB menu, and will boot 9.10. Unfortunately I still have some video issues, no gui, so back to Google.

---

### Post by talsemgeest on 2009-11-14
Well unfortunately Im not sure if the Alternate cd has the neccesary tools to do it. Sorry I cant be of more help.

---

### Post by von Stalhein on 2009-11-15
I celebrated to soon. 

I can boot into 9.10from the GRUB2 menu and get to a cli, but now I can't boot XP.

If I could get the live cd into GUI, I think life would be a lot easier. I'd love to know why a 9.04 will do so but a Karmic one won't.

Just fiddling a bit with grub.cfg, and if no luck there I'll have to do a fixboot or fixmbr and start again.

---

### Post by talsemgeest on 2009-11-15
> **von Stalhein said:**
> I celebrated to soon. 

I can boot into 9.10from the GRUB2 menu and get to a cli, but now I can't boot XP.

If I could get the live cd into GUI, I think life would be a lot easier. I'd love to know why a 9.04 will do so but a Karmic one won't.

Just fiddling a bit with grub.cfg, and if no luck there I'll have to do a fixboot or fixmbr and start again.
The grub.cfg is **not **designed to be edited by hand. You are supposed to edit the file /etc/default/grub, and the files in /etc/grub.d/, before running update-grub to implement the changes.

---

### Post by von Stalhein on 2009-11-17
It's all good, I managed to get the system installed (with a GUI and everything!!) and GRUB2.

However, for some reason, GRUB2 installs but even though XP is on /dev/sda it keeps designating /dev/sdb1, which is just an NTFS data drive. 

I've done the update-grub cmd from a terminal in Karmic without any change, despite what sudo fdisk -l says.

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3f79c20

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       14593   117210240    f  W95 Ext'd (LBA)
/dev/sda5               2       14593   117210208+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x960c960c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf66fc667

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1309    10514511   83  Linux
/dev/sdc2           18706       19457     6040440    5  Extended
/dev/sdc3            1310       18705   139733370   83  Linux
/dev/sdc5           18706       19457     6040408+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

How do I change it to the XP boot which is /dev/sda ??

---

### Post by talsemgeest on 2009-11-17
Take a look [here](http://ubuntuforums.org/showthread.php?t=1195275), especially the section "Adding entries to Grub 2", that page should have everything you need to know.

---

### Post by dastrn on 2009-11-19
I have 9.10 64 bit installed. I setup Windows 7 this morning, and ran into the whole "no way to get into Ubuntu" problem.

When I boot from the livecd, I did all this stuff. But when I run the sudo grub-install --root-dire... line, I am told:

grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read grub/core.img correctly

Anyone know what to do?

---

### Post by talsemgeest on 2009-11-19
> **dastrn said:**
> I have 9.10 64 bit installed. I setup Windows 7 this morning, and ran into the whole "no way to get into Ubuntu" problem.

When I boot from the livecd, I did all this stuff. But when I run the sudo grub-install --root-dire... line, I am told:

grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read grub/core.img correctly

Anyone know what to do?
From that error message it looks as though you have mounted the wrong disk. After running ```
sudo mkdir /media/sdax
sudo mount /dev/sdax /media/sdax
```
take a look in /media/sdax (the directory you just created), then go to /boot/grub/ and look for the file "core.img". If you cannot find it, it means you are using the wrong drive.

---

### Post by von Stalhein on 2009-11-20
> **talsemgeest said:**
> Take a look [here](http://ubuntuforums.org/showthread.php?t=1195275), especially the section "Adding entries to Grub 2", that page should have everything you need to know.

Hello talsemgeest,
I added XP in various combinations of dev & partition, without luck.
As per the tute I chmodded every 50_XX script and sudo update-grub, no dice.

I will prevail, I just need to find the key. 
Or the blue pill. ;)

---

### Post by Uriolaf on 2009-11-24
Hello,

I am quite new to Ubuntu and Linux. I downloaded Ubuntu 9.10 cd image, burned the cd and tried to install from it.

After I tried to reboot, this is what appeared on the screen:

> 
[FONT=Courier New]
[SIZE=2]GRUB loading.
error: biosdisk read error
grub rescue>_[/SIZE]
[/FONT] 
And I wasn't able to boot into neither Windows nor Ubuntu. All I could do is "repair" master boot record with Windows cd, and then managed to boot into Windows. Then I found this topic, tried... and... still cannot boot into Ubuntu. :(

I tried to follow the instructions -- booted with Ubuntu cd, opened terminal, here is what I did:

> 
[FONT=Courier New][SIZE=2]
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 61.5 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd43ad43a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        7476    39568095    b  W95 FAT32

Disk /dev/sdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00057581

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         977     7847721   83  Linux
/dev/sdb2             978        1027      401625    5  Extended
/dev/sdb5             978        1027      401593+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mkdir /media/sdb1
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /media/sdb1
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sdb1 /dev/sda
Installation finished. No error reported.
This is the contents of the device map /media/sdb1/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
ubuntu@ubuntu:~$ [/SIZE][/FONT]     



It didn't help. I still cannot boot Ubuntu. :(
What can be the problem?

Please, help!

---

### Post by Uriolaf on 2009-11-24
Hello,

I am quite new to Ubuntu and Linux. I downloaded Ubuntu 9.10 cd image, burned the cd and tried to install from it.

After I tried to reboot, this is what appeared on the screen:

> 
[FONT=Courier New]
[SIZE=2]GRUB loading.
error: biosdisk read error
grub rescue>_[/SIZE]
[/FONT] 
And I wasn't able to boot into neither Windows nor Ubuntu. All I could do is "repair" master boot record with Windows cd, and then managed to boot into Windows. Then I found this topic, tried... and... still cannot boot into Ubuntu. :(

I tried to follow the instructions -- booted with Ubuntu cd, opened terminal, here is what I did:

> 
[FONT=Courier New][SIZE=2]
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 61.5 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd43ad43a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        7476    39568095    b  W95 FAT32

Disk /dev/sdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00057581

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         977     7847721   83  Linux
/dev/sdb2             978        1027      401625    5  Extended
/dev/sdb5             978        1027      401593+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mkdir /media/sdb1
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /media/sdb1
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sdb1 /dev/sda
Installation finished. No error reported.
This is the contents of the device map /media/sdb1/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
ubuntu@ubuntu:~$ [/SIZE][/FONT]     



It didn't help. I still cannot boot Ubuntu, again I'm getting the same error messages instead. :(
What can be the problem?

Please, help!

---

### Post by talsemgeest on 2009-11-24
> **Uriolaf said:**
> Hello,

I am quite new to Ubuntu and Linux. I downloaded Ubuntu 9.10 cd image, burned the cd and tried to install from it.

After I tried to reboot, this is what appeared on the screen:

And I wasn't able to boot into neither Windows nor Ubuntu. All I could do is "repair" master boot record with Windows cd, and then managed to boot into Windows. Then I found this topic, tried... and... still cannot boot into Ubuntu. :(

I tried to follow the instructions -- booted with Ubuntu cd, opened terminal, here is what I did:



It didn't help. I still cannot boot Ubuntu, again I'm getting the same error messages instead. :(
What can be the problem?

Please, help!
Hi, this is a [known issue](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/396564), you may want to subscribe to the bug to be notified when this is fixed. However, most of the users with this problem are using some form of RAID setup (using 2 or more hard drives as a single hard drive). Are you doing anything like this?

As a workaround you may want to use Ubuntu 9.04, at least until the problem is fixed.

Also, it is best not to double post, thanks :)

---

### Post by Uriolaf on 2009-11-24
> **talsemgeest said:**
> Hi, this is a [known issue]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/396564"), you may want to subscribe to the bug to be notified when this is fixed. However, most of the users with this problem are using some form of RAID setup (using 2 or more hard drives as a single hard drive). Are you doing anything like this?

As a workaround you may want to use Ubuntu 9.04, at least until the problem is fixed.


Thank you. I don't use  RAID setup. I just have two hard disks, one for Windows and now one for Ubuntu.

> 
Also, it is best not to double post, thanks :)


Sorry, wasn't on purpose. I wanted to edit the post and somehow posted it again. :oops: I can't delete it.

---

### Post by talsemgeest on 2009-11-24
> **Uriolaf said:**
> Thank you. I don't use  RAID setup. I just have two hard disks, one for Windows and now one for Ubuntu.



Sorry, wasn't on purpose. I wanted to edit the post and somehow posted it again. :oops: I can't delete it.
Also, which Ubuntu CD did you install from?

---

### Post by berserkpi on 2009-11-25
Hi there. I tried to restore GRUB bootloader using your steps:

1) ```
fdisk -l
```

I figured out whar my root is...

/dev/sda1 -> Win7
/dev/sda2 -> Extended
/dev/sda5 -> Linux install (root)
/dev/sda6 -> Linux (home)
/dev/sda7 -> Swap

2) ```
mount /dev/sda5 /media/sda5
```

I dont have a boot partition, thus, I suppose my boot is /boot under root (device: /dev/sda5).

3) ```
grub-install --root-directory=/media/sda5 /dev/sda
```

After this I got the device.map message, this file contains just the reference to my hd.

4) OK, now reboot. But then I just got the 'GRUB's Minimal BASH-like' :(. I mean, I can't get into the boot menu, I just get this grub's command line.

What to do now?. Did I do something wrong?. I hope u can help me on this.

---

### Post by talsemgeest on 2009-11-25
> **berserkpi said:**
> Hi there. I tried to restore GRUB bootloader using your steps:

1) ```
fdisk -l
```I figured out whar my root is...

/dev/sda1 -> Win7
/dev/sda2 -> Extended
/dev/sda5 -> Linux install (root)
/dev/sda6 -> Linux (home)
/dev/sda7 -> Swap

2) ```
mount /dev/sda5 /media/sda5
```I dont have a boot partition, thus, I suppose my boot is /boot under root (device: /dev/sda5).

3) ```
grub-install --root-directory=/media/sda5 /dev/sda
```After this I got the device.map message, this file contains just the reference to my hd.

4) OK, now reboot. But then I just got the 'GRUB's Minimal BASH-like' :(. I mean, I can't get into the boot menu, I just get this grub's command line.

What to do now?. Did I do something wrong?. I hope u can help me on this.
Can you post the output of the commands you have run (into [noparse]```

```[/noparse] tags preferably). That will make it easier to tell what the problem is. Also, after running ```
mount /dev/sda5 /media/sda5
```, take a look in /media/sda5/boot/ and see if the normal grub files are there.

---

### Post by berserkpi on 2009-11-25
> **talsemgeest said:**
> Can you post the output of the commands you have run (into [noparse]```

```[/noparse] tags preferably). That will make it easier to tell what the problem is. Also, after running ```
mount /dev/sda5 /media/sda5
```, take a look in /media/sda5/boot/ and see if the normal grub files are there.

I couldn't post the outputs coz I was in another pc, sorry for that. I got the following  outputs:

1) sudo fdisk -l   

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       14593    76260555    5  Extended
/dev/sda5            5100        7531    19535008+  83  Linux
/dev/sda6            7532       14339    54685228+  83  Linux
/dev/sda7           14340       14593     2040223+  82  Linux swap / Solaris
```

So, my root is sda5 -(hd0,4) in grub's notation-.

2) sudo mount /dev/sda5 /media/sda5
```

no outout
```

3) Running ```
ls /media/sda5/boot
``` I get:

```
abi-2.6.28-16-generic     config-2.6.31-15-generic      memtest86+.bin                vmcoreinfo-2.6.31-14-generic
abi-2.6.31-14-generic     grub                          System.map-2.6.28-16-generic  vmcoreinfo-2.6.31-15-generic
abi-2.6.31-15-generic     initrd.img-2.6.28-16-generic  System.map-2.6.31-14-generic  vmlinuz-2.6.28-16-generic
config-2.6.28-16-generic  initrd.img-2.6.31-14-generic  System.map-2.6.31-15-generic  vmlinuz-2.6.31-14-generic
config-2.6.31-14-generic  initrd.img-2.6.31-15-generic  vmcoreinfo-2.6.28-16-generic  vmlinuz-2.6.31-15-generic
```

So... that is my boot, no doubt.

4) sudo grub-install --root-directory=/media/sda5 /dev/sda

output:
```
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect, fix it and re-run the script 'grub-install'.
```

Everything was ok at this point, but when I rebooted, GRUB just showed the shell (there was no menu)... u know:

```
[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub>
```

So, this **was** my problem, and I say was coz I already solved it. I'll explain this in my next reply -in a few minutes-.

---

### Post by berserkpi on 2009-11-25
Ok as I promised, this is how I restored my grub.

1) I downloaded a Super grub disk from: [http://www.supergrubdisk.org/index.php?pid=5]("http://www.supergrubdisk.org/index.php?pid=5")

2) I burned it on a CD and rebooted my system using it. I just made sure My BIOS could reboot fron CD.

It gives two options:

Boot Ubuntu GNU/Linux
AUTO MAGIC BOOT

Both of them worked like a charm for me. Once I got into my beloved KDE desktop I fixed the problem...

3) I just followed the steps at the beginning of this post. 

In my case:

```
sudo grub
```
```
grub> find /boot/grub/stage1
```
output: ```
(hd0,4)
```
```
grub> root (hd0,4)
```
```
grub> setup (hd0)
```
```
grub> quit
```

4) After that, I just edited my menu.lst (so I could boot win7):

```
sudo gedit /boot/grub/menu.lst
```

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
[B]title		Microsoft Windows 7 Ultimate
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1[/B]
```

---------------------------------

Ok, question time: What I did in step 3 means that my GRUB is not version 2?. How can I check the GRUB's version?

Also, booting from live CD, grub seems not to be installed. In those cases, can I install it using apt-get ??. Do I need internet connection?... or perhaps... install it from the CD??

Thak u very much for ur help. :)

---

### Post by talsemgeest on 2009-11-25
> **berserkpi said:**
> Ok as I promised, this is how I restored my grub.

1) I downloaded a Super grub disk from: [http://www.supergrubdisk.org/index.php?pid=5]("http://www.supergrubdisk.org/index.php?pid=5")

2) I burned it on a CD and rebooted my system using it. I just made sure My BIOS could reboot fron CD.

It gives two options:

Boot Ubuntu GNU/Linux
AUTO MAGIC BOOT

Both of them worked like a charm for me. Once I got into my beloved KDE desktop I fixed the problem...

3) I just followed the steps at the beginning of this post. 

In my case:

```
sudo grub
```
```
grub> find /boot/grub/stage1
```
output: ```
(hd0,4)
```
```
grub> root (hd0,4)
```
```
grub> setup (hd0)
```
```
grub> quit
```

4) After that, I just edited my menu.lst (so I could boot win7):

```
sudo gedit /boot/grub/menu.lst
```

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
[B]title		Microsoft Windows 7 Ultimate
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1[/B]
```

---------------------------------

Ok, question time: What I did in step 3 means that my GRUB is not version 2?. How can I check the GRUB's version?

Also, booting from live CD, grub seems not to be installed. In those cases, can I install it using apt-get ??. Do I need internet connection?... or perhaps... install it from the CD??

Thak u very much for ur help. :)
Well, if ```
sudo grub
``` actually works, it means you are using a version of ubuntu less than 9.10, that still uses grub 1.5. So, if you had followed the instructions for Ubuntu 9.04, using the Ubuntu 9.04 cd, that would have worked for you.

---

### Post by von Stalhein on 2009-11-26
I've not made much progress. I disconnected my other HDD to leave the XP disk and the Karmic one, and re-installed GRUB.

Output of sudo update-grub
```
 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done

```

Output of blkid
```
/dev/sda1: UUID="01C3D871F965AC80" LABEL="DSK1_VOL1" TYPE="ntfs" 
/dev/sdb5: UUID="27179ee5-e990-4dcb-9fc8-a5857a0f1b37" TYPE="swap" 
/dev/sdb1: UUID="ece48d4f-95ce-4c32-8ae6-20c3f3563597" TYPE="ext4" 
/dev/sdb2: UUID="b073ff20-47f8-440f-98fc-5bbc5fcbbd8d" TYPE="ext4"
```


My grub.cfg
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set ece48d4f-95ce-4c32-8ae6-20c3f3563597
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set ece48d4f-95ce-4c32-8ae6-20c3f3563597
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=ece48d4f-95ce-4c32-8ae6-20c3f3563597 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set ece48d4f-95ce-4c32-8ae6-20c3f3563597
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=ece48d4f-95ce-4c32-8ae6-20c3f3563597 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set ece48d4f-95ce-4c32-8ae6-20c3f3563597
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ece48d4f-95ce-4c32-8ae6-20c3f3563597 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set ece48d4f-95ce-4c32-8ae6-20c3f3563597
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ece48d4f-95ce-4c32-8ae6-20c3f3563597 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 01c3d871f965ac80
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

The Ubuntu disk is first in boot order in the BIOS

Output of fdisk -l /dev/sda
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x960c960c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    7  HPFS/NTFS
```

Output of fdisk -l /dev/sdb
```
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf66fc667

```

Unless I'm much mistaken, the above is all in order - happy to be corrected.

Before posting this I swapped the boot order and XP boots up fine, so it's not an MBR or fixboot issue. 

When selected in the GRUB menu, the XP HDD LED operates while a blinking bar is on the screen, then the screen fades and a hard reset is necessary - it's almost as if there is something in the boot command that fails to kick it over the hump. :confused:

Happy to redo or do any troubleshooting recommended, I can't believe this won't go - gotta be between the chair and keyboard issue!!! :p

---

### Post by talsemgeest on 2009-11-26
> **von Stalhein said:**
> I've not made much progress. I disconnected my other HDD to leave the XP disk and the Karmic one, and re-installed GRUB.

Output of sudo update-grub
```
 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done

```

Output of blkid
```
/dev/sda1: UUID="01C3D871F965AC80" LABEL="DSK1_VOL1" TYPE="ntfs" 
/dev/sdb5: UUID="27179ee5-e990-4dcb-9fc8-a5857a0f1b37" TYPE="swap" 
/dev/sdb1: UUID="ece48d4f-95ce-4c32-8ae6-20c3f3563597" TYPE="ext4" 
/dev/sdb2: UUID="b073ff20-47f8-440f-98fc-5bbc5fcbbd8d" TYPE="ext4"
```


My grub.cfg
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set ece48d4f-95ce-4c32-8ae6-20c3f3563597
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set ece48d4f-95ce-4c32-8ae6-20c3f3563597
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=ece48d4f-95ce-4c32-8ae6-20c3f3563597 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set ece48d4f-95ce-4c32-8ae6-20c3f3563597
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=ece48d4f-95ce-4c32-8ae6-20c3f3563597 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set ece48d4f-95ce-4c32-8ae6-20c3f3563597
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ece48d4f-95ce-4c32-8ae6-20c3f3563597 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set ece48d4f-95ce-4c32-8ae6-20c3f3563597
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ece48d4f-95ce-4c32-8ae6-20c3f3563597 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 01c3d871f965ac80
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

The Ubuntu disk is first in boot order in the BIOS

Output of fdisk -l /dev/sda
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x960c960c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    7  HPFS/NTFS
```

Output of fdisk -l /dev/sdb
```
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf66fc667

```

Unless I'm much mistaken, the above is all in order - happy to be corrected.

Before posting this I swapped the boot order and XP boots up fine, so it's not an MBR or fixboot issue. 

When selected in the GRUB menu, the XP HDD LED operates while a blinking bar is on the screen, then the screen fades and a hard reset is necessary - it's almost as if there is something in the boot command that fails to kick it over the hump. :confused:

Happy to redo or do any troubleshooting recommended, I can't believe this won't go - gotta be between the chair and keyboard issue!!! :p
Well, as it seems to be a problem with grub 2, and it still happens after a reinstall of grub2 (I'm pretty sure you have done reinstalls of Ubuntu as well?), it is classified as a bug. All I can suggest is that you file a bug report (as per [this post](http://ubuntuforums.org/showthread.php?t=1011078)). Either it is not a bug and the devs there will figure out the exact problem, or it is a bug and it gets fixed, both for you and for everyone else having the same problem as you. :)

I am sorry I have no more ideas, by all means it should be working.

---

### Post by von Stalhein on 2009-11-26
Thanks talsemgeest, I've listed it as a bug.

---

### Post by phillw on 2009-11-26
drs has a good how-to over this way --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It covers such delights as re-installing Grub from a boot disk, etc.

His more in-depth one is over here --> [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

For anyone running Wubi it's all slightly different .....

> [http://ubuntuforums.org/showthread.php?t=1335464&page=3](http://ubuntuforums.org/showthread.php?t=1335464&page=3)  Is the current proposed solution.

Phill.

---

### Post by talsemgeest on 2009-11-26
> **phillw said:**
> drs has a good how-to over this way --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It covers such delights as re-installing Grub from a boot disk, etc.

His more in-depth one is over here --> [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Haha, you got me! I actually used his grub2 tutorial when updating my tutorial for Ubuntu 9.10. I have thanked him very much on IRC for it though ;)

> **phillw said:**
> 

For anyone running Wubi it's all slightly different .....

  Is the current proposed solution.

Phill.

Hmm, what does wubi have to do with grub2? I thought that it uses the windows bootloader to boot, everything else is self-contained?

---

### Post by kansasnoob on 2009-11-26
I've not read every post so excuse me if I'm just repeating something. Given the number of grub2 failures and the number of those who lack a restore disc or the ability to burn one I decided to give ms-sys another look.

Well, forget ms-sys! Hello mbr! I've only been able to test this with Win XP but it's supposed to work with Vista and Win7 as well.

Boot your Ubuntu Live CD and run "sudo fdisk -l" just to determine which drive you want the mbr on. Then:

```
sudo apt-get install mbr
```

and:

```
sudo install-mbr /dev/sdX
```

(of course replace the X with your destination)

Then just reboot.

I actually tried that with XP and it worked fine.

I may be able to try that with Win7 in the next couple of days.

---

### Post by talsemgeest on 2009-11-27
Thanks for the help, I will try to incorporate it into the guide tomorrow. :)

---

### Post by Uriolaf on 2009-11-27
> **talsemgeest said:**
> Also, which Ubuntu CD did you install from?

I burned it from iso image named "Ubuntu Desktop 9.10 (32 bit)", which I downloaded here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) [URL="http://www.ubuntu.com/getubuntu/download"]
[/URL]

---

### Post by von Stalhein on 2009-11-27
talsemgeest - can you recommend a link for installing the older grub and replacing Grub 2?

I know the legacy one worked, and in the interim I'd like to use that, if I can find out how to :D

I've googled and found heaps on upgrading, but not downgrading.

Whoops!! Ignore that. Using different search words, found [http://ubuntuforums.org/showpost.php?p=8341799&postcount=4](http://ubuntuforums.org/showpost.php?p=8341799&postcount=4)

---

### Post by von Stalhein on 2009-11-27
The legacy version is back on and works a treat.

I did a little happy dance, but I am still perplexed.

---

### Post by berserkpi on 2009-11-27
> **talsemgeest said:**
> Well, if ```
sudo grub
``` actually works, it means you are using a version of ubuntu less than 9.10, that still uses grub 1.5. So, if you had followed the instructions for Ubuntu 9.04, using the Ubuntu 9.04 cd, that would have worked for you.

I'm not sure about that, look:


```
lsb_release -a
```

output:

```
Distributor ID: Ubuntu
Description:    Ubuntu 9.10
Release:        9.10
Codename:       karmic
```

```
sudo grub
```

output:

```
[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>
```

So, there is something extrange here ...:confused:

---

### Post by von Stalhein on 2009-11-27
I have read in my recent copious research of installations that did not completely overwrite the legacy version, and the situation you describe above occurring. It was to do with MBR issue IIRC.

I'm sorry, I don't remember exactly where.

I would suggest giving Google a flogging for similar situations and hopefully the remedy.

---

### Post by talsemgeest on 2009-11-27
> **von Stalhein said:**
> I have read in my recent copious research of installations that did not completely overwrite the legacy version, and the situation you describe above occurring. It was to do with MBR issue IIRC.

I'm sorry, I don't remember exactly where.

I would suggest giving Google a flogging for similar situations and hopefully the remedy.
Thanks for that von Stalhein :)

All I can guess is that perhaps you upgraded from 9.04 and grub2 didn't install?

---

### Post by dohzer on 2009-11-28
I'm having a similar problem to berserkpi. I followed the steps for Ubuntu 9.10 Grub repair, and when I reboot I simply get a Grub command line... it doesn't boot an OS or go anywhere.

> **berserkpi said:**
> 4) OK, now reboot. But then I just got the 'GRUB's Minimal BASH-like' :(. I mean, I can't get into the boot menu, I just get this grub's command line.

What to do now?. Did I do something wrong?. I hope u can help me on this.

I've got a Dell Vostro 1520 with Windows XP, Windows Vista (don't use it) and Ubuntu 9.10 installed. For some reason, occasionally when I reboot from Windows (say if I want to go into Linux), the Grub boot loader seems to be corrupting and it keeps power cycling after trying to load Grub. Last time I fixed it by simply formatting my Linux partition and reinstalling Ubuntu, but I'd rather keep the installation if I can this time.

Here's my computer setup:

I have three operating systems that were installed in the following order:

Windows XP
Windows Vista
Ubuntu 9.10

Here is the partition setup:
```

/dev/sda = 320GB Drive
/dev/sda1 = Windows XP Install
/dev/sda2 = 241GB Extended
/dev/sda5 = Windows Vista Install
/dev/sda6 = Ubuntu 9.10 Install
/dev/sda7 = Swap Partiton
/dev/sda8 = 16GB FAT32 Partition (random data)
/dev/sda9 = 117GB NTFS Partition (random data)
``````
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9561    76798701    7  HPFS/NTFS
/dev/sda2            9562       38912   235761907+   f  W95 Ext'd (LBA)
/dev/sda5            9562       19122    76798701    7  HPFS/NTFS
/dev/sda6           19123       21672    20482843+  83  Linux
/dev/sda7           21673       22716     8385898+  82  Linux swap / Solaris
/dev/sda8           22717       24628    15358108+   b  W95 FAT32
/dev/sda9           24629       38912   114736198+   7  HPFS/NTFS
```The first time I tried fixing Grub, I just ran through the steps in the OP, and everything seemed to go to plan, but I probably wasn't paying much attention to the terminal outputs. I tried it again a minutes ago, and I get the below error from the following command:

Command:
```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda6 /dev/sda
```Output:
```
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /media/sda6/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda

```This is what is inside /boot/grub/device.map:

```
(hd0)    /dev/sda
```Does that look correct? Should there be a complete list of all partitions?
Is there anything else I need to do/try?

---

### Post by dohzer on 2009-11-29
After rebooting and re-loading Ubuntu from the install CD, I just retried the Grub2 recovery steps from the OP, and the results seem to be inconsistent:

This time I get:

```
ubuntu@ubuntu:~$ sudo mkdir /media/sda6
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /media/sda6
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda6 /dev/sda6
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

```

I didn't get that warning the last time I used those commands. :confused:

---

### Post by talsemgeest on 2009-11-29
> **dohzer said:**
> I'm having a similar problem to berserkpi. I followed the steps for Ubuntu 9.10 Grub repair, and when I reboot I simply get a Grub command line... it doesn't boot an OS or go anywhere.



I've got a Dell Vostro 1520 with Windows XP, Windows Vista (don't use it) and Ubuntu 9.10 installed. For some reason, occasionally when I reboot from Windows (say if I want to go into Linux), the Grub boot loader seems to be corrupting and it keeps power cycling after trying to load Grub. Last time I fixed it by simply formatting my Linux partition and reinstalling Ubuntu, but I'd rather keep the installation if I can this time.

Here's my computer setup:

I have three operating systems that were installed in the following order:

Windows XP
Windows Vista
Ubuntu 9.10

Here is the partition setup:
```

/dev/sda = 320GB Drive
/dev/sda1 = Windows XP Install
/dev/sda2 = 241GB Extended
/dev/sda5 = Windows Vista Install
/dev/sda6 = Ubuntu 9.10 Install
/dev/sda7 = Swap Partiton
/dev/sda8 = 16GB FAT32 Partition (random data)
/dev/sda9 = 117GB NTFS Partition (random data)
``````
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9561    76798701    7  HPFS/NTFS
/dev/sda2            9562       38912   235761907+   f  W95 Ext'd (LBA)
/dev/sda5            9562       19122    76798701    7  HPFS/NTFS
/dev/sda6           19123       21672    20482843+  83  Linux
/dev/sda7           21673       22716     8385898+  82  Linux swap / Solaris
/dev/sda8           22717       24628    15358108+   b  W95 FAT32
/dev/sda9           24629       38912   114736198+   7  HPFS/NTFS
```The first time I tried fixing Grub, I just ran through the steps in the OP, and everything seemed to go to plan, but I probably wasn't paying much attention to the terminal outputs. I tried it again a minutes ago, and I get the below error from the following command:

Command:
```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda6 /dev/sda
```Output:
```
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /media/sda6/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda

```This is what is inside /boot/grub/device.map:

```
(hd0)    /dev/sda
```Does that look correct? Should there be a complete list of all partitions?
Is there anything else I need to do/try?
"grub-probe: error: Cannot open `/boot/grub/device.map'"
Either you are using the wrong partition, or grub is not installed. After you have mounted the hard drive, take a look inside /media/sdax, and see if all the files are in the boot directory. Also, it may be worth a shot trying the instructions for 9.04 using a 9.04 live cd, as it may be using the older version of grub.

---

### Post by talsemgeest on 2009-11-29
> **dohzer said:**
> After rebooting and re-loading Ubuntu from the install CD, I just retried the Grub2 recovery steps from the OP, and the results seem to be inconsistent:

This time I get:

```
ubuntu@ubuntu:~$ sudo mkdir /media/sda6
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /media/sda6
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda6 /dev/sda6
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

```

I didn't get that warning the last time I used those commands. :confused:
The problem there is that you are using ```
sudo grub-install --root-directory=/media/sda6 /dev/sda6
``` instead of ```
sudo grub-install --root-directory=/media/sda6 **/dev/sda
```**

---

### Post by dohzer on 2009-11-29
> **talsemgeest said:**
> The problem there is that you are using ```
sudo grub-install --root-directory=/media/sda6 /dev/sda6
``` instead of ```
sudo grub-install --root-directory=/media/sda6 **/dev/sda**
```
Oops... thanks for picking that up! It's been a long day. :p

> **talsemgeest said:**
> "grub-probe: error: Cannot open `/boot/grub/device.map'"
Either you are using the wrong partition, or grub is not installed. After you have mounted the hard drive, take a look inside /media/sdax, and see if all the files are in the boot directory. Also, it may be worth a shot trying the instructions for 9.04 using a 9.04 live cd, as it may be using the older version of grub.
I would have tried this, but after I removed the '6' from the command, it finally worked. I'm still not sure what was happening on the previous attempt (I'm sure I was using the correct syntax and partition before), but for now it is fixed.

Hopefully the boot loader doesn't corrupt again, but I'm betting it will. :(
At least now I know how to fix it if it does!
Thanks for the help.

---

### Post by talsemgeest on 2009-11-29
> **dohzer said:**
> Oops... thanks for picking that up! It's been a long day. :p


I would have tried this, but after I removed the '6' from the command, it finally worked. I'm still not sure what was happening on the previous attempt (I'm sure I was using the correct syntax and partition before), but for now it is fixed.

Hopefully the boot loader doesn't corrupt again, but I'm betting it will. :(
At least now I know how to fix it if it does!
Thanks for the help.
Ok, I hope it stays working for you! :)

---

### Post by meep_meep on 2009-12-06
solved

---

### Post by talsemgeest on 2009-12-06
> **meep_meep said:**
> solved
I'm glad you got it working :)

---

### Post by fgmart on 2009-12-06
talsemgeest, you saved my beans!  Your message to dohzer was exactly the mistake I was making.

Thanks so much.

---

### Post by talsemgeest on 2009-12-06
Haha excellent, I am always glad to help :)

---

### Post by Ferrari69 on 2009-12-08
Hello,

I had 2 partitions with 2 XP. I selected the 1st partition, i formatted it, and i installed Ubuntu 9.10 on it.

Now i cant boot into XP cz is showing me the XP loader of the XP that i deleted..
i tried fixmbr,fixboot but nothing.

In the beggining XP couldnt boot, but at least i could browse the folders from Linux.
Now in the Disk Utility its written Unrecognised, Unkown or unused.

Screenshots:


[http://img690.imageshack.us/i/screen1di.jpg/](http://img690.imageshack.us/i/screen1di.jpg/)

[http://img38.imageshack.us/i/screen2rj.jpg/](http://img38.imageshack.us/i/screen2rj.jpg/)





here it is:

    ~# fdisk -l
    
    
    Disk /dev/sda: 250.1 GB, 250059350016 bytes
    
    255 heads, 63 sectors/track, 30401 cylinders
    
    Units = cylinders of 16065 * 512 = 8225280 bytes
    
    Disk identifier: 0xb7e61057
    
    
       Device Boot      Start         End      Blocks   Id  System
    
    
    /dev/sda1   *           1       22508   180795478+  83  Linux
    
    /dev/sda2           22509       30400    63392490    f  W95 Ext'd (LBA)
    
    /dev/sda5   *       22752       30400    61440592+   7  HPFS/NTFS
    
    /dev/sda6           22509       22751     1951834+  82  Linux swap / Solaris

 

        ~#
        ~# ntfsfix /dev/sda5
        Mounting volume... $MFT has invalid magic.
        ntfs_mft_load(): Failed.
        Failed to load $MFT: Input/output error.
        Failed to startup volume: Input/output error.
        FAILED
        Attempting to correct errors... $MFT has invalid magic.
        ntfs_mft_load(): Failed.
        Failed to load $MFT: Input/output error.
        FAILED
        Failed to startup volume: Input/output error.
        Volume is corrupt. You should run chkdsk.

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

update view, after playing with some partition boot CDS:

```

root@ubuntu-tower:~# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7e61057

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22508   180795478+  83  Linux
/dev/sda3           22752       30400    61440592+   7  HPFS/NTFS

```


preparing now screenshot of GParted and Disk Utility:

[http://i46.tinypic.com/4hvdyc.jpg](http://i46.tinypic.com/4hvdyc.jpg)


wat should i do? any ideas?

Thanks.

---

### Post by kaspin on 2009-12-08
[FONT="Comic Sans MS"][COLOR="RoyalBlue"]Hi Talsemegeest,
I've just bought a 16GB SDHC card for my ASUS EEE (701 with 4GB SSD), with the intention of moving WinXP from the SSD and fitting it alongside Ubuntu 9,10. on the SDHC. 
I first installed XP, on half the card (SDB1 formatted NFTS) and then Ubuntu on the other half (SDB2 Ext4). I somehow messed up Grub2, and could only boot (XP) from the SSD (SDA1).
Fortunately, I found this post and was able to restore the grub bootloader by following your excellent instructions (saved me hours of frustration). So now, if I boot form the SDHC card, Grub gives me the option of booting either Ubuntu from SDB2 (the SDHC card) or XP from SDA1 (the SSD). 
However, I would like to be able to boot XP **_from the SDHC card (SDB1)_**, and perhaps put back the original Xandros OS on the SSD, and was wondering whether I could modify Grub2 to achieve this. I'm not sure if this is the right place to ask this question, but as you are obviously well versed in this area................... Many thanks in advance.[/COLOR][/FONT]

---

### Post by talsemgeest on 2009-12-08
> **kaspin said:**
> [FONT="Comic Sans MS"][COLOR="RoyalBlue"]Hi Talsemegeest,
I've just bought a 16GB SDHC card for my ASUS EEE (701 with 4GB SSD), with the intention of moving WinXP from the SSD and fitting it alongside Ubuntu 9,10. on the SDHC. 
I first installed XP, on half the card (SDB1 formatted NFTS) and then Ubuntu on the other half (SDB2 Ext4). I somehow messed up Grub2, and could only boot (XP) from the SSD (SDA1).
Fortunately, I found this post and was able to restore the grub bootloader by following your excellent instructions (saved me hours of frustration). So now, if I boot form the SDHC card, Grub gives me the option of booting either Ubuntu from SDB2 (the SDHC card) or XP from SDA1 (the SSD). 
However, I would like to be able to boot XP **_from the SDHC card (SDB1)_**, and perhaps put back the original Xandros OS on the SSD, and was wondering whether I could modify Grub2 to achieve this. I'm not sure if this is the right place to ask this question, but as you are obviously well versed in this area................... Many thanks in advance.[/COLOR][/FONT]
You can install the bootloader onto whichever device you want, simply run ```
sudo grub-install --root-directory=/media/sda5 /dev/sdx
``` replacing the x with the device letter of the SDHC.

---

### Post by talsemgeest on 2009-12-08
> **Ferrari69 said:**
> Hello,

I had 2 partitions with 2 XP. I selected the 1st partition, i formatted it, and i installed Ubuntu 9.10 on it.

Now i cant boot into XP cz is showing me the XP loader of the XP that i deleted..
i tried fixmbr,fixboot but nothing.

In the beggining XP couldnt boot, but at least i could browse the folders from Linux.
Now in the Disk Utility its written Unrecognised, Unkown or unused.

Screenshots:


[http://img690.imageshack.us/i/screen1di.jpg/](http://img690.imageshack.us/i/screen1di.jpg/)

[http://img38.imageshack.us/i/screen2rj.jpg/](http://img38.imageshack.us/i/screen2rj.jpg/)





here it is:

    ~# fdisk -l
    
    
    Disk /dev/sda: 250.1 GB, 250059350016 bytes
    
    255 heads, 63 sectors/track, 30401 cylinders
    
    Units = cylinders of 16065 * 512 = 8225280 bytes
    
    Disk identifier: 0xb7e61057
    
    
       Device Boot      Start         End      Blocks   Id  System
    
    
    /dev/sda1   *           1       22508   180795478+  83  Linux
    
    /dev/sda2           22509       30400    63392490    f  W95 Ext'd (LBA)
    
    /dev/sda5   *       22752       30400    61440592+   7  HPFS/NTFS
    
    /dev/sda6           22509       22751     1951834+  82  Linux swap / Solaris

 

        ~#
        ~# ntfsfix /dev/sda5
        Mounting volume... $MFT has invalid magic.
        ntfs_mft_load(): Failed.
        Failed to load $MFT: Input/output error.
        Failed to startup volume: Input/output error.
        FAILED
        Attempting to correct errors... $MFT has invalid magic.
        ntfs_mft_load(): Failed.
        Failed to load $MFT: Input/output error.
        FAILED
        Failed to startup volume: Input/output error.
        Volume is corrupt. You should run chkdsk.

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

update view, after playing with some partition boot CDS:

```

root@ubuntu-tower:~# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7e61057

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22508   180795478+  83  Linux
/dev/sda3           22752       30400    61440592+   7  HPFS/NTFS

```


preparing now screenshot of GParted and Disk Utility:

[http://i46.tinypic.com/4hvdyc.jpg](http://i46.tinypic.com/4hvdyc.jpg)


wat should i do? any ideas?

Thanks.
Simply run through the instructions for installing the Ubuntu bootloader for the version of Ubuntu you installed, then you should be able to boot into XP and ubuntu.

---

### Post by Ferrari69 on 2009-12-08
> **talsemgeest said:**
> Simply run through the instructions for installing the Ubuntu bootloader for the version of Ubuntu you installed, then you should be able to boot into XP and ubuntu.

the disk with xp its ntfs, but its not readable, so it cant boot

---

### Post by talsemgeest on 2009-12-08
> **Ferrari69 said:**
> the disk with xp its ntfs, but its not readable, so it cant boot
Ok, so you want to delete the XP partition and switch to Ubuntu?

---

### Post by Ferrari69 on 2009-12-08
> **talsemgeest said:**
> Ok, so you want to delete the XP partition and switch to Ubuntu?

no, i want to boot in both systems

---

### Post by talsemgeest on 2009-12-08
> **Ferrari69 said:**
> no, i want to boot in both systems
Ok, so if the XP partition is corrupted, you simply reinstall XP onto the corrupted partition, formating during the installation process, before booting into the ubuntu cd and fixing the bootloader as per the original post.

---

### Post by Ferrari69 on 2009-12-08
> **talsemgeest said:**
> Ok, so if the XP partition is corrupted, you simply reinstall XP onto the corrupted partition, formating during the installation process, before booting into the ubuntu cd and fixing the bootloader as per the original post.

yes i know that, but i wanted to fix the problem. cz i have a new XP system on that partition.

---

### Post by talsemgeest on 2009-12-08
> **Ferrari69 said:**
> yes i know that, but i wanted to fix the problem. cz i have a new XP system on that partition.
cz? Also, I am not entirely sure I see the problem.

---

### Post by Ferrari69 on 2009-12-08
> **talsemgeest said:**
> cz? Also, I am not entirely sure I see the problem.

cz=cause=because :)

---

### Post by talsemgeest on 2009-12-08
> **Ferrari69 said:**
> cz=cause=because :)
Ok, it is best to use proper English in the forums to avoid any misunderstandings. Also, can you please restate exactly what the problem is?

---

### Post by vsk_ram21 on 2009-12-09
please help me in enabling Fedora booting option in Ubuntu 9.10 Grub...
 my Partition details:

root@satz-laptop:/media/49AF-1EB3/pro# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea10ea10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1494    12000523+  83  Linux
/dev/sda2            5224       19457   114334605    c  W95 FAT32 (LBA)
/dev/sda3   *        3266        3291      204800   83  Linux
/dev/sda4            3292        5223    15518790    5  Extended
/dev/sda5            3292        5223    15518720   8e  Linux LVM

Partition table entries are not in disk order

/dev/sda1 -Ubuntu partion

---

### Post by talsemgeest on 2009-12-09
> **vsk_ram21 said:**
> please help me in enabling Fedora booting option in Ubuntu 9.10 Grub...
 my Partition details:

root@satz-laptop:/media/49AF-1EB3/pro# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea10ea10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1494    12000523+  83  Linux
/dev/sda2            5224       19457   114334605    c  W95 FAT32 (LBA)
/dev/sda3   *        3266        3291      204800   83  Linux
/dev/sda4            3292        5223    15518790    5  Extended
/dev/sda5            3292        5223    15518720   8e  Linux LVM

Partition table entries are not in disk order

/dev/sda1 -Ubuntu partion
Running ```
sudo update-grub
``` should automatically detect Fedora and add it to the Ubuntu grub menu.

---

### Post by kaspin on 2009-12-10
[FONT="Comic Sans MS"][COLOR="RoyalBlue"]Hello again Telsemgeest,
Many thanks for your speedy and helpful reply. 
The ubuntuforums.org site was down for a while so this posting is a little late.
I tried what you suggested  "sudo grub-install --root-directory=/media/sda5 /dev/sdx"  but without success.
To recap:
 - /dev/sda is my SSD with one partition (sda1) containing WinXP.
 - /dev/sdb is my SDHC card with sdb1 being NFTS (WinXP) and 
   sb2 being Ext4 (Linux), containing Ubuntu on sdb5 and the     Linux swap file on sdb6.
According to G-Parted, sda1 and sdb5 are both boot.
I couldn't understand what sda5 referred to in your formula. Should it have been sdb5 (i.e. the Ubuntu program which is boot)? Anyway, I tried sda5, sdb5, sdb1, sda1, followed each time by  sudo update-grub. Incidentally,"sdx" was always sdb. 
In the end I somehow screwed up my SDHC card so that if I try to boot from it now, 
I get "Grub loading error: File not found      grub rescue>"
and there I'm stuck...If you have any other ideas they'd be more than welcome. If it comes to it, I'll reformat the SDHC card, reinstall WinXP and Ubuntu on it, and try again to get grub to recognise sdb1 as well as sdb5.....
Thanks again, Kaspin[/COLOR][/FONT]

---

### Post by talsemgeest on 2009-12-10
> **kaspin said:**
> [FONT="Comic Sans MS"][COLOR="RoyalBlue"]Hello again Telsemgeest,
Many thanks for your speedy and helpful reply. 
The ubuntuforums.org site was down for a while so this posting is a little late.
I tried what you suggested  "sudo grub-install --root-directory=/media/sda5 /dev/sdx"  but without success.
To recap:
 - /dev/sda is my SSD with one partition (sda1) containing WinXP.
 - /dev/sdb is my SDHC card with sdb1 being NFTS (WinXP) and 
   sb2 being Ext4 (Linux), containing Ubuntu on sdb5 and the     Linux swap file on sdb6.
According to G-Parted, sda1 and sdb5 are both boot.
I couldn't understand what sda5 referred to in your formula. Should it have been sdb5 (i.e. the Ubuntu program which is boot)? Anyway, I tried sda5, sdb5, sdb1, sda1, followed each time by  sudo update-grub. Incidentally,"sdx" was always sdb. 
In the end I somehow screwed up my SDHC card so that if I try to boot from it now, 
I get "Grub loading error: File not found      grub rescue>"
and there I'm stuck...If you have any other ideas they'd be more than welcome. If it comes to it, I'll reformat the SDHC card, reinstall WinXP and Ubuntu on it, and try again to get grub to recognise sdb1 as well as sdb5.....
Thanks again, Kaspin[/COLOR][/FONT]

Ok, so install the Ubuntu Bootloader onto sdb, you need to boot from the live cd, ```
sudo mkdir /media/sdb5
sudo mount /dev/sdb5 /media/sdb5
sudo grub-install --root-directory=/media/sdb5 /dev/sdb

```
And hopefully that will install the grub mkbr onto sdb, assuming /media/sdb5/grub/ contains all the grub files, and sdb is the drive you want the mbr on.

---

### Post by shaon3343 on 2009-12-20
> **talsemgeest said:**
> 


[SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.10 and beyond)[/COLOR][/SIZE]

Since Ubuntu 9.10 uses Grub 2, the above method will not work. However, it can still be done and this is how:
 First you need to find out what your drives are called. You can do this by going to a terminal and typing: ```
sudo fdisk -l
``` You will get something like this:


[IMG]http://talsemgeest.doesntexist.com/blog/wp-content/uploads/2009/09/SVR8XIL.JPG[/IMG]

From that you need to find the device name of your Ubuntu drive, something like “/dev/sda5&#8243;.
 So, still in the terminal, type:
```

sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
```And then, to reinstall the grub: ```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```Push enter and you’re done! Of course you need to replace “/dev/sda5&#8243; and “/dev/sda” with what you found in the fdisk output.


[SIZE=2][B]
If i do so can GRUB2 automatically detect my windows xp. ( I use ubuntu 9.10 and windows xp ( dual boot)) . In GRUB legacy I'd to manually entry the other OS entry. In GRUB2 how can it happen? is it automatically detected during GRUB2 installation?[/B][/SIZE]

---

### Post by talsemgeest on 2009-12-20
> **shaon3343 said:**
> [SIZE=2][B]
If i do so can GRUB2 automatically detect my windows xp. ( I use ubuntu 9.10 and windows xp ( dual boot)) . In GRUB legacy I'd to manually entry the other OS entry. In GRUB2 how can it happen? is it automatically detected during GRUB2 installation?[/B][/SIZE]
Yes it is. If it is not already in the boot menu, running ```
sudo update-grub
``` should pick it up and add it to your list.

---

### Post by dohzer on 2009-12-23
> **talsemgeest said:**
> Ok, I hope it stays working for you! :)
OK... so it's corrupted again.
I think it is corrupting after Windows has been in use for a long time without rebooting.
I haven't used Ubuntu on my laptop in a week or two, and have had Windows continually running during that time, hibernating between use. Half an hour ago I rebooted so I could boot into Ubuntu, and Grub wasn't loading again.
Last time I reinstalled Grub, I tried restarting and rebooting the PC from/too Windows XP and Ubuntu several times without issues.

Can anyone recommend what I should do next? Should I give LILO a try? I don't want to have to waste time booting Ubuntu from CD to repair the bootloader each time it corrupts.

---

### Post by von Stalhein on 2009-12-23
As to what happens next, if you are resigned to ceasing GRUB 2, why not revert to the [original GRUB]("http://ubuntuforums.org/showthread.php?t=1298932")?

For reasons unbeknownst to man, beast or the Flying Spaghetti Monster, I too was unable to use GRUB 2.

I got over it, and I hope to get back to it at some stage :)

---

### Post by talsemgeest on 2009-12-23
> **dohzer said:**
> OK... so it's corrupted again.
I think it is corrupting after Windows has been in use for a long time without rebooting.
I haven't used Ubuntu on my laptop in a week or two, and have had Windows continually running during that time, hibernating between use. Half an hour ago I rebooted so I could boot into Ubuntu, and Grub wasn't loading again.
Last time I reinstalled Grub, I tried restarting and rebooting the PC from/too Windows XP and Ubuntu several times without issues.

Can anyone recommend what I should do next? Should I give LILO a try? I don't want to have to waste time booting Ubuntu from CD to repair the bootloader each time it corrupts.
All I can suggest is that you start from scratch, installing XP first onto a clean hard drive, then Ubuntu. Other than that I cannot see where the problem is coming from, so I can't fix it.

---

### Post by talsemgeest on 2009-12-23
> **von Stalhein said:**
> As to what happens next, if you are resigned to ceasing GRUB 2, why not revert to the [original GRUB]("http://ubuntuforums.org/showthread.php?t=1298932")?

For reasons unbeknownst to man, beast or the Flying Spaghetti Monster, I too was unable to use GRUB 2.

I got over it, and I hope to get back to it at some stage :)
This is also a very good suggestion, and should probably be tried before mine ;)

---

### Post by Joshua_805 on 2009-12-24
Hello I'm new to Ubuntu and i'm having the same problem. I already tried to follow the steps from the guide. Tried to type the codes but it comes up with unknown command. Whn i tried to boot the windows xp cd, it did load but it said that there were no files on the disk to reinstall window.

Does anyone have any other suggestions i would really appreciated.

---

### Post by talsemgeest on 2009-12-25
> **Joshua_805 said:**
> Hello I'm new to Ubuntu and i'm having the same problem. I already tried to follow the steps from the guide. Tried to type the codes but it comes up with unknown command. Whn i tried to boot the windows xp cd, it did load but it said that there were no files on the disk to reinstall window.

Does anyone have any other suggestions i would really appreciated.
Hi, I need a bit more info on your configuration. Which version of ubuntu do you have installed, which other operating systems, which order they were installed in, etc.

---

### Post by Joshua_805 on 2009-12-25
Well i installed the 9.10 vesion and i had Windows Xp intalled on it first.

---

### Post by talsemgeest on 2009-12-25
> **Joshua_805 said:**
> Well i installed the 9.10 vesion and i had Windows Xp intalled on it first.
Ok, please boot into the Ubuntu 9.10 Live CD and type ```
sudo fdisk -l
```

Post all of the output on here (copy and paste is best), and I will tell you the exact commands to run.

---

### Post by talsemgeest on 2009-12-26
> **laance said:**
> Hello,

Nice tutorial you mentioned here.

this is really a very useful information you mentioned here.

I really want to Vista Boot loader for last few days. But, Now i am using windows 7 so, did you any suggestion for windows 7?

Cheers !!!

**Merry  Christmas** !!!
Fixing the Windows 7 bootloader is exactly the same as the one for Vista, just using the windows 7 dvd instead of vista ;) Other than that, I am glad you like the tutorial, and a merry Christmas to you too :)

---

### Post by Joshua_805 on 2009-12-26
[QUOTE=talsemgeest;8558683]Ok, please boot into the Ubuntu 9.10 Live CD and type ```
sudo fdisk -l
```

Post all of the output on here (copy and paste is best), and I will tell you the exact commands to run.[/QUOTE  

And after i do that then what the next step?

---

### Post by talsemgeest on 2009-12-26
> **Joshua_805 said:**
> [QUOTE=talsemgeest;8558683]Ok, please boot into the Ubuntu 9.10 Live CD and type ```
sudo fdisk -l
```

Post all of the output on here (copy and paste is best), and I will tell you the exact commands to run.[/QUOTE  

And after i do that then what the next step?
After you had done that I would have taken the info in the fdisk output, and used it to change the commands in the first post to work with your computer. If you read the instructions carefully, I wouldnt have to, but I think this way is easier. :)

---

### Post by Joshua_805 on 2009-12-26
i already typed the command in but it always says unknown command

---

### Post by talsemgeest on 2009-12-26
> **Joshua_805 said:**
> i already typed the command in but it always says unknown command
For this to work you are going to have to do exactly what I say. I cannot help a person who does not want to be helped. So first of all, please make sure you have the Ubuntu 9.10 Live CD, such as the one that can be found on [this page](http://www.ubuntu.com/getubuntu/download). Boot from it, open a terminal and type ```
sudo fdisk -l
``` Open firefox, log into the forums and paste the output from the previous command into this thread.

---

### Post by zukario on 2009-12-27
I saved this thread in my desktop as i find this tutorial is useful.thank you for creating this useful tutorial.

---

### Post by talsemgeest on 2009-12-27
> **zukario said:**
> I saved this thread in my desktop as i find this tutorial is useful.thank you for creating this useful tutorial.
I am very happy to hear that :)

---

### Post by phillw on 2009-12-30
Oh yeah, I've never gotten around to thanking you either. I have sent lot's of people to this thread over the last couple of months !! -- It's a great How To.  Well done

:popcorn:

Phill.

---

### Post by mrlabor1 on 2009-12-31
Hello,  I am very new to the cammand line and anything other than synaptic package manager.  I am however having similar issues as the person above.  The issue I am having is when I type > 
sudo grub-install --recheck /dev/sda5         (my ubuntu 8.04 partion)

I get the response
 
> 
Probing devices to guess BIOS drives.  This may take a long rime.
Could not find device for /boot: Not found or not a block device.

 
any ideas?
 
big noob

---

### Post by talsemgeest on 2009-12-31
> **mrlabor1 said:**
> Hello,  I am very new to the cammand line and anything other than synaptic package manager.  I am however having similar issues as the person above.  The issue I am having is when I type 
I get the response
 

 
any ideas?
 
big noob
The command you posted is not in my guide. Please follow the instructions for Ubuntu 9.04 and before, and hopefully you will have your computer up and running again. :)

---

### Post by von Stalhein on 2009-12-31
> **mrlabor1 said:**
> Hello,  I am very new to the cammand line and anything other than synaptic package manager.  I am however having similar issues as the person above.  The issue I am having is when I type 
I get the response
 
any ideas?
 
big noob

> **talsemgeest said:**
> The command you posted is not in my guide. Please follow the instructions for Ubuntu 9.04 and before, and hopefully you will have your computer up and running again. :)

What talsemgeest said - also, I think you might benefit from [reading this thread]("http://ubuntuforums.org/showpost.php?p=7505203&postcount=1").

Stick with it, it's worth the effort.

---

### Post by ladi on 2010-01-04
Hi!

after following your tutorial i keep getting an error message that says pls specify the file system type.

here is the terminal display

root@ubuntu:~# sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61680184

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1176     9437184   27  Unknown
/dev/sda2   *        1176       18186   136636415+   7  HPFS/NTFS
/dev/sda3           18187       26246    64741950    5  Extended
root@ubuntu:~# mkdir /media/sda3
root@ubuntu:~#  mount /dev/sda3 /media/sda3
mount: you must specify the filesystem type

pls help,  

cheers!

ubuntu 9.10 / win 7

---

### Post by drs305 on 2010-01-04
> **ladi said:**
> 
root@ubuntu:~# mkdir /media/sda3
root@ubuntu:~#  mount /dev/sda3 /media/sda3
mount: you must specify the filesystem type

pls help,  

cheers!

ubuntu 9.10 / win 7

You don't mount an "extended" partition, which is what sda3 is. Think of it as a container for logical partitions. You have sda1 (unknown) which may be a recovery partition, then sda2, which is NTFS and most likely windows.

sda3 is an extended partition. Next you need to make logical partitions within the extended partition. The first logical partition will be sda5.

However, if you already have more partitions (sda5, sda6, etc) then don't do anything further with this disk. If you have a bad partition table you don't want to write anything more to the disk until you have the partition table fixed. 

Tell us what your situation is and we can help you. It might be helpful to start your own thread as this looks more than a partitioning problem rather than a boot problem (unless you had other partitions that were working until you tried to add Linux). At least give us a bit more information about what you are trying to accomplish.

---

### Post by 3thejoker4 on 2010-01-05
I know this will seem quite idiotic:
I deleted the partition on which Ubuntu was installed (DELETED not formated, it's just empty space that can't be used until I create a  new partition or extend an existing one) and went to the bathroom. When I went back into my room the computer was restarted by my brother and instead of the windows boot menu there was the Grub 2 with the message "no such partition" and the grub rescue started (I know other people had this error too).  The "sudo" command is unknown to the grub so basically I can't do anything. Does anyone have a solution for this? Oh and I almost forgot the Ubuntu version is 9.10

---

### Post by talsemgeest on 2010-01-05
> **3thejoker4 said:**
> I know this will seem quite idiotic:
I deleted the partition on which Ubuntu was installed (DELETED not formated, it's just empty space that can't be used until I create a  new partition or extend an existing one) and went to the bathroom. When I went back into my room the computer was restarted by my brother and instead of the windows boot menu there was the Grub 2 with the message "no such partition" and the grub rescue started (I know other people had this error too).  The "sudo" command is unknown to the grub so basically I can't do anything. Does anyone have a solution for this? Oh and I almost forgot the Ubuntu version is 9.10
You will need to boot from the live cd, recover the partition using something like [testdisk](https://help.ubuntu.com/community/DataRecovery), then restore the bootloader like in the first post. I will be away for a few days so, if you have any problems you will probably get an answer faster if you create your own thread. :)

---

### Post by Garypewitt on 2010-01-07
OK, I followed the steps on the first three pages.  I booted on the CD, did an alt-ctl-F1 to get to terminal mode.  I did the sudo fdisk -l  it showed my drives:
Windows is on /dev/sda1    a 500 Gig drive that should have been C: but shows up as G: in windows now.  system is HPFS/NTFS

Ubuntu 9.10 is on the 1Tbt drive  /dev/sdb1   Sys Linux
                                                /dev/sdb2   Sys Extended
                                                /dev/sdb5   Sys Linux Swap/Solarus

I got no error signals at all, it seemed to be working fine.  I rebooted with the disk removed and it came up in Windoz again.  

When running on the CD can changes be made and saved?  Or are they just temporary?

I thought the grub loader had to be on the first drive which would be sda1, right?

Still stumped.   Help!   Thanks Gary   :(

---

### Post by talsemgeest on 2010-01-08
> **Garypewitt said:**
> OK, I followed the steps on the first three pages.  I booted on the CD, did an alt-ctl-F1 to get to terminal mode.  I did the sudo fdisk -l  it showed my drives:
Windows is on /dev/sda1    a 500 Gig drive that should have been C: but shows up as G: in windows now.  system is HPFS/NTFS

Ubuntu 9.10 is on the 1Tbt drive  /dev/sdb1   Sys Linux
                                                /dev/sdb2   Sys Extended
                                                /dev/sdb5   Sys Linux Swap/Solarus

I got no error signals at all, it seemed to be working fine.  I rebooted with the disk removed and it came up in Windoz again.  

When running on the CD can changes be made and saved?  Or are they just temporary?

I thought the grub loader had to be on the first drive which would be sda1, right?

Still stumped.   Help!   Thanks Gary   :(
Hi Gary :)

Ok, simply running sudo fdisk -l will only show you which drives are which. You can go through the instructions for installing the ubuntu 9.10 bootloader onto whichever drive gets booted (usually sda1), and if windows does not boot after that you can run ```
sudo update-grub
``` from you ubuntu system.

---

### Post by 101011010010 on 2010-01-11
Hello there, I just wanted to say thank you for the excellent tut, just saved me another reinstall. Thanks.:)

---

### Post by talsemgeest on 2010-01-11
> **101011010010 said:**
> Hello there, I just wanted to say thank you for the excellent tut, just saved me another reinstall. Thanks.:)
Great to hear, I am glad it all worked for you :)

---

### Post by kaspin on 2010-01-16
[FONT="Comic Sans MS"][COLOR="Blue"]Hello again Talsemgeest,
Firstly, best wishes for a very happy new year.....
Secondly, despite your help a month or so ago which was much appreciated, I never managed to get Ubuntu and WinXP to boot from my 16GB SDHC card. I guess it's an issue with Windows, which only likes being booted from a fixed disk, so I've given up trying, at least for the time being.

My problem now is sluggish boot times. On my larger laptop (60GB HDD 1GB RAM), boot up time for WinXP or Ubuntu 9.10 is about 
1 minute - perfectly OK. WinXP is on 47GB NTFS and Ubuntu 9.10 on 13GB containing ext3 (12GB) and 897MB swap file.
But on my ASUS EEE (4GB SSD, 2GB RAM, 16GB SDHC card) it takes 4 minutes 30 seconds to boot Ubuntu 9.10 (or WinXP), of which half is spent stuck on "Grub Loading" !

Grub2 is used on both machines, the main difference being that, on the ASUS EEE, WinXP is on the SSD, and Ubuntu is on the 
SDHC card, whereas on the larger laptop, both are on the same physical HDD.

Other small differences are that the Linux partition on the larger machine is EXT3, whereas it's EXT4 on the EEE. Also, on the larger machine the boot possibilities are Ubuntu 2.6.31 - 16 generic, 15,or 14, mem test (twice) then WinXP, whilst on the EEE I have Ubuntu 2.6.31 - 17 generic, 17 recovery, 14 generic, 14 recovery, mem test (twice)then WinXP.

Incidentally, I have used WinXP on the EEE's 4GB SSD, with EasyPeasy (9.04) on an 8GB SDHC card without any boot time issues. But then it wouldn't have been using Grub2 presumably.

Any ideas you may have to speed things up would be most welcome.

Kaspin[/COLOR][/FONT]

---

### Post by talsemgeest on 2010-01-16
> **kaspin said:**
> [FONT="Comic Sans MS"][COLOR="Blue"]Hello again Talsemgeest,
Firstly, best wishes for a very happy new year.....
Secondly, despite your help a month or so ago which was much appreciated, I never managed to get Ubuntu and WinXP to boot from my 16GB SDHC card. I guess it's an issue with Windows, which only likes being booted from a fixed disk, so I've given up trying, at least for the time being.

My problem now is sluggish boot times. On my larger laptop (60GB HDD 1GB RAM), boot up time for WinXP or Ubuntu 9.10 is about 
1 minute - perfectly OK. WinXP is on 47GB NTFS and Ubuntu 9.10 on 13GB containing ext3 (12GB) and 897MB swap file.
But on my ASUS EEE (4GB SSD, 2GB RAM, 16GB SDHC card) it takes 4 minutes 30 seconds to boot Ubuntu 9.10 (or WinXP), of which half is spent stuck on "Grub Loading" !

Grub2 is used on both machines, the main difference being that, on the ASUS EEE, WinXP is on the SSD, and Ubuntu is on the 
SDHC card, whereas on the larger laptop, both are on the same physical HDD.

Other small differences are that the Linux partition on the larger machine is EXT3, whereas it's EXT4 on the EEE. Also, on the larger machine the boot possibilities are Ubuntu 2.6.31 - 16 generic, 15,or 14, mem test (twice) then WinXP, whilst on the EEE I have Ubuntu 2.6.31 - 17 generic, 17 recovery, 14 generic, 14 recovery, mem test (twice)then WinXP.

Incidentally, I have used WinXP on the EEE's 4GB SSD, with EasyPeasy (9.04) on an 8GB SDHC card without any boot time issues. But then it wouldn't have been using Grub2 presumably.

Any ideas you may have to speed things up would be most welcome.

Kaspin[/COLOR][/FONT]
Hmm, I had a similar problem with grub taking a while to load when it was installed to a drive other than the one that ubuntu was installed to. Do you have that setup?

---

### Post by harivaradhan on 2010-01-17
could you please help to bring the boot up sequence option windows xp/ubuntu. I have done as you told below, it gives error and say bad idea after the third command (grub root dicrectory). could you please please help me as i am new to ubuntu , thanks


sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5

---

### Post by talsemgeest on 2010-01-17
> **harivaradhan said:**
> could you please help to bring the boot up sequence option windows xp/ubuntu. I have done as you told below, it gives error and say bad idea after the third command (grub root dicrectory). could you please please help me as i am new to ubuntu , thanks


sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
Hi harivaradhan, please post the exact error message, inclusidng the command you used. The output of <sudo fdisk -l> would be useful too.

---

### Post by kaspin on 2010-01-20
[FONT="Comic Sans MS"][COLOR="Blue"]Hello again talsemgeest,
As far as I am aware Grub2 was on the SDHC card with Ubuntu (/dev/sdb5 - boot). WinXP was on the SSD (/dev/sda1 - boot). I wondered whether there was an issue with the 16GB SDHC (class 6) so I installed Ubuntu 9.10 on an 8GB SDHC, but the boot time was still about the same. I then installed Ubuntu 8.04 on the 8GB SDHC to see if boot time was quicker with the old Grub - and it was, at 1 minute 46 seconds.
I also tried reinstalling Ubuntu 9.10 on the 16GB SDHC card in persistent mode using the USB-Installer-for-Ubuntu.exe found on the pendrivelinux.com article for installing Ubuntu 9.10. Having done this, the boot time for Ubuntu 9.10 on the 16GB SDHC card went down to 2 minutes 20 seconds - over 2 minutes quicker than if installed "normally" from the CD. Windows MBR is on the SSD, Grub2 on the SDHC - so I have to select which to use on start up. 
As you will have gathered I'm not very computer literate, so unless there's something specific that I can search for on my system which might point to where the problem is, I'll carry on with the persistent boot mode, and hope that changes might be made to Grub2 in due course which would speed up the boot time.
One final question - is it easy to replace Grub2 in Ubuntu 9.10 by the old Grub? If it is, I might try that as an interim solution....
Many thanks again,
kaspin[/COLOR][/FONT]

---

### Post by jfda on 2010-01-21
What a great tutorial!

Thanks a lot! It was really helpful.

---

### Post by talsemgeest on 2010-01-21
> **kaspin said:**
> [FONT="Comic Sans MS"][COLOR="Blue"]Hello again talsemgeest,
As far as I am aware Grub2 was on the SDHC card with Ubuntu (/dev/sdb5 - boot). WinXP was on the SSD (/dev/sda1 - boot). I wondered whether there was an issue with the 16GB SDHC (class 6) so I installed Ubuntu 9.10 on an 8GB SDHC, but the boot time was still about the same. I then installed Ubuntu 8.04 on the 8GB SDHC to see if boot time was quicker with the old Grub - and it was, at 1 minute 46 seconds.
I also tried reinstalling Ubuntu 9.10 on the 16GB SDHC card in persistent mode using the USB-Installer-for-Ubuntu.exe found on the pendrivelinux.com article for installing Ubuntu 9.10. Having done this, the boot time for Ubuntu 9.10 on the 16GB SDHC card went down to 2 minutes 20 seconds - over 2 minutes quicker than if installed "normally" from the CD. Windows MBR is on the SSD, Grub2 on the SDHC - so I have to select which to use on start up. 
As you will have gathered I'm not very computer literate, so unless there's something specific that I can search for on my system which might point to where the problem is, I'll carry on with the persistent boot mode, and hope that changes might be made to Grub2 in due course which would speed up the boot time.
One final question - is it easy to replace Grub2 in Ubuntu 9.10 by the old Grub? If it is, I might try that as an interim solution....
Many thanks again,
kaspin[/COLOR][/FONT]
Since the delay seems to be in the grub rather than in the normal boot process, I can't think of any settings that would speed it up. As for replacing grub 2 with 1, I am sure it is possible, but I can't find any guides that walk you through it. All I can suggest is that you start a new thread with your problem, hopefully someone has another idea.

Sorry I couldnt be of more help.

---

### Post by talsemgeest on 2010-01-21
> **jfda said:**
> What a great tutorial!

Thanks a lot! It was really helpful.
Excellent, I am very happy it has helped you out. :)

---

### Post by kaspin on 2010-01-21
[FONT="Comic Sans MS"][COLOR="Blue"]Thanks again, talsemgeest. I've found another forum apparently devoted to a bug causing slow boot times in Grub2. So I'll get out of your hair, and start bugging them! Will report back if I find a solution that works  (I saw somewhere that a fix was due to be issued on 18th January......)
All the best, kaspin[/COLOR][/FONT]

---

### Post by talsemgeest on 2010-01-21
> **kaspin said:**
> [FONT="Comic Sans MS"][COLOR="Blue"]Thanks again, talsemgeest. I've found another forum apparently devoted to a bug causing slow boot times in Grub2. So I'll get out of your hair, and start bugging them! Will report back if I find a solution that works  (I saw somewhere that a fix was due to be issued on 18th January......)
All the best, kaspin[/COLOR][/FONT]
Haha ok, I hope it works out for you :)

---

### Post by kaspin on 2010-01-23
[FONT="Comic Sans MS"][COLOR="Blue"]Hi again talsemgeest,
Good news - I've reduced the boot time from 4 minutes 30 seconds to about 1 minute 45 seconds. You'll remember that WinXP is on my SSD (sda) and Ubuntu 9.10 on part of an SDHC card (sdb). I put Grub on the SDHC card ("sudo grub-install /dev/sdb") followed by "sudo update-grub" then rebooted. On reboot I changed the boot order in the BIOS to put the SDHC card before the SSD. That did it!
I expected to save more time if I put the boot on the SSD and altered the boot order accordingly, but it went up to nearly 4 minutes!
Anyway, I can live with the 1 minute 45 seconds with the SDHC card - but still hope to reduce it to around a minute one day. Next job is to put WinXP on the SDHC card and get Grub to boot it from there...........
Best wishes, kaspin[/COLOR][/FONT]

---

### Post by talsemgeest on 2010-01-23
> **kaspin said:**
> [FONT="Comic Sans MS"][COLOR="Blue"]Hi again talsemgeest,
Good news - I've reduced the boot time from 4 minutes 30 seconds to about 1 minute 45 seconds. You'll remember that WinXP is on my SSD (sda) and Ubuntu 9.10 on part of an SDHC card (sdb). I put Grub on the SDHC card ("sudo grub-install /dev/sdb") followed by "sudo update-grub" then rebooted. On reboot I changed the boot order in the BIOS to put the SDHC card before the SSD. That did it!
I expected to save more time if I put the boot on the SSD and altered the boot order accordingly, but it went up to nearly 4 minutes!
Anyway, I can live with the 1 minute 45 seconds with the SDHC card - but still hope to reduce it to around a minute one day. Next job is to put WinXP on the SDHC card and get Grub to boot it from there...........
Best wishes, kaspin[/COLOR][/FONT]
Excellent, glad to hear it and I wish you the best of luck! :)

---

### Post by emma00 on 2010-01-24
I have a query that to get back my grub menu back after reinstalling windows first i have to put Ubuntu live CD in it then do these steps you have mentioned????

---

### Post by drs305 on 2010-01-24
> **emma00 said:**
> I have a query that to get back my grub menu back after reinstalling windows first i have to put Ubuntu live CD in it then do these steps you have mentioned????

Yes. In the opening paragraphs of the first post talsemgeest states that you will use the LiveCD and provides a link to a HOWTO if you need help with the CD.

---

### Post by talsemgeest on 2010-01-24
> **drs305 said:**
> Yes. In the opening paragraphs of the first post talsemgeest states that you will use the LiveCD and provides a link to a HOWTO if you need help with the CD.
Thanks drs305 :)

---

### Post by thenapster8 on 2010-01-27
I found myself in a big jiffy. I had planned to just install Ubuntu on my external, and ended up installing the GRUB loader on my parents PC. It was... BAD. So i used my iPod and found this page, emailed it to myself and got on my old computer, hoping to create the recovery disk. Yeah... OLD computer, didn't have a DVD burner. I thought i was doomed. THEN, i thought, "What do i have that's Windows related... Windows 7 RC!" I printed the "How to restore the Windows Vista or 7 boot loader," directions, and sure enough, here i am typing in my good old Windows Vista. Thank you so much for this tutorial. And this is also for anyone who doesn't feel like burning yet another disk, just try and find something you have laying around first.
:popcorn:

---

### Post by talsemgeest on 2010-01-27
> **thenapster8 said:**
> I found myself in a big jiffy. I had planned to just install Ubuntu on my external, and ended up installing the GRUB loader on my parents PC. It was... BAD. So i used my iPod and found this page, emailed it to myself and got on my old computer, hoping to create the recovery disk. Yeah... OLD computer, didn't have a DVD burner. I thought i was doomed. THEN, i thought, "What do i have that's Windows related... Windows 7 RC!" I printed the "How to restore the Windows Vista or 7 boot loader," directions, and sure enough, here i am typing in my good old Windows Vista. Thank you so much for this tutorial. And this is also for anyone who doesn't feel like burning yet another disk, just try and find something you have laying around first.
:popcorn:
Excellent, I am happy to know that the instructions for windows have not gone to waste ;)

---

### Post by darco on 2010-02-03
I used this guide today after I re-installed my Win 7 OS. I am currently running Mint8 x64 with grub2. After running the commands in the livecd, grub came up fine. When I chose Win7, I received this: error: no such device c684a2884a27b1 Press any key
Here is my fdisk output:
```
   Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe868f6fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       34482   276976633+   7  HPFS/NTFS
/dev/sda2           35919       60801   199872697+  83  Linux
/dev/sda3           34483       34515      265072+  82  Linux swap / Solaris
/dev/sda4           34516       35918    11269597+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00017ea3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       21481   172546101    7  HPFS/NTFS
/dev/sdb2   *       21482       33108    93393877+  83  Linux
/dev/sdb3           33230       34535    10483712+   f  W95 Ext'd (LBA)
/dev/sdb4           34536       60801   210981645    7  HPFS/NTFS
/dev/sdb5           33230       34535    10483712    7  HPFS/NTFS

Disk /dev/sdg: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       29127   233956001    7  HPFS/NTFS

```

sdb contains another linux partition for testing purposes...

thxs

*edit* I edited the grub.conf ..uncommented GRUB_DISABLE_LINUX_UUID=true

---

### Post by talsemgeest on 2010-02-03
> **darco said:**
> *edit* I edited the grub.conf ..uncommented GRUB_DISABLE_LINUX_UUID=true
So it is fixed?

---

### Post by darco on 2010-02-03
Yes...sorry

---

### Post by talsemgeest on 2010-02-03
> **darco said:**
> Yes...sorry
Excellent, I am happy to hear it :)

---

### Post by arpan251089 on 2010-02-05
Hi I installed Xp and Ubuntu. I had grub loader to select one of these at boot time. Now I installed Windows 7 without removing windows xp or ubuntu.
My grub is now wipped off.
Will this method still work for me or if i install grub it will wipe my window 7's bootloader.

I want grub loader to either point to this three os or to ubuntu and bootloader of windows 7 from which i can load either xp or 7. pls tell me if anyone knows abt this

---

### Post by arpan251089 on 2010-02-05
Also tell me if i remove xp then how can i make my grub, point to ubuntu and windows 7. 

I mean remove my window 7 bootloader which have a link to xp

---

### Post by talsemgeest on 2010-02-05
Yes, simply run through the instructions for reinstalling the ubuntu bootloader, start up into ubuntu and run ```
sudo update-grub
```. If you choose to remove XP, just delete the XP partition, boot into Ubuntu and run ```
sudo update-grub
``` again. The menu will now only show Ubuntu and 7.

Hope this helps :)

---

### Post by emma00 on 2010-02-14
I tried to load grub 2 in Ubuntu 9.10 after reinstalling xp.I've followed the instructions to reinstall grub bootloader for ubuntu 9.10 but when I enter sudo grub-install --root-directory=/media/sda8 /dev/sda

 I get a message saying:


grub-setup:warn your embedding area is unusually small core.img won't fit in it.
grub-setup:warn:embedding is not possible
grub can only be installed using blocklists however blocklists are unreliable.
grub-setup:error:cannot read '/grub/core.img'.correctly


 I was running a dual boot between Win XP and Ubuntu 9.10 before 

any help or suggestions????

---

### Post by talsemgeest on 2010-02-14
> **emma00 said:**
> I tried to load grub 2 in Ubuntu 9.10 after reinstalling xp.I've followed the instructions to reinstall grub bootloader for ubuntu 9.10 but when I enter sudo grub-install --root-directory=/media/sda8 /dev/sda

 I get a message saying:


grub-setup:warn your embedding area is unusually small core.img won't fit in it.
grub-setup:warn:embedding is not possible
grub can only be installed using blocklists however blocklists are unreliable.
grub-setup:error:cannot read '/grub/core.img'.correctly


 I was running a dual boot between Win XP and Ubuntu 9.10 before 

any help or suggestions????
Hmm, I have never seen this error before. It seems that most people are getting this message when they try to install grub onto a flash drive. Please post the output of ```
sudo fdisk -l
``` to make sure that /dev/sda is the right one to be installing to.

---

### Post by emma00 on 2010-02-14
> **talsemgeest said:**
> Hmm, I have never seen this error before. It seems that most people are getting this message when they try to install grub onto a flash drive. Please post the output of ```
sudo fdisk -l
``` to make sure that /dev/sda is the right one to be installing to.


How can i post the output here after exiting from terminal am sure its dev/sda8 i have checked it twice newaz

you should know it :o

---

### Post by talsemgeest on 2010-02-14
> **emma00 said:**
> How can i post the output here after exiting from terminal am sure its dev/sda8 i have checked it twice newaz

you should know it :o
On the live cd, open up a terminal and run sudo fdisk -l, select the output, open firefox and navigate to the ubuntu forums, and middle click into the reply box for this thread. But if you are correct in saying that it is the right drive, I can't think of a lot you can do, since the space is simply missing. It may end up that you need to reinstall both windows and ubuntu to recreate the MBR at the start of the hard drive.

---

### Post by emma00 on 2010-02-14
No dontttttttttttttttttt say that 

i only reinstalled xp on seeing your toutorial that i can get back my grub#-o

---

### Post by emma00 on 2010-02-14
> **talsemgeest said:**
> On the live cd, open up a terminal and run sudo fdisk -l, select the output, open firefox and navigate to the ubuntu forums, and middle click into the reply box for this thread. But if you are correct in saying that it is the right drive, I can't think of a lot you can do, since the space is simply missing. It may end up that you need to reinstall both windows and ubuntu to recreate the MBR at the start of the hard drive.


am cuming back in 10 mins so wait plz.........

---

### Post by emma00 on 2010-02-14
This is it:


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
247 heads, 30 sectors/track, 84364 cylinders
Units = cylinders of 7410 * 512 = 3793920 bytes
Disk identifier: 0x2a0a219d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8292    30721845    7  HPFS/NTFS
/dev/sda2            8293       14068    21400080    7  HPFS/NTFS
/dev/sda3           14069       84363   260442975    f  W95 Ext'd (LBA)
/dev/sda4           84364       84364        3705   82  Linux swap / Solaris
/dev/sda5           14069       30651    61440000    7  HPFS/NTFS
/dev/sda6           30652       38942    30718140    7  HPFS/NTFS
/dev/sda7           38943       38998      207465    7  HPFS/NTFS
/dev/sda8           38999       47234    30514365   83  Linux
/dev/sda9           47235       84363   137562930    7  HPFS/NTFS

---

### Post by talsemgeest on 2010-02-14
> **emma00 said:**
> This is it:


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
247 heads, 30 sectors/track, 84364 cylinders
Units = cylinders of 7410 * 512 = 3793920 bytes
Disk identifier: 0x2a0a219d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8292    30721845    7  HPFS/NTFS
/dev/sda2            8293       14068    21400080    7  HPFS/NTFS
/dev/sda3           14069       84363   260442975    f  W95 Ext'd (LBA)
/dev/sda4           84364       84364        3705   82  Linux swap / Solaris
/dev/sda5           14069       30651    61440000    7  HPFS/NTFS
/dev/sda6           30652       38942    30718140    7  HPFS/NTFS
/dev/sda7           38943       38998      207465    7  HPFS/NTFS
/dev/sda8           38999       47234    30514365   83  Linux
/dev/sda9           47235       84363   137562930    7  HPFS/NTFS
Hmm, all looks fine to me. Only other thing I can suggest is that you create your own thread, and hopefully someone will be able to help you out there.

Sorry I couldn't be of more help.

---

### Post by themis on 2010-02-24
Hello,

I am trying to restore my ubuntu loader(grub).
you ask for a sudo fdisk -l
and I get 
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27f427f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749      121601   874361722+   f  W95 Ext'd (LBA)
/dev/sda5           12749       25496   102398278+   7  HPFS/NTFS
/dev/sda6           25497       50992   204796588+  83  Linux
/dev/sda7           50993       76488   204796588+  83  Linux
/dev/sda8          120606      121601     8000338+  82  Linux swap / Solaris
/dev/sda9          107858      120605   102398278+  83  Linux
/dev/sda10          76489      107857   251971461   83  Linux

Partition table entries are not in disk order

```


How can I tell which is my ubuntu drive???
Thanks you very much!

---

### Post by talsemgeest on 2010-02-24
> **themis said:**
> Hello,

I am trying to restore my ubuntu loader(grub).
you ask for a sudo fdisk -l
and I get 
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27f427f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749      121601   874361722+   f  W95 Ext'd (LBA)
/dev/sda5           12749       25496   102398278+   7  HPFS/NTFS
/dev/sda6           25497       50992   204796588+  83  Linux
/dev/sda7           50993       76488   204796588+  83  Linux
/dev/sda8          120606      121601     8000338+  82  Linux swap / Solaris
/dev/sda9          107858      120605   102398278+  83  Linux
/dev/sda10          76489      107857   251971461   83  Linux

Partition table entries are not in disk order

```
How can I tell which is my ubuntu drive???
Thanks you very much!

If you are in your ubuntu system, you can try running ```
mount | column -t
```, and look for the drive that is mounted as "/". Unfortunately I can't say definitively from your fdisk output.

Or, from the live cd, you can try opening/mounting the different drives and looking for the usual Ubuntu folders (/etc /var etc).

---

### Post by SecretCode on 2010-02-24
As well as _mount_, _df_ will tell you.

---

### Post by themis on 2010-02-25
SecretCode & talsemgeest Thank you!

---

### Post by talsemgeest on 2010-02-25
Cheers SecretCode, and I hope it works for you themis :)

---

### Post by themis on 2010-02-25
> Of course you need to replace &#8220;/dev/sda5&#8243; and &#8220;/dev/sda&#8221; with what you found in the fdisk output.

An other quostion too!
I know that sda5 of yours is mine sda9.
But how can I tell which is sda for me?
Stupid question? Sorryyy!

---->>> I followed the tutorial 
sudo mkdir /media/sda9
sudo mount /dev/sda9 /media/sda9
And then, to reinstall the grub:
Code:
sudo grub-install --root-directory=/media/sda9 /dev/sda

And I get:
Grub loading.
error: file not found
grub rescue>

(and I have the pc on that state,
I write from a laptop next to it,
so can easily apply any suggestions(???) )
It seems pretty scary though!

---

### Post by tikmikrik on 2010-02-25
After installing ubuntu 9.10 on my acer laptop I decided to revert to xp, after installing xp I am takien to the grub rescue terminal, my system cd has no rescue mode it goes straight onto recovery, how doo i restore xp bootloader in this case?

---

### Post by talsemgeest on 2010-02-25
> **tikmikrik said:**
> After installing ubuntu 9.10 on my acer laptop I decided to revert to xp, after installing xp I am takien to the grub rescue terminal, my system cd has no rescue mode it goes straight onto recovery, how doo i restore xp bootloader in this case?
You may want to give [this](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/) tutorial a try, which should allow you to install the xp bootloader from the ubuntu live cd.

---

### Post by talsemgeest on 2010-02-25
> **themis said:**
> An other quostion too!
I know that sda5 of yours is mine sda9.
But how can I tell which is sda for me?
Stupid question? Sorryyy!

---->>> I followed the tutorial 
sudo mkdir /media/sda9
sudo mount /dev/sda9 /media/sda9
And then, to reinstall the grub:
Code:
sudo grub-install --root-directory=/media/sda9 /dev/sda

And I get:
Grub loading.
error: file not found
grub rescue>

(and I have the pc on that state,
I write from a laptop next to it,
so can easily apply any suggestions(???) )
It seems pretty scary though!
It looks to me like you have chosen the wrong partition. After you run ```
sudo mkdir /media/sda9
sudo mount /dev/sda9 /media/sda9
``` take a look in the folder /media/sda9/boot and hopefully all the grub files will be there. If not, choose another partition :)

---

### Post by von Stalhein on 2010-02-25
Edit: Beaten by Talsemgeest :-) (As it should be).

> Originally Posted by **tikmikrik**
After installing ubuntu 9.10 on my acer laptop I decided to revert to xp, after installing xp I am takien to the grub rescue terminal, my system cd has no rescue mode it goes straight onto recovery, how doo i restore xp bootloader in this case?

You will need to do a fixmbr

GRUB has overwritten the MBR (Master Boot Record).

Have a read of [this]("http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/")

I've had to do it a few times :D

If that's not clear enough there are plenty of guides about - Google and take your pick.

---

### Post by themis on 2010-02-25
> **talsemgeest said:**
> It looks to me like you have chosen the wrong partition. After you run ```
sudo mkdir /media/sda9
sudo mount /dev/sda9 /media/sda9
``` take a look in the folder /media/sda9/boot and hopefully all the grub files will be there. If not, choose another partition :)

the grub files are here.
After these commands, what follows?
[B]sudo grub-install --root-directory=/media/sda9 /dev/sda
[/B] lead me to a grub_rescue mode....

should I run 
sudo grub-install --root-directory=/media/sda5 **[COLOR="Red"]/dev/sda9[/COLOR]**  ??????

---

### Post by talsemgeest on 2010-02-25
> **themis said:**
> the grub files are here.
After these commands, what follows?
[B]sudo grub-install --root-directory=/media/sda9 /dev/sda
[/B] lead me to a grub_rescue mode....

should I run 
sudo grub-install --root-directory=/media/sda5 **[COLOR="Red"]/dev/sda9[/COLOR]**  ??????
Ok, as long as you are sure that sda9 is your ubuntu partition (what is on the other linux partitions?), then running ```
sudo grub-install --root-directory=/media/sda5 /dev/sda
``` should work.

---

### Post by themis on 2010-02-25
> **talsemgeest said:**
> Ok, as long as you are sure that sda9 is your ubuntu partition (what is on the other linux partitions?), then running ```
sudo grub-install --root-directory=/media/**[COLOR="Red"]sda5[/COLOR]** /dev/sda
``` should work.

are you sure that is is sda5?????? I will not use on the command nowhere sda9??
Excuse my doubts please!


yes i am sure about the sda9 partition
```
maya@kiparissi:~$ mount | column -t
/dev/sda9         on  /                         type  ext3                   (rw,errors=remount-ro)
proc              on  /proc                     type  proc                   (rw)
none              on  /sys                      type  sysfs                  (rw,noexec,nosuid,nodev)
none              on  /sys/fs/fuse/connections  type  fusectl                (rw)
none              on  /sys/kernel/debug         type  debugfs                (rw)
none              on  /sys/kernel/security      type  securityfs             (rw)
udev              on  /dev                      type  tmpfs                  (rw,mode=0755)
none              on  /dev/pts                  type  devpts                 (rw,noexec,nosuid,gid=5,mode=0620)
none              on  /dev/shm                  type  tmpfs                  (rw,nosuid,nodev)
none              on  /var/run                  type  tmpfs                  (rw,nosuid,mode=0755)
none              on  /var/lock                 type  tmpfs                  (rw,noexec,nosuid,nodev)
none              on  /lib/init/rw              type  tmpfs                  (rw,nosuid,mode=0755)
binfmt_misc       on  /proc/sys/fs/binfmt_misc  type  binfmt_misc            (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon  on  /home/maya/.gvfs          type  fuse.gvfs-fuse-daemon  (rw,nosuid,nodev,user=maya)

```

---

### Post by talsemgeest on 2010-02-25
> **themis said:**
> are you sure that is is sda5?????? I will not use on the command nowhere sda9??
Excuse my doubts please!


yes i am sure about the sda9 partition
```
maya@kiparissi:~$ mount | column -t
/dev/sda9         on  /                         type  ext3                   (rw,errors=remount-ro)
proc              on  /proc                     type  proc                   (rw)
none              on  /sys                      type  sysfs                  (rw,noexec,nosuid,nodev)
none              on  /sys/fs/fuse/connections  type  fusectl                (rw)
none              on  /sys/kernel/debug         type  debugfs                (rw)
none              on  /sys/kernel/security      type  securityfs             (rw)
udev              on  /dev                      type  tmpfs                  (rw,mode=0755)
none              on  /dev/pts                  type  devpts                 (rw,noexec,nosuid,gid=5,mode=0620)
none              on  /dev/shm                  type  tmpfs                  (rw,nosuid,nodev)
none              on  /var/run                  type  tmpfs                  (rw,nosuid,mode=0755)
none              on  /var/lock                 type  tmpfs                  (rw,noexec,nosuid,nodev)
none              on  /lib/init/rw              type  tmpfs                  (rw,nosuid,mode=0755)
binfmt_misc       on  /proc/sys/fs/binfmt_misc  type  binfmt_misc            (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon  on  /home/maya/.gvfs          type  fuse.gvfs-fuse-daemon  (rw,nosuid,nodev,user=maya)

```
No, you do have to replace sda5 with sda9. Also, sda is the drive that you want to install grub to, so assuming you only have one drive, sda is correct.

---

### Post by themis on 2010-02-25
> **talsemgeest said:**
> No, you do have to replace sda5 with sda9. Also, sda is the drive that you want to install grub to, so assuming you only have one drive, sda is correct.

Nop, doesnt work.

I get back to sh:grub>

i exec these commands to load ubuntu again
```
linux /vmlinuz root=/dev/sda9 ro 
initrd /initrd.img
boot
```

what else can we check now?

---

### Post by talsemgeest on 2010-02-26
> **themis said:**
> Nop, doesnt work.

I get back to sh:grub>

i exec these commands to load ubuntu again
```
linux /vmlinuz root=/dev/sda9 ro 
initrd /initrd.img
boot
```

what else can we check now?
Well, assuming everything you have told me is correct, I am out of ideas. I can see no reason why its not working. All I can suggest is that you create your own thread and hope that someone is able to help.

---

### Post by Saudffs on 2010-02-26
First of all I have to thank you for this great and simple tutorial, I'm glad that I found it since I'm planing to install Windows 7 over Vista while keeping my beloved Ubuntu 9.10, which takes me to my inquiry: after a clean Windows 7 installation I should boot with a LiveCD and run:
 
```
sudo mkdir /media/sdb2
sudo mount /dev/sdb2 /media/sdb2
```

then run:

```
sudo grub-install --root-directory=/media/sdb2 /dev/sdb
```

this is what I get from sudo fdisk -l:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2907e04d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
/dev/sda2   *         192       19648   156284928    7  HPFS/NTFS
/dev/sda3           19648       38914   154748928    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d379805

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       20147   161830746    f  W95 Ext'd (LBA)
/dev/sdb2           20148       38913   150737895   83  Linux
/dev/sdb5               1       19490   156547790    7  HPFS/NTFS
/dev/sdb6           19491       20147     5277321   82  Linux swap / Solaris
```

is running :
```
sudo mkdir /media/sdb2
sudo mount /dev/sdb2 /media/sdb2
```
then:
```
sudo grub-install --root-directory=/media/sdb2 /dev/sdb
```

correct in my case?

 thank you for your time and excuse my noobness but hopefully I'll become a pro like you when I grow up :lol:
 cheers mate.

---

### Post by talsemgeest on 2010-02-27
> **Saudffs said:**
> First of all I have to thank you for this great and simple tutorial, I'm glad that I found it since I'm planing to install Windows 7 over Vista while keeping my beloved Ubuntu 9.10, which takes me to my inquiry: after a clean Windows 7 installation I should boot with a LiveCD and run:
 
```
sudo mkdir /media/sdb2
sudo mount /dev/sdb2 /media/sdb2
```

then run:

```
sudo grub-install --root-directory=/media/sdb2 /dev/sdb
```

this is what I get from sudo fdisk -l:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2907e04d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
/dev/sda2   *         192       19648   156284928    7  HPFS/NTFS
/dev/sda3           19648       38914   154748928    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d379805

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       20147   161830746    f  W95 Ext'd (LBA)
/dev/sdb2           20148       38913   150737895   83  Linux
/dev/sdb5               1       19490   156547790    7  HPFS/NTFS
/dev/sdb6           19491       20147     5277321   82  Linux swap / Solaris
```

is running :
```
sudo mkdir /media/sdb2
sudo mount /dev/sdb2 /media/sdb2
```
then:
```
sudo grub-install --root-directory=/media/sdb2 /dev/sdb
```

correct in my case?

 thank you for your time and excuse my noobness but hopefully I'll become a pro like you when I grow up :lol:
 cheers mate.
That should certainly work. However, if it still doesnt boot, try running ```
sudo grub-install --root-directory=/media/sdb2 /dev/sda
``` instead.

---

### Post by Saudffs on 2010-02-27
Thank you again talsemgeest, I'll let you know if it works as soon as I do it.

---

### Post by talsemgeest on 2010-02-27
> **Saudffs said:**
> Thank you again talsemgeest, I'll let you know if it works as soon as I do it.
Excellent, the best of luck to you :)

---

### Post by dariush_03 on 2010-03-08
Hi everybody,

I first had installed Ubuntu 9.10 then Windows 7. After the Win 7 installation, I was not able to enter my Ubuntu partition.

Then I followed the instructions for restoring the Bootloader of Ubuntu 9.10 in this thread and I finally got my Ubuntu partition back. The next problem was that I could enter to Windows 7 anymore.

Solution: make an update of Grub Bootloader !

Now I can enter both os.

Best regards

---

### Post by SyOliven on 2010-03-09
> **talsemgeest said:**
> **[SIZE=6][COLOR=blue]How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)[/COLOR][/SIZE]**

This How-to is for windows dual booters who reinstall an operating system only to find that it has taken away access to their other operating system. 
Whether you want to restore the XP, Vista, 7 or Ubuntu (Grub) bootloader, this guide will walk you through it.

All three parts of this tutorial require that you boot from a cd. If you don't know how to do this, check [here.]("http://www.hiren.info/pages/bios-boot-cdrom")

If you have made a mistake and want to revert the changes, simply follow the instructions for reinstalling the previous bootloader. For example, if you have installed vista over ubuntu, try to get the ubuntu bootloader back, but want to get the vista bootloader back, simply follow my instructions for installing the vista bootloader.


[SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.10 and beyond)[/COLOR][/SIZE]

Since Ubuntu 9.10 uses Grub 2, the above method will not work. However, it can still be done and this is how:
 First you need to find out what your drives are called. You can do this by going to a terminal and typing: ```
sudo fdisk -l
``` You will get something like this:


[IMG]http://talsemgeest.doesntexist.com/blog/wp-content/uploads/2009/09/SVR8XIL.JPG[/IMG]

From that you need to find the device name of your Ubuntu drive, something like &#8220;/dev/sda5&#8243;.
 So, still in the terminal, type:
```

sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
```And then, to reinstall the grub: ```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```Push enter and you&#8217;re done! Of course you need to replace &#8220;/dev/sda5&#8243; and &#8220;/dev/sda&#8221; with what you found in the fdisk output.

[SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.04 and older)[/COLOR][/SIZE]

First of all, all credit for this part of the tutorial goes to [catlet]("http://ubuntuforums.org/showpost.php?p=1308395&postcount=1"). I am simply rewriting his tutorial to have all three bootloaders in this tutorial.

So, lets begin. To restore the grub, you must boot off the ubuntu live cd. Any ubuntu live cd will do.

Once there, open a terminal (Applications>Accessories>Terminal) and type this:

```
sudo grub
```Next, you need to find which hard drive ubuntu and the grub is installed to. You do this by running this command:

```
find /boot/grub/stage1
```Take note of what it returns (something like (hd0,1).)

Now you need to tell Grub where it is installed. Using the output of the last command, change this one and run it:

```
root (hd<a>,<b>)
```Replacing <a> and <b> with what you got back before. For example, if "find /boot/grub/stage1" gave me "(hd0,1)", you would run "root (hd0,1)"

Ok, so thats the configuration over and done with. Now we just need to run one command to install the Grub to your hard drive:

```
setup (hd0)
```Now to quit and check if it has worked:

```
quit
``````
sudo reboot
```Make sure you have taken the live cd out of your disc tray. All going well, you should start back up and see the grub once again.

 
[SIZE=5][COLOR=red]How to restore the Windows XP bootloader[/COLOR][/SIZE]

For this you will need your Windows XP installation CD. Boot into it now.

You will get to a part where it asks if you want to repair or recover. To do so, press "r".

If prompted, enter your Windows XP administrator password. This will leave you at at a command line, so type in the following two commands:

```
fixboot
``````
fixmbr
```Then type ```
exit
``` then remove your XP cd. If everything has gone well, you should come to your XP bootloader.


[SIZE=5][COLOR=red]How to restore the Windows Vista or 7 bootloader[/COLOR][/SIZE]

To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download").
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

```
bootrec.exe /fixboot
``````
bootrec.exe /fixmbr
```Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader.
Dont really understand how to use this forum yet, but I guess I'll learn.  The information I received looks great and I will try it shortly.  Thank you to Forum members who were insrumental in getting me the answers to my questionh. I really appreciate it.

If someone can offer me assistance in knowing howto contact Forum members just to say thank you please let me know.

[email]SyOliven@aol.com[/email]
Tucson,Arizona USA

---

### Post by talsemgeest on 2010-03-09
> **SyOliven said:**
> Dont really understand how to use this forum yet, but I guess I'll learn.  The information I received looks great and I will try it shortly.  Thank you to Forum members who were insrumental in getting me the answers to my questionh. I really appreciate it.

If someone can offer me assistance in knowing howto contact Forum members just to say thank you please let me know.

[email]SyOliven@aol.com[/email]
Tucson,Arizona USA
Hi SyOliven, I hope the guide works well for you. Good luck :)

---

### Post by nelsonj on 2010-03-13
> **dariush_03 said:**
> Hi everybody,
 
I first had installed Ubuntu 9.10 then Windows 7. After the Win 7 installation, I was not able to enter my Ubuntu partition.
 
Then I followed the instructions for restoring the Bootloader of Ubuntu 9.10 in this thread and I finally got my Ubuntu partition back. The next problem was that I could enter to Windows 7 anymore.
 
Solution: make an update of Grub Bootloader !
 
Now I can enter both os.
 
Best regards
 
 
I am in the same boat. I upgraded from Vista to Win 7. After the upgrade I can no longer access Ubuntu 9.10. Aparently Win 7 replaced/overwrote my bootloader. If I follow the instructions for restoring the Bootloader for Ubuntu I assume that I will loose Win 7 access. Can you explaine the workaround to get both working? Any help is appreciated.

---

### Post by smittal on 2010-03-13
I had ubuntu 7.10, I upgraded it to ubuntu-9.10 recently. Now I need to install windows. I have heard the grub version has changed for ubuntu-9.10 so my question is : "Can i use ubuntu-7.10 live cd to restore grub for ubuntu-9.10 after installing windows?"

Thanks in advance :)


> **talsemgeest said:**
> **[SIZE=6][COLOR=blue]How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)[/COLOR][/SIZE]**

This How-to is for windows dual booters who reinstall an operating system only to find that it has taken away access to their other operating system. 
Whether you want to restore the XP, Vista, 7 or Ubuntu (Grub) bootloader, this guide will walk you through it.

All three parts of this tutorial require that you boot from a cd. If you don't know how to do this, check [here.]("http://www.hiren.info/pages/bios-boot-cdrom")

If you have made a mistake and want to revert the changes, simply follow the instructions for reinstalling the previous bootloader. For example, if you have installed vista over ubuntu, try to get the ubuntu bootloader back, but want to get the vista bootloader back, simply follow my instructions for installing the vista bootloader.


[SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.10 and beyond)[/COLOR][/SIZE]

Since Ubuntu 9.10 uses Grub 2, the above method will not work. However, it can still be done and this is how:
 First you need to find out what your drives are called. You can do this by going to a terminal and typing: ```
sudo fdisk -l
``` You will get something like this:


[IMG]http://talsemgeest.doesntexist.com/blog/wp-content/uploads/2009/09/SVR8XIL.JPG[/IMG]

From that you need to find the device name of your Ubuntu drive, something like “/dev/sda5&#8243;.
 So, still in the terminal, type:
```

sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
```And then, to reinstall the grub: ```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```Push enter and you’re done! Of course you need to replace “/dev/sda5&#8243; and “/dev/sda” with what you found in the fdisk output.

[SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.04 and older)[/COLOR][/SIZE]

First of all, all credit for this part of the tutorial goes to [catlet]("http://ubuntuforums.org/showpost.php?p=1308395&postcount=1"). I am simply rewriting his tutorial to have all three bootloaders in this tutorial.

So, lets begin. To restore the grub, you must boot off the ubuntu live cd. Any ubuntu live cd will do.

Once there, open a terminal (Applications>Accessories>Terminal) and type this:

```
sudo grub
```Next, you need to find which hard drive ubuntu and the grub is installed to. You do this by running this command:

```
find /boot/grub/stage1
```Take note of what it returns (something like (hd0,1).)

Now you need to tell Grub where it is installed. Using the output of the last command, change this one and run it:

```
root (hd<a>,<b>)
```Replacing <a> and <b> with what you got back before. For example, if "find /boot/grub/stage1" gave me "(hd0,1)", you would run "root (hd0,1)"

Ok, so thats the configuration over and done with. Now we just need to run one command to install the Grub to your hard drive:

```
setup (hd0)
```Now to quit and check if it has worked:

```
quit
``````
sudo reboot
```Make sure you have taken the live cd out of your disc tray. All going well, you should start back up and see the grub once again.

 
[SIZE=5][COLOR=red]How to restore the Windows XP bootloader[/COLOR][/SIZE]

For this you will need your Windows XP installation CD. Boot into it now.

You will get to a part where it asks if you want to repair or recover. To do so, press "r".

If prompted, enter your Windows XP administrator password. This will leave you at at a command line, so type in the following two commands:

```
fixboot
``````
fixmbr
```Then type ```
exit
``` then remove your XP cd. If everything has gone well, you should come to your XP bootloader.


[SIZE=5][COLOR=red]How to restore the Windows Vista or 7 bootloader[/COLOR][/SIZE]

To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download").
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

```
bootrec.exe /fixboot
``````
bootrec.exe /fixmbr
```Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader.

---

### Post by talsemgeest on 2010-03-14
> **nelsonj said:**
> I am in the same boat. I upgraded from Vista to Win 7. After the upgrade I can no longer access Ubuntu 9.10. Aparently Win 7 replaced/overwrote my bootloader. If I follow the instructions for restoring the Bootloader for Ubuntu I assume that I will loose Win 7 access. Can you explaine the workaround to get both working? Any help is appreciated.
Yes, once you have restored the ubuntu bootloader, boot into ubuntu and run ```
sudo update-grub
``` and you should have both on your boot menu.

---

### Post by talsemgeest on 2010-03-14
> **smittal said:**
> I had ubuntu 7.10, I upgraded it to ubuntu-9.10 recently. Now I need to install windows. I have heard the grub version has changed for ubuntu-9.10 so my question is : "Can i use ubuntu-7.10 live cd to restore grub for ubuntu-9.10 after installing windows?"

Thanks in advance :)
Im afraid to restore the 9.10 bootloader you need the 9.10 live cd. However, considering you have upgraded, you may still have the 7.10 bootloader installed, in which case you can restore it using the instructions for 9.04 and before.

---

### Post by nelsonj on 2010-03-14
> **talsemgeest said:**
> Yes, once you have restored the ubuntu bootloader, boot into ubuntu and run ```
sudo update-grub
``` and you should have both on your boot menu.
 
Worked like a charm. Thanks

---

### Post by talsemgeest on 2010-03-14
> **nelsonj said:**
> Worked like a charm. Thanks
Glad to hear it :)

---

### Post by kaax on 2010-03-15
hi everyone, i have one problem, i have dual os, xp and  ubuntu, last night i reinstall windows and wanted to restore grub loader and i did as writeen in first post of [talsemgeest]("http://ubuntuforums.org/member.php?u=397508") 
,  grub loader restored but there is another problem, i cant log in widows :(  eror e408f0c20pfo9460,,, can anyone help me? 
pls

sry about my inglish if there is any misteke :P i know english not well and i am surprised how i managed to write my problem there :D

thank

---

### Post by talsemgeest on 2010-03-15
> **kaax said:**
> hi everyone, i have one problem, i have dual os, xp and  ubuntu, last night i reinstall windows and wanted to restore grub loader and i did as writeen in first post of [talsemgeest]("http://ubuntuforums.org/member.php?u=397508") 
,  grub loader restored but there is another problem, i cant log in widows :(  eror e408f0c20pfo9460,,, can anyone help me? 
pls

sry about my inglish if there is any misteke :P i know english not well and i am surprised how i managed to write my problem there :D

thank
Im sorry, but that really seems like a windows problem, and a google search of the error code doesnt come up with anything.

---

### Post by kaax on 2010-03-16
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)
there is the same problem, but i cant undestand, if someone do help me please

my grub is restored but when i type grub in terminal it says that grub is not installed, what does it mean?

---

### Post by talsemgeest on 2010-03-16
Have you tried reinstalling the xp bootloader to make sure that it is not a windows fault?

---

### Post by kaax on 2010-03-16
its need administrative password,  i have no any pass

---

### Post by talsemgeest on 2010-03-16
> **kaax said:**
> its need administrative password,  i have no any pass
Ok then, it seems like a windows problem so I will not be able to be of any more help.

---

### Post by kaax on 2010-03-16
its not windows problem, its a grub problem, grub cant load windows :| 
today i reinstall windows with another cd but the same problem :| 
ok i ll try another way to restore grub,   do u know other method? 
not "sudo grub"
another


edited: i cant even update grub loader 

type: sudo update-grub2  but command not found :| 

damn this f** grub

---

### Post by talsemgeest on 2010-03-16
> **kaax said:**
> its not windows problem, its a grub problem, grub cant load windows :| 
today i reinstall windows with another cd but the same problem :| 
ok i ll try another way to restore grub,   do u know other method? 
not "sudo grub"
another


edited: i cant even update grub loader 

type: sudo update-grub2  but command not found :| 

damn this f** grub
Sorry, you mentioned in your first post something about the weird windows error message. Anyways, the command is ```
sudo update-grub
```, not update-grub2. Also, it seems like you might be trying to follow the instructions for 9.04 and below, when you have ubuntu 9.10.

---

### Post by tsaunders on 2010-03-24
I am getting an error when trying to restore Grub, it says that your are installing it to a partition and not to and MBR.

I am running 10.04 aplha 1 and am using the 9.10 Live cd as I couldn't find a live cd for 10.04

---

### Post by drs305 on 2010-03-24
> **tsaunders said:**
> I am getting an error when trying to restore Grub, it says that your are installing it to a partition and not to and MBR.

I am running 10.04 aplha 1 and am using the 9.10 Live cd as I couldn't find a live cd for 10.04

From the LiveCD, remember that you *mount* your Ubuntu partition (sda1, sda5, sdb1, etc) but normally you will *install* to the drive (sda, sdb). The reason has to do with how and where Grub2 will store the information. Installing to a specific partition requires the use of blocklists, which may cause Grub2 to fail if certain grub files are moved from their original location. Note you *can* install G2 to a partition, but it isn't recommended unless you must.

Here is a link to the community doc on reinstalling Grub2 from the LiveCD:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by tsaunders on 2010-03-24
I can't get anything to work in that link.  I just keep getting errors.

I think I am going to have to install 10.04 overtop of my current install and hopefully that will fix it - :\

As long as I can run the fixmbr for windows in case something goes wrong.

---

### Post by talsemgeest on 2010-03-24
> **drs305 said:**
> From the LiveCD, remember that you *mount* your Ubuntu partition (sda1, sda5, sdb1, etc) but normally you will *install* to the drive (sda, sdb). The reason has to do with how and where Grub2 will store the information. Installing to a specific partition requires the use of blocklists, which may cause Grub2 to fail if certain grub files are moved from their original location. Note you *can* install G2 to a partition, but it isn't recommended unless you must.

Here is a link to the community doc on reinstalling Grub2 from the LiveCD:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")
Thanks drs305 :)

---

### Post by cashyy on 2010-04-01
Hey Thanks for the help, I just have one problem. 

I tried to reinstall grub, which is on sda5, but now when I go to computer I have a folder called sda5, and then I have a filesystem which sda5 is also in, Could this be the reason why ubuntu is booting up with grub rescue, because they are 2 sda5? 

[IMG]http://img221.imageshack.us/img221/3740/screenshotcomputerfileb.png[/IMG]
[IMG]http://img221.imageshack.us/img221/8222/screenshotmediafilebrow.png[/IMG]

---

### Post by talsemgeest on 2010-04-02
There can technically only be one sda5, the one in /dev/. As long as you are not showing more than one up in "sudo fdisk -l", you should be fine.

---

### Post by nickhopkins07 on 2010-04-02
Firstly, thank you for this thread, it's helped me sort out part of my problem, and I'm really hoping you nice people will be able to help me out with the second part!
 
So I'm gunna post my original problem here, for clarities sake:
 
> 
**Win 7/Jaunty -Nothing Boots after jaunty installation** 
Hi Guys,
 
I'm sure this has been answered already, I've had a search, but given I don't really know what I've done, I'm not sure what to search for!
 
I've got a laptop with Win 7 on it, and I wanted to install Jaunty as a dual boot to further my understanding of Ubuntu, and I think I've screwed up big time :sad: I've read up prior, but I've still managed to mess up somehow.
 
So I had two partitions one with my Win 7 one and an empty one, so I downloaded jaunty and used netbootin to create a bootable USB stick and booted into Jaunty, ran the install, followed the install process, chose the empty partition for Jaunty, and then on the last page (before clicking the install button) I clicked advance, and chose the same partition for the Ubuntu's version of MBR to be installed to, so as not to get in the way of MBR, or so I thought.
 
Install went through ok, but now when I start up the computer I dont get a dual boot screen, Win 7 starts right up, although it doesn't finish, the Win 7 splash screen appears, then blue screens (disapears to quick to read) and thats that! I've tried using the Win 7 repair disk and the bootrec.exe functions, but to no avail, also cant get into Win 7 in safe mode.
 
So the only way I can get anything out of the laptop at the moment is to use the bootable USB stick I created.
 
Can someone please outline what they think I may have done, and if it's fixable? I'll start from scratch and re-install if need be, but I'd rather not to be honest, as I see it I've have both the OS's I want installed, i just need a way to select them/load them.
 
Many thanks in advance.
 
Nick

 
So I posted the above and was pointed in the direction of this thread. I followed the instructions for recovering grub, and when I start up my laptop I am faced with a dual boot screen, from here I can happily start up the installed edition of 9.04, wonderful.
 
I'm still having the same problem with Win7 though, If I chose to load windows from the dual boot screen, it starts the process, then blue screens and the laptop restarts, I've tried repairing it with the Win 7 rescue cd, but to no avail. What is interesting/confusing is in the dual boot screen, windows is listed Vista rather win 7, which seems odd to me!
 
When I boot into Jaunty and look at the drives, I have one partition with Win 7 on it, which when i browse to it seems fine, all the folders etc you'd expect to be there are. I have another partition called 'SYSTEM' which I beleive to house the original MBR on, and a third partition 'Filesystem' with all the Jauty stuff on.
 
Anyone any ideas how I can sort this out please? It would be much appreciated.
 
Thank you

---

### Post by talsemgeest on 2010-04-02
> **nickhopkins07 said:**
> Firstly, thank you for this thread, it's helped me sort out part of my problem, and I'm really hoping you nice people will be able to help me out with the second part!
 
So I'm gunna post my original problem here, for clarities sake:
 

 
So I posted the above and was pointed in the direction of this thread. I followed the instructions for recovering grub, and when I start up my laptop I am faced with a dual boot screen, from here I can happily start up the installed edition of 9.04, wonderful.
 
I'm still having the same problem with Win7 though, If I chose to load windows from the dual boot screen, it starts the process, then blue screens and the laptop restarts, I've tried repairing it with the Win 7 rescue cd, but to no avail. What is interesting/confusing is in the dual boot screen, windows is listed Vista rather win 7, which seems odd to me!
 
When I boot into Jaunty and look at the drives, I have one partition with Win 7 on it, which when i browse to it seems fine, all the folders etc you'd expect to be there are. I have another partition called 'SYSTEM' which I beleive to house the original MBR on, and a third partition 'Filesystem' with all the Jauty stuff on.
 
Anyone any ideas how I can sort this out please? It would be much appreciated.
 
Thank you
Ok, seems to be the usual "Windows throwing a fit", so I would suggest backing up any files you want to keep from the windows partition, reinstalling windows, then recovering the grub as-per this thread.

---

### Post by nickhopkins07 on 2010-04-02
Hmm, was worried you'd say that! My laptop wasn't supplied with the windows media disk, just the licence, and no recovery partition, although I think that may have been an oversight on my part. Really don't want to have to pay out on a Win 7 disk, paying twice for the privalige of using Windows is a bit of a kick in the teeth! although it sounds like I mnight not have much choice :(.
 
Thanks gain for your help.

---

### Post by talsemgeest on 2010-04-02
> **nickhopkins07 said:**
> Hmm, was worried you'd say that! My laptop wasn't supplied with the windows media disk, just the licence, and no recovery partition, although I think that may have been an oversight on my part. Really don't want to have to pay out on a Win 7 disk, paying twice for the privalige of using Windows is a bit of a kick in the teeth! although it sounds like I mnight not have much choice :(.
 
Thanks gain for your help.
I hate to mention it, but as you do own a windows 7 license, there are certain parts of the internet that you will be able to download an untouched dvd image of the installation disk.

---

### Post by balkrish999 on 2010-04-03
omg Thank You sho much ( how to resote windows vista and 7 boot loader)

i did  it thanks so much:): i got worried when i clicked on reapir you pc and it did but on restart grub error but i them typed in compan promte fix boot etc  

Thank soooooooo  much :)  Thank :)

---

### Post by talsemgeest on 2010-04-03
> **balkrish999 said:**
> omg Thank You sho much ( how to resote windows vista and 7 boot loader)

i did  it thanks so much:): i got worried when i clicked on reapir you pc and it did but on restart grub error but i them typed in compan promte fix boot etc  

Thank soooooooo  much :)  Thank :)
Excellent, I am glad it worked for you (or at least I think thats what you said ;))

---

### Post by dushy4 on 2010-04-06
> **talsemgeest said:**
> **[SIZE=6][COLOR=blue]How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)[/COLOR][/SIZE]**

This How-to is for windows dual booters who reinstall an operating system only to find that it has taken away access to their other operating system. 
Whether you want to restore the XP, Vista, 7 or Ubuntu (Grub) bootloader, this guide will walk you through it.

All three parts of this tutorial require that you boot from a cd. If you don't know how to do this, check [here.]("http://www.hiren.info/pages/bios-boot-cdrom")

If you have made a mistake and want to revert the changes, simply follow the instructions for reinstalling the previous bootloader. For example, if you have installed vista over ubuntu, try to get the ubuntu bootloader back, but want to get the vista bootloader back, simply follow my instructions for installing the vista bootloader.


[SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.10 and beyond)[/COLOR][/SIZE]

First you need to find out what your drives are called. You can do this by going to a terminal and typing: ```
sudo fdisk -l
``` You will get something like this:


[IMG]http://talsemgeest.doesntexist.com/blog/wp-content/uploads/2009/09/SVR8XIL.JPG[/IMG]

From that you need to find the device name of your Ubuntu drive, something like “/dev/sda5&#8243;.
 So, still in the terminal, type:
```

sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
```And then, to reinstall the grub: ```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```Push enter and you’re done! Of course you need to replace “/dev/sda5&#8243; and “/dev/sda” with what you found in the fdisk output.

[SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.04 and older)[/COLOR][/SIZE]

First of all, all credit for this part of the tutorial goes to [catlet]("http://ubuntuforums.org/showpost.php?p=1308395&postcount=1"). I am simply rewriting his tutorial to have all three bootloaders in this tutorial.

So, lets begin. To restore the grub, you must boot off the ubuntu live cd. Any ubuntu live cd will do.

Once there, open a terminal (Applications>Accessories>Terminal) and type this:

```
sudo grub
```Next, you need to find which hard drive ubuntu and the grub is installed to. You do this by running this command:

```
find /boot/grub/stage1
```Take note of what it returns (something like (hd0,1).)

Now you need to tell Grub where it is installed. Using the output of the last command, change this one and run it:

```
root (hd<a>,<b>)
```Replacing <a> and <b> with what you got back before. For example, if "find /boot/grub/stage1" gave me "(hd0,1)", you would run "root (hd0,1)"

Ok, so thats the configuration over and done with. Now we just need to run one command to install the Grub to your hard drive:

```
setup (hd0)
```Now to quit and check if it has worked:

```
quit
``````
sudo reboot
```Make sure you have taken the live cd out of your disc tray. All going well, you should start back up and see the grub once again.

 
[SIZE=5][COLOR=red]How to restore the Windows XP bootloader[/COLOR][/SIZE]

For this you will need your Windows XP installation CD. Boot into it now.

You will get to a part where it asks if you want to repair or recover. To do so, press "r".

If prompted, enter your Windows XP administrator password. This will leave you at at a command line, so type in the following two commands:

```
fixboot
``````
fixmbr
```Then type ```
exit
``` then remove your XP cd. If everything has gone well, you should come to your XP bootloader.


[SIZE=5][COLOR=red]How to restore the Windows Vista or 7 bootloader[/COLOR][/SIZE]

To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download for [Vista]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download") or [Win 7](http://neosmart.net/blog/2009/windows-7-system-repair-discs/).
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

```
bootrec.exe /fixboot
``````
bootrec.exe /fixmbr
```Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader.




thanks dear,you saved my life,,it worked perfectly without any problem):P

---

### Post by talsemgeest on 2010-04-06
> **dushy4 said:**
> thanks dear,you saved my life,,it worked perfectly without any problem):P
Excellent, happy to hear :)

---

### Post by airplus on 2010-04-14
Hi, please could someone help me with this?

I have 3 systems installed (XP, Vista & Ubuntu)

The grub in Ubuntu got corrupted, so after long hoursof looking at forums I managed to reinstall it.

However, it boots straight into Ubuntu (holding Shift does not work) and cant access neither of Windows (XP nor Vista).

I used to boot with the EasyBCD (configured in Vista) and all was great.

Now I am afraid to further damage things, as I need the computer for work and at least Ubuntu is working. ](*,)

This is the output of fdisk:
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       10199    61440000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           10199       14130    31576153   83  Linux
/dev/sda4           14131       14593     3719047+   5  Extended
/dev/sda5           14131       14593     3719016   82  Linux swap / Solaris

```Also this is the result of a script I got from [http://ubuntuforums.org/showpost.php?p=9015919&postcount=2](http://ubuntuforums.org/showpost.php?p=9015919&postcount=2)  (attached)

Thanks in advance!!!

Edit: I have done the sudo grub-update twice to no avail. I keeps going straight into Ubuntu.

Edit: SOLVED!!!! I did:

sudo grub-install /dev/sda3 (sda3 is my Ubuntu partition)
then in the Vista command line:
bootrec.exe /fixboot
bootrec.exe /fixmbr and restart. Fixed!!

Phew!!! this was close :)

All this happened because I wanted to uninstall Python 2.6 from Ubuntu Software Centre, after all (I thought) I already had Python 3.1 installed. BAD IDEA. Ubuntu crashed badly in the middle of the process and would crash on starting.

So I had to reinstall from LiveCD and untar the backup file, which did corrupt Grub. Lessons learnt:
Keep a fresh backup.
Be careful with Linux, if not broken, don't fix it.:)

---

### Post by Hman242 on 2010-04-17
When I put in 
```
bootrec.exe /fixboot
``` repair Win7, it says
```
This volume does not contain a recognized file system.
Please make sure that all required file system drivers are loaded and that the volume is not corrupted.
```What do I do? Before having the option of choosing Command Prompt, it didn't pick up my OS. I didn't load any driver and just clicked next. If I did need to do that, then where would I find the one(s?) I need to load?

---

### Post by talsemgeest on 2010-04-17
That does not sound good. It sounds as though you may have deleted your windows partition. Make sure you can access your windows files from ubuntu, to check if they are still there.

---

### Post by Hman242 on 2010-04-17
It's still there.

---

### Post by talsemgeest on 2010-04-18
Ok, what other drives/partitions are there on your system?

---

### Post by Hman242 on 2010-04-18
There are four partitions. Windows, Ubuntu, and two recovery partitions that were there by default. I remember back when I shrink the Windows partition and made the Ubuntu partition, it said something about the number of partitions I had would make the partitions secondary partitions or something like that. Then it said something along the lines of having one OS. I ignored it, but that might have had something to do with my problem.

---

### Post by talsemgeest on 2010-04-19
Ok, if you still want ubuntu I would suggest you run the instructions for ubuntu. If not, I suggest you delete all the partitions other than the windows one. After that you should be able to load windows.

---

### Post by abdusamed on 2010-04-23
Thanks.. it WORKED... i really didn't want to format my pc.. cuz of u, i saved a week of hardwork.. thanks.. Btw, for windows 7, you should have said to select the other option, not deselect it

---

### Post by talsemgeest on 2010-04-23
> **abdusamed said:**
> Thanks.. it WORKED... i really didn't want to format my pc.. cuz of u, i saved a week of hardwork.. thanks.. Btw, for windows 7, you should have said to select the other option, not deselect it
Excellent, I am glad it worked. But no, I did mean to deselect it, because then the recovery cd will try to fix the bootloader, and in my experience it never does. So it needs to be deselected to be able to go to the command line and enter the commands.

---

### Post by blittle on 2010-04-24
Hello!
Background: Recently reinstalled Windows XP 64 to test out for my regular job site on my personal computer where I originally had Vista installed, but rarely used it. Forgot that Windows wipes our mbr, but figured I'd use easyBCD to fix. No dice since EasyBCD wants to work with Vista and this is XP. Anyway, would rather use a Linux solution. So to get to my Linux partition, I booted using supergrubdisk 1.30 (for grub2) since I use Ubuntu 9.10.

Had great success booting i and so I found this thread.
So far, I have gotten this far:
 after rnning fdisk -l,

ubuntu@ubuntu:~$ sudo mkdir /media/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/sda1
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda1 /dev/sda

The istallation came back with no errors, but upon boot I get:

Grub Loading.

error: File not found

Grub Rescue

then a prompt.

Did I land grub on the wrong directory? I know my linux partition is on sda1


Any incite would be greatly appreciated.

---

### Post by talsemgeest on 2010-04-24
> **blittle said:**
> Hello!
Background: Recently reinstalled Windows XP 64 to test out for my regular job site on my personal computer where I originally had Vista installed, but rarely used it. Forgot that Windows wipes our mbr, but figured I'd use easyBCD to fix. No dice since EasyBCD wants to work with Vista and this is XP. Anyway, would rather use a Linux solution. So to get to my Linux partition, I booted using supergrubdisk 1.30 (for grub2) since I use Ubuntu 9.10.

Had great success booting i and so I found this thread.
So far, I have gotten this far:
 after rnning fdisk -l,

ubuntu@ubuntu:~$ sudo mkdir /media/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/sda1
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda1 /dev/sda

The istallation came back with no errors, but upon boot I get:

Grub Loading.

error: File not found

Grub Rescue

then a prompt.

Did I land grub on the wrong directory? I know my linux partition is on sda1


Any incite would be greatly appreciated.
Do you have any other hard drives in that machine? The fdisk -l output would be particularly useful to post.

---

### Post by drmikegreen on 2010-05-01
Following the instructions here has resulted in my digging a deeper hole for myself. Now I get the following when I try to reboot:
"error file not found.
grub rescue>"

I even get this message when I try to reboot from the Window 7 Rescue Disk -- not only from the hard drive.

Help!!!

---

### Post by drmikegreen on 2010-05-01
Well, I was able to get myself out of the deeper hole by using an Ubuntu live CD to repeat the first bits of the instructions -- the ones for re-installing Grub.

I still cannot get to Windows 7, even using the Windows 7 Recovery Disk.

---

### Post by drmikegreen on 2010-05-01
Finally I have (I hope) climbed out of the hole.

First, it required downloading the Windows 7 Rescue Disk again and burning a new CD. (Apparently there was something wrong with my first attempt.) 

Then I went through the steps described for the Windowns recovery in the instructions here -- with a couple of exceptions (perhaps Windows puts up different screens for different versions?). At the end of that process I could again boot into Windows 7. 

But then I could not boot into Ubuntu Linux. 

So I again used the Ubuntu live CD to repeat the first bits of the instructions -- the ones for re-installing Grub. 

And, finally, I am able to boot into either Ubuntu Linux (Lucid Lynx) or Windows 7.

Whew!

BTW, my guess is that my troubles were precipitated by the screen in the update process which asks one where to put Grub. I suspect I answered that incorrectly out of ignorance. I hope that someone will either provide better instuctions with that screen or - preferable remove it altogether and make the upgrade process figure out automatically where to put it.

Cheers!

Mike Green

---

### Post by emma00 on 2010-05-04
> **talsemgeest said:**
> **[SIZE=6][COLOR=blue]How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)[/COLOR][/SIZE]**

This How-to is for windows dual booters who reinstall an operating system only to find that it has taken away access to their other operating system. 
Whether you want to restore the XP, Vista, 7 or Ubuntu (Grub) bootloader, this guide will walk you through it.

All three parts of this tutorial require that you boot from a cd. If you don't know how to do this, check [here.]("http://www.hiren.info/pages/bios-boot-cdrom")

If you have made a mistake and want to revert the changes, simply follow the instructions for reinstalling the previous bootloader. For example, if you have installed vista over ubuntu, try to get the ubuntu bootloader back, but want to get the vista bootloader back, simply follow my instructions for installing the vista bootloader.


[SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.10 and beyond)[/COLOR][/SIZE]

First you need to find out what your drives are called. You can do this by going to a terminal and typing: ```
sudo fdisk -l
``` You will get something like this:


[IMG]http://img517.imageshack.us/img517/713/svr8xil.jpg[/IMG]

From that you need to find the device name of your Ubuntu drive, something like “/dev/sda5&#8243;.
 So, still in the terminal, type:
```

sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
```And then, to reinstall the grub: ```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```Push enter and you’re done! Of course you need to replace “/dev/sda5&#8243; and “/dev/sda” with what you found in the fdisk output.

[SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.04 and older)[/COLOR][/SIZE]

First of all, all credit for this part of the tutorial goes to [catlet]("http://ubuntuforums.org/showpost.php?p=1308395&postcount=1"). I am simply rewriting his tutorial to have all three bootloaders in this tutorial.

So, lets begin. To restore the grub, you must boot off the ubuntu live cd. Any ubuntu live cd will do.

Once there, open a terminal (Applications>Accessories>Terminal) and type this:

```
sudo grub
```Next, you need to find which hard drive ubuntu and the grub is installed to. You do this by running this command:

```
find /boot/grub/stage1
```Take note of what it returns (something like (hd0,1).)

Now you need to tell Grub where it is installed. Using the output of the last command, change this one and run it:

```
root (hd<a>,<b>)
```Replacing <a> and <b> with what you got back before. For example, if "find /boot/grub/stage1" gave me "(hd0,1)", you would run "root (hd0,1)"

Ok, so thats the configuration over and done with. Now we just need to run one command to install the Grub to your hard drive:

```
setup (hd0)
```Now to quit and check if it has worked:

```
quit
``````
sudo reboot
```Make sure you have taken the live cd out of your disc tray. All going well, you should start back up and see the grub once again.

 
[SIZE=5][COLOR=red]How to restore the Windows XP bootloader[/COLOR][/SIZE]

For this you will need your Windows XP installation CD. Boot into it now.

You will get to a part where it asks if you want to repair or recover. To do so, press "r".

If prompted, enter your Windows XP administrator password. This will leave you at at a command line, so type in the following two commands:

```
fixboot
``````
fixmbr
```Then type ```
exit
``` then remove your XP cd. If everything has gone well, you should come to your XP bootloader.


[SIZE=5][COLOR=red]How to restore the Windows Vista or 7 bootloader[/COLOR][/SIZE]

To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download for [Vista]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download") or [Win 7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/").
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

```
bootrec.exe /fixboot
``````
bootrec.exe /fixmbr
```Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader.

Are these instructions are same for ubuntu 10.04 :popcorn:

---

### Post by edekba on 2010-05-06
So i'm trying to recover my WinXp bootloader, after i installed 10.04 and I can not get the recovery console up ... 


any ideas?

---

### Post by progone on 2010-05-07
thanks for the solution 

[SIZE="6"]How to restore the Ubuntu grub bootloader (9.10 and beyond)****[/SIZE]

it worked!!! Yay!!! :KS

---

### Post by progone on 2010-05-07
> **talsemgeest said:**
> 

```
bootrec.exe /fixboot
``````
bootrec.exe /fixmbr
```Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader.


grrr.

I wish I read this part.  Now I lost my Grub2 again but this time only Vista starts up and Live Disk. 

I tried to redo the steps that helped me overcome the Grub rescue> issue as I did before.  No results.

---

### Post by nightspore1 on 2010-05-07
Hi, Talsemgeest ! Kudo's to you. I upgraded to the new Ubuntu and managed to lose access to my Vista. Being a starter in Ubuntu that didn't go well vwith me. But your instructions solved my problem perfectly, I've gotten my complete dual boot back, GRUB works like crazy!! 
Once more THANKS!!!!

---

### Post by wjz on 2010-05-13
talsegeest is the absolute business thanks for the bootloader info

---

### Post by Yaheed on 2010-05-16
Is it possible to use Grub to boot my Windows Vista installation on another hard drive?

e.g. sda is Ubuntu, sdb is Windows Vista.

sda has the grub bootloader on it, sdb has Windows' bootloader on it. I'd prefer to keep the two bootloaders separated but if there is no other way ...

---

### Post by drs305 on 2010-05-17
> **Yaheed said:**
> Is it possible to use Grub to boot my Windows Vista installation on another hard drive?

e.g. sda is Ubuntu, sdb is Windows Vista.

sda has the grub bootloader on it, sdb has Windows' bootloader on it. I'd prefer to keep the two bootloaders separated but if there is no other way ...

Yes, absolutely.

When you install Grub2 it should find Windows. If not, after installing run "sudo update-grub" and in most cases Windows will be automatically added to the Grub2 menu.

---

### Post by CrazyIvan24 on 2010-05-17
OK - so I am TOTALLY confused here.  I put a version of Ubuntu Netbook Remix on my EEEPC 900HA.  It looked nice, but the keyboard and touchpad ceased to work.  I looked around for another version of Ubuntu for my EEEPC and found EasyPeasy (eeebuntu).  So, I look on line and find that I need to delete the partition in Windows to get rid of Ubuntu.  Did that....but then....I end up with "grub rescue" each time I boot.  I've been looking at all the threads, and I am totally confused.  Folks mention using the restore CD that came with my computer.  Tried that.  Even though I've ensured the BIOS will go to that drive first, I get nothing.  I also found the thread that noted I should download/create a USB with Super Grub Disk on it.  Did that.  Again, changed the BIOS to load from the USB first....nothing, nada, zip.  Then I see threads that tell me to open a terminal window and type in various lines of code.  OK, I'd do that, but how the heck to I get to a terminal prompt from grub rescue?  Every line I've seen to list my drives works only to list the drives.  Then when I try to go deeper, all I get is 'unknown command' or 'unrecognized file type'.

Could someone please tell me, in simple terms, how the heck I can force my 'puter to either boot from the USB, USB Optical drive, or get to a windows command prompt where I can force the 'puter to load from my NTFS drive?

I'm really new to this linux-based stuff here, so please dumb it down for this one 8-)

Thanks!

---

### Post by dontfearthepenguin on 2010-05-18
Wow wish I would have seen this a couple weeks ago when I reloaded Windows 7 because I formatted my Linux HD and booted to plain black screen with a cursor up top.
 
This would have probably saved me about an hour of time wasted reinstalling both Windows AND ubuntu 10.04

---

### Post by S1n1ster on 2010-05-21
Someone please help me. I have a acer aspire as1410 with windows vista. I installed ubuntu but it did not work, after trying to make it work and giving up i decided to return to windows. when grub popped up i selected windows and used acer e-recovery management to reset the computer to factory settings with windows. now whenever i boot it says "grub loading. error no such partiton, grub rescue>" i am begging anyone i have spent months saving up for this computer and now i may have ruined it. please help me get vista working again.

Mike Cortez

---

### Post by Trent T on 2010-06-14
Thanks, talsemgeest, for this excellent and comprehensive guide to restoring grub!

I have a Toshiba Tecra A7 laptop with an 80 GB HDD.  It ran for about 6 years dual-booting Win XP and Xandros Linux.  Since Xandros is effectively no longer supported (another story), I was unable to fix it when it recently stopped working.  

I wiped the Linux partitions, left Win XP where it was, and installed Ubuntu 9.10 in the empty space (23 MB).  It worked very well on restart, and I was able to choose and start either operating system from the GRUB2 menu.  

However in Win XP, I noticed that my Norton Security Suite had been damaged, and was no longer working!  I reinstalled Norton, restarted the computer, and found that GRUB2 no longer worked!  

I reinstalled Ubuntu 9.10 from the ground up, and once again, Norton had been disabled.  When I re-enabled Norton, GRUB2 stopped working.

I followed your steps to re-install GRUB2.  An error message said that /dev/sdb1 could not be accessed.  

Upon restart, GRUB2 now says,

Loading GRUB - file not found
grub rescue>

I can load and run either WIN XP or Ubuntu 9.10 if I boot from the Grub2 rescue disk.

I assume that Norton Security Suite is interfering with GRUB somehow--
Do you know of a way to make Norton and GRUB2 keep away from each other?

If not, do you know of any other WIN XP security product that will not interfere with GRUB2?  

Thanks for any assistance you can provide!
--Trent T

Here's my GRUB2 reinstallation attempt:

trent@trent-laptop:~$ sudo fdisk -l

[sudo] password for trent: 



Disk /dev/sda: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x9e4c9e4c



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        6174    49592623+   7  HPFS/NTFS

/dev/sda2            9214        9729     4144770   1c  Hidden W95 FAT32 (LBA)

/dev/sda3            6175        9213    24410767+   5  Extended

/dev/sda5            6175        9081    23350446   83  Linux

/dev/sda6            9082        9213     1060258+  82  Linux swap / Solaris



Partition table entries are not in disk order

trent@trent-laptop:~$ sudo mkdir /media/sda5

trent@trent-laptop:~$ sudo mount /dev/sda5 /media/sda5

trent@trent-laptop:~$ sudo grub-install --root-directory=/media/sda5 /dev/sda

error: cannot open `/dev/sdb' while attempting to get disk size

error: cannot open `/dev/sdb' while attempting to get disk size

error: cannot open `/dev/sdb' while attempting to get disk size

error: cannot open `/dev/sdb' while attempting to get disk size

error: cannot open `/dev/sdb' while attempting to get disk size

error: cannot open `/dev/sdb' while attempting to get disk size

Installation finished. No error reported.

This is the contents of the device map /media/sda5/boot/grub/device.map.

Check if this is correct or not. If any of the lines is incorrect,

fix it and re-run the script `grub-install'.



(hd0)	/dev/sda

(hd1)	/dev/sdb

trent@trent-laptop:~$ 

===================================================

Here's my system information:
Toshiba Tecra A7 with Intel 32-bit CPU, 504 MB RAM.

/dev/sda1	Win XP SP3		48430	MB	NTFS
/dev/sda2	Hidden partition	04040 MB	FAT32
/dev/sda5	Ubuntu 9.10		22803 MB	ext4
/dev/sda3	extended		24410	MB	
Memory*: 504 MB RAM, 76 GB HDD

Display*:
Mobile Intel 945 Express Chipset Family

Adapter:
1394 Net Adapter
Intel Pro/1000 PL Network Connection
Intel Pro/Wireless 3945ABG Network Connection

---

### Post by Trent T on 2010-06-14
Hi Mike--

I have a similar situation going on--
While mine is not resolved either, I found that I can boot Windows from a Super Grub Rescue Disk.  You can download the .iso from this website or one of its mirrors, here:

[http://www.supergrubdisk.org/index.php?pid=1](http://www.supergrubdisk.org/index.php?pid=1)

Burn the .iso to a CD, and you are ready for the next step.

Next, put the CD in your drive, and select your "Start computer from CD" option when you boot up.

Super Grub 2 has an option called "detect any OS"--

Select it, and your Windows OS will appear on the list.
Arrow down to select Windows, and it should boot up your computer.

Next, make a full system backup of your Windows system, possibly to an external hard drive--Hopefully, you made a complete backup before your attempt to put in Linux. If not, back it all up as soon as possible!

You may have to restore Windows from backup, so its good to have a complete backup on another drive somewhere.

Next Step-- your decision.  You could continue to attempt to fix Windows, or if you just want to take a break from Operating System Madness (OSM), you could just reformat the hard drive, and restore your Windows from backup.  If it was me, and if I had the space, I would make two NTFS partitions.  Install Windows in one, and leave the other one for backing up your crash-prone Windows system.  If you decide later to try Linux again, you could install it in your second partition...

Good luck!

--Trent T


> **S1n1ster said:**
> Someone please help me. I have a acer aspire as1410 with windows vista. I installed ubuntu but it did not work, after trying to make it work and giving up i decided to return to windows. when grub popped up i selected windows and used acer e-recovery management to reset the computer to factory settings with windows. now whenever i boot it says "grub loading. error no such partiton, grub rescue>" i am begging anyone i have spent months saving up for this computer and now i may have ruined it. please help me get vista working again.

Mike Cortez

---

### Post by talsemgeest on 2010-06-17
> **S1n1ster said:**
> Someone please help me. I have a acer aspire as1410 with windows vista. I installed ubuntu but it did not work, after trying to make it work and giving up i decided to return to windows. when grub popped up i selected windows and used acer e-recovery management to reset the computer to factory settings with windows. now whenever i boot it says "grub loading. error no such partiton, grub rescue>" i am begging anyone i have spent months saving up for this computer and now i may have ruined it. please help me get vista working again.

Mike Cortez
Sorry for the delay, I have been extremely busy lately. Make sure you run through the instructions for windows vista, and if you don't have a vista install dvd there is a link to a recovery cd.

As long as the acer recovery successfully installed windows, and it is just the bootloader that is problematic, you should be fine.

---

### Post by talsemgeest on 2010-06-17
> **Trent T said:**
> 
I followed your steps to re-install GRUB2.  An error message said that /dev/sdb1 could not be accessed.  

Upon restart, GRUB2 now says,

Loading GRUB - file not found
grub rescue>


Ok, make sure that after you have mounted /dev/sda5 you can access the partition, so manually browse to /media/sda5 and see if you can access all the usual files. If not, norton may have corrupted the partition.

Also, I would suggest removing norton and installing one of the great free alternative antivirus programs. but of course that is up to your discretion.

---

### Post by LocutusSK on 2010-06-17
Hi,
 

 First, I would like to thank talsemgeest for excellent guide.  
 

 Now, here's my problem. I have two HDDs. On one I have Windows 7, on the second one I installed Ubuntu 10.04. After installing Ubuntu, I couldn't boot to Windows. So I ran bootrec.exe /fixboot and bootrec.exe /fixmbr in the console. Now I can boot into Windows, but I can't boot into Ubuntu.
 

 I followed your instructions for restoring Ubuntu grub bootloader (9.10 an beyond) and here's what I get when I run sudo fdisk -l


```
                           
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c320c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       13055   104755200    7  HPFS/NTFS
/dev/sda3           26109      121602   767044608    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT

```                                  This is what I get when I run sudo parted -l


```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SAMSUNG HD103UJ (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size   Type     File system  Flags
 1      1049kB  106MB   105MB  primary  ntfs         boot
 2      106MB   107GB   107GB  primary  ntfs
 3      215GB   1000GB  785GB  primary  ntfs


Model: ATA WDC WD20EARS-00J (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  2097kB  1049kB                        bios_grub
 2      2097kB  1976GB  1976GB  ext4
 3      1976GB  2000GB  24.6GB  linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label

```                                  So I thought that the ubuntu partition will be /dev/sdb2, but this is what I get when I run the remaining commands:


```

ubuntu@ubuntu:~$ sudo mkdir /media/sdb2
ubuntu@ubuntu:~$ sudo mount /dev/sdb2 /media/sdb2
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sdb2 dev/sdb/usr/sbin/grub-probe: error: cannot stat `dev/sdb'.
Invalid device `dev/sdb'.
Try `/usr/sbin/grub-setup --help' for more information.
```                                  Any ideas how to solve this ?


Many thanks.

---

### Post by COKEDUDE on 2010-06-18
This guide was very helpful. Thx for this.

---

### Post by imjscn on 2010-06-18
> **kansasnoob said:**
> 

```
sudo apt-get install mbr
```

and:

```
sudo install-mbr /dev/sdX
```

(of course replace the X with your destination)

Then just reboot.

I actually tried that with XP and it worked fine.

I partitioned my entire harddisk except a Hidden partition, and clean install winxp on laptop, then,** I couldn't boot OS and I couldn't boot from CD or floppy**. Luckily, an old Xunbuntu 8.04 CD can boot, and **I installed Xubuntu. Now can boot Xubuntu OS, still can't boot CD or floppy. **There's no boot choice or any menu when start. I guess mbr is damaged. Here's my boot info:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /COMMAND.COM

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    29,302,559    29,302,497  83 Linux
/dev/sda2         107,064,720   117,195,119    10,130,400  12 Compaq diagnostics
/dev/sda3    *     29,302,560    33,206,354     3,903,795  83 Linux
/dev/sda4          33,206,355   107,057,159    73,850,805   5 Extended
/dev/sda5          33,206,418    35,166,284     1,959,867  82 Linux swap / Solaris
/dev/sda6          35,166,348    74,236,364    39,070,017  83 Linux
/dev/sda7          74,236,428    76,196,294     1,959,867  83 Linux
/dev/sda8          76,196,358   107,057,159    30,860,802  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        257a7d04-2874-4282-9bb7-77b06fe4b471   ext3                                     
/dev/sda2        D005-3738                              vfat       IBM_SERVICE                   
/dev/sda3        ae9a8425-b9ec-41ac-8399-0fb9e41649c7   ext3                                     
/dev/sda5        3618fbc0-1750-46dd-938c-7437a39a469d   swap                                     
/dev/sda6        66b82697-508a-454e-b28a-2cfcb4d8db10   ext3                                     
/dev/sda7        cc6f9869-9ee1-4909-a377-a2142f3b1b6e   ext3                                     
/dev/sda8        f8c6f3d3-5f31-4cb3-990a-c4e332706e8f   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda3        /boot                    ext3       (rw,relatime)
/dev/sda6        /home                    ext3       (rw,relatime)
/dev/sda7        /tmp                     ext3       (rw,relatime)
/dev/sda8        /usr                     ext3       (rw,relatime)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=257a7d04-2874-4282-9bb7-77b06fe4b471 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=ae9a8425-b9ec-41ac-8399-0fb9e41649c7 /boot           ext3    relatime        0       2
# /dev/sda6
UUID=66b82697-508a-454e-b28a-2cfcb4d8db10 /home           ext3    relatime        0       2
# /dev/sda7
UUID=cc6f9869-9ee1-4909-a377-a2142f3b1b6e /tmp            ext3    relatime        0       2
# /dev/sda8
UUID=f8c6f3d3-5f31-4cb3-990a-c4e332706e8f /usr            ext3    relatime        0       2
# /dev/sda5
UUID=3618fbc0-1750-46dd-938c-7437a39a469d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: initrd.img
    .0GB: vmlinuz

================================ sda2/boot.ini: ================================

[boot loader]

timeout=0

default=C:\

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\ = "PC-DOS"


============================= sda3/grub/menu.lst: =============================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=257a7d04-2874-4282-9bb7-77b06fe4b471 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=257a7d04-2874-4282-9bb7-77b06fe4b471 ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=257a7d04-2874-4282-9bb7-77b06fe4b471 ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=================== sda3: Location of files loaded by Grub: ===================


  15.7GB: grub/menu.lst
  15.7GB: grub/stage2
  15.0GB: initrd.img-2.6.24-16-generic
  15.0GB: initrd.img-2.6.24-16-generic.bak
  15.0GB: vmlinuz-2.6.24-16-generic
```

Following this thread instruction, I did the 2 step:
```
sudo apt-get install mbr
```

Result: mbr is already the newest version.
        mbr set to manually installed.


```
sudo install-mbr /dev/sda1
```

Result: install-mbr:/dev/sda1: No boot signature found.  Use --force to override.

I'm a linux dummy, please instruct me what to do now.

---

### Post by imjscn on 2010-06-18
By the way, why can boot from Xubuntu LiveCD but not other CDs ? (my winxp is a copyright one)

---

### Post by oldfred on 2010-06-18
imjscn This thread is a how to and posts should relate to corrections, comments and improvements, not individual problems. Please start your own thread.

You have a variety of issues. Windows boots the partition with the boot flag but you do not have it on the windows partition. It looks like you moved from sda3 to sda2 as your boot.ini refers to sda3 not sda2 to boot.

---

### Post by imjscn on 2010-06-18
sorry for posting inproperly. I will start my own thread then. Thanks!

---

### Post by mistaken on 2010-06-18
Hello,
I upgraded to ubuntu to 10.04 and now unable to load any OS. 
I get that error, that no such device and GRUB RESCUE>
thats all. I can´t use a live cd, as have NO CD DRIVE, NO boot from flash, NO floppy.
Any suggestions how manually configure bootloader? Now works only ls and insmod commands as grub rescue is a little bit restricted... even help command not working :)
please answer grub rescue command line experts :)

P.S. before I had win xp+xubuntu and lots of partitions. Probably, too grubs, as I had to choose what I want to load twice :) and now - no possibility to choose at all.... help. :)

---

### Post by talsemgeest on 2010-06-18
> **LocutusSK said:**
> Hi,
 
 Now, here's my problem. I have two HDDs. On one I have Windows 7, on the second one I installed Ubuntu 10.04. After installing Ubuntu, I couldn't boot to Windows. So I ran bootrec.exe /fixboot and bootrec.exe /fixmbr in the console. Now I can boot into Windows, but I can't boot into Ubuntu.

Hmm, your fdisk output looks a little odd to me. It seems to be 2TB, and using an odd system. Can you tell me a bit more about the drive?

---

### Post by talsemgeest on 2010-06-18
> **mistaken said:**
> Hello,
I upgraded to ubuntu to 10.04 and now unable to load any OS. 
I get that error, that no such device and GRUB RESCUE>
thats all. I can´t use a live cd, as have NO CD DRIVE, NO boot from flash, NO floppy.
Any suggestions how manually configure bootloader? Now works only ls and insmod commands as grub rescue is a little bit restricted... even help command not working :)
please answer grub rescue command line experts :)

P.S. before I had win xp+xubuntu and lots of partitions. Probably, too grubs, as I had to choose what I want to load twice :) and now - no possibility to choose at all.... help. :)
I am unsure of any way to fix your problem without booting. Can you perhaps boot over a network?

---

### Post by LocutusSK on 2010-06-19
> **talsemgeest said:**
> Hmm, your fdisk output looks a little odd to me. It seems to be 2TB, and using an odd system. Can you tell me a bit more about the drive?
 
Hi, 
 
It's a 2TB WD Caviar Green WD20EARS. I've let the Ubuntu installation to format it automatically. I didn't format it myself.
 
Just a guess, could the problem be that this HDD is using the new 4kB sector blocks instead of the usual 512B blocks ??
 
Thanks.

---

### Post by mistaken on 2010-06-19
> **talsemgeest said:**
> I am unsure of any way to fix your problem without booting. Can you perhaps boot over a network?
well, I see there is a choise to boot with removable media, maybe I&#314;l try to buy usb stick... maybe it will work,,  and have no idea how to boot through network. Is this in bios? or in boot meniu?

---

### Post by mistaken on 2010-06-20
> **talsemgeest said:**
> I am unsure of any way to fix your problem without booting. Can you perhaps boot over a network?
thanks for an idea, managed through network. Lucky me, that still have my 15 years PC and a router with a few wires :))
sad, that I first tried with USB :) waisted money :)

---

### Post by Mahogan on 2010-06-29
Will this tutorial instruction work with a triple boot with OSX? It seems that the OSX is slightly different? I've posted a question about my setup here: [http://ubuntuforums.org/showthread.php?t=1506128](http://ubuntuforums.org/showthread.php?t=1506128)

---

### Post by ikeurb on 2010-06-30
talsemgeest, this is exactly what I needed. Thanks!

---

### Post by Chandler208 on 2010-07-02
I just reinstalled windows 7 on my machine and than i when back and installed ubuntu. I was able to get in to both just fine. Installed all the updates for ubuntu. then i restarted and loaded windows and installed all the updates there than restarted and now i get a blank screen with a flashing dash.
please help. im taking the A+ certification class and i need windows on my laptop but i love ubuntu.

---

### Post by dalesd on 2010-07-05
I've read through (most of) this thread, but I haven't found anything that fits my situation.

I got a new laptop from work, running Windows XP 64-bit.  I installed Ubuntu 10.04 onto a SD card from the liveCD.  Now when I start up, I get an error: no such device ######### (where ## is the UUID of the SD card.) 

Anyway, here's mu fdisk -l
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5f76d897

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       41344   312560608+   7  HPFS/NTFS

Disk /dev/mmcblk0: 8166 MB, 8166309888 bytes
4 heads, 16 sectors/track, 249216 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000de66b

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *          33      236928     7580672   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/mmcblk0p2          236960      249184      391169    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/mmcblk0p5          236961      249184      391168   82  Linux swap / Solaris

```
So before I mess anything else up, how do I fix this?  I guess GRUB got installed on sda, but my intent was to not use grub at all, just pick from the bios which device to boot off of (hard drive or the SD card).  Right now I'll take any solution that gets my work computer to boot back into XP.

I think I should do this:
```
ubuntu@ubuntu:~$ sudo mkdir /media/sdcard
ubuntu@ubuntu:~$ sudo mount /dev/mmcblk0p1 /media/sdcard
sudo grub-install --root-directory=/media/sdcard /dev/sda

```
Yes?  No?

---

### Post by dalesd on 2010-07-05
FYI, I used lilo to restore the mbr to get my Windows boot back.  It turns out that this laptop can't boot from the SD card anyway.

---

### Post by methoxyroxy on 2010-07-17
Dear talsemgeest,

I did the makedir /media/ubuntu thing and now my dual boot is not booting at all anymore, i get grub rescue> and from there I'm clueless.

Now when I put the original windows xp and turn the computer on it'll boot my ubuntu 10.04 but I still can't access windows, which was what started all the trouble in the first place.

Here's what Boot Info Script gave me, I really hope you can help me,

Thanks and Greetings from Amsterdam, 

Roxy




```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================[/SIZE] [SIZE=1]

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in [/SIZE] [SIZE=1]
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /media/sdb1/boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________[/SIZE] [SIZE=1]

    File system:       ntfs[/SIZE] [SIZE=1]
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 271959 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________[/SIZE] [SIZE=1]

    File system:       Extended Partition[/SIZE] [SIZE=1]
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________[/SIZE] [SIZE=1]

    File system:       ntfs[/SIZE] [SIZE=1]
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 271959 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________[/SIZE] [SIZE=1]

    File system:       ext4[/SIZE] [SIZE=1]
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 271959 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________[/SIZE] [SIZE=1]

    File system:       Extended Partition[/SIZE] [SIZE=1]
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________[/SIZE] [SIZE=1]

    File system:       swap[/SIZE] [SIZE=1]
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________[/SIZE] [SIZE=1]

    File system:       ntfs[/SIZE] [SIZE=1]
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================[/SIZE] [SIZE=1]

Drive: sda ___________________ _____________________________________________________[/SIZE] [SIZE=1]

Disk /dev/sda: 120.0 GB, 120034123776 bytes[/SIZE] [SIZE=1]
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System[/SIZE] [SIZE=1]

/dev/sda1    *             63    61,432,559    61,432,497   7 HPFS/NTFS[/SIZE] [SIZE=1]
/dev/sda2          61,432,560   234,420,479   172,987,920   f W95 Ext d (LBA)
/dev/sda5          61,432,623   234,420,479   172,987,857   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________[/SIZE]  [SIZE=1]

Disk /dev/sdb: 80.1 GB, 80054059008 bytes[/SIZE] [SIZE=1]
255 heads, 63 sectors/track, 9732 cylinders, total 156355584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System[/SIZE] [SIZE=1]

/dev/sdb1                  63   150,336,269   150,336,207  83 Linux[/SIZE] [SIZE=1]
/dev/sdb2         150,336,270   156,344,579     6,008,310   5 Extended
/dev/sdb5         150,336,333   156,344,579     6,008,247  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________[/SIZE]  [SIZE=1]

Disk /dev/sdc: 160.0 GB, 160041885696 bytes[/SIZE] [SIZE=1]
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System[/SIZE] [SIZE=1]

/dev/sdc1                  63   312,576,704   312,576,642   7 HPFS/NTFS[/SIZE] [SIZE=1]


blkid -c /dev/null: ____________________________________________________________[/SIZE]  [SIZE=1]

Device           UUID                                   TYPE       LABEL                         [/SIZE] [SIZE=1]

/dev/sda1        22EC27A3EC276FE9                       ntfs       The Falcon-1                  [/SIZE] [SIZE=1]
/dev/sda2: PTTYPE="dos" 
/dev/sda5        E69490B494908927                       ntfs       The Falcon-3                  
/dev/sda: PTTYPE="dos" 
/dev/sdb1        749b01da-8f28-429a-af94-2695e259f52f   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        a168466b-66ce-4b07-bf5c-fc88b150c14e   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        FA90895E9089226D                       ntfs       TOUGHDRIVE                    
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================[/SIZE] [SIZE=1]

Device           Mount_Point              Type       Options[/SIZE] [SIZE=1]

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)[/SIZE] [SIZE=1]
/dev/sda1        /media/The Falcon-1      fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/The Falcon-3      fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/TOUGHDRIVE        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=roxana)


================================ sda1/boot.ini: ================================[/SIZE]  [SIZE=1]

[boot loader] [/SIZE] [SIZE=1]
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdb1/boot/grub/grub.cfg: ===========================[/SIZE] [SIZE=1]

#[/SIZE] [SIZE=1]
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###[/SIZE] [SIZE=1]
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="10"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {[/SIZE] [SIZE=1]
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {[/SIZE] [SIZE=1]
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 749b01da-8f28-429a-af94-2695e259f52f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 749b01da-8f28-429a-af94-2695e259f52f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=20
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###[/SIZE] [SIZE=1]
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###[/SIZE] [SIZE=1]
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 749b01da-8f28-429a-af94-2695e259f52f
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=749b01da-8f28-429a-af94-2695e259f52f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 749b01da-8f28-429a-af94-2695e259f52f
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=749b01da-8f28-429a-af94-2695e259f52f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 749b01da-8f28-429a-af94-2695e259f52f
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=749b01da-8f28-429a-af94-2695e259f52f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 749b01da-8f28-429a-af94-2695e259f52f
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=749b01da-8f28-429a-af94-2695e259f52f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 749b01da-8f28-429a-af94-2695e259f52f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=749b01da-8f28-429a-af94-2695e259f52f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 749b01da-8f28-429a-af94-2695e259f52f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=749b01da-8f28-429a-af94-2695e259f52f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 749b01da-8f28-429a-af94-2695e259f52f
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=749b01da-8f28-429a-af94-2695e259f52f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 749b01da-8f28-429a-af94-2695e259f52f
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=749b01da-8f28-429a-af94-2695e259f52f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###[/SIZE] [SIZE=1]
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 749b01da-8f28-429a-af94-2695e259f52f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 749b01da-8f28-429a-af94-2695e259f52f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###[/SIZE] [SIZE=1]
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 22ec27a3ec276fe9
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###[/SIZE] [SIZE=1]
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

### BEGIN /etc/grub.d/40_custom ###[/SIZE] [SIZE=1]
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 22ec27a3ec276fe9
    drivemap -s (hd0) ${root}
    chainloader +1

### END /etc/grub.d/40_custom ###[/SIZE] [SIZE=1]
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================[/SIZE] [SIZE=1]

# /etc/fstab: static file system information.[/SIZE] [SIZE=1]
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=749b01da-8f28-429a-af94-2695e259f52f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=a168466b-66ce-4b07-bf5c-fc88b150c14e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================[/SIZE] [SIZE=1]


    .1GB: boot/grub/core.img[/SIZE]  [SIZE=1]
   4.2GB: boot/grub/grub.cfg
  11.2GB: boot/initrd.img-2.6.31-21-generic
  23.7GB: boot/initrd.img-2.6.32-21-generic
    .9GB: boot/initrd.img-2.6.32-22-generic
    .9GB: boot/initrd.img-2.6.32-23-generic
   5.1GB: boot/vmlinuz-2.6.31-21-generic
   1.1GB: boot/vmlinuz-2.6.32-21-generic
    .9GB: boot/vmlinuz-2.6.32-22-generic
    .8GB: boot/vmlinuz-2.6.32-23-generic
    .9GB: initrd.img
    .9GB: initrd.img.old
    .8GB: vmlinuz
    .9GB: vmlinuz.old
```

---

### Post by drs305 on 2010-07-17
methoxyroxy,

Welcome to the Ubuntu forums.

It looks like you have some work to do to restore things. Grub 2 is installed in several partitions where it probably shouldn't be, and is looking at the wrong location for its files. In addition, as configured your Windows won't work either. 

To get Ubuntu working again, reinstall Grub2 using the LiveCD.  Boot to the Desktop, then open a terminal (Applications, Accessories, Terminal).

Run the following command:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

Note in the second command the location is the device (sdb) and NOT the partition (sdb1).

Once installed, reboot and you should have a working Ubuntu installation. Although Windows will probably be listed in the menu, I don't think it will run. You will have to refer to *talsemgeest's* original post on how to restore Windows.

By the way, I have taken the liberty to reformat your previous post by adding "code" tags to condense the output of the RESULTS.txt.  You generate the tags by pressing the **#** icon in the post's menu and then paste the contents between the generated **[noparse]```

```[/noparse]** tags.

---

### Post by methoxyroxy on 2010-07-17
Thanks so much Drs. for the welcome and the help.
It's really ensuring to know that I'm not alone in this..

I'm burning the CD as I type.. and hopefully fix stuff with the help of your support.

However, since it is when things went wrong for me - I don't know I probably did something wrong though I'm usually very secure in copying commands and such - I'm a bit scared to repeat the stuff talsemgeest posted.. or do you think things were messed up before I entered those commands?

Anyway, is there any possibility that I can go back to Karmic Koala? It's really frustrating to have all these bugs on this computer (I'm at a friends now), at home I'm still running 9.10 and all is doing well. 

Well, my cd is finished now, I'll try what you said. Thanks again so much, 

Greetz from Holland,
Roxy

also, thanks for reformatting my post.. I didn't know which command to use but was too frustrated to take the time to find out...

Ps*
What do these codes do?

---

### Post by drs305 on 2010-07-17
I would recommend you stick to Lucid, as it's a long term support (LTS) version. If you don't like updating, this one will be around for quite a while once you get it set up.

I don't know which "codes" you are referring to. The 'code' blocks in a post just ensure a paste operation doesn't take up too much screen space.

If you are referring to the two commands to reinstall grub, the first one mounts your Ubuntu partition. You must do that so the system can write the files to it. If it was unmounted, sdb1 could not be written to.

The second command writes some code to the MBR, and then installs the grub files on sdb1. The "root-directory" switch tells the installer where to write the files. Since sdb1 is mounted on /mnt, assigning the 'root-directory' to '/mnt' is indirectly telling the system to install them on the sdb1 partition, with sdb1's / folder being the starting point.

---

### Post by methoxyroxy on 2010-07-17
Sorry for being unclear.. I indeed meant the terminal commands you gave..

Thanks so much, it worked perfectly! And glad to have learned more. 
I'll try to fix the windows boot now... thumbs crossed :D

*and it worked! Thanks for the help!

---

### Post by cinikal on 2010-07-21
Hi , Alot of posts here hope im not repeating. I have windows xp installed. i loaded ubuntu, then windows xp wouldnt boot. So i followed your steps to "fixboot" and "fixmbr" ...Windows works perfectly again. So how do i get it to open up grub again and give me the option to choose windows or ubuntu? Now i have a windows computer again...](*,) with ubuntu hidden in there somewhere. actually if i put the live cd in it starts to boot then hangs on a black screen with a cursor on the top left.

---

### Post by jbalgrim on 2010-07-23
hey guys,
Im running Vista and Ubuntu and updated Ubuntu today, and also updated grub. After the update, i could not boot from grub so i removed grub using the Vista cd recovery (did not have any live cd for Ubuntu) and restored Microsoft's boot loader ( using Bootrec.exe/FIXMbr), so my question is: if i use microsoft's boot loader to boot Ubuntu would there be any impending problems? or would i need to install grub again?, though both operating systems are currently booting with microsoft's boot loader.
thanks

---

### Post by sndarvekar on 2010-07-24
Same problem, trying out the recommendations.
Will get back with what happened:popcorn::popcorn::popcorn:

---

### Post by adamlack on 2010-07-26
Wasn't able to boot (Trying to dual boot Win7/Ubuntu), and after much searching, this was exactly what I needed. The command prompt solution from the windows disk worked perfectly.

Thank you very much!

---

### Post by Trent T on 2010-07-28
Hi Mistaken--
I wonder if you can borrow or buy a CD/DVD drive that plugs into USB?  If so, you could then boot off the installation disk for Ubuntu, or use the Grub2 rescue disk...

Best of luck!

---

### Post by Trent T on 2010-07-28
I was able to browse to /dev/sda5, but still received the rescue> prompt upon restart.  

Under another thread (Grub no longer boots anything [http://ubuntuforums.org/showthread.php?t=1538170&highlight=reinstall+grub2](http://ubuntuforums.org/showthread.php?t=1538170&highlight=reinstall+grub2) ), 
geoffjay (in Vancouver, BC) suggested the following commands;

sudo grub-install /dev/sda
sudo grub-update

Even though the second command was not recognized by Ubuntu 9.10, just the first one was sufficient to restore GRUB2, including the option on bootup to get into Win XP.  I'm back in business!:p

Thanks again, talsemgeest, for this tutorial!  I have bookmarked it in case the Win XP side trashes my Grub2 again..

> **talsemgeest said:**
> Ok, make sure that after you have mounted /dev/sda5 you can access the partition, so manually browse to /media/sda5 and see if you can access all the usual files. If not, norton may have corrupted the partition.

Also, I would suggest removing norton and installing one of the great free alternative antivirus programs. but of course that is up to your discretion.

---

### Post by bcbc on 2010-07-28
There is a recent grub-pc update that is causing some issues. For some wubi users, they are installing grub to their harddrive MBR. The fix is to reinstall the windows bootloader or use an alternative e.g. lilo

---

### Post by warpasylum on 2010-08-01
Awesome.  Thanx man.

---

### Post by brettman on 2010-08-07
Totally saved my a**!!  Can't thank you enough for posting these clear and effective instructions.  Used wubi to try out Ubuntu with dual boot.  Got into hot water after running some automatic updates.  The updater asked me some basic questions about grub which I clearly didn't answer correctly (I'm a child of the M$ dominion... this is basically my first exploration of linux).  Everything was fine until next reboot, where I got some kind of grub recovery command prompt and NO OS whatsoever. Was gearing up for a night of re-installations, but the windows 7 restore instructions got me both my OS's back in less than 20 mins.  AWESOME!

---

### Post by rainbowagent7 on 2010-08-08
I agree with Brettman, this tutorial saved my ****. I bought an new computer with Windows 7 pre-installed, but I love Linux so I instantly installed Ubuntu. However I didn't realize setting up windows would move GRUB (I'm half noob!). I followed the instructions to the tee and am now once again enjoying the fruits of a dual boot system. Many, many thanks to Talsemgeest and everyone else who takes the time and expends the energy to write concise tutorials like this and in doing so bridges the gap between sucksville and Linux.

---

### Post by sndarvekar on 2010-08-11
I did as said and Now my bot screen does not show windows. What to do?
pasting the boot info

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdc has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    48,837,599    48,837,537   7 HPFS/NTFS
/dev/sda2          48,837,600   151,235,909   102,398,310   7 HPFS/NTFS
/dev/sda3         151,235,910   253,634,219   102,398,310   7 HPFS/NTFS
/dev/sda4         253,634,220   356,032,529   102,398,310   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sdb2         102,398,371   976,773,119   874,374,749   f W95 Ext d (LBA)
/dev/sdb5         102,398,373   204,796,619   102,398,247   7 HPFS/NTFS
/dev/sdb6         204,796,683   511,991,549   307,194,867   7 HPFS/NTFS
/dev/sdb7         511,991,613   936,375,411   424,383,799   7 HPFS/NTFS
/dev/sdb8         936,376,320   974,985,215    38,608,896  83 Linux
/dev/sdb9         974,999,552   976,773,119     1,773,568  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0A3CE38B3CE3705D                       ntfs       XP Professional               
/dev/sda2        D2B4754FB47536D7                       ntfs       I                             
/dev/sda3        960C82930C826DD5                       ntfs       H                             
/dev/sda4        0028602F286025BE                       ntfs       K                             
/dev/sda: PTTYPE="dos" 
/dev/sdb1        88ACF8AEACF89840                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        E06074BD60749BCA                       ntfs       F                             
/dev/sdb6        F26C66686C662795                       ntfs       G                             
/dev/sdb7        369C96859C963F75                       ntfs       K                             
/dev/sdb8        9cce866c-19c2-439b-8912-8c1b307b2904   ext4                                     
/dev/sdb9        0f2d6416-095e-4b61-add3-cb2a7d3b3dc8   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc         8421-35D9                              vfat       PHONE                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb8        /                        ext4       (rw,errors=remount-ro)
/dev/sdc         /media/PHONE             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr1         /media/magicJack         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 

=========================== sdb8/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 9cce866c-19c2-439b-8912-8c1b307b2904
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 9cce866c-19c2-439b-8912-8c1b307b2904
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 9cce866c-19c2-439b-8912-8c1b307b2904
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=9cce866c-19c2-439b-8912-8c1b307b2904 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 9cce866c-19c2-439b-8912-8c1b307b2904
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=9cce866c-19c2-439b-8912-8c1b307b2904 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 9cce866c-19c2-439b-8912-8c1b307b2904
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=9cce866c-19c2-439b-8912-8c1b307b2904 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 9cce866c-19c2-439b-8912-8c1b307b2904
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=9cce866c-19c2-439b-8912-8c1b307b2904 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 9cce866c-19c2-439b-8912-8c1b307b2904
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 9cce866c-19c2-439b-8912-8c1b307b2904
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda9       /               ext4    errors=remount-ro 0       1
/dev/sda8       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb8: Location of files loaded by Grub: ===================


 481.7GB: boot/grub/core.img
 481.7GB: boot/grub/grub.cfg
 481.7GB: boot/initrd.img-2.6.32-21-generic
 481.8GB: boot/initrd.img-2.6.32-24-generic
 481.7GB: boot/vmlinuz-2.6.32-21-generic
 481.8GB: boot/vmlinuz-2.6.32-24-generic
 481.8GB: initrd.img
 481.7GB: initrd.img.old
 481.8GB: vmlinuz
 481.7GB: vmlinuz.old
Urgent help needed

---

### Post by sndarvekar on 2010-08-11
I could fix up the problem, thanks to a brilliant article at
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Thanks, and really Ubuntu rocks, I am a Fan of it

---

### Post by jctolton on 2010-08-25
I have tried reinstalling Ubuntu. I have tried repairing Windows XP bootloader with the Windows XP installation disk. Ubuntu starts just fine. WHen GRUB tries to boot the Windows XP partition all I get is the blinking cursor and it never advances to the next step.

Does anyone have more specific suggestions for me?

---

### Post by hoogvlieth on 2010-08-25
Hi !! 

I have the same problem that i can't load my grub any more. I did try to fix it but i get the following in the terminal venster. But when i restart it hasn't changed anything.

It happend when i update 9.10 to 10.04 
Can some one help me pleaseeee.
------------------------------------------------------------------------
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1215     9759456    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           19092       19457     2939895   82  Linux swap / Solaris
/dev/sdb2   *           1       19091   153348426   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo mkdir /media/sdb2
ubuntu@ubuntu:~$ sudo mount /dev/sdb2 /media/sdb2
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sdb2 /dev/sdb
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /media/sdb2/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/media/sdb2/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /media/sdb2/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/sda
(hd1)   /dev/sdb
ubuntu@ubuntu:~$ 



Bye Harry

---

### Post by von Stalhein on 2010-08-26
> **jctolton said:**
> I have tried reinstalling Ubuntu. I have tried repairing Windows XP bootloader with the Windows XP installation disk. Ubuntu starts just fine. WHen GRUB tries to boot the Windows XP partition all I get is the blinking cursor and it never advances to the next step.

Does anyone have more specific suggestions for me?

What's the output of ```
sudo fdisk -l
``` as a start?

---

### Post by jctolton on 2010-08-26
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x845a4551

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7016    56348668    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           18815       19452     5124735   1c  Hidden W95 FAT32 (LBA)
/dev/sda3           19453       19457       40162+  82  Linux swap / Solaris
/dev/sda4            7016       18814    94773249   83  Linux
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by von Stalhein on 2010-08-27
Sorry, not thinking straight last night - should also have asked at the same time which GRUB version?

If GRUB2, [this thread here could be useful]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by deviltalk on 2010-08-27
nice fix, but does anyone know how to install ubuntu netbook remix, without disturbing the lg netbook software restore partition and not deleting the windows xp allready on the system...
i get as far as installed, put the bootloader into the ubuntu partition, and viola windows loads every time no option for ubuntu..... its not listed in the boot.ini in windows and i cant look at the ext4 partition, within windows. please help ps mostly hapless noob.

---

### Post by jctolton on 2010-08-27
I checked the Ubuntu Software Center and it looks like I am running Grub version 2, grub-pc.

---

### Post by jctolton on 2010-08-27
deviltalk, do you know what the delay is for your GRUB installation? If the delay is not long enough then you will not have the time to choose.

---

### Post by mosquetero on 2010-09-01
Hi everyone!

I am having problems to access to my operating system because GRUB is not working (I get a Error 22). I have Ubuntu 9.04 and I tried to follow its tutorial but when I get to the command: 

```
find /boot/grub/stage1
```

I get>

```
Error 15 : File not found
```

Can anyone help me please? I am doing this using my Ubuntu 9.04 live CD

Thanks in advanced

---

### Post by dubingiai on 2010-09-10
> **talsemgeest said:**
> **[SIZE=6][COLOR=blue]How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 10.04)[/COLOR][/SIZE]**

This How-to is for windows dual booters who reinstall an operating system only to find that it has taken away access to their other operating system. 
Whether you want to restore the XP, Vista, 7 or Ubuntu (Grub) bootloader, this guide will walk you through it.

All three parts of this tutorial require that you boot from a cd. If you don't know how to do this, check [here.]("http://www.hiren.info/pages/bios-boot-cdrom")

If you have made a mistake and want to revert the changes, simply follow the instructions for reinstalling the previous bootloader. For example, if you have installed vista over ubuntu, try to get the ubuntu bootloader back, but want to get the vista bootloader back, simply follow my instructions for installing the vista bootloader.


[SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.10 and beyond)[/COLOR][/SIZE]

First you need to find out what your drives are called. You can do this by going to a terminal and typing: ```
sudo fdisk -l
``` You will get something like this:


[IMG]http://img517.imageshack.us/img517/713/svr8xil.jpg[/IMG]

From that you need to find the device name of your Ubuntu drive, something like “/dev/sda5&#8243;.
 So, still in the terminal, type:
```

sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
```And then, to reinstall the grub: ```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```Push enter and you’re done! Of course you need to replace “/dev/sda5&#8243; and “/dev/sda” with what you found in the fdisk output.

[SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.04 and older)[/COLOR][/SIZE]

First of all, all credit for this part of the tutorial goes to [catlet]("http://ubuntuforums.org/showpost.php?p=1308395&postcount=1"). I am simply rewriting his tutorial to have all three bootloaders in this tutorial.

So, lets begin. To restore the grub, you must boot off the ubuntu live cd. Any ubuntu live cd will do.

Once there, open a terminal (Applications>Accessories>Terminal) and type this:

```
sudo grub
```Next, you need to find which hard drive ubuntu and the grub is installed to. You do this by running this command:

```
find /boot/grub/stage1
```Take note of what it returns (something like (hd0,1).)

Now you need to tell Grub where it is installed. Using the output of the last command, change this one and run it:

```
root (hd<a>,<b>)
```Replacing <a> and <b> with what you got back before. For example, if "find /boot/grub/stage1" gave me "(hd0,1)", you would run "root (hd0,1)"

Ok, so thats the configuration over and done with. Now we just need to run one command to install the Grub to your hard drive:

```
setup (hd0)
```Now to quit and check if it has worked:

```
quit
``````
sudo reboot
```Make sure you have taken the live cd out of your disc tray. All going well, you should start back up and see the grub once again.

 
[SIZE=5][COLOR=red]How to restore the Windows XP bootloader[/COLOR][/SIZE]

For this you will need your Windows XP installation CD. Boot into it now.

You will get to a part where it asks if you want to repair or recover. To do so, press "r".

If prompted, enter your Windows XP administrator password. This will leave you at at a command line, so type in the following two commands:

```
fixboot
``````
fixmbr
```Then type ```
exit
``` then remove your XP cd. If everything has gone well, you should come to your XP bootloader.


[SIZE=5][COLOR=red]How to restore the Windows Vista or 7 bootloader[/COLOR][/SIZE]

To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download for [Vista]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download") or [Win 7](http://neosmart.net/blog/2009/windows-7-system-repair-discs/).
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

```
bootrec.exe /fixboot
``````
bootrec.exe /fixmbr
```Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader.

Hey!

And maybe you know what to do if i've forgotten my administrator password for win XP?

---

### Post by von Stalhein on 2010-09-11
> **dubingiai said:**
> Hey!

And maybe you know what to do if i've forgotten my administrator password for win XP?

[http://www.psychocats.net/ubuntucat/resetwindowspassword/](http://www.psychocats.net/ubuntucat/resetwindowspassword/)
[http://www.makeuseof.com/tag/3-ways-to-reset-the-forgotten-windows-administrator-password/](http://www.makeuseof.com/tag/3-ways-to-reset-the-forgotten-windows-administrator-password/)

---

### Post by Vampryss on 2010-09-14
[CENTER][COLOR="Blue"]I have to say I'm quite frustrated with the installation process of this OS. I wiped my 320GB drive, installed a fresh copy of XP on 120GB partition (as the BIOS doesn't support the full 320GB) & the rest was unpartitioned free space. When installing Ubuntu NOTHING in the [step by step instructions]("https://help.ubuntu.com/community/GraphicalInstall") say you must partition sections manually or else the MBR for windows gets wiped out. I selected run side by side etc as the instructions said, a second time after wiping & re-installing windows again thinking I've done something wrong. It doesn't work without having to go back in & type in all sorts of commands to get the grub and/or Windows Bootloader working. Upon installation ubuntu sees that I have XP installed. Why doesn't it create the needed partitions i.e. 10GB for the OS & the 2 others for the swap etc? Why do I have to be a rocket scientist or an experienced linux user just to install? I'm sorry if I'm a little gruff but I've spent all day doing this & I swear reading every single forum out there on the dual boot process. I am ready to just say forget it.. I enjoy using linux but I need Windows.[/COLOR][/CENTER]

---

### Post by drs305 on 2010-09-15
> **Vampryss said:**
> [CENTER][COLOR="Blue"]I have to say I'm quite frustrated with the installation process of this OS. ... When installing Ubuntu NOTHING in the [step by step instructions]("https://help.ubuntu.com/community/GraphicalInstall") say you must partition sections manually or else the MBR for windows gets wiped out. I selected run side by side etc as the instructions said, a second time after wiping & re-installing windows again thinking I've done something wrong. It doesn't work without having to go back in & type in all sorts of commands to get the grub and/or Windows Bootloader working.[/COLOR][/CENTER]

Sorry you had so much difficulty with the install. I'm reviewing the link you provided. I see a step 6 which states:
> 
If you want to install Ubuntu on a single partition Dual Booting, Select Guided – resize. In the New partition size area, drag the area between the two partitions to create your desired partition sizes. Click Forward. 


Is that the process you were using? Or did you go with manual partitioning? I know you say you chose "side by side", which to me means it should have set up the partitioning for you and should have done things for you. I haven't used the side-by-side option in quite some time.

I'm asking because I can edit Ubuntu Community docs but I'm not well-versed in dual-booting with Windows. In the link, if the "Guided resize" didn't work, perhaps we can add a note. If it was manual partitioning, I don't see that covered in the link. 

I can't speak for the Ubuntu team, but suppose the idea is that if you select manual partitioning there are so many variables they leave it to the user to determine how to do it.

If you were following a guided setup, the best thing to do is to file a bug report describing what happened. The package to report is *ubiquity*. You can file a bug report using the guidelines in this page:
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by Funkey Monkey on 2010-09-21
Thanks for the guide.

But for I had to run sudo update-grub2 to add XP to the Grub Boot List.
And then also remember the "Shift" is the new key to press during boot to get to the Grub Boot List.

```
sudo update-grub2
```

---

### Post by olivaw_daneel on 2010-10-10
I followed this guide but now when I restart my  computer all I get is an 'error: unknown filesystem' and then the grub  rescue prompt. I cannot boot either Windows or Ubuntu (I used wubi to install Ubuntu originally).

Here's what I did to get to this point:

1. Typed 

```
sudo fdisk -l
```and got the following output:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x58000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       38914   302027776    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
```

2. Then I did:

```
sudo mkdir /media/sda3
sudo mount /dev/sda3 /media/sda3
sudo grub-install --root-directory=/media/sda3 /dev/sda
```

3. Then I  got the message saying 'installation complete' and restarted my computer

4. However, on load up all I got was 'error: file not found' and the grub rescue prompt

5. I looked through this thread and found this post: [http://ubuntuforums.org/showpost.php?p=8393469&postcount=52](http://ubuntuforums.org/showpost.php?p=8393469&postcount=52)

6. So I did the following:

```
sudo apt-get install mbr
```then

```
sudo install-mbr /dev/sda3
```

7. Restarted my computer and now  I'm getting  'error: unknown filesystem' and then the grub rescue prompt

I've got a bad feeling I've done something very wrong here! Can anyone help at all?

---

### Post by Kinetic1001101 on 2010-10-13
Thanks very much...   this worked for me.

---

### Post by næl on 2010-10-26
Hello. I need some help. I am a noob so i need it easy. And my english is not any good but i ll try. I installed windows 7 and lubuntu 10.10. It worked like it have always done (use to have win7/lubuntu 10.04. But when i updated the ubuntu img (i think) windows boot got over written. So I fixed windows boot, and as always it deleted lubuntu boot. So i came here and used this guide, sent by phill from lubuntu. But now windows boot got deleted. So I guess I in some kind of evil circle.

---

### Post by drs305 on 2010-10-26
> **næl said:**
> But now windows boot got deleted. So I guess I in some kind of evil circle.

It may appear that it is an evil circle, but perhaps not. Perhaps the windows boot is still there (well, the boot files) but Grub hasn't seen Windows yet. The reason is that Lubuntu doesn't come with the software that searches for the Windows partition. You have to install it before Grub will find Windows.

So, if you are now booting to Ubuntu normally, without the LiveCD, open a terminal and run this command to install *os=prober*
```
sudo apt-get install os-prober
```
Once it is installed, update Grub. 
```
sudo update-grub
```
Now see if Windows is in your Grub menu:
```
grep "menuentry" /boot/grub/grub.cfg
```
If it is, reboot, choose Windows and see if it will boot. 

If it isn't there, or if Windows won't boot, then please run the boot info script from the following link and post the contents of the RESULTS.txt that it produces. This will allow us to see the boot status of Windows and Ubuntu and figure out how to fix your dual-boot system.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by næl on 2010-10-26
Thank you man!! really appreciate it!! But just a quick question. Is this a lubuntu bug?

---

### Post by drs305 on 2010-10-26
> **næl said:**
> Thank you man!! really appreciate it!! But just a quick question. Is this a lubuntu bug?

I don't know if the developers characterize it as a bug. It has been reported in [ Bug 665530]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/665530") and you can subscribe on that page to be kept aware of changes to its status.

As far as I know only Lubuntu is 'shipping' without os-prober in the basic installation. I don't know the reasons *os-prober* was not included in the release, I'm just dealing with the consequences...  ;-)

---

### Post by næl on 2010-10-26
Ok. Thanks again.

---

### Post by redmorning on 2010-10-31
First of all forgive me because i couldn`t read all posts. i`m in live usb and lost my grub menu while trying to retrieve my windows 7 i came here, from  a long way.

i followed the onstructions in the first post, here ther are:
```
ubuntu@ubuntu:/media$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04 LTS
Release:	10.04
Codename:	lucid

```

```
ubuntu@ubuntu:/media$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdda4dda4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1658    13312000   27  Unknown
/dev/sda2   *        1658        1671      102400    7  HPFS/NTFS
/dev/sda3            1671       40349   310682967+   7  HPFS/NTFS
/dev/sda4           41624       60802   154045441    5  Extended
/dev/sda5           41624       60468   151367187+  83  Linux
/dev/sda6           60468       60782     2518016   82  Linux swap / Solaris
/dev/sda7           60782       60802      158720   83  Linux

Disk /dev/sdb: 1000 MB, 1000341504 bytes
16 heads, 32 sectors/track, 3816 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007b16a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3816      976880    6  FAT16

```

here is the first point i`m lost. my root directory(/) is in sda5 and boot directory (/boot) is in sda7. i tried to mount sda5 and after sda7 with 
```
sudo grub-install --root-directory=/media/sdax /dev/sda
```
without any errors

but each time i reboot i have just `GRUB's Minimal BASH-like` command line. 

also if i mount root partition:
```
ubuntu@ubuntu:/$ ls /media/sda5/boot/
grub

```
and boot partition
```
ubuntu@ubuntu:/$ ls /media/sda7/
abi-2.6.32-21-generic     config-2.6.32-25-generic      lost+found                    vmcoreinfo-2.6.32-21-generic  vmlinuz-2.6.32-25-generic
abi-2.6.32-24-generic     grub                          memtest86+.bin                vmcoreinfo-2.6.32-24-generic
abi-2.6.32-25-generic     initrd.img-2.6.32-21-generic  System.map-2.6.32-21-generic  vmcoreinfo-2.6.32-25-generic
config-2.6.32-21-generic  initrd.img-2.6.32-24-generic  System.map-2.6.32-24-generic  vmlinuz-2.6.32-21-generic
config-2.6.32-24-generic  initrd.img-2.6.32-25-generic  System.map-2.6.32-25-generic  vmlinuz-2.6.32-24-generic

```

i need a urgent help please.

can i basically copy /boot to / because grub-install has not different arguments for boot and root, there is only ==root=directory option

*p.s one more time if this case already discussed and solved.*

---

### Post by drs305 on 2010-10-31
@ piratejackus,

Try reinstalling grub2 using the following commands. It is necessary to mount both your sda5 and sda7 partitions since you have a separate boot partition. 

If sda5 is your main Ubuntu partition, and sda7 is a separate /boot partition:

From the LiveCD desktop, open a terminal (Applications, Accessories, Terminal):
```
sudo mount /dev/sda5 /mnt
sudo mount /dev/sda7 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda
```

Then try rebooting and see if Ubuntu will boot.

If it doesn't, I'd recommend starting your own thread, and post the contents of the boot info script from here: 
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")
If you still need help, I could move your previous post to a new thread if what I recommend doesn't fix the Ubuntu part of the boot process.

---

### Post by redmorning on 2010-10-31
i was in the 20 th page of this thread and another experience came out; drs305. i read your answer and said ot myself:
 "how couldn't i think about composing partitions,how,how?" and answer came in a second:
 "experince boy!"

in 3 minutes i am back in ubuntu, thank you very much drs305, it was so fast, really.
by the way, i got a problem with windows 7 booting, and created a thread about that
[http://ubuntuforums.org/showthread.php?t=1606427]("http://ubuntuforums.org/showthread.php?t=1606427")
this threads readers may have some ideas about that and if they have, welcome. i would like to get back my windows too. 

thanks.

---

### Post by Cellomantiker on 2010-11-05
Thank you so much! I did exactly as you described it for restoring the Win7 bootloader and it helped! Haven't logged into Windows yet, but hopefully everything is still there! At least there is everything still there in Ubuntu 10.10, so won't give up hope, yet! ;)

---

### Post by jellevictoor on 2010-11-06
I have tried this serveral times now. I understand the process I'm going thru. I'm checking what my partintions are via 
sudo fdisk -l
I see that i have 2 linux partitions, 1 / and 1 home partion. I mount the / to /mnt and the home partion to /mnt/home
I then run grub-install on /mnt and my device so it can overwrite the mbr. I keep ending up with the 'minimal grub console'
Kind of stuck now :/

---

### Post by drs305 on 2010-11-06
> **jellevictoor said:**
> Kind of stuck now :/

Are you including the "--root-directory=/mnt" option with the grub-install command?

We probably should see the contents of RESULTS.txt from the boot info script, found here:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

You might get more people reading your post if you start your own thread.

---

### Post by Chilongola on 2010-11-12
Very great lesson here guys.

---

### Post by iqbal5435 on 2010-11-16
Hi, I got this when I boot

error: unknown filesystem
grub rescue>

What should I do? I am a newbie. Thank you for your help and guide. Your help would be very, very precious.:-k

---

### Post by drs305 on 2010-11-16
> **iqbal5435 said:**
> Hi, I got this when I boot

error: unknown filesystem
grub rescue>

What should I do? I am a newbie. Thank you for your help and guide. Your help would be very, very precious.:-k

Take a look at the thread below. If you need help, post there with the contents of the RESULTS.txt generated by the [boot info script]("http://bootinfoscript.sourceforge.net").

[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

---

### Post by COKEDUDE on 2010-12-02
Are there any advantages of using this grub as opposed to using this grub guide? 

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by von Stalhein on 2010-12-02
> **COKEDUDE said:**
> Are there any advantages of using this grub as opposed to using this grub guide? 

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

For me, having used both methods at various times, the advantage was the learning by doing I suppose - ymmv.

---

### Post by jao_madn on 2010-12-02
For me the advantage is the knowledge and experience you can get along the way. and the satisfaction and feeling of confidence when u do it right.

---

### Post by drs305 on 2010-12-02
> **COKEDUDE said:**
> Are there any advantages of using this grub as opposed to using this grub guide? 

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I've posted my response in the other thread, where the question was also asked:
[http://ubuntuforums.org/showpost.php?p=10189587&postcount=44]("http://ubuntuforums.org/showpost.php?p=10189587&postcount=44")

---

### Post by COKEDUDE on 2010-12-02
Thank you to everyone that responded to my question about the different grub guides.

---

### Post by VitasLoWang on 2010-12-05
Did sudo grub-install --root-directory=/media/sdb6 /dev/sdb and it is
"Probing devices to guess BIOS drives. This may take a long time."
for almost ten minutes now...

so now it finally finished. Trying reboot...

---

### Post by abybaddi on 2010-12-07
> 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x30123011

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        2550    20473985    f  W95 Ext'd (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2551       19456   135797413+   7  HPFS/NTFS
/dev/sda5               2        1345    10795618    7  HPFS/NTFS
/dev/sda6            1346        2493     9212928   83  Linux
/dev/sda7            2493        2550      460800   82  Linux swap / Solaris

Disk /dev/sdb: 4063 MB, 4063232000 bytes
125 heads, 62 sectors/track, 1024 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007e048

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1024     3967969    c  W95 FAT32 (LBA)

ubuntu@ubuntu:~$ sudo mkdir /media/sda6
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /media/sda6
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$


This happened in my pc, please help me..

---

### Post by aijo on 2010-12-09
for some unknows reasons, the command sudo fdisk -l gives me this:

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1828    14683378+  27  Unknown
/dev/sda2   *        1829        1841      104422+   7  HPFS/NTFS
/dev/sda3            1842       18666   135139103+   7  HPFS/NTFS
/dev/sda4           18666       60802   338457601    f  W95 Ext'd (LBA)
/dev/sda5           34694       60802   209713152    7  HPFS/NTFS

as you can see, there is no 'linux called' partition. however i have ubuntu installed on a ext4 partition. may this be the reason why its not there? or maybe its the sda4? then im unable to mount it, an error
mount: you must specify the filesystem type shows up.

Thank you for your answer, i'd really appreciate some help ;)

---

### Post by drs305 on 2010-12-09
aijo,

Do you know where the ext4 partition is supposed to be? You have a small sda1 that is not recognized. *fdisk* will recognize and correctly report ext4 partitions if there is nothing wrong with it.

When you get the filesystem error, how are you trying to mount it? Is this during the initial boot or from the LiveCD desktop?

If you are running the LiveCD, does Gparted show it (System, Administration, Gparted). If it does, you might try highlighting the partition and then allow Gparted to repair it. If it's not mounted: Partition, Check.

---

### Post by aijo on 2010-12-12
hey, thank you for your reply.
Well, the thing is..in Gparted it looked like there is no ubuntu whatsoever in my pc, so I installed it again, and it works. Luckily I didn't have much data in there, it was newly installed after the latest GRUB problems :D

i wrote the following message some time ago, but did not post..I only wonder, what could I do with the Vista thing. Seems like every time I would accidentally choose it, the GRUB problem would show up again.can i delete it? how? Thanks a lot.

"I think the sda1 disk got there from the vista repair CD. actually, i had a problem with GRUB before, reainstalled everything and it worked..but when booting, there was one extra option which i did not understand - the vista. (I have the 7 normally). So once when I was curious what the vista option would do, i chose it. It opened up something like a restore tool, which i didn't want, so i closed it. When booting again, there was the GRUB problem(a rescue prompt) and since then, i only managed to repair the windows part, so when booting, no options show up."

---

### Post by drs305 on 2010-12-12
> **aijo said:**
> 
i wrote the following message some time ago, but did not post..I only wonder, what could I do with the Vista thing. Seems like every time I would accidentally choose it, the GRUB problem would show up again.can i delete it? how? Thanks a lot.


There are two things to address here. The first is the Vista 'repair' option. Unfortunately Grub2 doesn't know the function and just labels it as another loader. You have to learn just not to select it, although even then just selecting *shouldn't* alter things unless you run it after it's called up. If you want to hide or rename the option, you can refer to my [Grub2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602") thread, but I have to warn that it's pretty geeky. Not hard, just geeky.  ;-)

The second possible issue if Grub seems to fail every time after you boot to Windows is that Windows apps are overwriting sections of the Grub files. There is an area of the disk where G2 writes that is also used by other Windows apps, among them Dell DataSafe, Adobe FlexNet and HP Protect Tools. The solution if you want to use Grub is to disable these apps.

---

### Post by marley07 on 2010-12-13
You sir or ma'am, are amazing. I keep on managing to screw up my bootloader every other month or so and it gets annoying trying to find the relevant information every time. This thread is now subscribed to!

---

### Post by rajeeja on 2010-12-14
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda6 /dev/sda

/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it. This software may cause boot or other problems in future. Please ask its authors not to store data in the boot track..
Installation finished. No error reported.

Reboot into the LiveCD and execute:

ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
mount: /dev/sda6 already mounted or /mnt busy
mount: according to mtab, /dev/sda6 is already mounted on /mnt

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

Simply rebooting without the live CD gets me to "grub>" prompt. 

It's because the old grub files are gone and the new one didn't update?

Vista doesn't show up now, so I don't know what to do?

Many thanks,

---

### Post by rajeeja on 2010-12-14
Forgot to mention, this is with Ubuntu 10.10 live CD. Please let me know if you need more info.

---

### Post by marley07 on 2010-12-14
> **rajeeja said:**
> Vista doesn't show up now, so I don't know what to do?

I fixed mine through My Windows 7 rescue CD. I simply ran the lines

bootrec.exe /fixboot

and

bootrec.exe /fixmbr

in the command line.

I know you're talking about a separate OS but I'm pretty sure the command is the same.

The full instructions are on the first page of this thread if you want more info under the section titled "How to restore the Windows Vista or 7 bootloader."

---

### Post by rajeeja on 2010-12-14
Thanks,

i want to restore both windows and ubuntu, after doing what you say, how do i get ubuntu to work?

should i try to remove all the flexnet files and try again. i'm saying this because i got this message when trying to install grub to my previous installation.

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda6 /dev/sda

/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it. This software may cause boot or other problems in future. Please ask its authors not to store data in the boot track..
Installation finished. No error reported.

---

### Post by marley07 on 2010-12-14
Assuming everything else is intact, running those two commands through your Vista rescue CD should, in theory, still make your Ubuntu partition accessible again when you boot up. All they are doing is fixing the boot parameters, not changing the OS's. (At least it always has for me).

I have no clue about the Flex files.

How did you first encounter this problem? What were you specifically doing just before it rendered itself unbootable?

---

### Post by rajeeja on 2010-12-14
> **marley07 said:**
> Assuming everything else is intact, running those two commands through your Vista rescue CD should, in theory, still make your Ubuntu partition accessible again when you boot up. All they are doing is fixing the boot parameters, not changing the OS's. (At least it always has for me).

I have no clue about the Flex files.

How did you first encounter this problem? What were you specifically doing just before it rendered itself unbootable?

I have a preinstalled Vista from Dell and I installed ubuntu, been upgrading for 2-3 versions of Ubuntu, they both worked well. The last time I upgraded Ubuntu to 10.10, none of my Ubuntu grubs would work. I was still able to boot windows from the list of grubs that are available. In an attempt to fix the ubuntu grubs, I did execute these commands to get to the current situation:

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda6 /dev/sda

/usr/sbin/grub-setup: warn: Sector 32 is already in use by **FlexNet**; avoiding it. This software may cause boot or other problems in future. Please ask its authors not to store data in the boot track..
Installation finished. No error reported.

Rebooted into the LiveCD and execute:

ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
mount: /dev/sda6 already mounted or /mnt busy
mount: according to mtab, /dev/sda6 is already mounted on /mnt

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

Many thanks,

---

### Post by rajeeja on 2010-12-14
so now, Simply rebooting without the live CD gets me to "grub>" prompt. 

I'm on the same system; typing this message via a Ubuntu 10.10 live CD. Should I put the OS (Vista) CD by Dell and follow the instruction you gave.

---

### Post by marley07 on 2010-12-14
Yes, I would try to at least get the Vista partition bootable again. Just follow the instructions on the first page of this thread that I cited earlier and you should be able to get that back up and running.

Make sure you **DO NOT** perform any OS recovery options. Those will erase **all** data on your hard drive. Simply run the fix commands for the boot and mbr from the command line option.

I am also not sure if your specific CD will have the correct options available on it. It may simply be an installation CD. If this is the case, you will not be able to access the command line and perform the two operations mentioned. The only way to figure out is try!

If it doesn't work, then there are plenty of .iso files for "Vista Rescue CD" on the internet that you can burn to a disk and run. Just make sure you get the correct .iso file (X86/32-bit or 64-bit).

---

### Post by rajeeja on 2010-12-14
> **marley07 said:**
> Yes, I would try to at least get the Vista partition bootable again. Just follow the instructions on the first page of this thread that I cited earlier and you should be able to get that back up and running.

Make sure you **DO NOT** perform any OS recovery options. Those will erase **all** data on your hard drive. Simply run the fix commands for the boot and mbr from the command line option.

I am also not sure if your specific CD will have the correct options available on it. It may simply be an installation CD. If this is the case, you will not be able to access the command line and perform the two operations mentioned. The only way to figure out is try!

If it doesn't work, then there are plenty of .iso files for "Vista Rescue CD" on the internet that you can burn to a disk and run. Just make sure you get the correct .iso file (X86/32-bit or 64-bit).


I have a OS CD and I did fixboot and fixmbr, after doing that (both of them ran successfully) I simply ejected the Vista CD. 

Now when I try to reboot, nothing comes to the screen just a cursor blinking. No more "grub>" prompt. 

Any pointers?

Should I run startup recovery on Vista CD or do something with the 10.10 live CD?

---

### Post by drs305 on 2010-12-14
> **rajeeja said:**
> I have a OS CD and I did fixboot and fixmbr, after doing that (both of them ran successfully) I simply ejected the Vista CD. 

Now when I try to reboot, nothing comes to the screen just a cursor blinking. No more "grub>" prompt. 

Any pointers?

Should I run startup recovery on Vista CD or do something with the 10.10 live CD?

It Windows is booting and you end up at a cursor, I can't really help.

If it's booting to GRUB, you should be able to get the Grub2 menu by holding down the SHIFT key while the computer boots. If you get the Grub menu, the blinking cursor probably means you are having a video issue after G2 passes control to Ubuntu.

This might be solved, especially if you have an nvidia card, by highlighting the first Grub menu item, pressing "e" and entering the 'edit' mode.

From there, find the "linux" line and add **nomodeset** to the end of the line. It probably ends now with **quiet splash**.

Once you've added **nomodeset** press CTRL-x to boot. If it boots to the Desktop, go to System, Administration, Additional Drivers and install your video card driver if it is displayed.

---

### Post by rajeeja on 2010-12-14
> **drs305 said:**
> It Windows is booting and you end up at a cursor, I can't really help.

If it's booting to GRUB, you should be able to get the Grub2 menu by holding down the SHIFT key while the computer boots. If you get the Grub menu, the blinking cursor probably means you are having a video issue after G2 passes control to Ubuntu.

This might be solved, especially if you have an nvidia card, by highlighting the first Grub menu item, pressing "e" and entering the 'edit' mode.

From there, find the "linux" line and add **nomodeset** to the end of the line. It probably ends now with **quiet splash**.

Once you've added **nomodeset** press CTRL-x to boot. If it boots to the Desktop, go to System, Administration, Additional Drivers and install your video card driver if it is displayed.

I was getting to the "grub>" or grub prompt and then I did fixboot and fixmbr and now I'm at this blinking cursor. 

I have a intel integrated graphics card and where it stands now is "a cursor blinking on the screen" - this is with normal boot up of the computer.

Holding the shift key during the startup doesn't work.

I can get to the grub prompt if I run "sudo grub-install --root-directory=/mnt/ /dev/sdX" from the live CD. Should I do that?

---

### Post by drs305 on 2010-12-14
rajeeja,

I've been following your posts. You said 10.10 wasn't working - was Grub booting to the blinking prompt or failing in some other way. *If* you know grub was working but were getting the blinking cursor, it might be worth trying to do a simple reinstall of Grub using the commands you mention. 

If you did a fixboot/fixboot on the drive BIOS is booting, more than likely you have a Windows problem since that should have restored the Windows bootloader. The only way it wouldn't would be if BIOS is looking at a different MBR on boot.

As far as G2 is concerned, I'd probably recommend a complete purge/reinstall of G2 via the chroot procedures detailed in the "G2-Chroot" link in my signature line. That's probably your best shot at getting Grub2 to work. And after running the Windows restore commands perhaps FlexNet won't cause any more problems (disable it to avoid future issues - but I can't give you the details).

Before you mount your Ubuntu partition after booting from the LiveCD you should probably run an fsck check on the partition. That could be why it won't mount. (sudo e2fsck -f -y -v /dev/sda6).

---

### Post by Medivh90 on 2010-12-14
Hi, 
this tut is great, but i have some big problems, they are maybe here beacose my mainboard is to old(my friend saying) maybe not, i for sure wanna ask professionals.
 
I'm on ubuntu for a long time, and with 10.04 i have installed GRUB 2. Few weaks ago i was updated system to 10.10. Now i must install Windows just to finish some work(with c# XNA), so i have installed windows XP SP3. 
 
I followed instructions from this topic and few more for dual booting.
First thing when i type 'sudo grub' result is 'grub command not found' so i used google and saw that i must re-install it, i followed next instructions:
 
sudo mount /dev/sdXY /mnt
sudo mount /dev/sdXY /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sdc
 
and reboot, after reboot notnig happens i should run update grub - command not found, i tried lots of things always the same file not found or command not found. i do not have file menu.lst.
(After trying to reinstall, i cannot boot win XP too, so i must fix with fixboot and fixmbr)
 
My friend saying that my mainboard is too old and it does not support booting from hd space that is larger than 7.5 GB (The board is MSI KT4A-V AMD).
 
So is this true reason or it is something else, what should i do, win XP is not important to me, just to restore ubuntu somehow. 
 
Thanks in advance.

---

### Post by rajeeja on 2010-12-14
> **drs305 said:**
> rajeeja,

I've been following your posts. You said 10.10 wasn't working - was Grub booting to the blinking prompt or failing in some other way. *If* you know grub was working but were getting the blinking cursor, it might be worth trying to do a simple reinstall of Grub using the commands you mention. 

If you did a fixboot/fixboot on the drive BIOS is booting, more than likely you have a Windows problem since that should have restored the Windows bootloader. The only way it wouldn't would be if BIOS is looking at a different MBR on boot.

As far as G2 is concerned, I'd probably recommend a complete purge/reinstall of G2 via the chroot procedures detailed in the "G2-Chroot" link in my signature line. That's probably your best shot at getting Grub2 to work. And after running the Windows restore commands perhaps FlexNet won't cause any more problems (disable it to avoid future issues - but I can't give you the details).

Before you mount your Ubuntu partition after booting from the LiveCD you should probably run an fsck check on the partition. That could be why it won't mount. (sudo e2fsck -f -y -v /dev/sda6).

Thanks drs for the replies. 

Please let me get you to the problem. I had a happy dual booting system (Vista and 9.1) before I upgraded to 10.10. 

After, starting my system I had a menu to choose the OS (the default was Ubuntu, i had natty kernels 2.xx31 and 2.xx35), after upgrade to 10.10 only Windows Vista would boot from the menu. 

I made a 10.10 CD and tried "to restore the Ubuntu grub bootloader" like you describe. I got the FlexNet message and I was getting "grub>" the grub prompt after restarting. 

Then, I did "to restore the Windows Vista or 7 bootloader" like you describe. This got me to the blank screen and a blinking cursor. No grub prompt. 

From what you describe, i should again do "to restore the Ubuntu grub bootloader" and then take it on from the grub.

Many thanks,

---

### Post by drs305 on 2010-12-14
rajeeja,

I'd like to be able to give you a firm answer, but there are too many variables.

We don't know why 10.10 wouldn't boot.

The Windows commands *may* have cleared Flexnet from the space G2 wants, but I've read posts that it didn't so we don't really know. Also, note that Grub reports the Flexnet issue but doesn't say it can't work around it.

We think, but aren't positive, the blinking cursor is a Windows issue although it sounds like a very common Ubuntu video driver issue.

So, all I can say is that if you chroot G2 and purge/reinstall Grub2, we will at least know that it isn't Grub causing your problems. And if G2 is installed and results in a blinking cursor, how to fix that issue has been addressed.

If you run the chroot commands and they don't fix things please post a new RESULTS.txt. Good luck.

---

### Post by rajeeja on 2010-12-14
> **drs305 said:**
> rajeeja,

I'd like to be able to give you a firm answer, but there are too many variables.

We don't know why 10.10 wouldn't boot.

The Windows commands *may* have cleared Flexnet from the space G2 wants, but I've read posts that it didn't so we don't really know. Also, note that Grub reports the Flexnet issue but doesn't say it can't work around it.

We think, but aren't positive, the blinking cursor is a Windows issue although it sounds like a very common Ubuntu video driver issue.

So, all I can say is that if you chroot G2 and purge/reinstall Grub2, we will at least know that it isn't Grub causing your problems. And if G2 is installed and results in a blinking cursor, how to fix that issue has been addressed.

If you run the chroot commands and they don't fix things please post a new RESULTS.txt. Good luck.

**Got this message, Attaching a results.txt file-- my chroot command results**.

You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ksysguard : Depends: libprocesscore4b (= 4:4.5.3-0ubuntu3) but it is not going to be installed
             Depends: libprocessui4a (= 4:4.5.3-0ubuntu3) but it is not going to be installed
             Depends: ksysguardd (= 4:4.5.3-0ubuntu3) but 4:4.5.1-0ubuntu8 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

root@ubuntu:/# apt-get -f install

This ultimately resulted in these errors:

Errors were encountered while processing:
 /var/cache/apt/archives/libprocesscore4b_4%3a4.5.85-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

*Still on 10.10 CD waiting for your reply.*

Many thanks,

---

### Post by rajeeja on 2010-12-14
Sorry, missed the attachment.

---

### Post by drs305 on 2010-12-14
> **rajeeja said:**
> 
Errors were encountered while processing:
 /var/cache/apt/archives/libprocesscore4b_4%3a4.5.85-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

*Still on 10.10 CD waiting for your reply.*

Are these commands from within chroot? Don't know why there are unmet dependencies. I assume running  "apt-get install -f" again still didn't work. 

You could try clearing the cache if you have an Internet connection and see if it reloads the necessary packages:
```
apt-get clean
apt-get update && sudo apt-get upgrade

```
From within the chroot, you can also try going into Synaptic. In the left pane go through the filters until you find the 'broken' packages and see if Synaptic can fix them.
Added: These don't look like critical packages.


ADDED AFTER REVIEWING YOUR ATTACHMENT:
You might go back into chroot and try purging grub on a separate command line since it didn't appear to uninstall and eventually reran grub instead of Grub2:
```
apt-get purge grub
apt-get install grub-pc
```

---

### Post by rajeeja on 2010-12-14
> **drs305 said:**
> Are these commands from within chroot? Don't know why there are unmet dependencies. I assume running  "apt-get install -f" again still didn't work. 

You could try clearing the cache if you have an Internet connection and see if it reloads the necessary packages:
```
apt-get clean
apt-get update && sudo apt-get upgrade

```
From within the chroot, you can also try going into Synaptic. In the left pane go through the filters until you find the 'broken' packages and see if Synaptic can fix them.
Added: These don't look like critical packages.


ADDED AFTER REVIEWING YOUR ATTACHMENT:
You might go back into chroot and try purging grub on a separate command line since it didn't appear to uninstall and eventually reran grub instead of Grub2:
```
apt-get purge grub
apt-get install grub-pc
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/temp 
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  # May be required to connect to the Internet.
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
**root@ubuntu:/# apt-get purge grub**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ksysguard : Depends: libprocesscore4b (= 4:4.5.85-0ubuntu3) but it is not going to be installed
             Depends: libprocessui4a (= 4:4.5.85-0ubuntu3) but it is not going to be installed
             Depends: ksysguardd (= 4:4.5.85-0ubuntu3) but 4:4.5.1-0ubuntu8 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Should I do this in chroot:

```
apt-get clean
apt-get update && sudo apt-get upgrade

```

---

### Post by rajeeja on 2010-12-14
I would assume it's chroot, that's what we are trying to fix..here is the o/p same result, unmet dependencies:

root@ubuntu:/# apt-get clean
root@ubuntu:/# apt-get update && apt-get upgrade
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                                                                     
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en                                         
.......
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/multiverse i386 Packages
Fetched 2,278B in 1s (1,221B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 ksysguard : Depends: libprocesscore4b (= 4:4.5.85-0ubuntu3) but it is not installed
             Depends: libprocessui4a (= 4:4.5.85-0ubuntu3) but it is not installed
             Depends: ksysguardd (= 4:4.5.85-0ubuntu3) but 4:4.5.1-0ubuntu8 is installed
E: Unmet dependencies. Try using -f.

On using -f
root@ubuntu:/# apt-get -f install

Unpacking libprocesscore4b (from .../libprocesscore4b_4%3a4.5.85-0ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libprocesscore4b_4%3a4.5.85-0ubuntu3_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libprocesscore.so.4', which is also in package libprocesscore4 4:4.4.2-0ubuntu14
Errors were encountered while processing:
 /var/cache/apt/archives/libprocesscore4b_4%3a4.5.85-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by drs305 on 2010-12-14
"KDE System Guard allows you to monitor various statistics about your system."

Doesn't seem to be a needed program. I don't know if the system will let you purge it, but I'd try (still in chroot).

The important thing is to purge grub and install grub-pc without errors, then run "update-grub".

---

### Post by rajeeja on 2010-12-14
> **drs305 said:**
> "KDE System Guard allows you to monitor various statistics about your system."

Doesn't seem to be a needed program. I don't know if the system will let you purge it, but I'd try (still in chroot).

The important thing is to purge grub and install grub-pc without errors, then run "update-grub".

Do you think the problem is my sources.list?

root@ubuntu:/# cat /etc/apt/sources.list 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository

Many thanks,

---

### Post by rajeeja on 2010-12-14
Added the 32-bit wget's from post #10 : Re: HOWTO: Purge and Reinstall Grub 2 from the Live CD

I was able to install grub-common, but grub-pc gave the following error.

root@ubuntu:/# dpkg -i grub-pc_1.98+20100804-5ubuntu3_i386.deb 
(Reading database ... 365551 files and directories currently installed.)
Preparing to replace grub-pc 1.98+20100804-5ubuntu3 (using grub-pc_1.98+20100804-5ubuntu3_i386.deb) ...
Unpacking replacement grub-pc ...
dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on ucf; however:
  Package ucf is not configured yet.
dpkg: error processing grub-pc (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 grub-pc

---

### Post by rajeeja on 2010-12-14
> **drs305 said:**
> "KDE System Guard allows you to monitor various statistics about your system."

Doesn't seem to be a needed program. I don't know if the system will let you purge it, but I'd try (still in chroot).

The important thing is to purge grub and install grub-pc without errors, then run "update-grub".

Purged ksysguard and all the steps in chroot wen't well. After restarting I get:
[B]
grub loading..
error: symbol not found: 'grub_err_printed_errors'[/B]

Then, I have a 'grub rescue>' prompt.

Tried pressing shift during startup, nothing happens. 

Many thanks,

---

### Post by drs305 on 2010-12-14
rajeeja,

The messages indicate it was trying to replace a G2 which was already installed. I think at this point you should try running the following commands in chroot:
```
grub-install /dev/sdX # Your Ubuntu drive (no partition number)
update-grub
```

I think the dependencies are messed up enough that either it is going to boot as is or it's likely you will end up having to reinstall. 

You briefly mentioned natty kernels and if you ended up with a mixture of natty and earlier packages it may be impossible to sort them out.

Even with the dependency problems, you do not seem to have a problem mounting the partition and you should be able retrieve and back up any data files you want to save if a clean installation is necessary.

---

### Post by rajeeja on 2010-12-15
> **drs305 said:**
> rajeeja,

The messages indicate it was trying to replace a G2 which was already installed. I think at this point you should try running the following commands in chroot:
```
grub-install /dev/sdX # Your Ubuntu drive (no partition number)
update-grub
```

I think the dependencies are messed up enough that either it is going to boot as is or it's likely you will end up having to reinstall. 

You briefly mentioned natty kernels and if you ended up with a mixture of natty and earlier packages it may be impossible to sort them out.

Even with the dependency problems, you do not seem to have a problem mounting the partition and you should be able retrieve and back up any data files you want to save if a clean installation is necessary.

Hi drs,

Thanks for being patient. Attaching results.txt for the above commands. I see the warning " Sector 32 is already in use by FlexNet"

Other than that all ran well. Is there a way to check that this will work from the CD itself? 

or 

I will have to reboot w/o the CD to test if the grub will work. 

After all this the last thing I want is format my system. I think it's close to fixing.

---

### Post by rajeeja on 2010-12-15
> **drs305 said:**
> rajeeja,

 And after running the Windows restore commands perhaps FlexNet won't cause any more problems (disable it to avoid future issues - but I can't give you the details).



So, now that I have grub 2 installed with FlexNet error, should I again go and try to do a fixboot/fixmbr using the Vista CD?

---

### Post by drs305 on 2010-12-15
> **rajeeja said:**
> So, now that I have grub 2 installed with FlexNet error, should I again go and try to do a fixboot/fixmbr using the Vista CD?

I would just try to reboot and see if Grub2 loads. The message the G2 devs added about avoiding the FlexNet sector seems to indicate they have altered the way it installs so prevent this from being a problem.

You don't want to rerun fixboot/fixmbr until you find out G2 fails, since it will once again wipe out Grub on the MBR.

---

### Post by rajeeja on 2010-12-15
> **drs305 said:**
> I would just try to reboot and see if Grub2 loads. The message the G2 devs added about avoiding the FlexNet sector seems to indicate they have altered the way it installs so prevent this from being a problem.

You don't want to rerun fixboot/fixmbr until you find out G2 fails, since it will once again wipe out Grub on the MBR.



**Cheers**, have your favourite drink, I'm sending it virtually, now that Ubuntu Boots !!!

The problem is when I try to boot vista it just restarts again?
any pointers.

---

### Post by drs305 on 2010-12-15
> **rajeeja said:**
> **Cheers**, have your favourite drink, I'm sending it virtually, now that Ubuntu Boots !!!

The problem is when I try to boot vista it just restarts again?
any pointers.

Run the boot info script again and post RESULTS.txt. Hopefully we won't have to reinstall the Windows boot loader to the same MBR we just put G2 back on...

---

### Post by rajeeja on 2010-12-15
> **drs305 said:**
> Run the boot info script again and post RESULTS.txt. Hopefully we won't have to reinstall the Windows boot loader to the same MBR we just put G2 back on...

Please find the results for sudo bash boot_info_script055.sh attached.

---

### Post by rajeeja on 2010-12-15
Results.txt attached.

---

### Post by drs305 on 2010-12-15
The results reveal a discrepancy between windows and ubuntu. Following a brief PM with *rajeeja* we've decided to recheck whether Windows is capable of booting by itself (once more).

Boot Ubuntu.
Save the MBR info (in case Windows boot fails).
```
sudo dd if=/dev/sda of=$HOME/Desktop/sda.mbr.img bs=512 count=1
```

Install lilo and write to MBR so Windows should boot. Disregard all the lilo messages and don't run any extra lilo commands:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Reboot to see if you get the Windows bootloader and if it boots to Windows.

Whether successful or not, boot the LiveCD and do the following to reset to Grub2:
```
sudo mount /dev/sda6 /mnt
sudo grub-install root-directory=/mnt /dev/sda
```
Do not include the partition number in the second command.

Reboot to Ubuntu and run "sudo update-grub" after rebooting.

(We ran the "dd" command as an insurance policy in case we needed it to restore the MBR, but the 'grub-install' command should do it as well).

---

### Post by rajeeja on 2010-12-15
Cool, all works now, both Ubuntu and Vista are happy again. Special thanks to *drs*.

Strangely Windows that boots is titled "Windows Recovery..."

**Wait...Over Both OS work now.**..Vista did boot and work....Ubuntu...is talking long to boot....

...got into the ubuntu recovery mode and now running 'repair broken packages' ...there are lots of updates......going on for more than an hour now!

....getting "GdkPixbuf-WARNING:cannot open pixbuf loader module file"

-----------------------------------------------------------------------------------
OKAY CONFIRMING THAT BOTH OS WORK FINE
____________________________________________________________________________________


An update on the newer version causes some problems, looks like are related to graphics, I have a intel integrated graphics card.....this might be a question of some other forum...any pointers?

Thanks a lot.

update-initramfs: Generating /boot/initrd.img-2.6.37-9-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
 * dkms: running auto installation service for kernel 2.6.37-9-generic          
 *       virtualbox-ose (3.2.12)...                                      [ OK ] 
 *       blcr (0.8.2)...                                                 [fail] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/zz-lilo 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
Warning: Not updating LILO; /etc/lilo.conf not found
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
exec: 15: update-grub: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.37-9-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.37-9-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because the error message indicates its a followup error from a previous failure.
      No apport report written because MaxReports is reached already
                                                                    dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.37-9-generic; however:
  Package linux-image-2.6.37-9-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.37.9.11); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.35-23-generic
 linux-image-2.6.37-9-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by rajeeja on 2010-12-15
kernel 2.6.35.23 leads to a blank screen

kernel 2.6.35.22 leads to a normal boot with the new natty. Applications menu is gone for some reason!

kernel 2.6.35.19 leads to a blank screen too.

Let me know if you need more info.

Many thanks,

---

### Post by drs305 on 2010-12-15
> **rajeeja said:**
> kernel 2.6.35.23 leads to a blank screen
kernel 2.6.35.22 leads to a normal boot with the new natty. Applications menu is gone for some reason!
kernel 2.6.35.19 leads to a blank screen too.
Let me know if you need more info.


I have only briefly played with natty, but if you are getting the unity desktop (icons on the left and a single ubuntu icon at the top left) that is the default. If you click on the ubuntu symbol, it opens what looks like the home folder. On closer inspection though, the contents are all the available apps. Click on one to start it.

You should be able to get a more familiar look by clicking on the terminal icon on the left and then run "gnome-panel".

As far as the blank screen, are they black, do you have a cursor flashing, are they empty splash screens, etc.

If you have Natty questions, it's time to open a new thread of your own in the Natty forum. I think the bulk of your original problems may have been a dependency problem caused by installing a natty kernel, but it really doesn't matter at this point. At least you are back to a dual boot system, even if it's not what you expected.  ;-)

---

### Post by rajeeja on 2010-12-15
> **drs305 said:**
> I have only briefly played with natty, but if you are getting the unity desktop (icons on the left and a single ubuntu icon at the top left) that is the default. If you click on the ubuntu symbol, it opens what looks like the home folder. On closer inspection though, the contents are all the available apps. Click on one to start it.

You should be able to get a more familiar look by clicking on the terminal icon on the left and then run "gnome-panel".

As far as the blank screen, are they black, do you have a cursor flashing, are they empty splash screens, etc.

If you have Natty questions, it's time to open a new thread of your own in the Natty forum. I think the bulk of your original problems may have been a dependency problem caused by installing a natty kernel, but it really doesn't matter at this point. At least you are back to a dual boot system, even if it's not what you expected.  ;-)

The screens are black no blinking cursor just empty blank and black.

---

### Post by hodad on 2010-12-22
Hello!

New to this thread.  I am also having trouble with bootloader with 10.04 and WinXP.

Did the instructions on page 1, and, upon rebooting, I get dropped into a screen starting with:

GNU GRUB version 1.98-1ubuntu7
Minimal BASH-like...

grub>

What do I do at this point to get a GRUB menu?

Thanks!

---

### Post by drs305 on 2010-12-22
> **hodad said:**
> Hello!

New to this thread.  I am also having trouble with bootloader with 10.04 and WinXP.

Did the instructions on page 1, and, upon rebooting, I get dropped into a screen starting with:

GNU GRUB version 1.98-1ubuntu7
Minimal BASH-like...

grub>

What do I do at this point to get a GRUB menu?

Thanks!

Is this a normal Ubuntu installation or a Wubi installation (within Windows)?

If it is a Wubi installation, boot the LiveCD and run the following commands to restore the MBR to boot Windows. This assumes Windows is on sda. If it is not on your primary drive, change "sda" to the appropriate value. Disregard the 'lilo' terminal messages as you aren't really fully installing lilo.

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

If you are using a separate, normally installed Ubuntu, please post the contents of RESULTS.txt from the boot info script, found here:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")
It will give us information about your boot files and probably tell us what is  going wrong.

---

### Post by hodad on 2010-12-22
I used the live CD to partition the 80 MB disk, and then partitioned the disk as NTFS for the windows portion (approx 45GB), and then a ext3 swap space of about 2GB, and the remainder as ext3 for 10.04.

I then installed Linux on the ext3 and Windows XP on the NTFS, and (embarrasingly enough), can't remember which I did first.

Since my posting last night, I found on one of the earlier posts the suggestion to download the "rescatux" program.  I burned it as an image file, and then tried to boot up with it, but came up with the same "grub>" prompt. 

I just rebooted with the live disk, and that's where I'm sitting at present.

I ran fdisk, with the following result:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001358b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5737    46082421    7  HPFS/NTFS
/dev/sda2            5738        9730    32066561    5  Extended
/dev/sda5            5738        5981     1952768   82  Linux swap / Solaris
/dev/sda6   *        5981        9730    30112768   83  Linux

Disk /dev/sdb: 506 MB, 506986496 bytes
17 heads, 32 sectors/track, 1820 cylinders
Units = cylinders of 544 * 512 = 278528 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1821      495088    6  FAT16

---

### Post by drs305 on 2010-12-22
hodad,

Time to run the boot info script so we can see what's up with your new installation. 

And please repeat what your current status is when you boot without a CD: Won't boot to Windows, won't boot to either, won't boot to Ubuntu, etc, and where it leaves you: flashing cursor, grub prompt, etc.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by hodad on 2010-12-22
Ran the bootscript, and it's attached...

When I boot up w/o live cd, it just drops into that "grub" cursor.  In other words, no grub menu, and doesn't boot into either Windows or Ubuntu.

---

### Post by rajeeja on 2010-12-22
hodad,

You are in good hands.

---

### Post by drs305 on 2010-12-23
hodad,

It appears that Grub2 wasn't fully installed and you may have a larger issue since the RESULTS.txt didn't find the kernel. 

You are missing the grub.cfg file which is why you can't boot; the missing kernel may or may not exist on your machine. It could be why there is no grub.cfg, but we can fix both problems.

Boot a LiveCD. You can use the 'chroot' procedures in the following guide to mount /dev/sda6 and then accomplish the necessary steps. Complete Steps 1 & 2 from [http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099"), mounting your Ubuntu partition (sda6). 

Once at the root prompt, make sure you have the kernel on the system by reinstalling it:
```
sudo apt-get install linux-image
```
If it says it's already installed that's ok.

Next run the following and watch the terminal output. Make sure you see a 'Generating grub.cfg' message and that it completes without any error messages. 
```

update-grub
```
That should have restored the kernel and provided the grub.cfg file. You can try to reboot. Type "exit" and then reboot.

If you got error messages or no "generating grub.cfg" message, or if you still can't boot, follow the guide's instructions on completely purging and reinstalling Grub2. In the 'apt-get purge' command you can omit **grub** since it isn't installed. The command would be "apt-get purge grub-pc grub-common" or more simply "apt-get purge grub-common", which will also remove grub-pc.

---

### Post by hodad on 2010-12-23
Attempted steps 1&2 on referenced thread, but was unable to connect with apt-get upgrade.  result:

E: Could not open lock file /var/lib/apt/lists/lock - open (2: No such file or directory)

Also, a step earlier, the "sudo cp /etc/resolve.conf ..." line resulted in :

cp: cannot stat 'etc/resolve.conf': No such file or directory.

I was able to ping the router, however, so I know that I have a physical internet connection.

---

### Post by hodad on 2010-12-23
Tried procedure again, and noticed the following:

Since Windows was already installed, I tried the "middle" procedure (though I don't know what  a "wubi" is).

I got error "fuse: failed to mount access mountpoint /mnt/windows: no such fle or directory

So I tried "Normal installation".  On line "sudo cp /etc/resolve.conf ...", I got:
cp: cannot stat '/etc/resolve.conf': no such file or dir.

I subsequently looked in /etc directory, and there was no "resolv.conf" file, only a resolvconf directory.

Should I just wipe the drive and reinstall ubuntu and windows xp again?  I don't mind doing it.  If so, do you have a recommended guide to follow for the proper procedure?

---

### Post by hodad on 2010-12-23
Too many problems encountered so far.   Decided to wipe the hd and reinstall windows and ubuntu from scratch. Will start with hash check on the live cd, then follow procedure at 

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20CD](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20CD)

Thanks for your help so far, I'll be back if I have a problem.

---

### Post by epopui on 2010-12-23
Thank you for that clear step by step tutorial  - 
Worked well for me
Merry Christmas

---

### Post by drs305 on 2010-12-23
> **hodad said:**
> Attempted steps 1&2 on referenced thread, but was unable to connect with apt-get upgrade.  result:

E: Could not open lock file /var/lib/apt/lists/lock - open (2: No such file or directory)

Also, a step earlier, the "sudo cp /etc/resolve.conf ..." line resulted in :

Those steps sound like some of the folders didn't get mounted properly, and thus the files didn't exist in the chroot environment. 

If you haven't already wiped everything, you might try running the procedure again. If it's not already your practice, using cut/paste is the most reliable way of entering complex commands.

In any case, hope you get your system up and running. Happy holidays.

---

### Post by hodad on 2010-12-24
Just to follow up:

I was able to get dual booting to work after following the procedure in this thread:

 [http://ubuntuforums.org/showthread.php?t=1649050&highlight=windows+dual+boot+install+procedure](http://ubuntuforums.org/showthread.php?t=1649050&highlight=windows+dual+boot+install+procedure)  

I think I had just gotten off on the wrong foot by not fully understanding the partitioning layout. There's a good explanation of partitioning in the procedure.

Thanks for your help, and Happy Holidays to all!

---

### Post by crgutierrez on 2010-12-26
Wonderfull
many thanks

---

### Post by miegiel on 2011-01-01
In [Grub2#Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD"), after :
> Run the grub-install command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device.
```
sudo grub-install --root-directory=/mnt/ /dev/sdX
```
Example: sudo grub-install --root-directory=/mnt/ /dev/sda
It says :
> Reboot
Refresh the GRUB 2 menu with sudo update-grub
But it doesn't say so in this "how to".

Any thoughts anyone?

---

### Post by drs305 on 2011-01-01
> **miegiel said:**
> In [Grub2#Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD"), after :

It says :

But it doesn't say so in this "how to".

Any thoughts anyone?

The reinstall will write to the MBR and regenerate the /boot/grub/core.img. It doesn't refresh the grub.cfg file. This may or may not be necessary, and after some installation commands it is run automatically.

In this case it is not automatically run, but executing the command (sudo update-grub) won't hurt and could possibly correct any problems currently existing in the grub.cfg file. (Note: It is listed as Step 7 in the Reinstalling section although it's not formatted as a command and might be overlooked. Note that this must be done after rebooting.)

Short answer: It won't hurt.  ;-)

---

### Post by Sanchenzo on 2011-01-03
Thank You

---

### Post by Anu1795 on 2011-01-14
I know this is very late....But i have a few problems....
1. I have a Netbook, Acer Aspire 1410 to be exact (it doesnt have a CD Drive)
2. This is a Windows 7 Enterprise and I recieved it from my school
3. I have Ubuntu 10.04 and have just upadated it and it says "Error: No such device found (lots of numbers) gurbrescue>"
4. Will doing these steps format and/or change any Data in my computer?
5. I have installed Ubuntu on My D: drive (Which already had sum stuff in it like documents and .exe stuff) and I have Windows 7 on my C: drive

---

### Post by miegiel on 2011-01-14
> **Anu1795 said:**
> I know this is very late....But i have a few problems....
1. I have a Netbook, Acer Aspire 1410 to be exact (it doesnt have a CD Drive)
2. This is a Windows 7 Enterprise and I recieved it from my school
3. I have Ubuntu 10.04 and have just upadated it and it says "Error: No such device found (lots of numbers) gurbrescue>"
4. Will doing these steps format and/or change any Data in my computer?
5. I have installed Ubuntu on My D: drive (Which already had sum stuff in it like documents and .exe stuff) and I have Windows 7 on my C: drive

from [http://grub.enbug.org/Manual](http://grub.enbug.org/Manual)
> **Symptom(s):**

All I get is a grub prompt
Welcome to GRUB!
grub>
grub rescue>

**Cause(s):**

GRUB 2 could not find a grub.cfg.
The grub.cfg was completely unworkable.

**Solution(s):**

cat /grub/grub.cfg. If the word 'title' appears anywhere in the stanzas, then someone copied a menu.cfg directly.
Try some grub shell commands to see how the drive looks to GRUB 2, look at the configuration, find some file(s) that will boot.

hope it helps

---

### Post by jao_madn on 2011-01-15
Try to install the grub2 bootloader  Instruction: 1. Boot to 10.04 Live CD 2. Find the partition where your ubuntu install in this case is drive D in windows and maybe /dev/sda2 for linux im not sure if it is /dev/sda to find out try this command #sudo fdisk -l --> this command if you have only 2 partition for win7 and ubuntu therefor only 2 /dev/sda1 for win7 and /dev/sda2 for ubuntu 3 mount your ubuntu partition #sudo mount /dev/sda2 /mnt 4.Execute grub-install script #sudo grub-install --root-directory=/mnt/ /dev/sda  --> remember no numbers in the end of the /sda 5 umount your ubuntu partition  Note: if you have diff root and home partition.Mount the root partition not the home.

---

### Post by Xerlith on 2011-01-21
I installed Ubuntu via Wubi at the end of the summer on my computer, which was already double-booting Windows 7 and XP. The install went fine and everything worked, and I didn't worry about it. I basically used Ubuntu out of curiosity for a month or two, but I never really got into anything beyond web browsing and playing music. I eventually switched back to Windows 7 in order to type papers, play games, etc. (I know I can do that in Ubuntu; I just didn't feel like setting it up.) Anyway, I just loaded Ubuntu back up tonight for the first time in a few months; my friend had told me that there was a new update and I should check it out. I started downloading update files, installed them, and restarted. All I see now is:

Loading Operating System...
error: no such device: #################.
grub rescue>

needless to say, I'm a little freaked out. But I found this thread, and now I just need to know if I should go ahead and plop my Windows 7 disc in the tray to fix the windows boot manager. That won't do any formatting or erasing, right?

Edit: Tried your fix for the boot and it worked perfectly. Thanks a lot!

---

### Post by Carmellotruffles on 2011-01-22
For some reason my computer won't boot from the windows recovery disk or the installation disk it goes straight back to the error: no such partition. Grub rescue screen.

---

### Post by miegiel on 2011-01-24
> **Carmellotruffles said:**
> For some reason my computer won't boot from the windows recovery disk or the installation disk it goes straight back to the error: no such partition. Grub rescue screen.

Check your [BIOS]("http://en.wikipedia.org/wiki/BIOS") and make sure your CD drive is listed before your harddisk in the boot devices list.

---

### Post by jojo_mtx on 2011-01-28
nice tutorial.. thanks :KS

---

### Post by bachor on 2011-02-09
Ok,went through all 37 pages and didn't find someone with same issue,so here we go:

 I've had XP with Ubu 10.10 with Grub on MBR.

 Ubu 10.10 didn't work for me, as I've had Kubu 9 before and liked it better. 

 So did Kubu 10.04 using alternate CD with LVM encryption dual boot with no changes made to XP.

 **But got grub rescue>** and can't boot to XP either.

 1st install I didn't make separate /boot and when asked on where to install Grub I hit MBR and got some "[COLOR="Red"]FATTAL ERROR"[/COLOR] = no luck

 2nd install I made separate /boot and installed Grub in there, and again grub rescue>

 
 Now running from LiveUSB Lubuntu 10.10

 Don't have a XP cd so did :
> sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

 **No luck!**

 **here's fdisk -l: [notice no * boot by XP]**

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd18ed18e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1829    14691411    7  HPFS/NTFS
/dev/sda2            1830       10948    73241600    b  W95 FAT32
/dev/sda3           10948       14594    29285377    5  Extended
/dev/sda5           10948       14594    29285376   83  Linux


 
 **and can't install it in Encrypted / either [because it's locked?]:**

> ubuntu@ubuntu:~$ sudo mkdir /media/sda5
mkdir: cannot create directory `/media/sda5': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/sda5
mount: unknown filesystem type 'crypto_LUKS'



 Any idea?

---

### Post by bachor on 2011-02-09
Ok, so I've tried it again with option to install Grub to MBR and error I got is:

> 
[B]!! Configuring Grub-pc

Unable to Install Grub in /dev/sda
Executing 'Grub-install /dev/sda' FAILED

This is a Fatal Error[/B]


 at least I fixed XP to boot.

 Is it better to install Grub in MBR or /boot? 

 I remember when I did to /boot, there were Grub files. It just didn't boot any.

---

### Post by miegiel on 2011-02-09
> **bachor said:**
> Ok, so I've tried it again with option to install Grub to MBR and error I got is:



 at least I fixed XP to boot.

 Is it better to install Grub in MBR or /boot? 

 I remember when I did to /boot, there were Grub files. It just didn't boot any.

(I) always put grub in the MBR!

Regarding encrypting your disk: What's your objective, to keep thieves and people who "found" your laptop out of you personal data, or to secure your data against the cops, secret services and criminals who hacked into your machine?

If it's just against ordinary thieves or curious people you could use the encryption built into the disk. You can turn it on in the BIOS (don't confuse it with the regular BIOS password). It's no protection against the real professionals if they don't mind spending some time and money to see what your "hobbies" are.

---

### Post by JLH02 on 2011-02-11
I have completely lost track of the number of times that I've visited this tutorial (maybe I should quit breaking my dual-boot systems).  

I figured it was time to say "Thank You Very Much" to the OP. Your tutorial has been extremely helpful.

-Joe

---

### Post by bachor on 2011-02-15
> **miegiel said:**
> (I) always put grub in the MBR!

Regarding encrypting your disk: What's your objective, to keep thieves and people who "found" your laptop out of you personal data, or to secure your data against the cops, secret services and criminals who hacked into your machine?

If it's just against ordinary thieves or curious people you could use the encryption built into the disk. You can turn it on in the BIOS (don't confuse it with the regular BIOS password). It's no protection against the real professionals if they don't mind spending some time and money to see what your "hobbies" are.


 I just like it encrypted. It won't hurt anything, except it makes it bit difficult to get it to work :)

 I fixed it. It is one of those times when you have to try it again and again :D  but it didn't let me to install Grub in MBR so had to go with /boot option. Btw, what you mean by BIOS encryption?

 And yes THANK YOU all for helping at this forum ):P

---

### Post by miegiel on 2011-02-16
> **bachor said:**
> I just like it encrypted. It won't hurt anything, except it makes it bit difficult to get it to work :)

 I fixed it. It is one of those times when you have to try it again and again :D  but it didn't let me to install Grub in MBR so had to go with /boot option. Btw, what you mean by BIOS encryption?

 And yes THANK YOU all for helping at this forum ):P

A bit off-topic, but ...

The BIOS is just used to turn the encryption on. All hard disks (except really old ones maybe) have built in "encryption". Actually nothing really gets encrypted, but you need to enter a key to unlock the disks electronics, without the key the disk plays dead and you can't get to the data. If you put the disk in another pc you'll still need the key to boot/access it. It's enough protection against ordinary thieves, but it won't keep a security scientist out (rocket scientists are overrated :D).

---

### Post by surfersat on 2011-02-26
Excelent, thank you!!!

---

### Post by Totally on 2011-03-09
Can someone help me here please.

I have windows XP and Ubuntu 10.10. I followed the directions and got this:


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
4 heads, 2 sectors/track, 39072726 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00047fc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1     6510335    26041339    7  HPFS/NTFS
/dev/sda2         6510336    39072512   130248708    f  W95 Ext'd (LBA)
/dev/sda5         6510337    39072512   130248704   83  Linux

Disk /dev/sdb: 3879 MB, 3879731200 bytes
128 heads, 23 sectors/track, 2573 cylinders
Units = cylinders of 2944 * 512 = 1507328 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2574     3788768+   c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudomkdir /media/sda5
sudomkdir: command not found
ubuntu@ubuntu:~$ sudo mkdir /media/sda5
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/sda5
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda5 /dev/sda
/usr/sbin/grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.



What do I do now and how do I get my bootloader to work for xp and ubuntu?

Please help.

---

### Post by drs305 on 2011-03-09
> **Totally said:**
> 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
**4 heads, 2 sectors/track, 39072726 cylinders**
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00047fc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1     6510335    26041339    7  HPFS/NTFS
/dev/sda2         6510336    39072512   130248708    f  W95 Ext'd (LBA)
/dev/sda5         6510337    39072512   130248704   83  Linux

Disk /dev/sdb: 3879 MB, 3879731200 bytes
**128 heads, 23 sectors/track, 2573 cylinders**
Units = cylinders of 2944 * 512 = 1507328 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18


I don't know a lot about disk properties, but the first highlighted entry above seems odd to me. Someone with more knowledge about disk properties will probably be able to shed some light on this issue but I suspect that is what is causing the problem.

You could try to install to the sdb MBR but the thumb drive would need to be inserted whenever you boot. But if you want to try it, just run the same commands you did but replace "sda" with "sdb" in the second command (grub-install).

---

### Post by Totally on 2011-03-09
Hi, thanks for the quick response:

its saying:

error: cannot find device for media/sda5/boot/grub (is /dev mounted?)

Just one thing, will this allow me to get to my files in linux that are still on my drive and be able to dual boot into windows too?

---

### Post by drs305 on 2011-03-09
> **Totally said:**
> its saying:

error: cannot find device for media/sda5/boot/grub (is /dev mounted?)

Just one thing, will this allow me to get to my files in linux that are still on my drive and be able to dual boot into windows too?

Did you miss a "/"? Here are the commands:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

This would leave whatever is on the sda MBR as it is, and have the sdb MBR point to your Grub files on sda5. If it works, you will end up with a grub menu that should allow you to boot either Windows or Ubuntu. 

The ability to boot Windows, however, depends on the integrity of the Windows boot files. If Windows boots now, it should boot after you install G2. If Windows doesn't boot, I would concentrate on getting Windows to boot using a Windows repair disk first. You can review the first post in this thread for resolving Windows boot issues.

Note the command earlier in this post may get Ubuntu to boot even if your attempts to boot Windows fail.

---

### Post by Totally on 2011-03-09
this is what I get:






ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root=directory=/mnt /dev/sdb
Unrecognized option `--root=directory=/mnt'
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into /boot/grub (or /grub on NetBSD and
OpenBSD), and uses grub-setup to install grub into the boot sector.

If the --root-directory option is used, then grub-install will copy
images into the operating system installation rooted at that directory.

Report bugs to <bug-grub@gnu.org>.
ubuntu@ubuntu:~$

---

### Post by drs305 on 2011-03-09
> **Totally said:**
> this is what I get:

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
**ubuntu@ubuntu:~$ sudo grub-install --root[B][COLOR="Red"]=[/COLOR]**directory=/mnt /dev/sdb[/B]
Unrecognized option `--root=directory=/mnt'


You have an **=** symbol where there should be a "-". If possible, it's often easier and more accurate to use copy/paste to enter the commands, then edit them as necessary.

---

### Post by Totally on 2011-03-09
Thanks man, did that and now I can login through the usb.

Really appreciate it.

Is there no way of fixing it or shall I just reinstall ubuntu?

---

### Post by drs305 on 2011-03-09
> **Totally said:**
> Thanks man, did that and now I can login through the usb. Is there no way of fixing it or shall I just reinstall ubuntu?

I am not sure reinstalling Ubuntu will fix the problem as I'm not sure if the problem is the way the Ubuntu partition was created or if it's the entire disk (or both/neither of the above).

You might start your own thread, post the *fdisk* results and state what problems you had. I wouldn't mention "Grub" or "boot" in the title, but something about sectors, heads or cylinders. 

I don't know enough about the issue to even know if it's a problem or how to correct it if it is (other than reformatting the entire disk, which I wouldn't do). Someone will have the answers for you though.

---

### Post by Totally on 2011-03-09
Thanks man, will try and see for other possibilities.

Cheers, for now.

---

### Post by awatt on 2011-03-10
Hello all,

I am new to Ubuntu and this question is technically about a Debian machine, but I'm using a 10.10 live CD to recover a Debian system after installing XP, so here goes:

I followed the dual booting instructions found here: [How to dual boot Linux and Windows XP (Linux installed first)]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1")
When I got to restoring grub, the command ```
sudo grub
``` didn't work. I gather that is because 10.10 uses Grub 2.
I found this thread (very nice indeed) and ran ```
sudo fdisk -l
```I got:
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 62 sectors/track, 12821 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Disk identifier: 0x023a0239

     Device Boot     Start         End      Blocks     Id     System
/dev/sda1     *        12246   12921   5110528+   7      HPFS/NTFS
```
This makes me think XP reformatted the non-Windows partitions. 
To add insult to injury I was too hasty when doing this and forgot to back up the hard drive, so there are some things on this computer that I only have on this computer. (Most of the stuff was backed up thanks to my regular backups, but not things from the last week or so.) I would really like to recover that stuff. 

Does anyone know if that is even possible?

Thanks a lot.

---

### Post by miegiel on 2011-03-10
> **awatt said:**
> Hello all,

...

This makes me think XP reformatted the non-Windows partitions. 
To add insult to injury I was too hasty when doing this and forgot to back up the hard drive, so there are some things on this computer that I only have on this computer. (Most of the stuff was backed up thanks to my regular backups, but not things from the last week or so.) I would really like to recover that stuff. 

Does anyone know if that is even possible?

Thanks a lot.

If a new partition has been made over the old partitions, the new partition has been formated and data has been written to the new partition, then you can consider your data lost.

Sorry for bringing the bad news.

You could go look for forensic data recovery tools, but that would only get bits of the lost data (like parts of files) and cost a lot of time and effort.

**ps**: Is that 1 partition covering the whole disk ?

---

### Post by drs305 on 2011-03-10
awatt,

Welcome to the Ubuntu forums - sorry for the circumstances that brought you here though...

You could try installing Test Disk and seeing if it can find any of your old files. Some find it difficult to use, but if you really need the files it's worth trying. Test Disk is in the Universe repository, so on the LiveCD to install it you would have to add the repository, then install it.

In Synaptic, the steps would be: System > Administration > Synaptic. Settings > Repositories > Ubuntu Software tab: Enable *universe* if it's not enabled. Then install "testdisk".

Here are two good guides on how to look for lost partitions/files:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/~herman546/p21.html")

---

### Post by awatt on 2011-03-10
Thanks for the replies.

@miegiel: The 1 partion is only on 5GB of the disk, which I freed up just for the installation of XP.

@drs305: Your advice was extremely helpful. I couldn't find testdisk with the liveCD, so I downloaded the windows version and ran it under XP. 
Lo and behold there were my previously lost partitions. The problem I have now is that I can't set the partitions exactly the way they were before.

I had a small FAT32 partition followed by my root partition, a swap partition and my main partition followed ultimately by a small NTFS partition for XP.

I can see all of these partitions in that order with testdisk. The problem is the program tells me that the structure is bad when I change the partition characteristics to what I think they should be namely:

P FAT32
* Linux (root)
L Linux Swap
L Linux (main)
P HPFS - NTFS

*=Primary bootable P=Primary L=Logical E=extended D=Deleted

By the way, two configurations testdisk does seem willing to accept are:

D FAT32
* Linux (root)
D Linux Swap
L Linux (main)
L HPFS - NTFS

and 

D FAT32
* Linux (root)
D Linux Swap
L Linux (main)
P HPFS - NTFS

Would either of these get me access to my 'lost' files long enough to save them and then maybe do a complete re-install starting with XP to avoid this problem the next time around?

---

### Post by brain90 on 2011-03-10
@talsemgeest
five stars for this tutorial : ;)
:KS:KS:KS:KS:KS

---

### Post by mcubt on 2011-03-15
Thank you for your good tutorial.   Windows 7 disappeared from multi-boot menu in my Win7/Ubuntu multi-boot MSI laptop after I upgraded Ubuntu to 10.04.   I boot the laptop from Window 7 recovery disk but it can't find Windows 7 installation after selected "Repair your computer."  What I should do next?    The paritions are as follows:

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10618    85286396+   7  HPFS/NTFS
/dev/sda2           10618       19458    71003137    5  Extended
/dev/sda5           10618       19092    68064256   83  Linux
/dev/sda6           19092       19458     2937856   82  Linux swap / Solaris

---

### Post by lnxfm on 2011-03-24
[QUOTE=talsemgeest;6391959]**[SIZE=6][COLOR=blue]How to restore the Ubuntu/XP/Vista/7 bootloader [/COLOR][/SIZE]**

subject:  mount  issue: "You must specify the filesystem type"

origial systems: xps, ubuntus 10.0+ dual boot
Cause of trouble: after resize xps use magic parttion:
error: unknown filesystem
grub rescue >
Followed your instruction: Booted from ubunton10.04

ubuntu@ubuntu:~$ sudo mkdir /media/sda5
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/sda5
mount: you must specify the filesystem type

tried: sudo mount -t ext2 /dev/sda5 /media/sda5

or -t ext3    or mount...  sda6, sda11 not work

any suggestions?

Regards

---------------- - ------------------------ - ------------------------ -----------------

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xea08ea08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8251    66276126    7  HPFS/NTFS
/dev/sda2            8252       12599    34925310    7  HPFS/NTFS
/dev/sda3           12600       17716    41101313    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda4           17717       19457    13984582+   7  HPFS/NTFS
/dev/sda5           12600       13561     7726312   83  Linux
/dev/sda6           13562       14387     6633472   83  Linux
/dev/sda7           14387       14430      353280   82  Linux swap / Solaris
/dev/sda8           14432       14477      367616   82  Linux swap / Solaris
/dev/sda9           14478       14566      707584   82  Linux swap / Solaris
/dev/sda10          14567       16845    18302910    7  HPFS/NTFS
/dev/sda11          16845       17672     6644736   83  Linux
/dev/sda12          17673       17716      352256   82  Linux swap / Solaris

Disk /dev/sdb: 129 MB, 129499136 bytes
33 heads, 32 sectors/track, 239 cylinders
Units = cylinders of 1056 * 512 = 540672 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         240      126448    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 32, 32) logical=(239, 16, 32)

---

### Post by whatthepuff on 2011-03-29
You completely saved my ***! Thank you!

I booted from the Win 7 repair disc on my USB drive using YUMI. Then, after that I figured out I had to cd to x: (rather than trying the commands in x:windows\system or something, I can't remember the exact path). I then restarted and I'm looking at Win 7 again. Thank you!

---

### Post by Mike_Short on 2011-03-29
I have Ubuntu 10.04 and Windoze 7 dual booting on my laptop.
Windoze now fails to boot almost every time, and repair doesn't usually fix it. I have to boot the Win7 disc, and repair, and it still takes 5-10 boots to come up successfully. I want to remove Win7 altogether. Can I do this without reinstalling Ubuntu?

If anything, I would put XP back on the partition. 

Ideas? 

Mike

---

### Post by drs305 on 2011-03-29
> **Mike_Short said:**
> I want to remove Win7 altogether. Can I do this without reinstalling Ubuntu?

If anything, I would put XP back on the partition. 

Ideas? 

Mike

Yes. If you are using Grub to boot, you can remove the Windows partition. In most cases, the Ubuntu installation is placed on sda5, so even if you delete sda1, sda2 or sda3 it won't change your Ubuntu partition designation. Even if the partition number changes, Grub 2 uses UUIDs as well so it should still boot without any problem.

If you have Windows set as your default OS in Grub just change it to Ubuntu before you remove Windows.

If you reinstall Windows, you will will have to reinstall G2 to the MBR by mounting the Ubuntu partition and using "sudo grub-install --root-directory=/mountpoint /dev/sda" to restore Grub.

---

### Post by E-One on 2011-04-08
Guys will you please (crying for help) help me?

I'm going crazy in last 3 days, trying to fix my laptop. I red and tried everything i found on your forum and google regarding my problem and still nothing :(

I have installed Ubuntu Netbook v10 and Win Xp on my Toshiba Satellite A50-109. After restarting computer i got: 

error: no such partition.
grub rescue> _

I tried all commands i found here but these are only ones that do anything, while the rest mainly give "Unknown command".

- ls {gives: (hd0) (hd0,msdos5) (hd0,msdos1) (fd0) }
- set root=(hdX,Y)
- set {gives: root=hd0,msdos6}

One thing i noticed is that when use set root command and change it to one of the values, when i reboot computer it returns to hd0,msdos6...

thank you in advance!
Ivan

---

### Post by drs305 on 2011-04-08
E-One,

We need to see the contents of RESULTS.txt, which you generate by running the boot info script: [http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

As a guess, you could try the following but we really need the RESULTS.txt to know what is happening:

```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod (hd0,5)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
```

---

### Post by E-One on 2011-04-08
I tried your guess, but on the 3rd line i get: 
error: unknown filesystem.

After 4th command i get: Unknown command 'initrd'

Regarding RESULTS.txt i don't know how to get it done. I downloaded the file, but not sure how to run it, since when i type command sudo, i get: Unknown command 'sudo' :P

Not to mention that i can't access my files to copy it on hd :(

---

### Post by drs305 on 2011-04-08
> **E-One said:**
> Regarding RESULTS.txt i don't know how to get it done. I downloaded the file, but not sure how to run it, since when i type command sudo, i get: Unknown command 'sudo' :P

Not to mention that i can't access my files to copy it on hd :(

Are you using the LiveCD? You should be able to use the 'sudo' command while on the LiveCD.

The instructions on how to run the boot info script are located on the site from which you downloaded it. The file is normally located on either your Desktop (~/Desktop) or in the ~/Downloads folder.

---

### Post by jao_madn on 2011-04-08
> **E-One said:**
> I tried your guess, but on the 3rd line i get: 
error: unknown filesystem.

After 4th command i get: Unknown command 'initrd'

Regarding RESULTS.txt i don't know how to get it done. I downloaded the file, but not sure how to run it, since when i type command sudo, i get: Unknown command 'sudo' :P

Not to mention that i can't access my files to copy it on hd :(

 Where did u run the sudo command the the grub-rescue> or in the command line in the boot live cd.

---

### Post by E-One on 2011-04-08
> **jao_madn said:**
> Where did u run the sudo command the the grub-rescue> or in the command line in the boot live cd.

On grub-rescue, i don't think i can start live cd.

I tried booting win xp and ubuntu cd, but i'm stuck on grub-rescue :(

---

### Post by SecretCode on 2011-04-09
Booting from the CD should be controlled by the BIOS, not by GRUB. You need to hit whatever key your computer has for changing the boot order (or entering bios setup) - usually displayed for a second or two on on the power-on screen - and make booting from CD top of the list.

---

### Post by E-One on 2011-04-09
> **SecretCode said:**
> Booting from the CD should be controlled by the BIOS, not by GRUB. You need to hit whatever key your computer has for changing the boot order (or entering bios setup) - usually displayed for a second or two on on the power-on screen - and make booting from CD top of the list.

I know i did that so many times ;)

But the problem is that it won't load any bootable cd (win xp, win 7, ubuntu) and it goes forward to grub-rescue..

I don't know what to do :(

---

### Post by SecretCode on 2011-04-09
Odd. An Ubuntu CD should be bootable even in a machine with nothing on the hard drive. If it doesn't, and the CD is OK (can you boot from it on another computer?), it suggests there's something wrong with the CD **drive**. Laptop CD drives aren't always the best quality ...

Is the laptop capable of booting from a USB drive? (The BIOS will tell you) You could try creating an Ubuntu Live USB stick and booting with that.

---

### Post by jao_madn on 2011-04-09
> **E-One said:**
> I know i did that so many times ;)

But the problem is that it won't load any bootable cd (win xp, win 7, ubuntu) and it goes forward to grub-rescue..

I don't know what to do :(

 the grub rescue is in the hard disk therefore your toshiba boot directly to the hard disk.I remember i troubleshoot toshiba last week.. it wont boot directly to CD you must first hit ctrl+atl+del many time to restart the system until it will detected the CD and boot to it..or after plug in the live CD then start the system what i mean is right timing..

---

### Post by E-One on 2011-04-09
Thank you guys for all advices, i'll try it all and let you know if i get any results :P

---

### Post by Fanatico on 2011-04-09
I have two questions about booting Windows 7 with Grub:

1. I wonder whether Legacy Grub (Grub 1) can boot Windows 7? Are there any technical difficulties or limitations in doing that?

2. I am trying to boot Windows 7 with help of Legacy Grub. I successfully start Grub stage1, then stage 2 displays Grub menu. As soon as I select windows 7 entry - I see nothing, no errors, just black screen.

I wonder how can I troubleshoot this problem when I have no error and no indications about what is happening. The only idea I have right now is to open Grub sources add some debug outputs to chainloader function, rebuild it and try to debug grub. But this is very difficult.

Can anyone advise about other options I might have?

Thanks

---

### Post by xalu on 2011-04-28
Thanks!  Once I realized I was installing the grub loader on the wrong drive it was easy.  For those having trouble make sure you install the grub booger on the Linux drive if you have more than one hard drive for each OS.  Worked with windows 7 and ubuntu 10.10.

---

### Post by bororeh on 2011-05-05
> **talsemgeest said:**
> 
[SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.10 and beyond)[/COLOR][/SIZE]

...
From that you need to find the device name of your Ubuntu drive, something like &#8220;/dev/sda5&#8243;.
 So, still in the terminal, type:
```

sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
```And then, to reinstall the grub: ```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```Push enter and you&#8217;re done! Of course you need to replace &#8220;/dev/sda5&#8243; and &#8220;/dev/sda&#8221; with what you found in the fdisk output.


Hey there! It didn't work for me =(
I was upgrading ubuntu from 10.04 to 10.10 and my grub got screwed. Whenever I restarted, a strange message appeared:
[I]error: the symbol `grub_xputs` not found.
grub rescue[/I]

So I found this topic and tried the quoted solution (Yes, I checked the device and it is, indeed, sda5). But now, instead of the display of the strange message, I got a also strange weird fast-blinking cursor (not Grub!!).

What can I do?

Thanks!

---

### Post by drs305 on 2011-05-05
> **bororeh said:**
> So I found this topic and tried the quoted solution (Yes, I checked the device and it is, indeed, sda5). But now, instead of the display of the strange message, I got a also strange weird fast-blinking cursor (not Grub!!).

What can I do?

If this is a normal installation on a separate partition (not Wubi), the blinking cursor may be a video driver issue. When Grub2 fails, it either generates a message or leaves you at a 'grub' or 'grub rescue' prompt.

If it's a video issue, get to the Grub2 menu (if you don't see it, hold down the SHIFT key during boot). Highlight the Linux menu item, then press 'e' to edit it. 

At the end of the 'linux' line, remove 'quiet splash' and add **nomodeset**

Press CTRL-x to boot. If it boots to the desktop, go to System, Additional Drivers and install your video card driver.

---

### Post by gringo88 on 2011-05-09
I have followed the guide for Windows 7 and i got dreaded "A disk read error occured - Press Ctrl + Alt + Del to restart" upon boot. 

What should i do now? Windows repair disc didn't do anything, and i don't want to open computer as i'm not too tech savy and it's not my PC (i'm helping someone). Can someone help me or should i just format disk and install a fresh copy of Windows 7 :(

---

### Post by HunkirDowne on 2011-05-10
> **gringo88 said:**
> I have followed the guide for Windows 7 and i got dreaded "A disk read error occured - Press Ctrl + Alt + Del to restart" upon boot. 

What should i do now? Windows repair disc didn't do anything, and i don't want to open computer as i'm not too tech savy and it's not my PC (i'm helping someone). Can someone help me or should i just format disk and install a fresh copy of Windows 7 :(

Consider this a first-responder response: Do NOT open computer.
(At least not yet... ;-) )

If there were no disk problems before, and then you (or someone else) did something without opening the computer, it was done with software and software can generally fix it -- no need to touch the hardware.

**Question**
Can you boot from a LiveCD?  If so, before you go reinstalling Windows from scratch, you can at least backup files out of C:/Users/<username>/ to an external drive.

Have you tried the Windows 7 Recovery disk?

I have not (yet) had  this problem as the only thing I have on my Win7 box is wubi.  I have yet to do a permanent install on this machine and my others are windows free.  That said, those with more experience with this issue will likely be better served with a little more information.

Keep us informed as best you can.


take care,
hd.

---

### Post by Mspirit on 2011-05-17
> **talsemgeest said:**
> 

[SIZE=5][COLOR=red]How to restore the Windows Vista or 7 bootloader[/COLOR][/SIZE]

To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download for [Vista]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download") or [Win 7](http://neosmart.net/blog/2009/windows-7-system-repair-discs/).
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

```
bootrec.exe /fixboot
``````
bootrec.exe /fixmbr
```Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader.

I can't thank you enough XD

---

### Post by jcma1987 on 2011-05-23
Hi there,

As per this topic, I have lost access to my Windows XP boot in Ubuntu's Grub bootloader following a recent upgrade to 11.04. However I am unable to run the fixboot command from the XP recovery console as I hit a blue screen error whilst booting from the XP install CD, which I believe is as a result of having PGP WDE.

Are there any other suggestions as to how the boot can be fixed in this situation?

Happy to provide further information.

Many thanks in advance

---

### Post by jcma1987 on 2011-05-23
Here are the contents of RESULTS.txt to support the above

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   479,023,545   479,023,483   7 NTFS / exFAT / HPFS
/dev/sda2         479,025,150   625,141,759   146,116,610   5 Extended
/dev/sda5         479,025,152   619,096,063   140,070,912  83 Linux
/dev/sda6         619,098,112   625,141,759     6,043,648  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda5        31621b00-296f-42a4-ba46-a163052a8b06   ext4       
/dev/sda6        5c137f76-ef05-4fe1-a266-44aaf51ddf16   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,user=ashwin)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=31621b00-296f-42a4-ba46-a163052a8b06 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=31621b00-296f-42a4-ba46-a163052a8b06 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=31621b00-296f-42a4-ba46-a163052a8b06 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=31621b00-296f-42a4-ba46-a163052a8b06 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=31621b00-296f-42a4-ba46-a163052a8b06 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=31621b00-296f-42a4-ba46-a163052a8b06 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 31621b00-296f-42a4-ba46-a163052a8b06
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=31621b00-296f-42a4-ba46-a163052a8b06 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5c137f76-ef05-4fe1-a266-44aaf51ddf16 none            swap    sw              0       0
/dev/sr0   /media/cdrom0   udf,iso9660 user,noauto,exec   0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 274.544593811 = 294.790012928  boot/grub/core.img                             1
 236.741409302 = 254.199152640  boot/grub/grub.cfg                             1
 251.279548645 = 269.809360896  boot/initrd.img-2.6.35-28-generic              2
 275.342918396 = 295.647207424  boot/initrd.img-2.6.38-8-generic               2
 275.425216675 = 295.735574528  boot/initrd.img-2.6.38-8-generic-pae           2
 274.854393005 = 295.122657280  boot/vmlinuz-2.6.35-28-generic                 1
 264.120422363 = 283.597144064  boot/vmlinuz-2.6.38-8-generic                  1
 264.186950684 = 283.668578304  boot/vmlinuz-2.6.38-8-generic-pae              1
 275.425216675 = 295.735574528  initrd.img                                     2
 275.342918396 = 295.647207424  initrd.img.old                                 2
 264.186950684 = 283.668578304  vmlinuz                                        1
 264.120422363 = 283.597144064  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  fd 70 8c 92 34 36 7e af  a9 5a 86 8f 99 71 57 2a  |.p..46~..Z...qW*|
00000010  fd a5 5e 80 de e7 6c 39  5f d6 db 6a 33 b7 0d dd  |..^...l9_..j3...|
00000020  72 10 8f be 98 f8 71 0e  08 15 a9 a3 af 1b 7f c7  |r.....q.........|
00000030  96 86 82 c4 91 47 fe 42  35 a2 2d d1 c4 6e 6c 8d  |.....G.B5.-..nl.|
00000040  7e c8 97 55 f3 f8 ff cf  d7 b0 b0 07 57 42 74 3a  |~..U........WBt:|
00000050  ef cc e8 2a a6 6f df 30  5c b8 3f 40 39 bb 54 cb  |...*.o.0\.?@9.T.|
00000060  5c 0b 9d 8f a9 08 2e 13  37 77 d0 bb 3d 46 1b 36  |\.......7w..=F.6|
00000070  ff 4c 75 9e 39 e0 1d ba  82 be 37 86 15 a1 5b aa  |.Lu.9.....7...[.|
00000080  27 34 8b 2e 81 36 1e e5  da 98 ae 1c 5b cb a8 86  |'4...6......[...|
00000090  a4 4d 64 58 61 93 a7 e5  04 e5 0a 3e ba 27 dc 95  |.MdXa......>.'..|
000000a0  83 84 ba 37 50 08 92 e0  45 44 1f ee c7 aa 81 52  |...7P...ED.....R|
000000b0  20 7b 18 e7 ff 87 d3 af  b5 20 57 ce 66 7b 59 60  | {....... W.f{Y`|
000000c0  14 1a e5 82 5b 5c 32 f5  71 3c f7 e0 28 49 5a c0  |....[\2.q<..(IZ.|
000000d0  2d fc ba b2 81 d4 2e 68  de ba c8 ca f2 37 1d a2  |-......h.....7..|
000000e0  14 4d a4 d2 31 89 62 df  3f 3c 21 06 f2 b8 d3 67  |.M..1.b.?<!....g|
000000f0  e3 cf 9f bf 09 23 33 d6  8e 88 9c fd 7c 56 29 6b  |.....#3.....|V)k|
00000100  d5 20 dc e5 f9 32 58 e9  07 00 30 99 a2 33 bb 4a  |. ...2X...0..3.J|
00000110  3e b9 85 3b ef 77 15 63  b5 b4 43 95 37 b5 80 bf  |>..;.w.c..C.7...|
00000120  9e 35 c5 e0 59 67 68 26  56 e3 06 b1 f3 35 bf 40  |.5..Ygh&V....5.@|
00000130  ff 66 43 91 94 7a 16 b0  e7 14 37 f6 c1 63 4b 5f  |.fC..z....7..cK_|
00000140  54 fc 22 39 09 46 f9 8f  a3 d2 a3 bb 26 b3 21 14  |T."9.F......&.!.|
00000150  6a 57 f5 76 3d 65 50 d0  6c d4 d9 f1 54 02 87 be  |jW.v=eP.l...T...|
00000160  4c ec 40 3c d1 af 1d 15  0e 98 7d 38 d9 02 98 19  |L.@<......}8....|
00000170  71 90 46 fb f2 7a 40 1b  f3 54 81 cd 3b 3d f3 32  |q.F..z@..T..;=.2|
00000180  53 21 f7 74 80 25 7e e9  6b 48 1b 65 ca 27 62 5c  |S!.t.%~.kH.e.'b\|
00000190  d3 7f 08 f7 e4 bf 44 b2  dc c6 98 a4 7a b3 af 9d  |......D.....z...|
000001a0  b7 96 8f c5 6a 41 1d b6  d7 a2 47 26 7d 03 bd b5  |....jA....G&}...|
000001b0  e0 97 68 0c af 0f 8d be  dd f0 09 ca f2 70 ba 9f  |..h..........p..|
000001c0  89 b9 6f 82 50 88 06 a5  dd 1e a9 3c 73 54 14 47  |..o.P......<sT.G|
000001d0  a7 fb bb 6c 1b 19 2a c8  f4 64 7a 0f cc 1e 73 6c  |...l..*..dz...sl|
000001e0  d0 9f 94 be a8 77 fc 40  89 64 5d 36 4b 94 7e e1  |.....w.@.d]6K.~.|
000001f0  d7 90 ba 35 9c 9b 51 d4  b3 63 25 95 02 45 d7 0c  |...5..Q..c%..E..|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by jcma1987 on 2011-05-23
Apologies for the triple post, but here is the result of fdisk -l to further support the above, many thanks in advance for any help

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29818   239511741+   7  HPFS/NTFS
/dev/sda2           29818       38914    73058305    5  Extended
/dev/sda5           29818       38537    70035456   83  Linux
/dev/sda6           38538       38914     3021824   82  Linux swap / Solaris

---

### Post by cayphed on 2011-05-23
Thank you for this simple to read tutorial Talsemgeest.
It worked great for my win7 install.

---

### Post by kbitz23 on 2011-06-06
Greetings

Talsemgeest, first I want to thank you for your continued support regarding this issue.  I've read through the thread and it's been very helpful.  With that said.. i'm having an issue with the final step:

[sudo grub-install --root-directory=/media/sda5 /dev/sda]

When I do this I get the the response:

"The drive (hd0) is defined multiple times in the device map /media/sdf5/boot/grub/device.map"


Here is the information from fdisk and my RESULTS.TXT

```
Disk /dev/sda: 400.1 GB, 400088457216 bytes
240 heads, 63 sectors/track, 51681 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa0f87713

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       50453   381424648+   7  HPFS/NTFS
/dev/sda3           50454       51681     9283680    7  HPFS/NTFS

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0007e21a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       15298   122878976    7  HPFS/NTFS
/dev/sdf2           15298       22947    61438977    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdf3           22947      243202  1769194496    7  HPFS/NTFS
/dev/sdf5           15298       22572    58425344   83  Linux
/dev/sdf6           22572       22947     3012608   82  Linux swap / Solaris
```


```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdf and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for (,msdos2)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/BCD

sdf1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdf2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdf5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
240 heads, 63 sectors/track, 51681 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   762,849,359   762,849,297   7 NTFS / exFAT / HPFS
/dev/sda3         762,849,360   781,416,719    18,567,360   7 NTFS / exFAT / HPFS


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1               2,048   245,759,999   245,757,952   7 NTFS / exFAT / HPFS
/dev/sdf2         245,762,046   368,639,999   122,877,954   5 Extended
/dev/sdf5         245,762,048   362,612,735   116,850,688  83 Linux
/dev/sdf6         362,614,784   368,639,999     6,025,216  82 Linux swap / Solaris
/dev/sdf3         368,640,000 3,907,028,991 3,538,388,992   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        E26AE78B6AE75AB5                       ntfs       HP
/dev/sda3        2C88743C8874071C                       ntfs       FACTORY_IMAGE
/dev/sdf1        3420C55C20C52628                       ntfs       
/dev/sdf3        7FB75C222713F1B7                       ntfs       Storage
/dev/sdf5        0599fec9-4cdd-4398-88e7-a7f8ecf5590d   ext4       
/dev/sdf6        c7edafa7-2456-4bb7-b250-7f6064a64dc1   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf5        /media/sdf5              ext4       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== sda1/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e26ae78b6ae75ab5
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e26ae78b6ae75ab5
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-28-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e26ae78b6ae75ab5
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-28-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, Linux 2.6.32-28-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e26ae78b6ae75ab5
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-28-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e26ae78b6ae75ab5
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e26ae78b6ae75ab5
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e26ae78b6ae75ab5
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

============================= sda1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda1/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   8.321208954 = 8.934830080    boot/grub/grub.cfg                             1
   0.937500000 = 1.006632960    boot/initrd.img-2.6.32-24-generic              2
   1.117187500 = 1.199570944    boot/initrd.img-2.6.32-28-generic              2
   6.378772736 = 6.849155072    boot/vmlinuz-2.6.32-24-generic                 1
   6.510925293 = 6.991052800    boot/vmlinuz-2.6.32-28-generic                 1
   1.117187500 = 1.199570944    initrd.img                                     2
   0.937500000 = 1.006632960    initrd.img.old                                 2
   6.510925293 = 6.991052800    vmlinuz                                        1
   6.378772736 = 6.849155072    vmlinuz.old                                    1

=========================== sdf5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 0599fec9-4cdd-4398-88e7-a7f8ecf5590d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 0599fec9-4cdd-4398-88e7-a7f8ecf5590d
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 0599fec9-4cdd-4398-88e7-a7f8ecf5590d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=0599fec9-4cdd-4398-88e7-a7f8ecf5590d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 0599fec9-4cdd-4398-88e7-a7f8ecf5590d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=0599fec9-4cdd-4398-88e7-a7f8ecf5590d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 0599fec9-4cdd-4398-88e7-a7f8ecf5590d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 0599fec9-4cdd-4398-88e7-a7f8ecf5590d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root E26AE78B6AE75AB5
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 2C88743C8874071C
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdf5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=0599fec9-4cdd-4398-88e7-a7f8ecf5590d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=c7edafa7-2456-4bb7-b250-7f6064a64dc1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdf5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 120.032867432 = 128.884310016  boot/grub/core.img                             1
 120.033081055 = 128.884539392  boot/grub/grub.cfg                             1
 169.383789062 = 181.874458624  boot/initrd.img-2.6.38-8-generic               4
 121.227790833 = 130.167349248  boot/vmlinuz-2.6.38-8-generic                  1
 169.383789062 = 181.874458624  initrd.img                                     4
 121.227790833 = 130.167349248  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 
```


Thank you for any help you can give! :)

---

### Post by tlcrenshaw on 2011-06-07
I would just like to thank you for the information on repairing Windows 7. I thought I had lost my laptop but by following your directions managed to repair my OS. Thank you so much!:p

---

### Post by Koffeehaus on 2011-06-08
> **talsemgeest said:**
> 

 Of course you need to replace “/dev/sda5&#8243; and “/dev/sda” with what you found in the fdisk output.



Wouldn't /dev/sda always be the same since the bootloader always has to be at the first sector for the PC to load it?

---

### Post by virsto on 2011-06-09
Your instructions were "right on target" --- I followed your instructions exactly. But, I still have a problem.

First, I have a dual-boot system (Windows Vista-Ubuntu) or perhaps I should say "had" a dual-boot system. My problem started when I upgraded my Ubuntu to 10.10 and something went wrong with GRUB (see my postings under user --- virsto **Upgrade to 10.10 --- grub_xputs**.

Now, I never get a screen that allows me to choose the system to boot to --- I automatically boot to Windows Vista. How can I recover the ability to boot to my Ubuntu 10.10 (or earlier installations)?

---

### Post by Koffeehaus on 2011-06-12
> **virsto said:**
> Your instructions were "right on target" --- I followed your instructions exactly. But, I still have a problem.

First, I have a dual-boot system (Windows Vista-Ubuntu) or perhaps I should say "had" a dual-boot system. My problem started when I upgraded my Ubuntu to 10.10 and something went wrong with GRUB (see my postings under user --- virsto **Upgrade to 10.10 --- grub_xputs**.

Now, I never get a screen that allows me to choose the system to boot to --- I automatically boot to Windows Vista. How can I recover the ability to boot to my Ubuntu 10.10 (or earlier installations)?

There are instructions on the first page of this topic.

---

### Post by kbitz23 on 2011-06-13
Well i've managed to recover Windows 7 to some extent.  The windows bootloader is now showing up, which lists Windows 7 twice and Ubuntu once. 

With that said, I still cannot get into Ubuntu 11.04.  Whenever I try to reinstall Grub 2 using your instructions I end up where I started in my first post (about 4 posts back).  Why can't I make my MBR happy??

Can anyone help?  Much appreciated, I miss my Ubuntu!

---

### Post by Cerulean Starlight on 2011-06-21
> **talsemgeest said:**
> To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download for [Vista]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download") or [Win 7](http://neosmart.net/blog/2009/windows-7-system-repair-discs/).The former link has no download.
Until recently, my computer was a Vista/Linux dual-boot. I formatted my Linux partition, so GRUB is now telling me "error: no such partition."
How can I uninstall GRUB and replace it with the normal Vista bootloader when I have no Vista recovery DVD?

---

### Post by drs305 on 2011-06-21
> **Cerulean Starlight said:**
> How can I uninstall GRUB and replace it with the normal Vista bootloader when I have no Vista recovery DVD?

If your Windows boot files are still intact and all you have to do is tell the MBR where your Windows boot files are located, you can do this from the Ubuntu LiveCD. In the instructions, it's assumed your Windows OS is on 'sda'. If not, change it to the proper drive.
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Just run the two commands. Disregard the messages that you need to complete lilo configuration.

If the BIOS boots the drive in the command, the boot flag is on your Windows partition, and the Windows boot files are intact this should revert the boot process back to the Windows bootloader.

---

### Post by theTemest on 2011-06-22
> **talsemgeest said:**
> 

[SIZE=5][COLOR=red]How to restore the Windows Vista or 7 bootloader[/COLOR][/SIZE]

.....On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the following: ".....


I second the "Thank you", extended by Mspirit on May 17th, to **talsemgeest **and ubuntuforums for making this clear and concise tutorial available. Kind of funny that an issue in the wheelhouse of Windows 7 was best addressed in a Linux forum.:confused:

I do have one question just out of morbid curiosity. In capital letters **talsemgeest **instructs that the selected (highlighted) Windows 7 OS be UNSELECTED before proceeding with the command prompt (command line). Why was it necessary to do that? No great rush for an answer, just curious.

---

### Post by nash_p on 2011-06-27
i have installed windows 7 and ubuntu 11.04. After running kaspersky virus removal tool and restart the computer i got a message 
"error:no such partition
grub rescue>"
so i followed the instructions given here and got a error saying 
"/media/sda1/boot/grub/stage1 not read correctly"

also my Ubuntu partition is no longer shown in the disk utility.
 please help with this

---

### Post by rickyLOLZ on 2011-06-28
I don't know what's a bootloader... But OK. :popcorn:

---

### Post by AngelFox on 2011-07-01
Thank you so Much <3 Ok I know this topic is old

But it helped me out so much so I done something silly and really missed up my pc and I was scared I had to format and lose all my stuff (not backed up) I was so close to crying :( but thanks to this topic am so happy :D



<3 I love this site & Ubuntu & the users ^.^


-Fox

---

### Post by hero2 on 2011-07-05
Hi!

I am hereby moving the discussion of this post to this new thread: 
[http://ubuntuforums.org/showthread.php?p=11027252](http://ubuntuforums.org/showthread.php?p=11027252) 
So don't comment here.

- Hero2


This thread looks like what I need, but the command "sudo fdisk -l" gives the following output:


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2b987600

   Device Boot      Start          End       Blocks      Id   System
/dev/sda1               1            1567    12586896   27  Unknown
/dev/sda2   *        1568         1580      104422+   7  HPFS/NTFS
/dev/sda3            1581        11158    76929562+   7  HPFS/NTFS
/dev/sda4           11158       30402   154575873    f  W95 Ext'd (LBA)
/dev/sda5           17792       30402   101289984    7  HPFS/NTFS

Disk /dev/sdb: 4011 MB, 4011851776 bytes
88 heads, 24 sectors/track, 3710 cylinders
Units = cylinders of 2112 * 512 = 1081344 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           4        3711     3913792    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 


BUT as you can see, there is no "Linux"-partition, so what do I do?

Additional info:

It's an Acer netbook, originally with Windows 7 Starter (and a recovery-partition!), later I split the windows partition and recently I installed ubuntu 10.04.2. 
On the boot-menu, beside Linux, there is "Windows Vista" and "Windows 7", and unfortunately I wanted to try "Vista". This started the backup/restore program called "*Acer eRecovery Management*", and although I did NOT ask it to do anything before terminating it, it has destroyed the Ubuntu booter, so when I try to boot the machine, I get this message:

[B]"error: no such partition 
  grub rescue>"[/B]

The "/dev/sdb: 4011 MB" above is a USB-memory stick I am booting from, to run the terminal.

Can anyone help me, please?

---

### Post by Rog 3236 on 2011-07-05
[SIZE=2]I attempted the procedure provided by talsemgeest on my dual boot Windows 7 Home Edition/ Linux Mint. I had to reset my Windoze mbr after a fault thus losing my dual boot capability.

I loaded a mini Linux distro in order to use a terminal to execute the sudo commands which all were taken with no problems. After I hit enter to complete the procedure my monitor screen gave a message "input not supported". When I rebooted I got a screen saying "Welcome to Grub!" followed by no boot module found press any key to continue. I eventually after a number of tries managed to boot my Windows Recovery CD and fix my mbr to again boot into windows.

Bottom line is although the procedure looked good it certainly didn't work for me at all. I must have missed something along the way. Anyway, I had hoped I would not have to do a complete reinstall of Mint which it appears I may have to do. Bummer!![/SIZE]

---

### Post by YannBuntu on 2011-07-14
**@talsemgeest :** there is now a very simple way to reinstall GRUB2:

1) Install Boot-Repair

[HTML]sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair-ubuntu[/HTML]

2) Run it via System->Administration->Boot-repair or :

[HTML]gksu boot-repair[/HTML]


[IMG]http://pix.toile-libre.org/upload/original/1306401412.png[/IMG]

More information on : [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Enjoy ! :P

---

### Post by XProflmfao on 2011-07-17
Thank you so much!!!! I immediately now see my hard drive on the desktop of my ubuntu 10.10 live cd! thanks so much, still haven't tested to see if my computer will now boot up correctly... i'll update later...

EDIT: ...and it works! Thank you very much!!!! I bow down to your wisdom... [-o<

UPDATE: For some reason when i boot up, libcrypt says that there is no /dev/sda7, it takes half a minute before ubuntu starts booting up, also i am wondering if i can boot from an extended drive since I have two different ubuntu versions in a single extended partition?

---

### Post by Honzacz on 2011-07-17
Thanks for all advices here, but so long I managed only to repair my Win 7.
I Tried Boot repair (I started it on usb-stick linux), but in menu where i choose system I found only one (probably one from stick??). But there wasnt mentioned "system you are currenty running" as it is here on screenshot.
After running Boot repair and restarting there is still same error.

I tried to install ubuntu first from windows installer, after that booting from usb and in the end i booted to live ubuntum, from which i installed it. None of those helped, only it crushes windows booting.

Any idea what to do??:confused:
Machine is HP Tc 4200.

---

### Post by YannBuntu on 2011-07-18
Hi

> **XProflmfao said:**
> when i boot up, libcrypt says that there is no /dev/sda7, it takes half a minute before ubuntu starts booting up, also i am wondering if i can boot from an extended drive since I have two different ubuntu versions in a single extended partition?

Yes 2 Ubuntu versions in a single extended partition should be ok (this is what I am using now).
I have no idea for the "libcrypt" error you get, please create a new thread for this.


> **Honzacz said:**
> I Tried Boot repair (I started it on usb-stick linux), but in menu where i choose system I found only one (probably one from stick??). But there wasnt mentioned "system you are currenty running" as it is here on screenshot.

This is normal : "system you are currenty running" does not appear when you run Boot-repair from a live-USB or live-CD. 


> **Honzacz said:**
> After running Boot repair and restarting there is still same error.

Please open a new thread describing the error message, and giving the output of BootInfoScript ([https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)).

---

### Post by rahulkale on 2011-07-19
hey hi guys, 
If I have created 3 drives /boot  /swap  and  / (root)

and i try to boot it goes directly to Xp..

So should I install the bootloader in /(root) directl ???

---

### Post by YannBuntu on 2011-07-19
> **rahulkale said:**
> hey hi guys, 
If I have created 3 drives /boot  /swap  and  / (root)

and i try to boot it goes directly to Xp..

So should I install the bootloader in /(root) directl ???


Hi
Try pressing Shift key just after BIOS screen and before it boots in Xp.

Also you should redo your installation, as separate /boot is not necessary and /swap mount point does not exist (or maybe you meant you just created a swap partition). Which installation tutorial did you follow ?  --> please open a new thread for this.

---

### Post by NamiJason on 2011-08-06
deleted

---

### Post by slc1185 on 2011-08-09
1. For all intensive purposes we can assume I'm completely new to Linux based OSes

2. I'm also new to this Ubuntu Forum and am really sorry if i'm posting in the wrong place

3. My issue: I was trying to clean up my Dell Inspiron 1545 (getting rid  of my Kubuntu and Windows partition, reinstalling Windows). I was using  GParted to do the job and had just finished wiping Windows and Kubuntu  and reformatting. Was ready to exit and reinstall Windows when curiosity  got the best of me and I started wondering what would happen if I  deleted the 100mb system reserved partition. Well, that was a bad idea.

4. I can no longer access BIOS, I can't boot off of my Windows7 install.  disc, most of these actions result in a terminal-like environment:

error: no such partition.
grub rescue>

My GParted disc, however, is still entirely useful...?

5. I'm a tad confused and would be very appreciative of a solution, or at the least, an explanation.

Thank You.

---

### Post by drs305 on 2011-08-09
> **slc1185 said:**
> 

error: no such partition.
grub rescue>

My GParted disc, however, is still entirely useful...?

5. I'm a tad confused and would be very appreciative of a solution, or at the least, an explanation.


The MBR is looking for your previous Grub2 files and can no longer find them, since the partition it's looking for no longer exists.

I'm not sure what partitions you may still have on your drive (if any). If you still have one or more, please boot the Ubuntu LiveCD, then download/extract/run the boot info script. It will give us a good overview of (what's left of) your system:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by slc1185 on 2011-08-09
soo..this is embarrassing....I couldnt boot to my Windows7 disc....because the disc i stuck in wasnt actually the right disc. Put the right one in and things ran beautifully. whoops, thanks for your time, patience, and response!

---

### Post by COKEDUDE on 2011-09-11
```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```

Does this step require internet activity? I am trying to help a friend that is a long way away on an old laptop that does not have internet connectivity.

---

### Post by holyskeleton on 2011-09-12
> **talsemgeest said:**
> When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

```
bootrec.exe /fixboot
``````
bootrec.exe /fixmbr
```Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader.

This saved me from a reinstall. Thank you.

---

### Post by drs305 on 2011-09-12
> **COKEDUDE said:**
> ```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```

Does this step require internet activity? I am trying to help a friend that is a long way away on an old laptop that does not have internet connectivity.

It should run without an Internet connection provided the normal Grub 2 files are on the disk. (The packages don't have to be in /var/cache/apt/archives)

---

### Post by Despotism on 2011-09-14
I had tested Ubuntu 11.04 on a Laptop that also had Windows 7 installed first and I no longer needed Ubuntu. I loaded up Win7 and used dos commands to recover the 50gb pretty easy, but after a reboot I got the "Grub Rescue>" prompt.

A quick search found this thread, but what took a little while was finding a free rescue CD. The links in the OP point to a site which no longer distribute the CD for free, it costs $10 just to download one. Here are the rescue CD's from a site which still has them legally and free for all to get.

Windows 7 64Bit - Rescue CD - (This one worked for me as I had Win7 64B installed)
[Thread]("http://digiex.net/downloads/download-center-2-0/applications/2660-windows-7-64-bit-x64-recovery-disc.html") - [Download]("http://digiex.net/attachments/downloads/download-center-2-0/applications/3056d1255891654-windows-7-64-bit-x64-recovery-disc-windows-7-64-bit-repair-disc.zip")

Windows 7 32Bit - Rescue CD
[Thread]("http://digiex.net/downloads/download-center-2-0/applications/2659-windows-7-32-bit-x86-recovery-disc.html") - [Download]("http://digiex.net/attachments/downloads/download-center-2-0/applications/3055d1255890482-windows-7-32-bit-x86-recovery-disc-windows-7-32-bit-repair-disc.zip")

Windows Vista 64Bit - Rescue CD
[Thread]("http://digiex.net/downloads/download-center-2-0/applications/957-windows-vista-64-bit-x64-recovery-disc.html") - [Download]("http://digiex.net/attachments/applications/1178d1231979698-windows-vista-64-bit-x64-recovery-disc-windows-vista-x64-recovery-disc.zip")

Windows Vista 32Bit - Rescue CD
[Thread]("http://digiex.net/downloads/download-center-2-0/applications/956-windows-vista-32-bit-x86-recovery-disc.html") - [Download]("http://digiex.net/attachments/applications/1177d1231978419-windows-vista-32-bit-x86-recovery-disc-vista_recovery_disc.zip")

Usage is exactly as the OP Described but these CD's are 160mb, can be loaded onto a Flash Drive even.

Don't worry Ubuntunian's I dedicated a Duel Core 4GB RAM to a Media Center with 8TB of Harddrive space setup as a Hotswap RAID 5 NAS Storage for Ubuntu. I just didn't want Ubuntu on my Work laptop.

---

### Post by RpDn on 2011-09-17
Edited.   Seemed to have fixed my prob.
Your reply was too fast for me... drs305.
(Now I can't undo my edit.
update-grub did fix my partition parameters 'permanently' in grub.
Thanks for the response though ;))

---

### Post by drs305 on 2011-09-17
RpDn,

The update-grub command should find the new partition scheme if you are running the OS and not the LiveCD. 

If it doesn't, please open your own thread and post the contents of RESULTS.txt  That file is generated by the boot info script - click the BIS link in my signature line.

There is also the Boot Repair Tool, which may fix it and also has the ability to help you run the Boot Info Script:
[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by RpDn on 2011-09-17
Sorry I edited my post, deleted problem scenario away... hoped nobody would be fast enough to reply.  Thanks anyway.  That'll teach me to change the order of my partitions though... update-grub (at some point) seems to have fixed the drive/partition pointers.  Boot Repair Tool looks interesting too... thanks.

---

### Post by dariusdwtt on 2011-10-28
Hope I'm not repeating something, that someone else already said, but I  thought it would be of value to mention, that if you have Win 7 or XP,  on the same PC and it will boot, you could use [grud24dos.]("http://sourceforge.net/projects/grub24dos/")

Install it on the MS OS and then you will have a "virtual grub", that  you can use to boot into any other OS that you lost, and then follow the  usual procedures to restore grub from your other OS.

No need to boot from any other media.
No need to write to the mbr.
No need to burn discs.
No need to download isos.
Grub will be compatible.

and I'm sure there are a bunch of other good reasons.

---

### Post by jwmaddox on 2011-11-05
Greetings all,

I recently installed Ubuntu 11.04 and subsequently upgraded to 11.10 via the standard updates.  I am experiencing the following error when I turn on my laptop, after the initial "hp" screen:
[COLOR=DarkSlateBlue]error: no such device: badb25c6-b285-4b00-47e-68bc69ee3668
grub rescue>[/COLOR]
The badb25c6... is a UUID.

I can bypass this and get to the GRUB2 boot menu by holding "Shift", as was suggested in one post I found, and this actually works for me, usually after at least two attempts.  But this is a little inconvenient, and I'd rather be able to just boot Ubuntu without having to do this.  I have looked around a good deal on the fora and many people have indeed run into a similar situation with "grub rescue".  The initial post to this thread offers a simple solution in fact, but I'm still a very green Ubuntu user, and am not sure if it applies to my situation exactly, and I don't want to try something that will mess up the system since I can at least use it now, so I thought I'd ask the user community.

So, this is what I think I need to do:
Enter the following commands from a CD boot (the "Try Ubuntu" option):
[COLOR=DarkSlateBlue]sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
sudo grub-install --root-directory=/media/sdb1 /dev/sdb[/COLOR]

The above commands are based on the first post to this thread and my understanding of how my system is structured.  The system information is posted below for your consideration.

Using the fdisk command:
```

Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x58b1cbf9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    16390079     8195008+   7  HPFS/NTFS/exFAT
/dev/sda2        16390080   117195119    50402520    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00067125

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      503807      250880   83  Linux
/dev/sdb2          505854  1953517567   976505857    5  Extended
/dev/sdb5          505856     4409343     1951744   82  Linux swap / Solaris
/dev/sdb6         4411392    23941119     9764864   83  Linux
/dev/sdb7        23943168  1953517567   964787200   83  Linux

Disk /dev/mapper/cryptswap1: 1998 MB, 1998585856 bytes
255 heads, 63 sectors/track, 242 cylinders, total 3903488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0e66f6ad

```

Using the df -h command:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb6             9.2G  3.2G  5.6G  36% /
udev                  488M  4.0K  488M   1% /dev
tmpfs                 199M  848K  198M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  497M  188K  497M   1% /run/shm
/dev/sdb1             230M   56M  163M  26% /boot
/dev/sdb7             906G  476M  860G   1% /home
/home/james/.Private  906G  476M  860G   1% /home/james

```

Using the blkid command:
```

/dev/sda1: UUID="528CEC848CEC63C7" TYPE="ntfs" 
/dev/sda2: UUID="7684EB4884EB0A07" TYPE="ntfs" 
/dev/sdb1: UUID="badb25c6-b286-4b00-947e-68bc69ee3668" TYPE="ext2" 
/dev/sdb6: UUID="ebfe821d-062d-40ab-b2b5-1767fabc3a14" TYPE="ext4" 
/dev/sdb7: UUID="d6d9f94a-3812-4a35-bf73-b6edf4a2430a" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="47fd01bc-cd22-4946-a440-8b8e67fd7f81" TYPE="swap"

```

And, finally, using the mount | column -t (if memory serves) command:
```

/dev/sdb6             on  /                         type  ext4                   (rw,errors=remount-ro,commit=0)
proc                  on  /proc                     type  proc                   (rw,noexec,nosuid,nodev)
sysfs                 on  /sys                      type  sysfs                  (rw,noexec,nosuid,nodev)
fusectl               on  /sys/fs/fuse/connections  type  fusectl                (rw)
none                  on  /sys/kernel/debug         type  debugfs                (rw)
none                  on  /sys/kernel/security      type  securityfs             (rw)
udev                  on  /dev                      type  devtmpfs               (rw,mode=0755)
devpts                on  /dev/pts                  type  devpts                 (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs                 on  /run                      type  tmpfs                  (rw,noexec,nosuid,size=10%,mode=0755)
none                  on  /run/lock                 type  tmpfs                  (rw,noexec,nosuid,nodev,size=5242880)
none                  on  /run/shm                  type  tmpfs                  (rw,nosuid,nodev)
/dev/sdb1             on  /boot                     type  ext2                   (rw)
/dev/sdb7             on  /home                     type  ext4                   (rw,commit=0)
binfmt_misc           on  /proc/sys/fs/binfmt_misc  type  binfmt_misc            (rw,noexec,nosuid,nodev)
/home/james/.Private  on  /home/james               type  ecryptfs               (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=29915eb965aaf1b8,ecryptfs_fnek_sig=d5aca81cbf441900)
gvfs-fuse-daemon      on  /home/james/.gvfs         type  fuse.gvfs-fuse-daemon  (rw,nosuid,nodev,user=james)

```

Rather than try the commands I mentioned above and have it create more problems, I prefer to ask for confirmation.  Could someone please advise if my approach is the right thing to attempt?

Thanks folks,
James

---

### Post by drs305 on 2011-11-05
> **jwmaddox said:**
> 
rather than try the commands i mentioned above and have it create more problems, i prefer to ask for confirmation.  Could someone please advise if my approach is the right thing to attempt?


It appears you have a separate /boot partition on sdb1 and your main partition on sdb6.

If that is the situation, run can just run these commands:
```

sudo mount /dev/sdb6 /mnt
sudo mount /dev/sdb1 /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sdb
sudo umount /dev/sdb1 
sudo umount /dev/sdb6
```

Then make sure your BIOS is set to boot the sdb drive first.

---

### Post by jwmaddox on 2011-11-05
drs305,

Is it possible to run these commands from a terminal within my installed Ubuntu (the one on sdb), or must I run them from a CD after selecting the "Try Ubuntu" option?

Thanks,
James

---

### Post by drs305 on 2011-11-05
If you are already 'on' the Ubuntu OS you want to use as the default, all you have to do is run the following to get the correct Ubuntu to have the controlling Grub 2:
```

sudo grub-install /dev/sdX
```
with X being the drive letter (sda, sdb, etc).

If you are able to boot into your desired Ubuntu, but want to repair the UUID boot problem, you should be able to fix it by running:
```
sudo update-grub
```
This command should reread your partitions and rewrite the Grub configuration files to assign the correct UUIDs to your OS's.

---

### Post by jwmaddox on 2011-11-05
drs305,

I executed the two latest commands (grub-install and grub-update) in succession from within the installed Ubuntu OS, and now the Ubuntu boot proceeds correctly. However, XP was the original OS and is still on there, and I want to be able to choose XP when necessary, but have Ubuntu as the default.  I looked for the XP option on the GRUB2 boot menu which I accessed by pressing Esc when the screen displayed "GRUB Loading stage1.5", below which there is a message with a countdown to a default selection of the OS to boot.  The only options were for Ubuntu.  Note that previously, for what it is worth, when the "grub rescue" problem occurred, "Shifting out" of the initial screen did take me to a GRUB menu that included both the Ubuntu OS and the XP OS options.  How might I get GRUB2 to "see" XP so that I can choose it if I need to?

Thanks,
James

---

### Post by drs305 on 2011-11-06
@ jwmaddox,

If you are getting a "Grub loading 1.5" message you are most likely still using Grub legacy. Please download/run the boot info script from the following link. It will generate a RESULTS.txt file. 

Post the contents of RESULTS.txt here, between 'code' tags which you can generate by pressing the # icon in the message's menubar. The script provides us with a detailed view of your boot file status and setup.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by jwmaddox on 2011-11-06
drs305,

As requested:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid badb25c6-b286-4b00-947e-68bc69ee3668 root 
    set 
    prefix=($root)/grub--------------------------------------------------------
    ------------------------.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on the 
    same drive in partition #1 for /grub/stage2 and /grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /ntdetect.com

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.cfg /grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    16,390,079    16,390,017   7 NTFS / exFAT / HPFS
/dev/sda2          16,390,080   117,195,119   100,805,040   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       503,807       501,760  83 Linux
/dev/sdb2             505,854 1,953,517,567 1,953,011,714   5 Extended
/dev/sdb5             505,856     4,409,343     3,903,488  82 Linux swap / Solaris
/dev/sdb6           4,411,392    23,941,119    19,529,728  83 Linux
/dev/sdb7          23,943,168 1,953,517,567 1,929,574,400  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 89e01b53-9b3e-449d-a934-ddc12cebed51   swap       
/dev/sda1        528CEC848CEC63C7                       ntfs       
/dev/sda2        7684EB4884EB0A07                       ntfs       
/dev/sdb1        badb25c6-b286-4b00-947e-68bc69ee3668   ext2       
/dev/sdb6        ebfe821d-062d-40ab-b2b5-1767fabc3a14   ext4       
/dev/sdb7        d6d9f94a-3812-4a35-bf73-b6edf4a2430a   ext4       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /boot                    ext2       (rw)
/dev/sdb6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb7        /home                    ext4       (rw,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]  
timeout=1  
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS  
[operating systems]  
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect  
C:\BOOTSECT.DAT="System Restore" /minint  
--------------------------------------------------------------------------------

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

============================= sdb1/grub/menu.lst: ==============================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=badb25c6-b286-4b00-947e-68bc69ee3668

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 11.10, kernel 3.0.0-12-generic
uuid        badb25c6-b286-4b00-947e-68bc69ee3668
kernel        /vmlinuz-3.0.0-12-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro quiet splash 
initrd        /initrd.img-3.0.0-12-generic
quiet

title        Ubuntu 11.10, kernel 3.0.0-12-generic (recovery mode)
uuid        badb25c6-b286-4b00-947e-68bc69ee3668
kernel        /vmlinuz-3.0.0-12-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro  single
initrd        /initrd.img-3.0.0-12-generic

title        Ubuntu 11.10, kernel 2.6.38-11-generic
uuid        badb25c6-b286-4b00-947e-68bc69ee3668
kernel        /vmlinuz-2.6.38-11-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro quiet splash 
initrd        /initrd.img-2.6.38-11-generic
quiet

title        Ubuntu 11.10, kernel 2.6.38-11-generic (recovery mode)
uuid        badb25c6-b286-4b00-947e-68bc69ee3668
kernel        /vmlinuz-2.6.38-11-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro  single
initrd        /initrd.img-2.6.38-11-generic

title        Chainload into GRUB 2
root        badb25c6-b286-4b00-947e-68bc69ee3668
kernel        /boot/grub/core.img

title        Ubuntu 11.10, memtest86+
uuid        badb25c6-b286-4b00-947e-68bc69ee3668
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

============================= sdb1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set=root ebfe821d-062d-40ab-b2b5-1767fabc3a14
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
    linux    /vmlinuz-3.0.0-12-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
    linux    /vmlinuz-2.6.38-11-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /vmlinuz-2.6.38-11-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-11-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 528CEC848CEC63C7
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 7684EB4884EB0A07
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  2
               =                grub/grub.cfg                                  1
               =                grub/menu.lst                                  1
               =                grub/stage2                                    2
               =                initrd.img-2.6.38-11-generic                  79
               =                initrd.img-3.0.0-12-generic                   84
               =                vmlinuz-2.6.38-11-generic                     19
               =                vmlinuz-3.0.0-12-generic                      19

=========================== sdb6/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=badb25c6-b286-4b00-947e-68bc69ee3668

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 11.10, kernel 3.0.0-12-generic
uuid        badb25c6-b286-4b00-947e-68bc69ee3668
kernel        /vmlinuz-3.0.0-12-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro quiet splash 
initrd        /initrd.img-3.0.0-12-generic
quiet

title        Ubuntu 11.10, kernel 3.0.0-12-generic (recovery mode)
uuid        badb25c6-b286-4b00-947e-68bc69ee3668
kernel        /vmlinuz-3.0.0-12-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro  single
initrd        /initrd.img-3.0.0-12-generic

title        Ubuntu 11.10, kernel 2.6.38-11-generic
uuid        badb25c6-b286-4b00-947e-68bc69ee3668
kernel        /vmlinuz-2.6.38-11-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro quiet splash 
initrd        /initrd.img-2.6.38-11-generic
quiet

title        Ubuntu 11.10, kernel 2.6.38-11-generic (recovery mode)
uuid        badb25c6-b286-4b00-947e-68bc69ee3668
kernel        /vmlinuz-2.6.38-11-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro  single
initrd        /initrd.img-2.6.38-11-generic

title        Chainload into GRUB 2
root        badb25c6-b286-4b00-947e-68bc69ee3668
kernel        /boot/grub/core.img

title        Ubuntu 11.10, memtest86+
uuid        badb25c6-b286-4b00-947e-68bc69ee3668
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sdb6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set=root ebfe821d-062d-40ab-b2b5-1767fabc3a14
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
    linux    /vmlinuz-3.0.0-12-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
    linux    /vmlinuz-2.6.38-11-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /vmlinuz-2.6.38-11-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-11-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 528CEC848CEC63C7
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 7684EB4884EB0A07
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 /               ext4    errors=remount-ro 0       1
/dev/sdb1       /boot           ext2    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=d6d9f94a-3812-4a35-bf73-b6edf4a2430a /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
#UUID=911e8316-1642-4547-ae98-104d3ed0c1e3 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             2
               =                boot/grub/grub.cfg                             1
               =                boot/grub/menu.lst                             1
               =                boot/grub/stage2                               2
               =                boot/initrd.img-2.6.38-11-generic             79
               =                boot/initrd.img-3.0.0-12-generic              84
               =                boot/vmlinuz-2.6.38-11-generic                19
               =                boot/vmlinuz-3.0.0-12-generic                 19
               =                initrd.img                                    84
               =                initrd.img.old                                79
               =                vmlinuz                                       19
               =                vmlinuz.old                                   19

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by drs305 on 2011-11-06
> **jwmaddox said:**
> How might I get GRUB2 to "see" XP so that I can choose it if I need to?

Currently you have Grub 2 on sda (60GB, Windows) and Grub Legacy on sdb (1000GB). Since you are seeing the 'Grub loading 1.5' message, we can assume that BIOS is booting the sdb drive first. 

Here is how I would configure your system.
1. Get rid of Grub legacy and install/use Grub 2 on the sdb drive.
2. After reinstalling Grub 2, make sure it includes the Windows option.
After G2 is working and you also can boot into Windows from the sdb drive:
3. Restore the Windows bootloader to sda to use as a backup if the sdb drive or Grub 2 fails.

1. Purge/Install
[LIST]
[*]Boot normally into Ubuntu.
[*]Check to make sure your Internet connection is working. If it isn't, stop here and let me know.
[*]```
sudo apt-get update
```
[*]Purge Grub legacy and Grub 2. You will be warned about needing a boot loader. Tab to OK or Yes and press ENTER.
[*]```
sudo apt-get purge grub-common grub grub-pc
```
[*]Install Grub 2 (installs grub-common, grub-pc, grub-gfxpayload-list
[*]```
sudo apt-get install grub-commmon grub-pc
```
[*]During the installation, you will be asked if you want to add any kernel options. Normally users don't need any. Tab to OK and press ENTER.
[*]You will be asked where to install Grub 2. Use the SPACEBAR to place an asterisk next to **sdb**. Remove any asterisks for sdb partitions (sdb6, etc) or sda. Tab to OK to continue.
[/LIST]
2. Update the Grub 2 Menu.
Update the grub menu and watch for Windows in the terminal output. This command should have been run during the installation, but it won't hurt to run it again:
```
sudo update-grub
```

Reboot and make sure Ubuntu and Windows both boot from the Grub 2 menu. If they both work:

3. Restore the Windows Bootloader to the sda MBR.
Partially install *lilo*, an alternative bootloader. Run only the two commands. Disregard messages stating lilo is not fully configured.
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
If the Windows files are intact, you should be able to change the BIOS boot order to boot sda and get the Windows menu when you boot. There will not be an Ubuntu option in the menu.

---

### Post by dez93_2000 on 2011-11-06
Hi. Sorry to add to an already massive thread. I hope that this hasn't been explicitly asked before - I've done some searching through a fair few pages of this thread, and also looked into the help on Boot Repair.

I upgraded to 11.10 but various problems occurred and ubuntu came crashing down over a period of days then didn't boot. I did an upgrade install which repaired it but messed lots up. My config is:
sda1: win XP bootable

sdb1: ubuntu
sdb2: extended
sdb5: swap

sdc1: ntfs files
sdd1: Win XP bootable (a 'just in case' xp install which i never ever boot to)
sde1: ntfs external drive.

But only the linux install on sdb is available on the GRUB menu. I've tried Boot Repair, to put grub on the other drives,  but no joy from that (equally, it didn't ruin everything which i half expected). I also tried using Boot Repair to repair mbr on sda using the sda (xp generic) option but that did nothing. My latest paste after Boot Repairing is: [http://paste.ubuntu.com/730175/](http://paste.ubuntu.com/730175/)

I'm concerned that an extant RAID config might be causing problems. I had the sda & sdb drives in a mirror RAID before I had ubuntu.

In short: should I just try to restore the windows MBRs using tip #16 from here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) ? [edit: this is drs305's option 3 above] Can I do this in GUI using Boot Repair instead? Should I do anything about the RAID bug ("[SIZE=1]dmraid -  wrong # of devices in RAID set")[/SIZE]?

Many thanks in advance!
Dez

---

### Post by jwmaddox on 2011-11-06
drs305,

I performed steps 1 and 2 successfully and now have the configuration that I wanted, namely, automatic listing of the GRUB2 menu with Ubuntu as the default selection but with the option to select XP if desired.  I see no reason to implement step 3 unless there is a technical reason I'm missing.  Thoughts?

Regards,
James

---

### Post by YannBuntu on 2011-11-06
@dez93_2000: Hello, your XP on sda1 is not seen by os-prober (GRUB), so reinstalling GRUB (this is what Boot-Repair does by default) will not change anything. I recommend you :
- first fix this problem via a XP rescue CD ( [http://www.vista-xp.fr/forum/topic240.html](http://www.vista-xp.fr/forum/topic240.html) ). Boot on it, choose the "Repair menu (R)" then type "fixmbr". Reboot with your BIOS booting on sda disk, you should get back access to your sda1 XP
- then use Boot-Repair's "Recommended repair" to reinstall GRUB, it should detect sda1's XP this time.

---

### Post by drs305 on 2011-11-06
> **jwmaddox said:**
> drs305,

I performed steps 1 and 2 successfully and now have the configuration that I wanted, namely, automatic listing of the GRUB2 menu with Ubuntu as the default selection but with the option to select XP if desired.  I see no reason to implement step 3 unless there is a technical reason I'm missing.  Thoughts?

1. You don't need to accomplish Step 3, and I never can find fault in leaving a working system alone. ;-)

2. You might just make a note of how to restore the Windows bootloader to the sda if you need it in the future. 

3. And finally, what is in sda's MBR at the moment is useless. You can run the following from your current installation to point sda's MBR to your working Grub 2 folder if you wish. In that case, if either sda or sdb is the boot drive your sdb Ubuntu should boot. Nothing will be harmed, and the BIOS is still set to boot sdb first. However, see paragraph #1.  
```
sudo grub-install /dev/sda
```

Happy Ubuntu-ing !

---

### Post by dez93_2000 on 2011-11-07
> **YannBuntu said:**
> @dez93_2000: Hello, your XP on sda1 is not seen by os-prober (GRUB), so reinstalling GRUB (this is what Boot-Repair does by default) will not change anything. I recommend you :
- first fix this problem via a XP rescue CD ( [http://www.vista-xp.fr/forum/topic240.html](http://www.vista-xp.fr/forum/topic240.html) ). Boot on it, choose the "Repair menu (R)" then type "fixmbr". Reboot with your BIOS booting on sda disk, you should get back access to your sda1 XP
- then use Boot-Repair's "Recommended repair" to reinstall GRUB, it should detect sda1's XP this time.

Nice, thanks! And I guess I do exactly the same for my windows install on sdd1 right?
Cheers Yann.

---

### Post by jwmaddox on 2011-11-07
drs305,

Ok.  I will make note of this for possible future use, but for the time being - "if it ain't broke, don't fix it".
Thank you for your help; I am grateful for your generous and prompt assistance with my Ubuntu concerns.
I am new to Ubuntu, but thus far am impressed both with the philosophy  behind the software and the nature of the support community.  It's nice  to be a part of it.

Regards,
James

---

### Post by YannBuntu on 2011-11-07
> **dez93_2000 said:**
> Nice, thanks! And I guess I do exactly the same for my windows install on sdd1 right?
Cheers Yann.

if it does not appear in the GRUB menu, yes.

---

### Post by dez93_2000 on 2011-11-07
Hmm. Fixed the mbr of one of the windows options (had d drive &f drive, choose option 1 for d and it said F:/windows after I remembered the password, and now it won't boot to grub.
Can I use boot repair from a live CD, somehow?

---

### Post by YannBuntu on 2011-11-07
If you can now boot to your Windows, yes you can reinstall GRUB via Boot-Repair (to use it from a live-CD, or get a CD including it, see [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) )

---

### Post by fattyz on 2011-11-08
:D:D:D:D:D

talsemgeest, thank GOD I found your post I have been screwing around with this for days!!!

Thanks Thanks Thanks!!!!

FattyZ

---

### Post by dez93_2000 on 2011-11-09
Hmm. I did the XP (R) mbr repair technique for both drives, which killed any bootloaders and i couldn't get into my system. Then i made a boot-repair boot disc from my girlfriend's laptop and did a repair, amnd now i'm back where i started, i.e. with ubuntu but no windows options.

Which is definitely better than no OS at all!

Any further ideas / tips?

---

### Post by YannBuntu on 2011-11-09
> **dez93_2000 said:**
> I did the XP (R) mbr repair technique for both drives, which killed any bootloaders and i couldn't get into my system.

This looks to be a Windows problem only. I suggest to ask on Windows forums how to use the XP rescue CD in order to repair XP. When this is done, you will just have to reinstall GRUB (via Boot-Repair or else) to get back access to both XP and Ubuntu.

---

### Post by dez93_2000 on 2011-11-09
> **YannBuntu said:**
> This looks to be a Windows problem only. I suggest to ask on Windows forums how to use the XP rescue CD in order to repair XP.

True, but a windows problem caused by ubuntu. Anyway, I tried an XP repair using the disc [http://www.techspot.com/vb/topic8356.html](http://www.techspot.com/vb/topic8356.html) however I can't because the disk says " ["this disk does not contain a windows-compatible partition"]("http://www.tomshardware.co.uk/s/this-disk-does-not-contain-a-windows-compatible-partition") . I'm now looking through windows forums trying to work out what ubuntu install or repair or boot-repair has done to the windows installs whereby they no longer are recognised or work. Any ideas appreciated. So much work just because i clicked "update to 11.10"...

Unplugging the ubuntu drive so windows it the first (which it already was, but just in case) didn't help. Indeed it meant that the windows boot disc wouldn't run, and i ended up at the grub rescue prompt. God only knows what's going on.

---

### Post by loumakas on 2011-11-14
I have a dual boot netbook (Ubuntu and Windows XP). I upgraded from Ubuntu 11.04 to 11.10 and even though my Ubuntu installation works fine, I cannot boot into my Windows XP installation anymore. I get a message: "<Windows root>\system32\hal.dll is corrupted or missing". After spending two days on trying several things, I realized that **the drive letter on my Windows partition has changed from D: (which is the correct one) to C:**, so I am guessing this is the reason hal.dll cannot be found, although it is right there (I can see all files in my Windows partition when I boot into Ubuntu). I even booted the machine with the XP recovery CD and that brings me to C:>WINDOWS, instead of the correct D:>WINDOWS. 

When I run fixboot I get the following message: 

FIXBOOT cannot find the system drive, or the drive specified is not valid. 

I guess this is related to the problem with the drive letter mentioned above. 

I am not sure if it makes sense to run fixmbr without running fixboot first. 

I am looking into ways to bring back the drive letter to D:, but I don't see how this can be done from outside (dos or ubuntu). Before experimenting further, I wanted to ask in case there is a good suggestion on what to do. 

Thank you in advance!

To provide a better picture of my system to the experts, here is the output of bootinfoscript (you can ignore /dev/sdb - it is a USB flash I forgot plugged in):

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>..............0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1438376 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 16.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,046    29,300,735    29,298,690   5 Extended
/dev/sda5               2,048    27,222,015    27,219,968  83 Linux
/dev/sda6          27,224,064    29,300,735     2,076,672  82 Linux swap / Solaris
/dev/sda2         167,750,730   312,496,379   144,745,650   7 NTFS / exFAT / HPFS
/dev/sda3         312,496,380   312,576,704        80,325  ef EFI (FAT-12/16/32)
/dev/sda4          29,302,560   167,750,729   138,448,170  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4072 MB, 4072669184 bytes
4 heads, 16 sectors/track, 124288 cylinders, total 7954432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             16     7,954,431     7,954,416   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        D02839C92839AF7A                       ntfs       
/dev/sda4        076b6d89-df98-46b5-a1f1-205f994b05f7   ext4       
/dev/sda5        a43c9d6c-bd40-4ade-ba84-57283a5bfdbb   ext4       
/dev/sda6        6e0cb0cb-7b42-4a0c-8960-8cb5bd1549c2   swap       
/dev/sdb1        57B8-83AA                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda4        /home                    ext4       (rw,commit=0)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/57B8-83AA         vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root a43c9d6c-bd40-4ade-ba84-57283a5bfdbb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root a43c9d6c-bd40-4ade-ba84-57283a5bfdbb
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root a43c9d6c-bd40-4ade-ba84-57283a5bfdbb
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a43c9d6c-bd40-4ade-ba84-57283a5bfdbb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root a43c9d6c-bd40-4ade-ba84-57283a5bfdbb
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a43c9d6c-bd40-4ade-ba84-57283a5bfdbb ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root a43c9d6c-bd40-4ade-ba84-57283a5bfdbb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root a43c9d6c-bd40-4ade-ba84-57283a5bfdbb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home English (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root D02839C92839AF7A
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a43c9d6c-bd40-4ade-ba84-57283a5bfdbb /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=076b6d89-df98-46b5-a1f1-205f994b05f7 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=6e0cb0cb-7b42-4a0c-8960-8cb5bd1549c2 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.223697662 = 2.387677184    boot/grub/core.img                             1
   4.499130249 = 4.830904320    boot/grub/grub.cfg                             1
   5.076156616 = 5.450481664    boot/initrd.img-3.0.0-12-generic               1
   2.209365845 = 2.372288512    boot/vmlinuz-3.0.0-12-generic                  1
   5.076156616 = 5.450481664    initrd.img                                     1
   2.209365845 = 2.372288512    vmlinuz                                        1

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home English" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

To be able to see for which directory Grub2 (v1.99) looks for, install "unlzma".

```

---

### Post by loumakas on 2011-11-17
Solution: I had to change partition(2) to partition(1) in the boot.ini  file because my NTFS partition from inside Windows was seen as  PARTITION1 now, as opposed to PARTITION2 before. Everything worked fine  after that! Windows booted correctly and the drive letter is still D!

---

### Post by jwmaddox on 2011-11-18
drs305,

It has been a few weeks now since I implemented your suggestions.  I had thought that all was well, but I must have tested the reboot with restart rather than a full shutdown and power off, because I have noticed the following: every time I turn the laptop on from a full shutdown, the "grub rescue" prompt appears with the same error as before (cannot find a UUID).  If I power off, then power on, it goes straight to the GRUB2 menu, which is what I want it to do.  This is not so bad really - better than having to hold Shift, but a normal boot would be nice.  I have read somewhere that "grub rescue" is loaded when the previous shutdown did not occur properly, so perhaps there's something there in my situation, although I don't do anything unusual when I shutdown the laptop.  Any ideas?

Regards,
James

---

### Post by drs305 on 2011-11-19
> **jwmaddox said:**
> I have read somewhere that "grub rescue" is loaded when the previous shutdown did not occur properly, so perhaps there's something there in my situation, although I don't do anything unusual when I shutdown the laptop.  Any ideas?

You might try using YannBuntu's Boot Repair app to see if that fixes things. If it solves it you could state so here. Otherwise... 

I had a response typed out but it might be better for everyone for you to start a separate thread. Restate the cold boot/warm boot issue and provide an updated copy of RESULTS.txt

Provide a link to the new post here for anyone who is following your issue.

---

### Post by dez93_2000 on 2011-11-22
Hi all.
Separately to this discussion my ubuntu install is giving me constant headaches so i'm going to fresh install with liveCD. My plan was to
1. Do more research to try to find out how to repair my now-unbooting XP installs
2. Unplug my ubuntu drive and repair the XP drives in turn
3. Unplug my XP drives and plug in my ubuntu drive and wipe then install 11.10 from liceCD
4. Plug the XP drives back in... and run boot repair to get them to be recognised?

Could anyone please let me know if i'm going to be going about this the wrong way, relative especially to the grub install. The liveCD install will setup grub as default right? Would it be better to have the XP drives plugged in when i install ubuntu, in case they're added to the boot list from the start?

Thanks
dez

---

### Post by drs305 on 2011-11-22
> **dez93_2000 said:**
> Hi all.
Separately to this discussion my ubuntu install is giving me constant headaches so i'm going to fresh install with liveCD. My plan was to
1. Do more research to try to find out how to repair my now-unbooting XP installs
2. Unplug my ubuntu drive and repair the XP drives in turn
3. Unplug my XP drives and plug in my ubuntu drive and wipe then install 11.10 from liceCD
4. Plug the XP drives back in... and run boot repair to get them to be recognised?

Could anyone please let me know if i'm going to be going about this the wrong way, relative especially to the grub install. The liveCD install will setup grub as default right? Would it be better to have the XP drives plugged in when i install ubuntu, in case they're added to the boot list from the start?

Thanks
dez

I'd agree with your plan up to Step 4. 

Getting Windows to boot independently of Grub is always a good idea; it eliminates a lot of variables and it is much easier to work trying to fix Grub than it is to do the same with Windows.

Once you have completed Step 3, you really shouldn't need to use Boot Repair. After connecting the Windows drive, you should be able to boot into Ubuntu and just run "sudo update-grub". Grub should find your Windows installation and add it to the Grub 2 menu. Hopefully Boot Repair won't be needed...

Also, I wouldn't use the "**lice**CD" - I've heard it is very buggy.  Sorry, I couldn't help it. ;-)

---

### Post by dez93_2000 on 2011-11-28
Cheers for this. All up & running now - the fresh install was a good idea, lots of problems seem to have disappeared. The liceCD worked well, although it's quite confusing... it certainly had me scratching my head a few times.

And on that note - hopefully i won't need to darken this thread again! Cheers guys.
dez

---

### Post by grubgy on 2011-11-29
Here's my story:

Had XP installed and Ubuntu next to it. Worked fine until I had to replace xp with 7. Grub was gone but I had printed this opening posting before to make sure I could recover grub.

I booted a live CD and went to the terminal:

**sudo fdisk -l** showed me that my Ubuntu installation sat on sda6

[B]sudo mkdir /media/sda6
sudo mount /dev/sda6 /media/sda6
sudo grub-install --root-directory=/media/sda6 /dev/sda[/B]

Don't know if the last /dev/sda is correct but the install seemed to work.

Rebooted the system and got a grub prompt instead of the boot menu which I expected. :confused:

Maybe I missed the point of this tutorial and I need to do more steps. I booted the live CD again (which I'm actually writing this post from) and checked the file system. In /boot/grub/ only these two files exist:
[B]/boot/grub/gfxblacklist.txt
/boot/grub/grubenv
[/B]
and this is how the boot directory looks:

[B]-rw-r--r-- 1 root root  734707 2011-10-07 20:37 abi-3.0.0-12-generic
-rw-r--r-- 1 root root  141616 2011-10-07 20:37 config-3.0.0-12-generic
drwxr-xr-x 1 root root      60 2011-11-29 06:55 grub
-rw-r--r-- 1 root root  176764 2011-05-02 22:53 memtest86+.bin
-rw-r--r-- 1 root root  178944 2011-05-02 22:53 memtest86+_multiboot.bin
-rw------- 1 root root 2130938 2011-10-07 20:37 System.map-3.0.0-12-generic
-rw------- 1 root root    1215 2011-10-07 20:40 vmcoreinfo-3.0.0-12-generic[/B]

I have no clue how to get my boot menu back...

Edit:
Browsed the system a little more and found on sda6 (Ubuntu system partition) that there is a boot/grub directory, too. It obviously contains the original grub files with menu.list and all. I'm a little confused now since I never really took a look under the hood. What's in my MBR now? I guess I 'only' have to make the system boot the old grub and change the setting in the menu from win xp to 7.

Edit2: Retried using this tutorial:
[http://www.lancelhoff.com/restore-grub2-after-installing-windows/](http://www.lancelhoff.com/restore-grub2-after-installing-windows/)
but received a [B]Your /usr is broken; please fix it before calling this wrapper!
[/B] message when calling grub-install.

---

### Post by drs305 on 2011-11-29
grubgy,

Welcome to the Ubuntu forums.

You are missing critical Ubuntu system files. In /boot you should have a kernel (vmlinuz-3.0.....) and initrd.img-3.0... 

Since these files are missing, Grub can't boot Ubuntu. You may have other critical system files missing as well, as indicated by the /usr messsage.

I would recommend starting your own thread. Boot the LiveCD and install Boot Repair. It probably can't fix your system, but you can run the boot info script from the app. Post the link it generates or the contents of RESULTS.txt. This file will give us a comprehensive look at the status of your boot files.

You can find a link to the Boot Repair thread in my signature line. Just provide us with a link to your new thread.

---

### Post by grubgy on 2011-11-29
Thx. Will do as you suggested once I'm back home.
One question though. I have one boot directory on sda6 and another one when booting the Live CD, opening a terminal and typing cd /boot. Is the latter just in RAM from the Live CD and not part of my problem?
Because the directory structure I've posted is the one from the Live CD terminal. The one existing on sda6 has many files and directories below sda6/boot/grub

---

### Post by drs305 on 2011-11-29
> **grubgy said:**
> Thx. Will do as you suggested once I'm back home.
One question though. I have one boot directory on sda6 and another one when booting the Live CD, opening a terminal and typing cd /boot. Is the latter just in RAM from the Live CD and not part of my problem?
Because the directory structure I've posted is the one from the Live CD terminal. The one existing on sda6 has many files and directories below sda6/boot/grub

To see the contents of your real /boot folder, you need to mount your Ubuntu partition, and then look at that content:```

sudo mount /dev/sda6 /mnt
ls /mnt/boot
```
So if you were actually reporting what you saw in /boot, those are the LiveCD's boot files.

Hopefully your kernel and initrd files really do exist, which would be expected unless you've done something odd. My recommendation remains the same - install Boot Repair. The only change to my previous post would be that Boot Repair has a good chance of working if your boot files really are on the Ubuntu partition. So give Boot Repair a chance to work, and it if doesn't start a new thread with the RESULTS.txt (or link).

---

### Post by grubgy on 2011-11-29
boot repaid did not help.
here is my new thread 
[http://ubuntuforums.org/showthread.php?p=11498767#post11498767](http://ubuntuforums.org/showthread.php?p=11498767#post11498767)

---

### Post by YannBuntu on 2011-11-29
Hello
Boot-Repair does not repair the system folders such as /usr, only the /boot and MBR. If I had this /usr problem, I would simply reinstall Ubuntu above the current Ubuntu partition, this will preserve your /home (there is an option for this in the 11.10 installer).

---

### Post by ak333 on 2011-12-10
i'm new to the forum and am not sure if this problem is already answered...
i had a dual boot on my laptop - windows7 was installed first then ubuntu.i wanted to switch back to only windows7 so i went to manage  storage on right clicking 'my computer' and deleted the volume space associated with ubuntu . when i restarted my laptop and only thing that appears on screen is grub rescue> prompt .i've no clue regarding booting nor other commands that are to be used. i tried commands suggested on various other threads that i could find regarding this but all the commands just display 'unknown command'.commands such as sudo , find etc aren't working.
when i typed 'ls' the only thing that was displayed was:
(hd0) (hd0,msdos1) (hd0,msdos2) (hd0,msdos1)

i'm completely clueless what i should do ? :( 

Unfortunately i don't know where i've put my windows installation cd nor my ubuntu cd . Is there anything i can do to get back to only windows7 ?
i would be grateful if someone could help.

---

### Post by mitul_45 on 2011-12-16
Great !!! Helped me a lot...exaccct Answer *thumbs up*

---

### Post by YannBuntu on 2011-12-16
@ak333: you can try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by super_nerd on 2012-02-09
Thank you so very much OP for this straghtforward and excellent tutorial! :D

My grub went down mysteriously like 20 minutes ago and after I found this thread I was able to fix grub in 5 minutes flat. Last time this happened to me a few years back, I did not know what grub was or how to use the linux terminal (or use Google to my advantage or think for myself:redface: lol) so I spent hours unnecessarily doing a fresh install. Just re-installing the grub was so much easier.

---

### Post by tommyleinen on 2012-02-12
Thanks from me too - most useful post i've used anywhere for ages.

For reference:

[IMG]http://i957.photobucket.com/albums/ae55/tommyleinen/tech%20public/IMG_20120212_215925.jpg[/IMG]


(I knocked the 5 off the end before hitting enter)

---

### Post by YannBuntu on 2012-02-12
For people who don't like command lines, here is a tool to repair GRUB in 1 click : [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[IMG]http://pix.toile-libre.org/upload/original/1322150524.png[/IMG]

---

### Post by anxolakos on 2012-02-23
Hello, this is my first post here!

I got hold of this Ubuntu 10.10/XP (FastTrak (Bios 1.00.0.37)
that was working but really slow, so I decided to format. Not having handled a dual system before, I followed a guide and erased the partitions from within XP interface, and then attempted to boot from the XP CD and attempt the formatting (wanted to format and install XP only) However, I got the GRUB error 22 message that everybody got. The real problem here, is that probably due to my partition involvement, neither the XP or the Ubuntu CD's can load, since it says there is no hard drive detected! Up until the partition deleting everything was fine, and in BIOS Primary IDE Master and Slave are not even detected. 

Did I kill it?

---

### Post by sirriffsalot on 2012-02-29
Mate, I am forever indebted to you. I literally had an orgasm in my chest when I saw that dual-boot screen appear again after countless encounters with the torturous "grub rescue". If the musical and literal material you saved is in any way successful, your Ubuntu forums name will be on the "thank you, big time" list, haha:)

Thanks a million! You basically saved about 100 hours worth of guitar riffs and whatnot. Silly me never taking backups.. Doing it right now though!!!

Peace!!

---

### Post by Petkus on 2012-04-22
> **talsemgeest said:**
> **[SIZE=6][COLOR=blue][/COLOR][/SIZE]**

[SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.10 and beyond)[/COLOR][/SIZE]

First you need to find out what your drives are called. You can do this by going to a terminal and typing: ```
sudo fdisk -l
```From that you need to find the device name of your Ubuntu drive, something like “/dev/sda5&#8243;.
 So, still in the terminal, type:
```

sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
```And then, to reinstall the grub: ```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```Push enter and you’re done! Of course you need to replace “/dev/sda5&#8243; and “/dev/sda” with what you found in the fdisk output.

[SIZE=5][COLOR=red][/COLOR][/SIZE].

HI!

I did this (without errors in terminal), but now after Ubuntu loading I get black screen. What I did wrong?

---

### Post by davidb89 on 2012-05-04
Man I registered to the forums specially to thank you. You saved my life and my windows. Thanks again.
David.

---

### Post by bookcrazy on 2012-05-12
> **YannBuntu said:**
> For people who don't like command lines, here is a tool to repair GRUB in 1 click : [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[IMG]http://pix.toile-libre.org/upload/original/1322150524.png[/IMG]

You are a Fricking Rock Star :guitar:

I installed 12.04 from a USB on my computer this morning and was getting GRUB Rescue. Thankfully I found your post and sorted this situation out in less than 10 minutes! 

Thank you thank you thank you!

---

### Post by RimSide on 2012-06-13
It's awesome that this has helped alot. I am going to be trying out above poster's quoted comment when I get home. I tried the dual boot but it showed up with the command line interface of grub, so I am going to try this.
 
I'll post back if it works!

---

### Post by dojida on 2012-06-26
Thank you so much for this how to, I tried a live cd to upgrade from 10.10 to 12.04 dual booted with XP and lost the grub screen with error 15. Luckily I stumbled upon this thread and using the live cd and terminal I am back in business. You're a star!

---

### Post by Elfy on 2012-06-29
This thread is closed. 
 
The information is now held on the community wiki at  [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
 
Thank you for your thread and the work you have done in keeping it current and of use to the community. 
 
A thread for discussion of the wiki can be found at  [http://ubuntuforums.org/showthread.php?t=2012409](http://ubuntuforums.org/showthread.php?t=2012409)
 
 
Support threads regarding the wiki and it's content should be created in a suitable forum.

---

