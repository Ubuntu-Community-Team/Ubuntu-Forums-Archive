---
title: "chown my partition"
date: 2008-02-14
forum: Server Platforms
---

### Post by th1bill on 2008-02-14
i cleaned out a 36 gig partition on the drive hdb  where my Ubuntu OS is and I can manually mount it but the permissions are set to root;root.  I log in as the superuser but I cannot seem to chown the unnamed partition.  When I mount it it appears on my desk top as 'disk.'  I created the partition with gparted and it is /dev/hdb2 and is formatted as ext3 and the mountpoint is /media/disk.  The size is 36.49gb, the used reads 762.49mb and the unused is 35,74gb w/no flags. 

Please help.

---

### Post by faulkes on 2008-02-14
> **th1bill said:**
> i cleaned out a 36 gig partition on the drive hdb  where my Ubuntu OS is and I can manually mount it but the permissions are set to root;root.  I log in as the superuser but I cannot seem to chown the unnamed partition.  When I mount it it appears on my desk top as 'disk.'  I created the partition with gparted and it is /dev/hdb2 and is formatted as ext3 and the mountpoint is /media/disk.  The size is 36.49gb, the used reads 762.49mb and the unused is 35,74gb w/no flags. 

Please help.

I'm unsure what you are trying to do here.

You cannot "chown" a partition.  You could chown the mount point (in this case /media/disk) but I wouldn't suggest that.  A better option would be to chown the files and directories on the partition itself.

Faulkes

---

### Post by rok3 on 2008-02-14
> **th1bill said:**
> i cleaned out a 36 gig partition on the drive hdb  where my Ubuntu OS is and I can manually mount it but the permissions are set to root;root.  I log in as the superuser but I cannot seem to chown the unnamed partition.  When I mount it it appears on my desk top as 'disk.'  I created the partition with gparted and it is /dev/hdb2 and is formatted as ext3 and the mountpoint is /media/disk.  The size is 36.49gb, the used reads 762.49mb and the unused is 35,74gb w/no flags. 

Please help.


sudo chown -R USERNAME:GROUP /media/disk/*

Should work nicely for you.

---

### Post by astrotech226 on 2008-02-14
If you want to change the user/group for all the files on the partition, do this:

```
$ sudo chown -R youruser.yourgroup /media/disk/*
```

---

### Post by polmir on 2008-02-15
Type in terminal
```
cat /etc/fstab
```
or
```
gedit /etc/fstab
```

```
sudo fdisk -l /dev/hd*
```
-------------
hd*=hda or sda or hdb or sdb or itd.

and post output of it

---

