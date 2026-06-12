---
title: "lost grub, how to reinstall it to the drive?"
date: 2014-04-11
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-04-11
Its complex.
I took my usb hard drive and upgraded trusty, the drive is plugged into my PC.
The upgrade had new kernel. So grub got written to the usb drive  but the drive in the PC no.

So now when booting the PC, It cant boot, I get a grub rescue prompt.
So I plugged in my usb drive and am running from it to ask this question.

I tried the instructions here
[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.U0iTLKbALzB](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.U0iTLKbALzB)

It seemed to work, said it was writing etc... but no luck. cant boot.

The drive that needs to boot with grub is sdb, the usb hard drive is sdc, sdb1 is a windows partition. sdb6 is the os partition

---

### Post by cariboo on 2014-04-11
You need to install grub to the mbr of the first hard drive in your system, in most cases it would be /dev/sda. Use the following command:

```
grub-install /dev/sda
```

---

### Post by sdowney717 on 2014-04-11
thanks.
I gave up on brain power and fell back on painless

boot-repair-disk-64bit.iso

which I downloaded last time this happened. :KS

Anyway, I have a PC which has no internet access.

I pull the drive and make it a usb drive, boot on my PC and like to do updates, testing which works.
But like this kernel update caused grub update to run which ruins my normal boot.

So how can I keep grub from doing that? Otherwise it cause this trouble.

AND, I know the usb drives grub will have extra entries which dont exist when run on it's PC.
I will take the boot repair disk with me, smart idea I think.

---

### Post by Bashing-om on 2014-04-11
sdowney717; Hey,

Those direction should have worked. But I have in mind to try a simpler method.
Is the lIveUSB the same same version as that of the install?

If so, we can proceed and try this simpler method and see what results.

[INDENT][/INDENT]Where there is a will there is a way

---

### Post by sdowney717 on 2014-04-12
yes, same version.
But it is not a liveusb. It is a full install on a hard drive which is a usb drive because it is in a usb enclosure.
I pulled from off remote PC, put the drive in the usb enclosure and set PC to boot from the usb drive by selecting F8 while the bios boots.

link to boot repair, I used unetbootin to write that to a thumb drive.
[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

---

### Post by rrnbtter on 2014-04-12
Greetings,
This doesn't help your immediate problem but it makes sense to me to disconnect the internal HD before installing to a USB or other drive. I did the same as you a couple of years ago. Amazing that Grub hasn't fixed this glitch yet.

---

### Post by sdowney717 on 2014-04-12
yes, physical disconnection would be the only fix until developers decide to not write grub over all things without an understandable user input.
But that is unnecessary pain to open the machine. At least I can run this grub fix usb live program to get it working again.
Question is what is worse pulling cables or booting that live usb to fix it after grub breaks itself.

Who knows just a queses for the mystery of grub.
My history is when first booting the usb drive and doing upgrade, I did get a warning from the grub meisters saying the drive id's dont match the original install and gave me  list of selectable drives to install grub onto.
Naturally not wanting to screw up my internal drive, and also slightly confused about what was happening,  I only selected the external sdc usb drive, hoping it would only do something with that. So it updates grub and I saw it printing out all my internal partitions, I got this sinking feeling that grub had just destroyed my internal boot drive grub. And yes it did. Later I ran dist-upgrade and that also updated grub but this time no user input was requested.

---

### Post by sdowney717 on 2014-04-12
Unhappily, I took the drive and the boot repair thumb drive to the boat where is no internet access

That boot repair requires internet access and if you do not have that, refuses to repair your grub disc.

So is there a better program to painlessly install fix grub without internet access?

I brought the hard drive back home and I might have to open the PC, yank out the drives, put this one in and then run it here at the house?

---

### Post by sdowney717 on 2014-04-12
I have 4 discs in the pc for the moment
sda is windows
sdb is my trusty internal
sdc is a thumb drive
sdd is a usb drive

So what did this do?
```
scott@scott-P5QC:~$ sudo grub-install /dev/sdd
Installing for i386-pc platform.
Installation finished. No error reported.
scott@scott-P5QC:~$ 

```

What if I do this?
sudo grub-install /dev/sdb

What will happen if i remove sdd for either scenario?

---

### Post by oldfred on 2014-04-12
If you have removeable drives you want grub for the install in that drive to be in the MBR of that drive. Boot-Repair does that automatically if you have one external drive an tell it that it is an external drive. Not sure about multiple externals, but with internal drives it installs one grub to every drive, which may not be correct.

To totally uninstall and reinstall grub you need Internet, so it can download grub.

But if just reinstalling grub2's boot loader to the MBR of a drive you do not need Internet.
If you can boot into your install you just install to the MBR of the same drive. 
If you are booting from another install or Live installer you have to mount / in other install and then install grub. Somewhat of a minor chroot. But if that does not work then you have to do a full chroot and install.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub


 #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by sdowney717 on 2014-04-12
Hi old fred, 

I have an ide hard drive.
It will be the only drive in a PC
I bring the drive home
I put the drive in a USB enclosure.
The computer at home has an internal drive.
I boot from the drive F8 select usb wdc 200 gb drive
It boots.

I am sitting here right now running on the usb drive.
sdc is what I want grub on, currently the usb enclosure drive, I want sdb to be ignored, like it does not exist, like unplugged.

sdb is my internal drive. that will have to be fixed after I unplug sdc, i suppose?

Can you give me custom commands to run ?

Thanks.

If you cant help me, then I will have to unplug sdb and run the boot repair, I think that will work.
But I would like to do it your way, if possible.

---

### Post by oldfred on 2014-04-12
If you have booted into the install in sdc:
Just to confirm it is sdc:
sudo fdisk -l
Then:
sudo grub-install /dev/sdc
sudo update-grub

---

### Post by sdowney717 on 2014-04-12
Ok, I ran it with no errors.

It has however not ignored sdb with the windows partition and Trusty.

Do you think it will still boot at the boat?
And maybe then run 
sudo update-grub out there???

```
boat@boat-MS-7529:~$ sudo fdisk -l
[sudo] password for boat: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00042686

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976768064   488384001    7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.
/dev/sda2       976768065  1953520064   488376000   83  Linux
Partition 2 does not start on physical sector boundary.

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb822ff08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   245151899   122575918+   7  HPFS/NTFS/exFAT
/dev/sdb2       245153790  1465147391   609996801    5  Extended
/dev/sdb5       842551296  1465147391   311298048   83  Linux
/dev/sdb6       245153792   284214338    19530273+  83  Linux
/dev/sdb7       284217344   292028415     3905536   82  Linux swap / Solaris
/dev/sdb8       292030464   842549247   275259392   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00007d34

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    19531775     9764864   83  Linux
/dev/sdc2        19533822   390721535   185593857    5  Extended
/dev/sdc5       382337024   390721535     4192256   82  Linux swap / Solaris
/dev/sdc6        19533824   382337023   181401600   83  Linux

Partition table entries are not in disk order
boat@boat-MS-7529:~$ sudo grub-install /dev/sdc
Installing for i386-pc platform.
Installation finished. No error reported.
boat@boat-MS-7529:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found linux image: /boot/vmlinuz-3.13.0-23-generic
Found initrd image: /boot/initrd.img-3.13.0-23-generic
Found linux image: /boot/vmlinuz-3.13.0-21-generic
Found initrd image: /boot/initrd.img-3.13.0-21-generic
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
Found Ubuntu 14.04 LTS (14.04) on /dev/sdb6
done
boat@boat-MS-7529:~$ 

```

---

### Post by Bashing-om on 2014-04-12
sdowney717; & oldfred ; Hey.

I am back and looking too at this situation.
If it does not boot now, recon we ought to look at '/boot/grub/grub.cfg' and make sure that all the device id's match the UUIDs ?

Now a thought, when the drive is reinstalled to the box it is to operate in, will not the device-ID/UUIDs have to re-confirmed ?
hd0 = 1st hard drive and msdos1 is that 1st partition
hd3 = 3rd hard drive msdos7 is the 7th partition
In accord with what 'sudo blkid' relates.

so
(hd0,msdos1) = sda1
(hd3,msdos8) = sdd8

Mind yall, I am still very much in a learning mode in respect to booting and grub and how grub relates to 'init'.

So everyone is on the same page
[INDENT][INDENT]booting wisely
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-04-12
I find my devices change. 
I managed to skip a SATA port when I installed drives. So if I plug in my flash drive it is sde, but if I reboot then that flash drive is sdb and all others are one letter more. Or I have to pay attention to which drive if not using UUIDs.

Grub works from hd0 which is always the boot drive as defined by BIOS. With my system then every other drive is hd1, hd2 etc. But there is no match between grub's hd0 and sdd or sda as it depends on which drive I boot from. I usually boot sdd which is my SSD.  But they always seem to be in the same order after hd0 is used.

Or when I boot sdd as hd0 then sda is hd1. And depending on whether flash drive was plugged in or not it change also change order.
But if I boot sda as hd0, then sdb is hd1.
Confused yet? :) 
I often have to use e on my grub menu and just try hd1, hd2 etc on some of my boot stanza's where I do not use UUIDs. As I cannot keep track either.

---

### Post by ronb19495 on 2014-04-12
from my experience running grub on usb drives or usb flash sticks if you dont unhook your internal drives it will wipe the boot loaders on internal drives

---

