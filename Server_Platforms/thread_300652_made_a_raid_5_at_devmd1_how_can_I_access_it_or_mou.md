---
title: "made a raid 5 at /dev/md1 how can I access it or mount it?"
date: 2006-11-16
forum: Server Platforms
---

### Post by RunsWithScissors on 2006-11-16
I have 4 120Gb Hard Drives. I wanted to make a Raid 5 volume out of them.
so made gave them each a single unformateed partition that was the maximum size.

then I ran the following command:
$sudo mdadm --create --verbose /dev/md1 --level=5 --raid-devices=4 /dev/hde1 /dev/hdg1 /dev/sda1 /dev/sdb1

which returned:

mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: size set to 117218176K
mdadm: array /dev/md1 started.

by my calulation I should have a new raid 5 volume approx. 333GB

Unfortunatly I cannot find out what I need to do next. 

Help me please!

---

### Post by Shay Stephens on 2006-12-12
I am interested in setting up a raid 5 setup and found your post.  Did you get this working?  If I had to guess, you just needed to mount that new array right?

---

### Post by psusi on 2006-12-13
You should now have a raid device probably named /dev/md0.  If you want to format it then man mkfs.

---

### Post by EmmEff on 2006-12-13
[The Software-RAID HOWTO](http://tldp.org/HOWTO/Software-RAID-HOWTO.html) is a good read.

Essentially, you create a filesystem on /dev/md0 using 'mke2fs -j /dev/md0' and then mount that filesystem.

Also, you might want to look into LVM ([LVM HOWTO](http://tldp.org/HOWTO/LVM-HOWTO/)) to split up the huge RAID partition into separate "virtual" partitions.

---

### Post by drewrockshard on 2006-12-21
> **EmmEff said:**
> [The Software-RAID HOWTO](http://tldp.org/HOWTO/Software-RAID-HOWTO.html) is a good read.

Essentially, you create a filesystem on /dev/md1 using 'mke2fs -j /dev/md0' and then mount that filesystem.

Also, you might want to look into LVM ([LVM HOWTO](http://tldp.org/HOWTO/LVM-HOWTO/)) to split up the huge RAID partition into separate "virtual" partitions.

actually,  you would want to do:

```

mkfs -j /dev/md1

```

you should also edit you /etc/fstab file.  Add the mount point the device. and the filesystem and options.

you must also create the mountpoint (folder):

```

mkdir /data        # make the mountpoint
chown root:users /data             # make sure root is owner/users is group owner
chmod 750 /data             # owner gets RWX permissions / group get RX permissions

```

you do not have to use the same users and permissions as i did above.

then to mount it:

```

mount /dev/md1

```

hope this helps

---

### Post by EmmEff on 2006-12-21
The first RAID device is also /dev/md0, not /dev/md1 in case there is confusion.

---

