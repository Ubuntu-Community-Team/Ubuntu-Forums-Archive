---
title: "How to mount software raid1?"
date: 2011-10-01
forum: Server Platforms
---

### Post by petri on 2011-10-01
Created raid mentioned above but now I can't mount it, must have forgotten something while installing. Have been searching but didn't find anything about mounting raid seems like everyone just have success with it right away.

```
$ sudo mount /dev/md0 /media/raid
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I can see with Gparted that both drives are equally full so the raid should be working right?

---

### Post by petri on 2011-10-01
mdstat:

```
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdf1[1] sde1[0]
      976759936 blocks [2/2] [UU]
      
unused devices: <none>
```

No I didn't format.

edit: But what does RAID partition mean exactly? Is it the md0 or the two hard drives in it?

---

### Post by rubylaser on 2011-10-01
You need to put a filesystem on top of the RAID volume and mount it in /etc/fstab.  Like this...
```
sudo mkfs.ext4 /dev/md0
```
create a mountpoint for it like /storage
```
sudo mkdir /storage
```
```
sudo nano /etc/fstab
```
and paste this in...
```
/dev/md0	/storage	    ext4	defaults	0	0
```
Mount it
```
sudo mount -a
```
It should now be available at /storage.  Good luck :)

---

### Post by petri on 2011-10-01
Thank your, rubylaser! It was the filesystem on top of the RAID volume what was missing.

---

### Post by rubylaser on 2011-10-01
Great, glad to be of service :) Please don't forget to mark the thread as solved under the thread tools at the top.

---

