---
title: "raid auto-assemble broken"
date: 2008-05-27
forum: Server Platforms
---

### Post by pagingmrherman on 2008-05-27
I upgraded from Dapper LTS to 8.04 LTS and now my RAID arrays never assemble automatically.  What happened?  I run LVM on top of software RAID for my data drives and they don't auto-mount on bootup any more.  I have to do the following:

mdadm --assemble /dev/md0 /dev/sdb /dev/sdc
mdadm --assemble /dev/md1 /dev/sdd /dev/sde

Then udev kicks in and the LVM devices appear so I can mount them.

Does the CONFIG_MD_RAID1 module have to be built into the kernel?
Do I have to put a custom mdadm.conf in the initrd?

All I want is to be able to take the 4 drives out, slam them in another system in case things go wrong, reboot, and have all the lvm devices automatically generated.  Is that such a huge thing to ask??

Lost in RAID hell,
PW

---

### Post by windependence on 2008-05-28
Well IMHO this would be hell to recover from if you had a problem with corrupted disks. I would use either LVM or RAID but not both. Recovering from either on can be difficult if you don't have a very good backup.

Just my $.02

-Tim

---

### Post by pagingmrherman on 2008-05-28
I've got a DLT tape drive that runs daily backups so that's fine.  What's so hard about recovering from a corrupt disk?  Replace the drive, resynch the array, redetect the volume groups and mount them.  I just want to know what's so hard about auto-assembling RAID1 arrays?  It used to work before in Dapper! 

PW

---

### Post by pagingmrherman on 2008-06-01
I guess I was right - auto-assembly of RAID arrays is impossible.  Looks like if you want auto assembly, you have to spend some $$ on a hardware RAID card.

---

