---
title: "cryptsetup / FS Problem after Upgrading 12.04."
date: 2012-05-05
forum: Server Platforms
---

### Post by Knurz on 2012-05-05
Hi!

I've just upgraded my 10.04LTS Server to 12.04LTS Server.
My System has several disks running in a RAID5, which has a volume Group and 2 LVs of this VG are encrypted using cryptsetup.

After upgrading I can't mount one of these two LVs. 

This is the LV I can't mount.
```

[16:48:48] root@vdr:~# cryptsetup status lun000
/dev/mapper/lun000 is active.
  type:    PLAIN
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
  device:  /dev/mapper/vgB-lv01
  offset:  0 sectors
  size:    3830374400 sectors
  mode:    read/write

```

This is the LV I can mount.
```

[16:48:52] root@vdr:~# cryptsetup status lun001
/dev/mapper/lun001 is active.
  type:    LUKS1
  cipher:  aes-cbc-essiv:sha256
  keysize: 128 bits
  device:  /dev/mapper/vgB-lv02
  offset:  1032 sectors
  size:    2536545272 sectors
  mode:    read/write

```

When I'm trying to mount /dev/mapper/lun000 it tells me:
```
mount: wrong fs type, bad option, bad superblock on /dev/mapper/lun000,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

dmesg tells me:
```

[ 1678.262362] EXT3-fs error (device dm-9): ext3_check_descriptors: Block bitmap for group 0 not in group (block 3849927026)!
[ 1678.345743] EXT3-fs (dm-9): error: group descriptors corrupted
[ 2189.975385] EXT3-fs error (device dm-9): ext3_check_descriptors: Block bitmap for group 0 not in group (block 3849927026)!
[ 2189.999487] EXT3-fs (dm-9): error: group descriptors corrupted

```

Any help would be VERY appreciated. 
At moment I added a LV and dd the lun000 to this disk to run a fsck to this partition.

If someone knows an easier solution for this problem, PLEASE tell me.

Thanks in advance.

Brgds.

---

### Post by Knurz on 2012-05-06
Hi!

Ok there must be a bug in cryptsetup or something similar.

I bootet up with an old server10.04 LTS, started the crypt and it worked fine, no FS errors or something.

Anyone knows if there is a bug in cryptsetup in 12.04 using type: PLAIN (which is the recommended way in the community-help) ?

Brgds.

---

### Post by snoopy66 on 2012-05-31
After upgrading from 10.04 to 12.04, I was having a very similar problem.  In my case, I mount the partition manually, but I hope a similar solution may work for you.

When I read this post, I had the thought to compare the man pages for cryptsetup between 10.04 and 12.04, and there was one thing that stood out for me:  The default for the --cipher option differed.  For 10.04, the default is "aes-cbc-plain" and for 12.04, it is "aes-cbc-essiv:sha256".  So in 12.04, I added the specific cipher to the cryptsetup command:

[FONT="Courier New"]# cryptsetup [COLOR="Red"]-c 'aes-cbc-plain'[/COLOR] create backup /dev/sdc1[/FONT]

[I provided the password here.]

[FONT="Courier New"]# mount /dev/mapper/backup /mnt/backup[/FONT]

and life was good.

Best wishes!

:popcorn:

---

### Post by aeg1s on 2012-09-14
Snoopy: Thank you so much!  I upgraded one of my secondary/alternate servers to test how things would go from 10.4 to 12.04.1 and this exact situation happened to me.  I could not get into my encrypted partition.  

This should REALLY be fixed somehow because people can really flip out when they think the partition has been corrupted.  The error messages you receive make it seem that is in fact what happened...  AND I can imagine people trying all sorts of draconian methods to repair the partition and end up actually destroying their data when the fix you have described was all that was required.

Thank you again.

Rob

---

