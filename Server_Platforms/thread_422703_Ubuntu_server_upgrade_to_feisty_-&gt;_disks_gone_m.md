---
title: "Ubuntu server upgrade to feisty -&gt; disks gone mad"
date: 2007-04-25
forum: Server Platforms
---

### Post by GoBieN on 2007-04-25
My situation.

My server started out as a dapper server, i had only few disks then. AFter upgrade to edgy the /etc/fstab was auto modified to the UUID system. Wich i don't understand one bit about.

After some time i added extra disks. I have no raid (its a home server) and no LVM's. As i said the UUID's are japanese to me so i added, manual entries in /etc/fstab. just old style -> /dev/hdb1 /mnt/disk ... you get the picture right. This wan't a problem for edgy. He mounted the partition good.

Now i upgrade to feisty and every disk i added manually in edgy refuses to mount. After nosing around it seems all the disks have changed from /dev/hd (abcd) to /dev/mapper/sd (abcd)
Btw: These are all simple IDE disks (no sata) and i have 1 SCSI disk (formerly /dev/sda).

Why this changed i don't know, but i do suspect the mdadm package. It asked me something during upgrade which i didn't know what to answer to so i choose the default (ENTER).

I changed my fstab manually to /dev/mapper/sdb1 etc ... but i don't know where my SCSI disk has gone to ?
And 1 partition refuses to mount because fschk says it can't find the superblock. But it was fine before ?

Can i convert back to the old situation by removing mdadm or so ? Please advise me.

---

### Post by huygens on 2007-04-25
Hello,

I had loads of problem during the Feisty beta test with mdadm, especially because I was not using it. So if you are not using it (RAID software) you can safely remove it.
```
sudo apt-get remove mdadm --purge
```For the hd* sd* thingy, yes with Feisty all IDE (PATA, for parallel ATA, the standard old one) hard disk are now handles by the same subroutine as the SATA disks.
So you can call them either via /dev/sda1 or /dev/mapper/sda1, and this is equivalent to the old /dev/hda1.
For your SCSI disk, I would look in the output of dmesg. As I do not have a SCSI disk, I cannot answer you more precisely, but if you try:
```
dmesg | grep SCSI
```Hopefully it will gives you some output with the device used by your SCSI disk.

For the superblock not detected problem. What is the filesystem type of this particular partition. Any differences for this partition in comparison with others?

---

### Post by GoBieN on 2007-04-25
pff i finally found all my disks.

hda -> sda
hdb -> sdb
hdc (cdrom)
hdd -> sdc
sda -> sdd

You can see were i was a little confused, with hdd becoming sdc and sda becoming sdd.
If have now entered UUID's in my fstab. I looked them up with dev-by-uuid thing and typed it over in fstab.
But i think i'll be removing the mdadm anyways,** but is it safe ?**

Additional problems: 
apache2 and webmin did no start after reboot. strange

---

### Post by huygens on 2007-04-25
> **GoBieN said:**
> But i think i'll be removing the mdadm anyways,** but is it safe ?**

Additional problems: 
apache2 and webmin did no start after reboot. strange


Removing mdadm is safe if you are not using software RAID. I have removed it on my desktop, laptop and server. I have also removed LVM and EVMS (apart on the laptop where I use LVM).
If you do not use them but you feel they are giving you problems, then you can safely remove them.

As for apache2 and webmin. They are both started automatically on my laptop and server after reboot. So it should be working. Now to find out why it does not on your machine, we will have to look into the log files.
Could you look inside /var/log/messages for any entry regarding apache or webmin? Is there any error message? Perhaps you could post here relevant lines so we could help you further.

---

### Post by GoBieN on 2007-04-26
Perhaps continue with the start problems here:
[http://ubuntuforums.org/showthread.php?t=422963](http://ubuntuforums.org/showthread.php?t=422963)

---

### Post by Chazall1 on 2007-04-26
It is safe to remove mdadm. I did it last night and all is well

[PHP]sudo aptitude remove mdadm[/PHP]

---

