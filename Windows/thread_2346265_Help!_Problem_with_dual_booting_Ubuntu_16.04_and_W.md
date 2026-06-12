---
title: "Help! Problem with dual booting Ubuntu 16.04 and Windows 7 x64"
date: 2016-12-13
forum: Windows
---

### Post by enforcerer on 2016-12-13
So i have Ubuntu 16.10 installed on my laptop but i want to dual boot with Windows 7 aswell since im sharing the laptop with my brother and he finds Ubuntu too overwhelming. I've read tons of topics about this but i still fail :S. I have burned and windows iso on a usb using Etcher (I tried with winusb but i always got an error 256) i have created a new partition for windows ntfs formated but when i try to boot from usb nothing happens.Im sure that the usb is not damaged and its working because i installed Ubuntu with it but for some reason the pc doesnt boot from it with windows iso burned on it (I have checked the bios set it to Legacy, set the boot priority properly with USB on top).

Here are my partitions.
Device     Boot     Start        End    Sectors   Size Id Type
/dev/sda1            2048     999423     997376   487M 83 Linux
/dev/sda2         1003518 1465145634 1464142117 698,2G  5 Extended
/dev/sda5       539807744 1465145634  925337891 441,2G 83 Linux
/dev/sda6   *      1003520  524386332  523382813 249,6G  7 HPFS/NTFS/exFAT
/dev/sda7       524388352  539799551   15411200   7,4G 82 Linux swap / Solaris

Partition 2 does not start on physical sector boundary.
Partition table entries are not in disk order.

i'm new to Ubuntu so sorry if i sound ignorant, also sorry for my bad English its a second language.

---

### Post by yancek on 2016-12-13
I've never used 'Etcher' so have no idea what the problem is with it.  You have two problems.  One, the inability to boot the flash drive and two, no primary ntfs partitions.  You have one primary partition on which you have Linux (sda1) and a second primary (sda2) used as an Extended partition in which you have several logical partitions.  Even if you were able to boot the usb, you would need a primary partition on which to install windows boot files.  You have sda6 as an ntfs partition marked as active/bootable.  That won't works as it is a logical partition. 

You might try using 'Etcher' again or test the usb on another computer.  Did you download the correct version of the software for Linux 64/32 bit??

After reviewing several sites on Etcher, I don't see anything indicating it will create a bootable windows flash dirve.  It is a program that will run on Linux, Mac or windows but I don't see anything on any of the sites indicating it will create a bootable windows usb.  Generally, you need to extract the windows iso, copy it to a flash drive and boot from Grub on Ubuntu.

---

### Post by howefield on 2016-12-13
Thread moved to the "*Windows*" forum.

---

### Post by enforcerer on 2016-12-13
First thank you for taking your time to help me, yes i installed the 64 version of the software and looking into Grub some threads say to install it on the usb drive aswell i will go ahead and do that and i will boot live version of Ubuntu to create a primary partition for windows

---

### Post by oldfred on 2016-12-13
It looks like your sda6 is at beginning of extended partition. It then can be converted to a primary as you have a primary partition left.

Some Windows tools may do it, or fixparts, but use it just to change logical to physical.
 [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by enforcerer on 2016-12-13
I went and did all that u guys suggested but when i tried to install grub on the usb i got the following error
grub-install: warning: File system `ntfs' doesn't support embedding.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.

---

### Post by yancek on 2016-12-13
If you have Grub installed with Ubuntu on your hard drive, there is no reason to try to install Grub on the flash drive.  Exactly how (what command) did you try to install Grub to the flash drive?  You can put an entry such as the example below in the grub.cfg file on Ubuntu and you should be able to boot with it.  This has worked for me.  If you put an entry in grub.cfg to use as a one time boot, do not run update-grub.  You need to change the uuid entry from the one below to the appropriate one for the windows partition on the flash drive which you can get by running:  sudo blkid

> menuentry "Start Windows Installation" {
 insmod ntfs
 search --no-floppy --fs-uuid 459532DE5D8D5C3A --set root 
 chainloader +1 
 boot
}

I still haven't seen anything indicating 'Etcher' will create a bootable windows flash drive.

---

### Post by oldfred on 2016-12-13
You never ever install grub to a NTFS partiiton's boot sector (PBR). Windows has essential boot info in the PBR.
And you rarely install grub to a partition. It should be installed to a MBR or first sector of a hard drive if a BIOS/MBR system. Or if UEFI only to drive seen as sda.

You do not normally install grub to a flash drive unless you are doing a full install to the flash drive.

If you want to dual boot with Windows & Ubuntu, you still have grub in MBR of your hard drive, and boot Windows from the grub menu.

---

### Post by enforcerer on 2016-12-14
Ok so turns out i have grub installed with ubuntu :D 
@yancek  I tried pasting the code in the grub.cfg but it didnt let me save it i got a message saying i dont have the permission to change the file.
I tried different method for burning the iso i used Disks option Restore Disk Image and this time when i try to boot form the usb right after the bios loading screen i get stuck ona a black screen 
with blinking underscore on it :D I cant type anything only thing i can do is ctrl+alt+del wich restarts the pc.

---

### Post by yancek on 2016-12-14
>  I tried pasting the code in the grub.cfg but it didnt let me save it i  got a message saying i dont have the permission to change the file.

That would indicate to me that you were attempting to do this as a normal user.  That won't work because all the Grub files are system files and you need root privileges to make changes to these files.  If you have a standard install, you should be able to open it  with the following command in a terminal if you are using gedit as a text editor.  Make the change and save the file and reboot.

```
sudo gedit /boot/grub/grub.cfg
``` 

I don't know what the 'Disks' option does, never used it but I doubt that it will create a bootable windows flash drive.  There may be other methods that I am not aware of, but the only way I know to create a bootable 'windows' flash drive is what I referenced in post two above and which is explained in detail at the link below.  I used this to install and boot windows 10 and 7 so it works.  From what I have read about 'Etcher', it is similar to other software such as unetbootin and pendrivelinux which can be run on Linux, windows or Mac but only to create a bootable Linux flash drive.  I'm sure you can understand that there wouldn't be much incentive for Linux developers to create software to make a proprietary windows bootable usb. 

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

Is there some reason you cannot burn the windows iso to a DVD?  That would seem to be the simplest solution unless you do not have a CD/DVD drive.

---

