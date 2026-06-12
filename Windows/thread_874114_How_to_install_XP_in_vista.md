---
title: "How to install XP in vista"
date: 2008-07-29
forum: Windows
---

### Post by kingkong22 on 2008-07-29
I brought a HP-dv6000 laptop which is pre-installed with vista home edtion. later, I made a partition on vista side and then installed ubuntu successfully. Now, I want to make a partition against vista again, so I can install window-xp in it. Because I found a lot of software that don't run in vista. Does anybody tell me how to do it ? Thank you very, very much !!!

Regards,

---

### Post by SkonesMickLoud on 2008-07-29
Did you partition for Ubuntu manually?  If so, simply do the same thing, but instead of making an ext3 partition, make it NTFS, then install XP.

For future reference, we have a Windows forum here:

[http://ubuntuforums.org/forumdisplay.php?f=170](http://ubuntuforums.org/forumdisplay.php?f=170)

---

### Post by knightcoder on 2008-07-29
Does Vista allow you to do that ??
I believe that vista takes ownership of all NTFS partitions thereby disabling to install any other version of Windows.

---

### Post by SkonesMickLoud on 2008-07-29
> **knightcoder said:**
> Does Vista allow you to do that ??
I believe that vista takes ownership of all NTFS partitions thereby disabling to install any other version of Windows.

Wait, Windows snags ownership of other partitions???

:lolflag:

Didn't know that, but if it's the case, you could always make a FAT32 partition.  This would also let you share data between XP and Ubuntu.

---

### Post by nbayiha on 2008-07-29
Why don't you try to make a new partition and install Xp on that partition ?
To create a new partition you can use Gparted in Linux or Partition Magic(Vista).
But dont forget that installing XP ,vista will remind you that a newer version is already installed.

By the way why dont u move to Ubuntu at all :lolflag:

---

### Post by kingkong22 on 2008-07-29
Oh, Sir, " Did you partition for Ubuntu manually? " -- I could not answer your question for sure.  How will I know partition for ubuntu manually ?
My Concerning is making partition on vista will affect ubuntu side. -- I'm not sure. please give more in details. thanks alot.

---

### Post by SkonesMickLoud on 2008-07-29
> **kingkong22 said:**
> Oh, Sir, " Did you partition for Ubuntu manually? " -- I could not answer your question for sure.  How will I know partition for ubuntu manually ?
My Concerning is making partition on vista will affect ubuntu side. -- I'm not sure. please give more in details. thanks alot.

When you did the installation, did you select "Manual Partitioning" or "Guided"?

---

### Post by kingkong22 on 2008-07-29
>Why don't you try to make a new partition and install Xp on that partition ?
>To create a new partition you can use Gparted in Linux or Partition >Magic(Vista).
>But dont forget that installing XP ,vista will remind you that a newer >version is already installed.

>By the way why dont u move to Ubuntu at all

To nbayiha, 
  It seems a quick way to install xp. Yes. I want to use Magic from vista to create a new partition, then install xp in it. By doing that, will it affect 
ubuntu side ? -- that's my big concern. please answer me. I dont' want really destroy my ubuntu. Thank you all your guys. I alway stay with ubuntu, But I need to handle some chinese documents with some software that don't work on vista & ubuntu.

---

### Post by SkonesMickLoud on 2008-07-29
As long as Ubuntu and XP are in different partitions, one will not effect the other.

---

### Post by nbayiha on 2008-07-29
```
It seems a quick way to install xp. Yes. I want to use Magic from vista to create a new partition, then install xp in it. By doing that, will it affect
ubuntu side ? -- that's my big concern. please answer me. I dont' want really destroy my ubuntu. Thank you all your guys. I alway stay with ubuntu, But I need to handle some chinese documents with some software that don't work on vista & ubuntu.
```

Nope it won't affect your Ubuntu Partition , cause they wont be in the same partition. 
Try it without fear. 
And report if you got some problem.

---

### Post by kingkong22 on 2008-07-29
Thank Guys, Nbayiha & SkonesMickLoud ! will do it later & report it.

Thanks again. :)

---

### Post by kingkong22 on 2008-08-02
Today, I just did only 2 steps:
(1) created 20 GB partition from vista & format it for XP home
(2) inserted XP install-CD and re-boosted the laptop, I
got the following error messages:

GRUB Loading Stage1.5.
GRUB Loading, please Wait......

Error 17


What causes the above problem ?

How can I fix it ? plese guide me and help fix it.
Thank you very much !!!

Regards,


P.S. Before I did it, my laptop first pops up the memu that contains ubuntu and vista, after hitting the desire, then it goes.

---

### Post by astroboy78 on 2008-08-02
I hope you have the Vista install CD!

What you just did was removing the ubuntu partition, but the bootloader (Grub) from Ubuntu is still there looking for the Ubuntu partition, hence the error.

The first thing to do is to start the Vista Install CD (not the recovery CD from your computer manufacturer) and "repair" your Vista installation. Basically it will just rewrite the Master Boot Record (removing Grub) and install the Vista Bootloader.

Second, if Vista boots, you have another problem: You can't install XP AFTER Vista! You can install XP then Vista, but not the opposite. Vista was made after XP and the way it start is completely different from XP. XP doesn't know about Vista, so if you install it after it will rewrite the Master Boot Record (first area of the disk that tells how to boot the OS) and you'll loose the ability to boot Vista.

What you can do is backup your data (when Vista is booting), then format everything, install XP on a partition, then install Vista on a second partition.

There is some programs that manages to let you install XP after installing Vista, but I don't have experience on those. Google is your friend!

Last resort: if you DO NOT have the Vista Install CD, install XP on the second partition (make sure you boot from the CD, set this in the bios), backup your data from your Vista partition, format and reinstall in order XP, then VISTA... ;)

---

### Post by cybrsaylr on 2008-08-03
> **SkonesMickLoud said:**
> Wait, Windows snags ownership of other partitions???

:lolflag:

Didn't know that, but if it's the case, you could always make a FAT32 partition.  This would also let you share data between XP and Ubuntu.

I have a dual boot setup where XP is NTFS and have no problems sharing data with XP and Ubuntu.

---

### Post by /////// on 2008-08-03
Download Gparted live CD, remove all the partitions, make 3 empty partitions (1 ext2 and 2 NTFS, install XP, then install Vista, then install Ubuntu. You do this because first XP will install which creates its own bootloader, then install Vista on top of that which will see the XP partition, delete the XP bootloader and install its own bootloader which will include the XP partition. Then you install Ubuntu which will install GRUB which will find the Vista bootloader, rewrite the MBR to load itself at start up and then have an option where you can load the Vista bootloader which will give you options to start XP or Vista.

---

### Post by thegodfaza on 2008-08-03
Vista doesn't go and take over other NTFS partitions. I have MCE 2005 & Vista Ultimate x64 on the same drive. All working fine.

---

### Post by cariboo on 2008-08-03
Before following some of the drastic advice posted here, why not enable boot from cd in your bios, then install windows xp.

Jim

---

### Post by kingkong22 on 2008-08-04
> Before following some of the drastic advice posted here, why not > enable boot from cd in your bios, then install windows xp.

> Jim

Hi, Jim,
   How can I enable boost from cd in my bios ? I'm quite new to configure systems. what is more, I still want to keep that vista & ubuntu in my laptop.(unless it is no way to keep them). Thank you all guys for the suggestions. Now, I get in online not so easy, plase stand for my late feedback. thank you so much !!!

Regards,

---

### Post by bodhi.zazen on 2008-08-04
You just install Windows XP and then restore grub.

1. Keep in mind Windows must be in a primary partition.

2. Personally I would partition with the Ubuntu Live CD (the vista partition manager is not so good, IMO).

Restore GRUB :

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

Last, you will need to "hide" the windows installations from each other :

[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_)

---

### Post by kingkong22 on 2008-08-05
I followed bodhi.zazen's suggestion to install GRUB, after I installed GRUB, re-booted the laptop, it pops up the menu as before: 

ubuntu 7.10 kernel 2.6.22-15-generic
ubuntu 7.10 kernel 2.6.22-15 (recovery mode)
other operating systems:
Windows vista/longhorn (Loader)

from the menu above, if I select the first two options, it just
pops error message:
Error 17: cannot mount selected partition
press any key to continue...

if I select the last one, namely, windows vista, it pops up the second selective menu:
vista
linux

over here, if I select the vista, it goes well as before, working
good. But if I select the linux, it goes below:

BusyBox V1.1.3 (Debian 1:1.1.3-5Ubuntu7) built-in Shell (ash)
Enter 'help' for a list of built-in commands
(initramfs)

under above prompt, I can type 'ls' or 'help' command.

So far, it seems vista has been restored already. but linux still need to be configured. plase help fix. Thank you all !!!!!!

Regards,

---

### Post by kingkong22 on 2008-08-05
my main concern is that firstly, restore ubuntu & vista, then consider to try to install xp. thanks a lot !!!

---

### Post by bodhi.zazen on 2008-08-05
Hard to know, did you install ubuntu with wubi ? If so, that is most likely the source of teh problem.

Another common problem is a corrupt file system.

Boot a live cd and run fsck on your Ubuntu partition. Hard to know which one without more information.

To list your partitions, boot the live cd, open a terminal, and run :

```
sudo fdisk -l
```

Then,

```
fsck -rfv /dev/sdxy
```

where "sdxy" is your ubuntu partition (For example /dev/sda5)

See also : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

Gurb errors are mysterious, 

See also :

[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by kingkong22 on 2008-08-05
I don't know where my ubuntu partition. So After I issued
the command 'sudo fdisk -l', I got the following:

Device      Boost  Start  End   Blocks         Id    System
/dev/sda1       *   1     26771    215032868+   7     HPFS/NTFS
/dev/sda2          26771   29320   20478976     f    W95 Ext'd(LBA)
/dev/sda3          29321  29382    498015    82   Linux wap/Solaris
/dev/sda4          29383  30391    8104792+     83   Linux
/dev/sda5          26771  29320    20477952     7    HPFS/NTFS

I guess my ubuntu partition is /dev/sda4 !?  I'm not sure ! please correct me if I get wrong. Thank you again !!!!!!

Regards,

---

### Post by bodhi.zazen on 2008-08-05
/dev/sda4

---

### Post by kingkong22 on 2008-08-05
Ok, after I typed in 'fsck -rfv /dev/sda4', it was denied
then I did again 'sudo fsck -rfv /dev/sda4', then it took some
times. 
> pass 1
> blah blah
> pass 2
> blah blah

then I re-booted Laptop, it still got the same error message:
Error 17: cannot mount selected partition
press any key to continue ...

If I select vista, then pick up linux, still goes to (initramfs) as
previous message stated.

---

