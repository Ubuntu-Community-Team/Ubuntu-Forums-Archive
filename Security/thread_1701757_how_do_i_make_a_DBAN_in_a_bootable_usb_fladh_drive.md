---
title: "how do i make a DBAN in a bootable usb fladh drive?"
date: 2011-03-06
forum: Security
---

### Post by shiningkenmonster on 2011-03-06
basically i want to sell my dell mini 10v netbook. it is running the Ubuntu 10.10 netbook edition.

I need to completely wipe my hard drive to ensure someone who can not recover my old data.

I have downloaded the dban iso.
I am having a hard time making a bootable USB flash drive with it. I have used the default USB-creator in Ubuntu, but it doesn't let me create it. I couldn't find another program close to it.

I have also tried the dd command line. which is:
```
sudo dd if=/dev/sdc1 of=/home/kenny/Downloads/dban-2.2.6_i586.iso bs=2048

```

I used an empty 2GB Kingston USB flash drive. it has worked. but it actually makes the dban-2.2.6_i586.iso file into a 1.9GB file. I am not sure if i typed in the command line right, or it might be a bug. I remember i did this right doing the dd command line to upload the 8.04 Ubuntu iso before.

how do i make a dban bootable usb flash drive on ubuntu?

---

### Post by cariboo on 2011-03-06
The Ubuntu startup disk creator only works for Ubuntu isos, I would suggest you try unetbootin, it's in the repositories.

---

### Post by alphaamanitin on 2011-03-07
I think this only works from windows machines, but IMO it is the easiest way to make bootable USBs.
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

That works with DBAN.

AlphaA

---

### Post by shiningkenmonster on 2011-04-02
I am still having problems with dban not working. When I did download ubootnetin and installed the dban-2.2.6_i586.iso unto a new 2GB usb flash drive. upon power up of the computer with my usb flash drive plugged in. On the BIOS i pushed the F12 key to enable to boot with the USB flash drive. Which shows loads a text base DBAN options of which nukes to pick.
However, for which ever options i click on, it says this:

```
Loading /DBAN.BZI.....
Could not find ramdisk image:/ubninit
boot:
```

and it doesn't let me procedure to format my hard drive at all. I tried google and looked at the DBAN site, but i couldn't find a solution. Is there a work around for this Ubuntu users?

---

### Post by bodhi.zazen on 2011-04-03
You do not need dban, just boot any live CD (form USB) and write zeros to the hard drive with dd.

[http://www.anti-forensics.com/disk-wiping-one-pass-is-enough](http://www.anti-forensics.com/disk-wiping-one-pass-is-enough)

---

### Post by avents on 2011-04-04
As said, a live CD should work perfectly/

But also Unetbutin - the version for Linux - you can keep it for use later on

---

### Post by shiningkenmonster on 2011-04-06
ah it works!

the command line is:
```
dd if=/dev/zero of=/dev/your_drive_here
```

I could use the 
```
sudo fdisk -l
```
to see what kind of hard drive disk name it is!

I disk wiped to three different partition! Thanks guys!

---

### Post by zero4281 on 2012-03-30
First I formatted my USB stick as vfat.  Then I used UNetbootin to install the dban-2.2.6_i586.iso.

After it finished I edited syslinux.cfg and replaced every occurrence of ```
ubninit
``` with ```
ISOLINUX.BIN
``` and replaced ```
ubnkern
``` with ```
DBAN.BZI
```

A couple of find/replace and everything seemed to work. :D

---

### Post by oklokl on 2012-03-30
sudo -i

cd ~/download

wget [http://sourceforge.net/settings/mirror_choices?projectname=dban&filename=dban/dban-2.2.6/dban-2.2.6_i586.iso](http://sourceforge.net/settings/mirror_choices?projectname=dban&filename=dban/dban-2.2.6/dban-2.2.6_i586.iso)

usb input
mkfs.vfat /dev/sdb1

umount -l /media/usb



dd if=/dev/zero of=/dev/sdb bs=446 count=12345

dd if=dban-2.2.6_i586.iso of=/dev/sdb bs=1M

---

### Post by emiller12345 on 2012-03-30
> **oklokl said:**
> sudo -i

cd ~/download

wget [http://sourceforge.net/settings/mirror_choices?projectname=dban&filename=dban/dban-2.2.6/dban-2.2.6_i586.iso](http://sourceforge.net/settings/mirror_choices?projectname=dban&filename=dban/dban-2.2.6/dban-2.2.6_i586.iso)

usb input
mkfs.vfat /dev/sdb1

umount -l /media/usb



dd if=/dev/zero of=/dev/sdb bs=446 count=12345

dd if=dban-2.2.6_i586.iso of=/dev/sdb bs=1M

Before you do this command, you need to make sure that '/dev/sdb' is related to you usb drive and not any other drive (like your harddrive).  You can check this by doing ```
ls /dev/sd*
``` BEFORE inserting you usb drive and again AFTER inserting your usb drive and noting the difference.
and I've read that the bs parameter should usually be a power of 2 (like 256, 512, or 1024, etc)

---

### Post by dark_harmonics on 2012-08-23
Here is how I did this:
[LIST=1]
[*]Install gparted if you dont have it with " sudo apt-get install gparted"
[*]Open gparted and delete any partitions from the drive. Be careful not to wipe the wrong one!
[*]Create a new fat32 partition and set the boot flag. 
[*]Replug the drive to mount the new partition.
[*]Open the dban iso file and copy all the files to the new partition. 
[*]Use syslinux to make it bootable with "syslinux -i /dev/sdx1" - Replace x with the letter for the drive 
[*]rename the isolinux.cfg file to syslinux.cfg
[/LIST]
Done!

---

### Post by rookcifer on 2012-08-25
> **shiningkenmonster said:**
> basically i want to sell my dell mini 10v netbook. it is running the Ubuntu 10.10 netbook edition.

I need to completely wipe my hard drive to ensure someone who can not recover my old data.

Don't worry with Dban.  Simply insert your Ubuntu livecd, open a root shell and type:

```
dd if=/dev/urandom of=/dev/sda
```

where /dev/sda is the disk in question.  Be sure to erase the correct disk!

But this will accomplish exactly what DBan does.

---

### Post by bodhi.zazen on 2012-08-25
> **rookcifer said:**
> But this will accomplish exactly what DBan does.

Well, not exactly, but close enough.

scrub is a nice command which will do the same, biggest benefit is that it is faster then either dd or DBAN


[http://linux.die.net/man/1/scrub](http://linux.die.net/man/1/scrub)

---

### Post by dark_harmonics on 2012-08-27
I would agree with other posters that DBAN is not needed for most "Home" purposes, but the paranoid might find its wipe comforting before you dispose of that old hard drive.  

From a business perspective, it is not a certified utility does not guarantee compliance with any security standards. 
[http://www.dban.org/node/52]("http://www.dban.org/node/52")

What it does do is a very thorough wipe that (in my company's tests using CBL 3rd party data recovery service) is extremely difficult or impossible to recover data from.

---

### Post by bodhi.zazen on 2012-08-27
> **dark_harmonics said:**
> I would agree with other posters that DBAN is not needed for most "Home" purposes, but the paranoid might find its wipe comforting before you dispose of that old hard drive.  

From a business perspective, it is not a certified utility does not guarantee compliance with any security standards. 
[http://www.dban.org/node/52]("http://www.dban.org/node/52")

What it does do is a very thorough wipe that (in my company's tests using CBL 3rd party data recovery service) is extremely difficult or impossible to recover data from.

From the scrup man page 

> The dod scrub sequence is compliant with the DoD 5220.22-M procedure for sanitizing removeable and non-removeable rigid disks which requires overwriting all addressable locations with a character, its complement, then a random character, and verify. Please refer to the DoD document for additional constraints.

The nnsa (default) scrub sequence is compliant with a Dec. 2005 draft of NNSA Policy Letter NAP-14.x (see reference below) for sanitizing removable and non-removable hard disks, which requires overwriting all locations with a pseudorandom pattern twice and then with a known pattern. Please refer to the NNSA document for additional constraints.

Please consult local authorities regarding your site policy for disk sanitization. 

---

### Post by rookcifer on 2012-08-28
> **dark_harmonics said:**
> I would agree with other posters that DBAN is not needed for most "Home" purposes, but the paranoid might find its wipe comforting before you dispose of that old hard drive.  

DBan does nothing different than dd or scrub.  All of them simply write random data or zeros to the disk.  The only thing Dban does is add in all of these useless DoD and Gutmann passes, which are totally unnecessary as research proves.  You aren't recovering data from a disk that has been overwritten one time. Some guy, years ago, had a challenge to any data forensics firm to try and do so.  All of them declined.

---

