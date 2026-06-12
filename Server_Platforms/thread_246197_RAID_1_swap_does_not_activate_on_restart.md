---
title: "RAID 1 swap does not activate on restart"
date: 2006-08-28
forum: Server Platforms
---

### Post by Akhran on 2006-08-28
I have 2 harddisks, sda and sdb.

/dev/md0 consists of sda2 and sdb2, mounted as /

I have created /dev/md1 consisting of two swap partitions, /dev/sda1 and /dev/sdb1, with the following:

# mdadm --create /dev/md1 -l1 -n2 -x0 /dev/sda1 /dev/sdb1
# mkswap /dev/md1

Then I edit /etc/fstab to add the following:

/dev/md1 none swap sw 0 0

# swapon -a

Following which, I edit the /etc/mdadm/mdadm.conf with 

# rm /etc/mdadm/mdadm.conf
# mdadm --detail --scan > /etc/mdadm/mdadm.conf
# MAILADDR root >> /etc/mdadm/mdadm.conf

After I reboot, the swap (/dev/md1) is active. However, if I unplug one of the disk (sda) to test if the RAID works, the system still boot (I've installed GRUB on the both harddisks), but the swap (/dev/md1) is not active.

How should I go about enabling /dev/md1 to activate on boot when one of the disk is unplugged?

Thanks !

---

