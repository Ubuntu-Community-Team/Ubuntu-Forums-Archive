---
title: "Cloning Ubuntu Server 14 boot drive (usb flash drive) to SSD drive?"
date: 2015-01-25
forum: Server Platforms
---

### Post by Mike_Burt on 2015-01-25
Hi currently I have a Lenovo Server TS140 that I use a 64GB flash drive as the boot drive and has two 3.5" drive for my raid configuration. This machine has webmin and my samba shares. My question is how and if could I go cloning/moving the usb flash boot drive to a SSD drive?

---

### Post by sudodus on 2015-01-25
It is possible to clone drives between USB and {SSD and HDD} SATA drives without problems as long as the target drive is of the same size or larger. I have done it several times.

I don't think it makes a difference if it is a desktop system or a server system, at least as long as it is not part of RAID. (I don't know how to manage RAID.)

---

### Post by Mike_Burt on 2015-01-25
> **sudodus said:**
> It is possible to clone drives between USB and {SSD and HDD} SATA drives without problems as long as the target drive is of the same size or larger. I have done it several times.

I don't think it makes a difference if it is a desktop system or a server system, at least as long as it is not part of RAID. (I don't know how to manage RAID.)


Thanks for your input, I will have to do a little more research as this USB boot drive is what sees the raid 1 devices but is not copied to the internal drive if you get what I mean, it's my root partition and all configuration and settings reside on the USB flash drive , the raid device are for regular files such as documents and media.

---

### Post by sudodus on 2015-01-25
I'm sure it would work if you connect the SSD via USB. I don't know if connecting the SSD internally to a SATA port would reset the device definitions /dev/sda etc. If that happens you might need to change the RAID setup. Maybe if you connect the SSD to the third SATA port it will be /dev/sdc and the RAID will remain /dev/sda and /dev/sdb, and everything will continue to work (if that is how your server manages the SATA ports).

---

### Post by darkod on 2015-01-25
mdadm these days is assembled by UUID so you don't need to worry that much about device names. My home server has 4 disks, sda-sdd, and what I noticed booting it with a usb stick connected (just a stick, the root partition is on the HDDs), is that the stick caught sda and the HDDs were sdb-sde.

That made no difference to mdadm and both the root array and the data array assembled automatically on boot without issues. In fact if you look in /etc/mdadm/mdadm.conf at the ARRAY definitions you will see that the line contains the mdadm device name and the UUID. It has also the server name but that is not really needed for assemble. So, it uses UUID and disk order doesn't really matter.

As for cloning the root to another disk, not sure if you mean a real cloning process since that is not needed. You only need to make adequate partitions on the new disk, and from live mode for example copy all files retaining ownership and permissions. There are few commands for that like:
rsync -av /source /dest
cp -ax /source /dest

I did the cp -ax when moving my desktop root from hdd to ssd and it worked perfectly. Of course you reinstall and update grub to get the new UUID of the ssd but that is no real issue since you would want to install grub on the MBR of the new disk anyway.

---

### Post by sudodus on 2015-01-26
> **darkod said:**
> mdadm these days is assembled by UUID so you don't need to worry that much about device names. ...

Thank you for this positive message :-)

---

