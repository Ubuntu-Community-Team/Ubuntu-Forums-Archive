---
title: "Software RAID Problems"
date: 2006-11-02
forum: Server Platforms
---

### Post by mcvaughan on 2006-11-02
I created a simple RAID 0 array using mdadm.  For some reason, I have two md devices, instead of one (md0).  I have one incomplete array and one complete.  I don't know if I'm missing something here, but I cannot remove the incomplete array.  I don't know why my array became md1.  Here is what it looks like:

Personalities : [raid1] 
md1 : active raid1 sdc1[0] sdd1[1]
      17775808 blocks [2/2] [UU]
      
md0 : active raid1 sdd[1]
      17783168 blocks [2/1] [_U]

---

md1 is the array I created as md0, but something's hosed here.  It's been a long time since I've done any admin stuff on linux, so go easy on me.  ;-)


Thanks.

---

### Post by syoung on 2007-01-01
I'm having the same problem, although with RAID1. I'm using Edgy server. I've tried configuring the RAID1 array with the installer and manually with mdadm.

The array breaks down on reboot, I think because there are two RAID devices going after it. Long story short, the superblock of one of the partitions gets hosed.

I think there might me some discrepancy between mdadm.conf in initrd and the local fs file. See [http://ubuntuforums.org/showthread.php?t=287723](http://ubuntuforums.org/showthread.php?t=287723). I'll let you know if I have any luck.

---

### Post by syoung on 2007-01-04
Yes, that might be your problem. As in the thread I posted above, use mdadm --detail --scan to write your /etc/mdadm/mdadm.conf file. Then dpkg-reconfigure mdadm so initrd is regenerated.

You should then have only one array. You can verify that it worked by the following:

```

mkdir tmp
cp /boot/name-of-initrd-image ~/tmp/initrd.gz
cd tmp
gunzip initrd.gz
cat initrd | cpio -id

```

That will create a directory tree in ~/tmp that contains initrd's copy of mdadm.conf. Make sure it matches the one you created manually.

---

