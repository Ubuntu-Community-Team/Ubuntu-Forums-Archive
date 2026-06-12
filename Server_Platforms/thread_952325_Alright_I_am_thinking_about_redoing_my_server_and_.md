---
title: "Alright I am thinking about redoing my server and got some questions to be answered"
date: 2008-10-19
forum: Server Platforms
---

### Post by kustomjs on 2008-10-19
Alright guys
I am thinking about redoing my server and I would like to know how would I be able to transfer my whole hard drive to a new 500gb sata hard drive.

and would you guys think using 500gb sata hard drive with 2gb of memory with gigabyte pci ethernet pci adapter and 56k modem to handle being my webserver and fax server all on one machine and yes I am using a Asus A7S333 motherboard.

---

### Post by kustomjs on 2008-10-19
anybody?

---

### Post by jamesrfla on 2008-10-19
Are you building a new PC? What hardware are you changing?

---

### Post by lykwydchykyn on 2008-10-19
In the old days, I would boot up to a live CD, recreate the partition layout (changing partition sizes as needed) on the new disk, then just copy over the contents of the old partitions onto the new ones.  Reinstall grub and you're good.

That technique is somewhat complicated now by the fact that Ubuntu identifies drives using UUIDs, which are different for every physical partition.  So trying that now you'll get an unbootable volume.  You can fix this by editing the /etc/fstab and /boot/grub/menu.list files, but that gets tedious.

You can also try cloning the drive with G4L or clonezilla, but you might still run into the UUID issue.  It's so trivial to reinstall in most cases that I just opt for a fresh install on a new hard drive.

---

### Post by kustomjs on 2008-10-19
is there anyway that i can transfer the files off of my old hard drive and transfer it to my new hard drive what is the code or the best way of doing this.

---

### Post by cariboo on 2008-10-19
There are two ways to do what you want:

```
dd if=<oldhdd> of=<newhdd>
```

The problem with dd is that it makes a byte for byte copy of the hard drive including the empty space.

Partimage does the same thing, but it ignores the empty space.

dd is installed by default, partimage is available in the repositories.

Jim

---

### Post by lykwydchykyn on 2008-10-19
Download G4L and check out the click'n'clone feature.  Like I said, though, this can be a problem due to UUIDs if you're cloning the system partition(s).  

Are you trying to copy the actual OS install or just your data?

---

