---
title: "Ubuntu Server 8.10 on Compaq 1850r w/3200 RAID Controller - Not booting"
date: 2009-02-17
forum: Server Platforms
---

### Post by |DDD| on 2009-02-17
Greets!

I have a Compaq 1850r with a Compaq Smart Array 3200 RAID controller.

I have 4 Seagate 18.2 10k rpm SCSI drives configured as follows:
Drive 1 - 18.2gb volume (/dev/ida/c0d0p1)
Drive 2-4 - RAID 5 array

I installed 8.10 server on drive 1 and left the array to be mounted for redundant storage later.

The problem is that after I successfully install 8.10 server and get to the point that it wants to eject the disc and reboot. I reboot and I get "Not a valid system disc. Insert and press any key to continue." (wording may be off just slightly, but its close enough).

I have tried reinstalling the GRUB boot loader with no results.

I tried a procedure that I found on here that worked for someone with a ML530 and a 221 RAID controller, but that did not work either.

I am to the point of trying to install GRUB on a floppy to see if I can get the stupid thing to boot from that.

Any ideas? Thanks! ;)

- David

---

### Post by windependence on 2009-02-17
I really think there is a major problem with 8.10 and the way it detects and uses devices. I just had a terrible time with 8.10 configuring everything in menu.lst and fstab to use the uuid of the device. A nice idea but it's broke and caused me to lose a whole day of consulting work because like yourself, my install went perfectly, but no boot. I was going to try to change all the uuid references to the device IDs like /dev/sda, etc., but it would have been too time consuming.

My fix? Load the LTS version 8.04 which I just happened to have already burned. Worked perfectly. Save yourself the hassle, and just load the LTS because it's long term supported anyway, and is probably better as far as stability goes. Just wanted to give you the heads up. 

Can you boot from the install disk into rescue mode and then post the output of 

```
fdisk -l
```

Also, the output of 

```
cat /etc/fstab
```

and 

```
cat /boot/grub/menu.lst
```

will be helpful.

-Tim

---

### Post by |DDD| on 2009-02-19
Hey, thanks for the info.

Here are the outputs you asked for...
```
fdisk -l
```Nothing.

```
#cat /etc/fstab
#/etc/fstab:static file system information
#
#<file system><mount point><type><options><dump><pass>
proc /proc proc defaults 0 0
#/dev/ida/c0d0p1
UUID=7e3105ab-6e7b-4b0e-b26d-c9c16a052577 / ext3 relatime,errors=remount-ro 0 1
#/dev/ida/c0d0p5
UUID=8a33b086-6595-4a98-a2c3-4706043bdf74 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

```
#cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
```

I am downloading Ubuntu Server 8.04 LTS right now. I am going to nuke 8.10 and give 8.04 a try.

---

### Post by windependence on 2009-02-19
It looks like you were running the commands on the CD mounted system. You would need to mount the filesystems on your disk to do what we need.

At any rate, before we go any further, I'm gonna wait until you try 8.04. I am 99% sure it will work.

BTW, one thing may be a gotcha for you. You may want to nuke the boot sector before you try 8.04 because on mine, the old grub install was still trying to boot from the master boot record of the old system. I would suggest overwriting it with zeros.

-Tim

---

### Post by netztier on 2009-02-19
> **|DDD| said:**
> I reboot and I get "Not a valid system disc. Insert and press any key to continue." (wording may be off just slightly, but its close enough).

I have tried reinstalling the GRUB boot loader with no results.


I don't think that the fault lies with primarily with GRUB here, because the BIOS (or whatever these darn old Compaqs have instead) does not find a boot sector - from where it could find GRUB.

Did you verify that the partition you are trying to boot from has the "bootable" flag set? You might have to boot into rescue mode and run **fdisk /dev/ida/c0d0** from there.

If all else fails, and you have another classic Wide SCSI disk, install it in one of the 5.25" trays below the CD ROM drive (actually, the trays already are 3.5"/5.25" drive cages) and connect it to one of the onboard SCSI adapters and install Ubuntu on that disk. This takes the sometimes a bit picky SmartArray 3200 controller out of the problem discussion - and might leave you with 4 more disks to do the RAID-5.

Come to think of it ... you might just as well connect the 4x drive cage to the other onboard SCSI channel to avoid the hassle with the SmartArray 3200 altogether. I've come to loathe that controller a lot in my old play-around-with 1850R - it would spin up the disks only on every second boot (reproducibly!), for example *eeeek* 

regards

Marc

---

### Post by windependence on 2009-02-19
I actually LIKE that controller :).

I had commercial web clients on one of these for years without incident. I think I can pretty much assure you that there is a problem with 8.10 and the way it installs the bootable devices by uuid instead of device node. The machine I had problems on was a customer's Power Edge 700 with a brand new drive in it. Once 8.04 was loaded, instant success. I could have made 8.10 work by changing the menu.lst and fstab, but I didn't have the time and the client wanted the box back. I am 99% sure the OP has the same problem I did. If you google "/dev/disk/by-uuid" you will get hundreds of hits from people with the same problem. It will be interesting to see if 8.04 works for him. 

-Tim

---

