---
title: "mhddfs issues"
date: 2012-02-19
forum: Server Platforms
---

### Post by rinorho on 2012-02-19
Hi to all
 
I've installed mhddfs on ubuntu server 10.04.4 64 bit edition as showed into [http://romanrm.ru/en/mhddfs](http://romanrm.ru/en/mhddfs) guide.
 
when I use mhddfs manually, everything is ok and df -h
return me 
 
0ne 7.3 Gb big volume mounted in /mnt/globale point as well,
 
but if I add in /etc/fstab the line :
 
[COLOR=blue]mhddfs#/mnt/hd1, /mnt/hd2, /mnt/hd3, /mnt/hd4 /mnt/globale fuse defaults,allow_other 0 0[/COLOR]
 
 
 
ubuntu return me an error at the boot:
 
 
an error occurred during /mnt/hd2 mounting.
Hit S or M..........
 
mountall: mount /mnt/hd2, [982] termined with status 32
mountall: the filesystem can't be mounted: /mnt/hd2
 
 
 
In the attachment I posted my fstab file.
 
Please, :confused: help me
 
bye
rinorho

---

### Post by rubylaser on 2012-02-19
You need to add the mountpoints for all of those other drives for that to work correctly. Something like this.

```
sudo nano /etc/fstab
```

and paste...
```
/dev/sdb1 /mnt/hd1 ext4 defaults 0 0
/dev/sdc1 /mnt/hd2 ext4 defaults 0 0
/dev/sdd1 /mnt/hd3 ext4 defaults 0 0
```

And then your mhddfs line underneath those.  These devices or filesystems could be different from your setup, but that will give you the ides.  Just like when you when you manually mounted mhddfs, you needed to have the devices already mounted, you need to do that same via fstab.

---

### Post by rinorho on 2012-02-20
> **rubylaser said:**
> You need to add the mountpoints for all of those other drives for that to work correctly. Something like this.
 
```
sudo nano /etc/fstab
```
 
and paste...
```
/dev/sdb1 /mnt/hd1 ext4 defaults 0 0
/dev/sdc1 /mnt/hd2 ext4 defaults 0 0
/dev/sdd1 /mnt/hd3 ext4 defaults 0 0
```
 
And then your mhddfs line underneath those. These devices or filesystems could be different from your setup, but that will give you the ides. Just like when you when you manually mounted mhddfs, you needed to have the devices already mounted, you need to do that same via fstab.
 
Thank you rubylaser,
 I'll try your suggestion this evening,
but in my fstab file all drive are already mounted:
 
UUID=55622cf1-6122-4ddb-a837-13762dd58c9d /mnt/hd1 ext4 defaults 0 0
UUID=3a13b5e5-ab88-439b-bd67-3f252b9f9eca /mnt/hd2 ext4 defaults 0 0
UUID=1ad51f44-ada1-4c98-87f0-b9e9e1065978 /mnt/hd3 ext4 defaults 0 0
UUID=4c64a3bc-332a-454b-9583-4297450b945c /mnt/hd4 ext4 defaults 0 0
 
UUID codes are refered to all drives! (/dev/sdb1, /dev/sdX...)
 
 
If I remove in fstas mhddfs's line, everything is ok and all the drives are mounted!
 
 
bye

---

### Post by rubylaser on 2012-02-20
If you already have the disks mounted (UUIDs are fine and the preferred method), it looks like /dev/hd2 is spinning up a little too slowly.  What I would do is keep your fstab the same and then just add your manual mount command to /etc/rc.local or create a regular init script and start it late in the boot process (99).

---

### Post by rinorho on 2012-02-20
> **rubylaser said:**
> If you already have the disks mounted (UUIDs are fine and the preferred method), it looks like /dev/hd2 is spinning up a little too slowly. What I would do is keep your fstab the same and then just add your manual mount command to /etc/rc.local or create a regular init script and start it late in the boot process (99).
 
 
Thank you ruby
 
I added the line:
[COLOR=blue]mhddfs /mnt/hd1, /mnt/hd2, /mnt/hd3, /mnt/hd4 /mnt/globale -o allow-other [/COLOR]
 
[COLOR=black]in /etc/rc.local and everything is ok[/COLOR]
 
Only the speed is very bad :frown: only 33 Mb/s, before for single HDD were 120 Mb/s!

---

### Post by rubylaser on 2012-02-21
> **rinorho said:**
> Thank you ruby
 
I added the line:
 [COLOR=blue]mhddfs /mnt/hd1,  /mnt/hd2/, /mnt/hd3, /mnt/hd4 /mnt/globale -o allow-other [/COLOR]
[COLOR=#0000ff][/COLOR] 
[COLOR=black]in rc.local and everything is ok[/COLOR]
 
Only the speed is very bad :frown: only  25 Mb/s, before for single HDD were 120 Mb/s!

mhddfs is not very fast because it's FUSE based.  This is why I always use mdadm and build a RAID array :)  I just recently put together a (3) 2TB disk array with mdhhfs to do some backups to and was only able to get around 45MB/s reading from it.  The same (3) disks in a mdadm RAID5 array would have been much faster, but I needed maximum storage space to move my files so it was either mhddfs, LVM, or an mdadm RAID0.

Personally, I'd pick up one more disk and build a RAID5 array if speed is a concern.

---

### Post by rinorho on 2012-02-21
> **rubylaser said:**
> mhddfs is not very fast because it's FUSE based. This is why I always use mdadm and build a RAID array :) I just recently put together a (3) 2TB disk array with mdhhfs to do some backups to and was only able to get around 45MB/s reading from it. The same (3) disks in a mdadm RAID5 array would have been much faster, but I needed maximum storage space to move my files so it was either mhddfs, LVM, or an mdadm RAID0.
 
Personally, I'd pick up one more disk and build a RAID5 array if speed is a concern.
 
Thanks a lot.
 
bye
 
rinorho

---

