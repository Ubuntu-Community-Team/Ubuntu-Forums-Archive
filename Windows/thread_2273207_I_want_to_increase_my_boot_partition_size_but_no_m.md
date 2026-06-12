---
title: "I want to increase my boot partition size but no method is working"
date: 2015-04-11
forum: Windows
---

### Post by sarab2 on 2015-04-11
My boot partition when I installed ubuntu had some 244 MB . Now I wish to uninstall ubuntu and replace it with windows 7 .
I have windows 7 set up in a folder , and that folder includes the setup.exe , the starting point of windows installation. When I click it, it shows the start up screen of installation but soon says "error : minimum required space 683 MB required in boot directory for temporary files" 
The issue is I have a windows 7 installation cd but my cd drive is broken ! 
So I tried setting up a bootable usb but after repeated trial and error I reached nowhere . I have been trying since yesterday now to install win 7 and now my only hope is in increasing /boot size . 
So having searched all the threads and "SOLVED" solutions, I tried booting my PC with the installation usb I used for installing ubuntu 14.
but even in "try ubuntu" mode , it won't allow me to resize partitions with gparted . So I tried fresh install of ubuntu , and selected "something else" in installation screen , but even there the size is not modifiable of a partition. Its really confusing and frustrating because installing windows 7 shouldn't be such a terribly long ordeal.

So please tell me how do I resize my /boot to around 1GB so that I am finally able to install win 7 from my win 7 folder on ubuntu desktop .

thank you very much

---

### Post by coffeecat on 2015-04-11
I'm really mystified as to why Windows would want to use an Ubuntu boot partition. A /boot partition would be formatted ext2, unreadable by Windows.

Let's get some information.

Either from your installed Ubuntu or from "try Ubuntu" in the live session, open a terminal and post the output of this command:

```
sudo fdisk -lu
```

This will tell us your partition layout and may give us answers as to why you are seeing these issues. My hunch is that you have a LVM whole disk installation with a tiny 256 MB boot partition and the Windows installer is completely confused by this. The something else option in the Ubuntu installer wouldn't allow you to resize the LVM partition anyway.

Next question. Windows 7 setup in a folder? How does that work? Where is the folder? Also - do you believe the Windows USB installer is usable? The reason I ask is that it's possible the only way to proceed is to re-format the whole hard drive with Gparted in the Ubuntu installer, and then start afresh with the Windows USB installer. But let's see what the output of fdisk tells us.

---

### Post by grahammechanical on 2015-04-11
Here is your problem

> The issue is I have a windows 7 installation cd but my cd drive is broken !

 If you had a Windows 7 ISO image you could use Ubuntu to create a USB Windows 7 installer. But you do not have one of those, do you.?

> Its really confusing and frustrating because installing windows 7 shouldn't be such a terribly long ordeal.

It will not be a terribly long ordeal if you buy or borrow another DVD drive. I know that you do not want to hear that, but it is the truth.

Regards.

---

### Post by sarab2 on 2015-04-11
hi 
so I installed ubuntu again , completely wiping out previous installation. And yes I did manage to secure 2.5 GB for /boot directory
and after installing wine (because setup.exe of win 7 won't run directly on ubuntu) , 
but guess what, I am still having the issue, the very same error "atleast 683 MB needed for temporary files in boot directory 
I think its looking into boot directory of windows wine . isn't it ?

I did try writing iso to pendrive to make it bootable , but the "windows usb installer tool" said my iso ain't valid >_<

the same iso I made from the folder in which set up files were kept . It was 3.5 GB something 

Its almost 1 and a half days now I can't get my hands on anything, wanna go back to win 7 , all I have is a set up cd but no cd drive and I wanna save on some money bcoz  anyways who uses cd thesedays . most ppl use pendrive, so cd drive gonna stay useless for most part. 

Is there anyway out ? 

The thing is when I click on "setup.exe" it does show windows 7 installation screen , but soon gives error "error <code>: min space 683 mb needed for temp files" 

help me out please thank u :)

---

### Post by sarab2 on 2015-04-11
o/p of 
sudo fdisk -lu
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6a68

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      501757      249855   82  Linux swap / Solaris
/dev/sda2          501758   312580095   156039169    5  Extended
/dev/sda5          501760   312580095   156039168   8e  Linux LVM

Disk /dev/mapper/ubuntu--vg-root: 157.1 GB, 157106044928 bytes
255 heads, 63 sectors/track, 19100 cylinders, total 306847744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 2675 MB, 2675965952 bytes
255 heads, 63 sectors/track, 325 cylinders, total 5226496 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

---

### Post by sarab2 on 2015-04-11
now trying to download an iso image of win 7 from here 
[http://mirror.corenoc.de/digitalrivercontent.net/](http://mirror.corenoc.de/digitalrivercontent.net/)

god bless me , its gonna take friggin 12 hours -_-

edit ---
even thats not downloading

---

### Post by sarab2 on 2015-04-11
or if someone can do me a favor and actually upload win7 iso online and give me the reference link . thank u :)

---

### Post by westie457 on 2015-04-11
You will not get a Windows iso file on here.
As a rule we do not knowingly break the terms of EULAs and copyright laws.

---

### Post by coffeecat on 2015-04-11
I've merged your two threads because one follows on from the next and I've moved the merged thread to our Windows section.

Your problem with the digitalriver download is explained here:

[http://www.howtogeek.com/186775/how-to-download-windows-7-8-and-8.1-installation-media-legally/](http://www.howtogeek.com/186775/how-to-download-windows-7-8-and-8.1-installation-media-legally/)

But you can download a legal Windows 7 ISO from Microsoft if you have the product key:

[http://www.microsoft.com/en-us/software-recovery](http://www.microsoft.com/en-us/software-recovery)

As westie457 says, we don't support activity on this forum that contravenes EULAs or Terms of Service, so we cannot recommend anywhere else to get a Windows ISO except from Microsoft.

---

### Post by sarab2 on 2015-04-11
> **westie457 said:**
> You will not get a Windows iso file on here.
As a rule we do not knowingly break the terms of EULAs and copyright laws.

sad indeed. but theres many available on internet anyways

---

### Post by sarab2 on 2015-04-11
(BUMP)

anyways , I am VERY close to my solution . I have used unetbootin to make my usb bootable from winXp iso . and it throws the error "BOOTMGR is missing. Press Ctrl-Alt-Del to restart" 
Can someone atleast please suggest me a way to fix this bootmgr message . I am using ntfs to format my bootable usb . is that the problem ?
In my bootable usb (after the processing) , there's no bootmgr ? is that the issue ?

---

### Post by ubfan1 on 2015-04-11
To recap your problem, you want to set up a dual boot system with Ubuntu and Windows7.  This is not the forum for Windows
issues, but there are certainly Ubuntu issues you should be aware of:
1)  Windows installer tends to take over the whole disk, so backup everything of value on you existing Ubuntu system.
2)  Have any Ubuntu install media prepared, assuming the Windows install will wipe it out.
3)  The Microsoft Windows 7 ISO offer is really limited to NON-OEM product keys -- that means if your machine came with
a Windows product key sticker on the bottom, that WONT work.
4)Grahammemechnical's point is that regardless of the physical size of your Ubuntu boot partition, it has an ext? filesystem on
it, and Windows cannot read it at all so thinks there is 0 free space on it.
5)Ubuntu install USB media need a FAT filesystem. Don't know what Windows needs.

Things to be aware of before the install are the type of partition table (MSDOS vs GPT), if MSDOS, the difference bewteen primary and
logical partitions (Windows needs a primary, Ubuntu doesn't).

---

### Post by sarab2 on 2015-04-11
I didn't receive much help from this thread unfortunately , but still found out a way , using the good ol' UNetButtin , like who would have though ! -_- 
anyways , so here's what I did :
1) I already had the contents of setup cd folders in pendrive . I converted those folders to iso file using brasero (available with ubuntu)
2) then I formatted the pendrive disk using gparted , format it to ntfs , set bootable flag under the "manage flags" menu
3) save changes, remove and replug pen drive
4) now use UNetBootin to convert the iso to "bootable pendrive "
5) Boot from pendrive . Yay done 

now m spared from those boring "sudo-apts" for the most part -_- 
On the other hand, I don't knw whether I shud even be saying that , considering I am a software programmer myself 
Anyways its time to mark this thread [SOLVED] , might help a troubled soul in future

---

