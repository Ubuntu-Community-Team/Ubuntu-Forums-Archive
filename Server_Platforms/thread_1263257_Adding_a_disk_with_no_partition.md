---
title: "Adding a disk with no partition"
date: 2009-09-10
forum: Server Platforms
---

### Post by Vegan on 2009-09-10
On my antique IBM, I have a 80GB disk as the root. No problem with it at present.

I have a 500GB disk that the IBM cannot boot. I wanted to slave the disk off the CD which is easy to do.

So the disk is not partitioned. I wanted to partition the disk and format it with ext4 so I can use very large files on it.

I also want to be sure the disk is OK, so I plan to use badblocks several times.

Finally I have my MP3 collection as a SAMBA share. I could link the disk, but I have other shares. So I was wondering what strategy I shoud use to use this large disk for my shares.

I expect I could move directories to the bigger disk, and point SAMBA there.

Suggestions?

---

### Post by Vegan on 2009-09-10
BTW I tried:

```
sudo fdisk /dev/hdb
```

and it claimed no such disk

here is some more info

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/CEDAR-root
                      74460344  38531028  32146868  55% /
tmpfs                   384100         0    384100   0% /lib/init/rw
varrun                  384100       352    383748   1% /var/run
varlock                 384100         0    384100   0% /var/lock
udev                    384100       140    383960   1% /dev
tmpfs                   384100         0    384100   0% /dev/shm
/dev/sda5               233335     67122    153765  31% /boot

so what should the new ATA disk be called?

---

### Post by Vegan on 2009-09-10
Figgered out what the problem, IBM maps the EIDE as SCSI so I found the disk as /dev/sdb so I was able to get FDISK to see the disk, partition it.

So now I am formatting it with ext4 as wanted

sudo mkfs -t ext4 /dev/sdb1

as I wanted to be able to use huge files

so now to fix SAMBA, any ideas?

I can mv files easy enough, just wanted to make shares on the new hardware

argh: i cannot mount ext4, :(

can sombody fix mount please?

---

