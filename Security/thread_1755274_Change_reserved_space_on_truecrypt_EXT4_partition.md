---
title: "Change reserved space on truecrypt EXT4 partition"
date: 2011-05-11
forum: Security
---

### Post by seanlano on 2011-05-11
How do I go about setting the reserved space in the EXT4 filesystem in a truecrypt partition to 0%? I don't need the super-user to have any reserved space, but using the normal way doesn't work: ```
sudo tune2fs -m 0 /media/truecrypt1
tune2fs 1.41.14 (22-Dec-2010)
tune2fs: Is a directory while trying to open /media/truecrypt1
Couldn't find valid filesystem superblock.
``` and ```
sudo tune2fs -m 0 /dev/sdb2
tune2fs 1.41.14 (22-Dec-2010)
tune2fs: Bad magic number in super-block while trying to open /dev/sdb2
Couldn't find valid filesystem superblock.

```


Which isn't really surprising, since it is encrypted. Does truecrypt have an option for this?

---

### Post by keihall on 2011-06-25
I just had the same problem (1TB non-root drive), and I discovered the solution.

First, run the following command:

```
$ df -h
```

You output will look something like the following:

```
Filesystem    Size  Used Avail Use% Mounted on
/dev/loop0    917G  859G   12G  99% /media/truecrypt1
```

You need to run the following command to remove the reserved space (notice I'm using /dev/loop0 NOT /media/truecrypt1):

```
$ sudo tune2fs -m 0 /dev/loop0
```

If you run df -h again, you'll see something like the following:

```
Filesystem    Size  Used Avail Use% Mounted on
/dev/loop0    917G  859G   59G  94% /media/truecrypt1
```

Hope it helps! It worked for me :D

---

### Post by seanlano on 2011-06-26
Fantastic! Thanks heaps. I'll try this right now.

---

### Post by seanlano on 2011-06-26
For my system, with TrueCrypt 7.0a and Natty 64bit, the mount point was "/dev/mapper/truecrypt1" instead of "/dev/loop0". But it worked! :P

---

