---
title: "Server won't boot - help with repair on boot"
date: 2012-10-25
forum: Server Platforms
---

### Post by xkaliburx on 2012-10-25
Have 2 identical servers and overnight a cleanup script didnt run.  When I tried to delete some logs I got a r/o filesystem so simply rebooted.  The box is remote but I have remote PDU for power and KVM.  On boot the systems fails after initial ramdisk, then run through some stuff ending with;
Please append a correct "root=" boot option here are the available partitions (with a list of the partitions).

I had a friend stick a server 12.04 LTS cd in and it booted.  I went into Rescue a broken system but I am a bit confused (I'm used to the old partition days), but have an identical server which helps.  So I booted into recovery, but stuck at one spot.   The computers have 3 drives;
sda = 160G (primay OS, etc.)
sdb = 3T (data)
sdc =1T (data)

The partition tables look like this;
sda1 - boot partition
sda2 - swap
sda3 - / root partition

The problem is when I do a mount I see;
/dev/mapper/svr1-root           125G  6.6G  112G   6% /  (along with the other things)

So I will have to read up on how these work vs the old mount the partition, but how do I fix this.  When I go into rescue,  I see both the partitions (the sda1 and the /dev/mapper/svr ones)

Which do I select for the root partition when it asks, I don't see /dev/sda3 (the root) but do see /dev/svr1/root as well as assemble raid do not a root file system.

Once /dev/svr1/root was selected I was greeted with;
execute a shell in /dev/svr1/root
execute a shell in the installer environment
choose a different root file system

Which of the above should I select and what commands should be issued?


Also, if I have problems with rescue mode, could I simply say install, not format the drive (note I may lose some patches which I can re-do) but would that work as well?  I really want to avoid a long drive to our co-lo!

Thanks

---

