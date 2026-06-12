---
title: "Improve data integrity using virtual RAID?"
date: 2013-01-05
forum: Virtualisation
---

### Post by JoeSabido on 2013-01-05
Base system: Ubuntu 12 64
Storage: Two 500GB hard drives, setup as RAID1 during setup (using Alternate CD)
Virtualisation: KVM (Using virt-manager)

Guest: Ubuntu 10.04 LAMP server.

I know that thanks to the array, if ONE hard drive were to fail, my information would be safe.

Now, let's say for the sake of argument, that Earth has been invaded by strange crab-like creatures from another planet, and one of these creatures ungracefully unplugs the HOST.

If that were to induce errors in the HOST filesystem, and that in turn damaged the IMG filesystem file of the GUEST, wouldn't that pretty much damage the GUEST itself? Like hitting the virtual hard drive with a hammer.

Now, what would happen if I created my GUEST with two virtual IMG files and declared them as RAID1? That way even if one of the IMG files gets corrupted, I would detach it from the guest, add another one, then boot the guest with a degraded array and dechare the new IMG file as a spare.

Does this make any sense? Would it work? 
Yes/no >> Why?

Thanks!

---

### Post by dcstar on 2013-01-10
RAID protects against individual hardware failure, not software failure or power failure (unless you are very lucky and circumstances result in sufficient devices not suffering corruption).

Unless your RAID devices - virtual or real - are all on separate hardware devices then you do not have **any** protection.


* Please note that RAID protection never, ever applies to so-called "RAID-0" striping which **guarantees total loss of all data** if any device fails - it is the exact opposite of redundancy.

---

### Post by drdos2006 on 2013-01-10
I have just started to look at Nexentastor ( which requires a barebone box rather than a VM ). The file system is based on Solaris ZFS which manages data integrity on-the-fly and allows for the RAID to transfer from a backup harddisk, if the disk starts to fail.

It might be what you want.

regards

---

