---
title: "28GB used out of 2TB on fresh ext4 RAID1 LUKs"
date: 2012-05-13
forum: Server Platforms
---

### Post by salvo84 on 2012-05-13
can anyone explain this? or any insight as to what is using up 28GB?

I just setup a 2TB software RAID1 with LUKs on a 12.04 sever install. After making the ext4 file system and mounting:

```
/# df -h /storage
Filesystem             Size  Used Avail Use% Mounted on
/dev/mapper/crypto     1.9TB  28G  1.7T   2% /storage

```

when I switch it to xfs:

```
/# df -h /storage
Filesystem             Size  Used Avail Use% Mounted on
/dev/mapper/crypto     1.9TB  33M  1.9T   1% /storage

```

I used the defaults for both mkfs.ext4 and mkfs.xfs, i.e.:

```
/# mkfs.ext4 /dev/mapper/crypto
```

The drives are WD20EARS and are aligned for the 4k sector. I would like to use ext4 but I don't want to lose 28GB...

---

### Post by Gyokuro on 2012-05-13
try mkfs.ext4 -m0 /dev/mapper/crypto (set reserved blocks to 0)

---

### Post by elico on 2012-05-13
try to use the command 
tune2fs -l /dev/mapper/crypto

to see some more info about the ext4 partition.

---

### Post by oldfred on 2012-05-13
I think the previous posts discuss how to remove/reduce the use, it is there for system partition. 
If just a data partition it is not really required and I normally suggest small system partitions so not as much is used.

Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using tune2fs -m). This is to prevent you from filling drive and crashing system. But with new very large drives it it a lot of space and can be reduced. You might want to reduce not eliminate or if sure you will never write too much to drive then you can make it as small as your want.

---

### Post by salvo84 on 2012-05-14
> **elico said:**
> try to use the command 
tune2fs -l /dev/mapper/crypto
to see some more info about the ext4 partition.

good call. tune2fs confirmed that the 28G was from the reserved blocks.

```
...
Reserved block count:        683593
...
Block size:                  4096

```

which equals 28GB

> **Gyokuro said:**
> try mkfs.ext4 -m0 /dev/mapper/crypto (set reserved blocks to 0)

Either the -m 0 doesn't function correctly or it doesn't allow you to reserve 0 blocks because it actually needs a percentage to function properly.

I did find this post [http://askubuntu.com/questions/131516/new-ext4-partition-and-used-space/136608#136608]("http://askubuntu.com/questions/131516/new-ext4-partition-and-used-space/136608#136608") where it looks like they where having the same problem with the "-m 0" option.

> **oldfred said:**
> Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using tune2fs -m)

Also found this page [http://www.walkernews.net/2007/02/28/tune2fs-increase-linux-free-disk-space/]("http://www.walkernews.net/2007/02/28/tune2fs-increase-linux-free-disk-space/") where you can use tune2fs to set the Reserved block count to 0. 

```

tune2fs -m 0 <device>

```

This worked setting it to zero and it freed up the 28GB. Although do not do this to a drive where you have your / and system files, as stated in the last link and also by oldfred...

Thanks for all the responses!

---

