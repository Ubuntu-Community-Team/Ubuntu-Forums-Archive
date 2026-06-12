---
title: "Love to try the daily builds - is there a way without having to burn a DVD each time?"
date: 2014-03-03
forum: Ubuntu Development Version
---

### Post by cwmoser on 2014-03-03
Love to try the daily builds of Ubuntu 14.04, but is there a way to install the daily
builds without having to burn a DVD each time?

Just asking.

Carl

---

### Post by oldfred on 2014-03-03
If booting with grub2, yes.
Of course you can just install once and update, unless you also want to test the install process.

Use zsync to download a new ISO. Then reboot and use grub to boot new ISO.

 This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by grahammechanical on 2014-03-03
Use Test Drive.

> [COLOR=#333333][FONT=Ubuntu Beta]TestDrive is a unique, Ubuntu tool for "test-driving" daily development releases of Ubuntu (desktop, server, Kubuntu, etc.) by incrementally syncing and running it in a virtual machine. TestDrive provides a simple mechanism for any Ubuntu user to download, test and provide feedback on the [/FONT][/COLOR][current Ubuntu release under development]("https://iso.qa.ubuntu.com/")[COLOR=#333333][FONT=Ubuntu Beta].[/FONT][/COLOR]

[https://wiki.ubuntu.com/QATeam/Testdrive](https://wiki.ubuntu.com/QATeam/Testdrive)

I am too tired to explain further. Regards.

---

### Post by ventrical on 2014-03-03
> **cwmoser said:**
> Love to try the daily builds of Ubuntu 14.04, but is there a way to install the daily
builds without having to burn a DVD each time?

Just asking.

Carl

 You can use your USB pendrive and boot the .iso from there, then decide to install or run live.

Regards..

---

### Post by cwmoser on 2014-03-06
I followed the procedures in the links in post #2.
I tried both the grub-rescue and the manual entry for my trusty ISO 
but neither method will insert an entry in my Grub2 menu when I boot.

Any ideas?

Carl

---

### Post by oldfred on 2014-03-06
You have to manually add an entry to grub2 in 40_custom.
And the examples in links have to be adjusted for your path to your ISO folder.

       gksudo gedit /etc/grub.d/40_custom

 sudo update-grub

This is my entry, but I use gpt partitioning (even on flash drive) and my iso folder is in partition 4.

```
menuentry "Ubuntu 14.04 Trusty ISO 64bit" {
    set isofile="/iso/trusty-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd0,4)$isofile 
    linux (loop)/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

```

---

### Post by OGpmpdog on 2014-03-06
> **cwmoser said:**
> I followed the procedures in the links in post #2.
I tried both the grub-rescue and the manual entry for my trusty ISO 
but neither method will insert an entry in my Grub2 menu when I boot.

Any ideas?

Carl

Hi there, I suggest an easy solution: DVD-RW:D

I've used a Verbatim DVD-RW since Lucid :KS  Last night, I did a fresh install (UG), and the same disk, rewritten about 30 times, still worked :)

I dont like to tweak GRUB beyond inserting a pretty pic into the boot menu, so good luck with that :)

Peace.

---

### Post by Mateusz Stachowski on 2014-03-06
I would suggest using grml-rescueboot.

> **Integrates Grml ISO booting into GRUB** 
This package provides a script for update-grub which looks for
 Grml ISO images in /boot/grml and automatically adds an entry
 for each image. The purpose is to use one of those images to
 boot a Grml rescue system without using a CD or USB stick.

You can change the location of ISO images from default /boot/grml to something more convenient. For example I changed it to the directory on one of my user writable partitions.

Edit this file:

```
sudo nano /etc/default/grml-rescueboot
```

and change the ISO_LOCATION to your desired directory

> # Location of ISOs:
ISO_LOCATION="/media/Wolne/iso/"

Once you have everything setup you have to run:

```
sudo update-grub
```

To add your ISO images to GRUB.

---

### Post by 1clue on 2014-03-06
+1 for usb boot.

I bought a blu-ray for backups some years back and then about 3 months after that I realized that USB sticks are much more practical for booting, and hard drives are much more cost effective for backups.

---

