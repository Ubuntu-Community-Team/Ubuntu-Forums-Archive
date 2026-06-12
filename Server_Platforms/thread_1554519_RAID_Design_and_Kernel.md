---
title: "RAID Design and Kernel"
date: 2010-08-16
forum: Server Platforms
---

### Post by iaw4 on 2010-08-16
Dear Experts:

I have been running ubuntu 10.04 for a while now.  The boot drives are software RAID-1 mirrored (mdadm).  Interestingly, they nicely mount at bootup and are rather stable AS LONG AS I use the kernel that came with the original ubuntu-server 10.04 release, which is 2.6.32-21.  as soon as I try one of the newer kernels pushed via the update, such as the -22, -23, or -24 kernels, the drives are no longer seen.  (even the /dev/by-uuid hierarchy disappears, which means that my uuid identified array no longer mounts.)

well, I now have the chance to rebuild my server, because the CPU water-cooler leaked.  not fun.

I want to use this opportunity to rebuild my system.  I would like some opinions and advice on what a solid configuration is.

I am thinking of building a new RAID array.  Safety and simplicity are first and foremost.  capacity is unimportant---1GB is enough.  so, I am thinking of building a software RAID-0 array with 4 drives.  a 1GB drive costs about $50/drive, so we are talking $200.  Reading speed is important.  Writing speed, oh well, not as important.  I presume the read speed of a 4*RAID-1 system will be about 3-4 times that of an individual drive, but the write speed will only be about the same as that of one individual drive.

I presume the recommendation for file system is still ext4.  btrfs is close, but no cigar yet.  correct?

now, is there a way to get around the weird ubuntu-server mdadm issues?

should I use LVM?  again, reading speed and reliability (both hardware crashes and new kernel compatibility) matter.  is LVM on its way out now that btrfs is on its way in, so I may as well just wait until btrfs does it?

(is btrfs in all ubuntu server and desktop kernels, so using it would guarantee that any kernel would understand a RAID-1 array controlled by it?)

any other advice?

/iaw

(It would be nice if the linux RAID-1 were smart enough to do "lazy writes"---as soon as one of the drives has a good copy, the others can be delayed for a few ms .  they all should be in themselves coherent, but they don't have to be in exactly the same coherence state.  if one drive dies, at most, I should lose a few ms worth of writes.  this should improve RAID-1 writing speed.)

---

