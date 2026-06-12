---
title: "'boot' partition size 100MB?"
date: 2014-12-18
forum: Ubuntu Studio
---

### Post by kurja on 2014-12-18
A while back a friend of mine with no prior linux experience installed Ubuntu Studio 14.04 on an old pc, presumably with default options during the install. Now the install has developed a problem: automatic update fails due to insufficient space on 'boot' partition. I took a look at the machine via gparted, and there seems to be a 'boot' partition that is only ~100MB large. Is it supposed to be so small by default??

Extended partition has a few hundred GB of space, most of it free. There is no unpartitioned space on the disk. I have never used gparted to resize partitions (previously done that in ms-dos, ahem, a while back), and did not dare to start playing with it; should it be ran from live cd/dvd if I wanted to touch the 'boot' partition? I suppose I need to reduce the extended partition first, so I could allocate more space for boot partition - is that as easy as it sounds? Or is there a different recommended fix for this?

---

### Post by Elfy on 2014-12-18
Are you sure it's ~100Mb - I'd expect it to be ~240Mb and if it is then

> presumably with default options during the install

isn't what happened - they probably installed with LVM - not default at all.

[lpbug]1357093[/lpbug]

You can't resize an [LVM]("http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume") partition in the same way. 

Of course without seeing how the partitions are laid out this could be guess work. 

```
df -h
```

As it stands, without resizing, removing old kernels is what you need to do. Then you'll be able to update to new kernels, then in future watch /boot prior to updating kernels.

---

### Post by sudodus on 2014-12-18
I'd recommend to have /boot as a directory in the root partition, and I think it is standard, at least it was in Ubuntu Studio 12.04 LTS. If a separate boot partition, it should definitely be bigger, at the very least 200 MB, and still it must be maintained carefully (removing old kernels), otherwise it will be too full to allow installing new kernels.

Before editing partitions, ***backup everything important***, at least all personal files and make recovery files for Windows if dual boot. It is not difficult but ***risky***. Not only mistakes, but also an electric power outage during the process might destroy the partition system and or some file system.

Boot from an external drive and use gparted to edit the partitions. If you move the head of the boot partition (or the partition with the boot directory), you must also reinstall grub, which is possible but an extra thing to do.

-o-

It might be better (easier and faster) to make a clean installation (to re-install and copy back the personal files from the backup) instead of editing the partitions.

---

### Post by Elfy on 2014-12-18
> I think it is standard, at least it was in Ubuntu Studio 12.04 LTS.

maybe, but we're talking about 

> installed Ubuntu Studio 14.04

:)

---

### Post by ajgreeny on 2014-12-18
The alternative which is much easier, as mentioned by Elfy and sudodus, is simply to clear out the unnecessary kernels in your /boot partition which are taking the space.  How many kernels have you got installed?
Let's see the output of ```
ls /boot | grep vmlinuz
```

---

### Post by kurja on 2014-12-18
I can't give more details atm as it's not my computer and I don't have it here, but since the system has not seen much tweaking or had lots of software installed on it, he's just been using the bundled software for his music stuff, I think it might really be easiest to just do a reinstall - this time paying more attention to any and all options presented during install ;)

Thanks for the responses everyone, I didn't even know about lvm.

---

### Post by Elfy on 2014-12-18
> **kurja said:**
> ... this time paying more attention to any and all options presented during install ;)

Thanks for the responses everyone, I didn't even know about lvm.

If they (or you) re-install and use encrypted it will set up a /boot partition. Bear that in mind :)

---

