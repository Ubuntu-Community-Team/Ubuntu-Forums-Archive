---
title: "EFI GPT - Can't mount filesystem"
date: 2006-02-19
forum: Server Platforms
---

### Post by Spikextrem on 2006-02-19
Hi!

I reinstalled Ubuntu in my server because the root hd failed and linux cn't boot anymore. I reinstalled on another hd. My server is mainly used as a fileserver. It has a 160 gig hd that was formated as Reiserfs. It worked perfectly in my last installation. But now I can't find a way to mount the partition. (There's only one partition on it.)

fdisk gives :[B]
Disk /dev/hdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       19930   160086527+  ee  EFI GPT
[/B]

I swear that it's format with reiserfs! I can't tell the way it was mounted before, I never paid attention to the entry in fstab file since it was working perfectly since the first boot...

Now if I try to mount:
[B]
mount -t reiserfs /dev/hdc1 /media/server/
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/B]


Nothing special in dmesg
[B]
[4295362.215000] ReiserFS: hdc1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on hdc1
[/B]

I tried to mount the partition with ext3, doesnt work more...

Anyone have experience with GPT (large partition)?

plz help ::confused:

---

### Post by Druke on 2006-11-27
try mounting hdc3 instead.. sounds weird but thats how my  EFI GPT mounts.. yet mine is still read only... anyone else able to help on the subject?

---

