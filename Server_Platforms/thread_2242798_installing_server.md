---
title: "installing server"
date: 2014-09-04
forum: Server Platforms
---

### Post by leofer on 2014-09-04
I've downloaded and installed Ubuntu 14.04 Server Edition, but I don't know how to continue from here... My setup is 3 physical disks, one small where I have installed the OS, and two (unformatted) big ones that will be RAIDed (level 1, or mirrored, is the best setup in a server, I've been told). 

How do I accomplish this? I don't recall having the option to do this during the install.
I've installed the desktop, but I read somewhere that this consumes a lot power, can I just remove it, or should I reinstall the server?
SAMBA have to be setup after the disks are raided?

Thanks

---

### Post by nadeemanjum on 2014-09-04
start installation of Ubuntu server either using cdrom or a USB stick.
Once the installation process finished, then configure SAMBA server.

---

### Post by lisati on 2014-09-04
*Thread moved to **Server Platforms**.*

---

### Post by mastablasta on 2014-09-04
you can also look at zentyal - ubutnu based and supported by Canonical (use expert install mode to install without the desktop). you connect to it with a web browser and do all the setting up from there.

---

### Post by SeijiSensei on 2014-09-04
You need to create the RAID array after installation.  Install the system to the smaller drive, then use mdadm to create the RAID device.  Format it as ext4, and add an entry to /etc/fstab to mount the drive to the location you've chosen.  

Suppose the two large drives are /dev/sdb and /dev/sdc.  Use gparted or fdisk to create a single partition on each drive and mark them as type "fd" the "Linux RAID" type.  Now run
```

sudo mdadm --create --device /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
sudo mkfs -t ext4 /dev/md0

```
That creates a RAID1 device called /dev/md0 and formats it with an ext4 file system.

---

### Post by leofer on 2014-09-04
Exelent, I guess... The mdadm complained about '--device' so I replaced it with '--verbose' (as suggested at [https://raid.wiki.kernel.org/index.php/RAID_setup](https://raid.wiki.kernel.org/index.php/RAID_setup)). It really helps knowing what to search for, thanks! I didn't "mark them as type "fd" the "Linux RAID" type" because I didn't see that option. Is that something I can do now, or do I need to start the process all over again?

---

### Post by SeijiSensei on 2014-09-05
I don't know what you used as a partitioner.  I use fdisk rather than something like gparted, and in fdisk you set the the type there with the "t" command.

I believe the partition type triggers auto-assembly of the RAID device during boot, but I'm not sure.  I haven't used mdadm in quite some time.

You might be able to change the type with fdisk but not have to re-partition.  If you try that, back up anything important on the RAID device.

Sorry about --device.  I misread the help file in mdadm.  You can get help on any of its features by including "--help" after a command like "mdadm --create --help".

---

