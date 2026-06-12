---
title: "Problems with df in gutsy server"
date: 2007-12-07
forum: Server Platforms
---

### Post by MatthewMetzger on 2007-12-07
I just upgraded my server from dapper to gutsy (aptitude dist-upgrade through each release). It seemed to work fine, but I'm getting strange output from df.

I usually use df -h to check on the status of my mounted volumes, but now df -h only shows this:

Filesystem            Size  Used Avail Use% Mounted on
varrun                506M  176K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M   27M  480M   6% /dev
devshm                506M     0  506M   0% /dev/shm

There is no mention of my partitions /boot, /, or /storage (my mount point for a large RAID and LVM volume). This makes me a bit worried.

Has anyone else experienced this problem? Has the basic behavior of df changed?

My /etc/fstab does have this line:
/dev/mapper/storage-backup /storage        xfs     noatime         0       2

so I know that my LVM volume is mounted correctly, but df -h just doesn't behave as I think it should.

---

### Post by MatthewMetzger on 2007-12-07
There was something wrong with the kernel I was using. I booted from the previous kernel and everything seems to be fine.

Here's what I removed to get it working:

sudo aptitude remove linux-image-2.6.22-14-386
sudo apt-get remove linux-image-2.6.22-14-server

Major problems with 2.6.22-14, but everything seems to work fine with 2.6.20-16-server. I'm not sure why that is.

---

