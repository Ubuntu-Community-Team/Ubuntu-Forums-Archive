---
title: "Is btrfs ready for / partitions?"
date: 2011-04-12
forum: The Cafe
---

### Post by Starks on 2011-04-12
I have a separate /home that I intend to keep as ext4, but I'm curious if all the stability and repair issues have been resolved for btrfs.

---

### Post by davidmohammed on 2011-04-12
no - stay well clear for btrfs for / - its known to take forever to boot from... some-sort of incompatibility with ureadahead or something like that.

If you must use it in ubuntu - use it from /home and keep to ext4 for /

---

### Post by earthpigg on 2011-04-12
[http://arstechnica.com/science/news/2011/04/high-performance-computing-on-gamer-pcs-part-2-the-software-choices.ars](http://arstechnica.com/science/news/2011/04/high-performance-computing-on-gamer-pcs-part-2-the-software-choices.ars)

some dudes working on a $40,000 cluster say no.

they used ext4 for /, and (i think?) btrfs for /home - opposite of what you intend.

im sure they are also doing very frequent backups, including of /home, to mitigate risk.

---

### Post by del_diablo on 2011-04-12
Btrfs is ready for /, but it requires a ext2/3 /boot partition <3

---

### Post by Starks on 2011-04-12
Leading with /home is beyond stupid.

Your data is more valuable than your settings.

Also, I'm rather surprised that the /boot issue is still present. It should be resolved for Natty.

---

### Post by jerenept on 2011-04-12
> **earthpigg said:**
> [http://arstechnica.com/science/news/2011/04/high-performance-computing-on-gamer-pcs-part-2-the-software-choices.ars](http://arstechnica.com/science/news/2011/04/high-performance-computing-on-gamer-pcs-part-2-the-software-choices.ars)

some dudes working on a $40,000 cluster say no.

they used ext4 for /, and (i think?) btrfs for /home - opposite of what you intend.

im sure they are also doing very frequent backups, including of /home, to mitigate risk.



ZFS > BTRFS right now imho. 
This may change in the future though.

---

### Post by earthpigg on 2011-04-12
> **Starks said:**
> Leading with /home is beyond stupid.

Your data is more valuable than your settings.

Also, I'm rather surprised that the /boot issue is still present. It should be resolved for Natty.

i suppose that, for the slaves in a cluster, the configuration of / essentially becomes the vital data. 

with /home as just a very large extension of the ram, intended to store things only temporarily until the results of the calculations are determined and then returned to the master. is that a correct understanding?

could explain why they are OK with btrfs as /home on the slaves, if its performance is significantly better and assuming bad mojo resulting from btrfs is detected so that the resulting conclusions from that subset of calculations can be discarded. 

if that happens 3% of the time but makes the calculations 10% faster, it is a reasonable economic trade on the margin (the goal was a $40,000 cluster using off-the-shelf components that performed comparably to a $400,000 IBM). meanwhile, the custom software that runs the slaves is safe-and-sound from btrfs shenanigans in ext4.

---

### Post by Starks on 2011-04-12
ZFS is amazing filesystem if you overlook the fact that Oracle's license makes it difficult to incorporate into Linux.

---

### Post by jerenept on 2011-04-12
> **Starks said:**
> ZFS is amazing filesystem if you overlook the fact that Oracle's license makes it difficult to incorporate into Linux.

True. I suppose btrfs is trying to combat that?
If I need the features of ZFS, though, I would just run FreeBSD. :P

---

### Post by BlacqWolf on 2011-04-12
> **Starks said:**
> I have a separate /home that I intend to keep as ext4, but I'm curious if all the stability and repair issues have been resolved for btrfs.
 
I have previously had a good experience with a speed boost with BTRFS on 10.10 when I ran Ubuntu from a flash drive. But with my experience with it running on 11.04 on a virtual HD, it just doesn't boot, whereas XFS, JFS, and ext all work fine.

---

### Post by matthewbpt on 2011-04-12
I have btrfs root and boot and home on my netbook, it works great! (syslinux supports /boot being btrfs atm) I had one problem though... I enabled transparent compression (very cool btrfs option!) without realizing that syslinux doesn't support reading compressed files, I then edited the syslinux conf file because i wanted to change some boot parameters, saving it subsequently meant that the file was now compressed, and when rebooting syslinux couldn't read the configuration so it would not into the kernel by itself, I had to drop to the syslinux prompt and manually select the kernel image and initrd image and parameters to boot, which took a while to figure out how to do as I didn't have internet access at the time. Once I did I just disabled compression and reedited the file, now it works again. So remember kids, don't enable compression on /boot !

---

