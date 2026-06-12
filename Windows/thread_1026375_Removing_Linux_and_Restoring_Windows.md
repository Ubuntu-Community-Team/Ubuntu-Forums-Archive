---
title: "Removing Linux and Restoring Windows"
date: 2008-12-31
forum: Windows
---

### Post by bengreer on 2008-12-31
I am currently removing linux using the live cd. I have these partitions: fat32, linux-swap, ntfs, ext 3.

Which partitions should i remove, resize, etc.

Your help would be much appreciated!

---

### Post by s3a on 2008-12-31
Does any partition contain data you would like to keep? And just out of curiosity, why are you ditching Ubuntu?

---

### Post by bengreer on 2008-12-31
I would like to keep my windows partitions and I am not ditching it, it is on my parent's computer and they don't like it, I got my own now!

---

### Post by s3a on 2008-12-31
I am not too sure what your asking here but:

Click System-->Administration-->Partition Editor and then swap off the swap partition by right clicking on it, delete it. Also delete the ext3 partition and after that you can use the freed up space for either your fat32 or ntfs partition by right clicking on whichever one it is you want to resize and then look at the maximum available size and enter the digits and you should be good.

---

### Post by bengreer on 2008-12-31
I removed all partitions except for my windows partition. Now when I turn my computer on I get this:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 22


What do I do?

---

### Post by s3a on 2008-12-31
[http://ubuntuforums.org/showthread.php?p=6467098#post6467098](http://ubuntuforums.org/showthread.php?p=6467098#post6467098)

---

### Post by bengreer on 2008-12-31
How would I fix the mbr with the ubuntu live cd?  I don't have my windows xp install disk.

---

### Post by cabbiinc on 2008-12-31
> **bengreer said:**
> How would I fix the mbr with the ubuntu live cd?  I don't have my windows xp install disk.

You might try this [http://www.majorgeeks.com/UBCD4Win_d5710.html](http://www.majorgeeks.com/UBCD4Win_d5710.html)
Let us know if it helps.

---

### Post by bengreer on 2008-12-31
That doesn't explain to me what to do!

---

### Post by Cocoabean on 2008-12-31
Download UBCD4Win, burn to a CD, boot like you did with your Linux Live CD, wait a while, (UBCD takes FOREVER to load) then look for the MBR tools, there are two of them, use the one with the graphical interface, I forget which one it is, just open both. I use UBCD4Win at work all the time, should work for you. You can also use 'fixmbr' from Ubuntu's live CD. `man fixmbr` for details, good luck!

---

### Post by cabbiinc on 2008-12-31
> **bengreer said:**
> That doesn't explain to me what to do!

That download I linked too is a link to a boot CD. [under downloads click one of the locations, I've found that the mirror sites are faster downloads than the MG's sites] It will help you install XP. You will need to make a CD much like your Ubuntu CD, i.e. burn an image.

[http://mbrwizard.com/](http://mbrwizard.com/) is a support page from the creators website. That program should be on the boot CD. You will probably have to navigate with DOS code. I've never dealt with a MBR failure and appologize if this isn't much help.

[http://www.ubcd4win.com/index.htm](http://www.ubcd4win.com/index.htm) here's the main page for ubcd4win. If you click the Tools link it will tell you what comes on the disk.

---

### Post by -kg- on 2009-01-01
> **cabbiinc said:**
> That download I linked too is a link to a boot CD. [under downloads click one of the locations, I've found that the mirror sites are faster downloads than the MG's sites] It will help you install XP. You will need to make a CD much like your Ubuntu CD, i.e. burn an image.

[http://mbrwizard.com/](http://mbrwizard.com/) is a support page from the creators website. That program should be on the boot CD. You will probably have to navigate with DOS code. I've never dealt with a MBR failure and appologize if this isn't much help.

[http://www.ubcd4win.com/index.htm](http://www.ubcd4win.com/index.htm) here's the main page for ubcd4win. If you click the Tools link it will tell you what comes on the disk.

I looked on the UBCD website under the Tools subsection, and nowhere in the tools could I find a utility that would restore a Generic Windows MBR.  Unless you saved it before you did your Linux install (and incidentally installed GRUB), you will need to install a generic Windows MBR for your particular Windows version.

MBRWizard is specifically for dealing with the MBR (as it's name implies) and, though it *is* done through a terminal window-type environment. will do specifically what you need to do.

From the site:

> How do I repair the MBR?  The Repair option is designed to replace the boot loader with a standard Windows XP boot loader. The only parameter currently available for /Repair is 1, which indicates Windows XP, additional options will be available in future versions to support Vista and others as required. Making sure the Disk=x option is set correctly (you don't want to repair the wrong disk), use the following command to perform the repair:

```
MBRWiz /Repair=1 /Disk=0
```


I have other software that will restore the MBR with a generic one, as well.  Quite a while back I bought Norton's System Commander, which is a Multi-Boot software (unfortunately, I was never able to get it to recognize Ubuntu, but GRUB works just as well for me) and as part of the recovery CD that I created as part of the installation process, I am able to replace System Commander (or GRUB) with a generic Windows MBR (works perfectly, too!).

You might also find something that will work at the [Super Grub Disk site.]("http://www.supergrubdisk.org/")  I've used the Super Grub Disk for several of my problems, and though it might not replace GRUB with the actual Windows bootloader, there should be a way to chainload Windows through GRUB.

There is a setting in GRUB that will auto-load the first OS in the list (in your case, this would be Windows, since that will be the only OS on your parent's computer).  There is also a setting that gives a countdown time until auto-launching occurs.  Set that to 1 or 0 and Windows will boot as if it's own bootloader is doing it.

---

