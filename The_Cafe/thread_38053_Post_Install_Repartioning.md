---
title: "Post Install Repartioning?"
date: 2005-05-29
forum: The Cafe
---

### Post by Kyral on 2005-05-29
Okay, II'm thinking about moving /home off of the main super huge (300 GB) partition and shrinking the system partition down to maybe around 20GB and moving /home off into the new partition. Now, is this a good idea? And can it be done? I know I'll prolly have to change my fstab, but I just want get some comments on this one :D

---

### Post by Arthemys on 2005-05-29
Coming from the windows world, this is probably the wrong answer, but it is my input.
You could possibly pull the drive and put it into a box running Partition Magic and edit the partitions that way. Essentially you will need a "non-destructive" partitioning utility, in linux I'm not aware of any, but I'm sure they must exist. I used PM here on my thinkpad after I got it from IBM to split my Windows partition and make a linux portion.

---

### Post by Kyral on 2005-05-29
Ths is why I love my two 3 1/2 inch Partition Magic boot disks :D

This is more like "Is this a good idea" thing, since I'll be honest, I'm the kind of user who messes around way too much and can't go a month without fatally screwing up something

---

### Post by jeremy on 2005-05-30
If you have a second HD, I recommend using partimage (run it from knoppix cd) to image your install before you start, then, if anything goes wrong just restore the image.

---

### Post by TravisNewman on 2005-05-30
you can do non destructive ext3 partitioning with parted/gparted/qtparted

so unless it's reiser you should be good with it. I'd suggest booting off a live cd to do everything. Well, you'd HAVE to boot from a livecd unless you have another drive.

I use the System Rescue CD. It's never failed me :)

---

### Post by jerome bettis on 2005-05-30
don't use partimage if you're going to be shrinking the partition.  it won't work.  if you're making the partition bigger it's fine though.

instead, use cd / ; tar -cvpf /path/fileSystem.tar bin boot etc home lib opt root sbin srv tmp usr var
to put everything into a tarball.  you can add the z or j option to use gzip or bz2 compression to make it smaller at the cost of speed.

then to restore it just cd / ; tar -xvpf /path/fileSystem.tar  - also you'll have to restore any directories (dev sys proc media and so on) that you didn't put in the tarball.  take a note of this before you fdisk and mkfs.

that $100 i spent on that usb hard drive was well worth it for reasons like this.  use a live cd to back up and do the repartitioning with fdisk.  also the reiser4 filesystem is pretty damn stable now and it's a lot faster than ext3 ... another thing to consider.

---

### Post by Seti on 2005-05-30
And don't forget finally to edit /etc/fstab to reflect the new location of home.

---

### Post by jeremy on 2005-05-30
[QUOTE=jerome bettis]don't use partimage if you're going to be shrinking the partition.  it won't work.  if you're making the partition bigger it's fine though.

instead, use cd / ; tar -cvpf /path/fileSystem.tar bin boot etc home lib opt root sbin srv tmp usr var
to put everything into a tarball.  you can add the z or j option to use gzip or bz2 compression to make it smaller at the cost of speed.

then to restore it just cd / ; tar -xvpf /path/fileSystem.tar  - also you'll have to restore any directories (dev sys proc media and so on) that you didn't put in the tarball.  take a note of this before you fdisk and mkfs.

that $100 i spent on that usb hard drive was well worth it for reasons like this.  use a live cd to back up and do the repartitioning with fdisk.  also the reiser4 filesystem is pretty damn stable now and it's a lot faster than ext3 ... another thing to consider.[/QUOTE]
 You are right, of course, about the partition size.
What I meant in my post suggesting partimage, was that if an image was made, befor resizing the partition, then, at worst, Kyral could get things back to how they were before.

---

### Post by Kyral on 2005-05-31
[QUOTE=panickedthumb]you can do non destructive ext3 partitioning with parted/gparted/qtparted

so unless it's reiser you should be good with it. I'd suggest booting off a live cd to do everything. Well, you'd HAVE to boot from a livecd unless you have another drive.

I use the System Rescue CD. It's never failed me :)[/QUOTE]

Just booted into Knoppix and tried its copy of QtParted. It won't let me resize the partition (its in ext3). Then I tried my PM Disks and it wouldn't let me either. What gives?

---

