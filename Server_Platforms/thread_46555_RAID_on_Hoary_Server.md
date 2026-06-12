---
title: "RAID on Hoary Server"
date: 2005-07-05
forum: Server Platforms
---

### Post by Zinkeldonk on 2005-07-05
Hi folks,

I set up a client with Ubuntu Hoary. Server has 2 SATA disks and I have set up RAID 1 on the disks. Everything installed swimmingly until the reboot. Then, it would not start properly. It seems the problem is that md* are not created in the /dev/ directory. I create them manually, run mdadm command to "create" the new RAID device (even though it was created before). I then hotadd  the partitions that were part of the original array and mount the md device and viola, things work again.

My questions are:
1) Why, if I create the /dev/md* do they not stay created
2) Why should the RAID device not start at system boot (although, I do suspect that it has something to do with (1) above)

What is happening here? Any assistance will be most helpful.

Thanks
zD

---

### Post by steven_ellis on 2005-07-06
Have you tried re-creating your initrd files since your installed raid. Chances are you don't have full raid support in there.

Also what does your /etc/mdadm/mdadm.conf look like. I also had some raid issues, but they were with RAID 0 partitions.

What it sounds like is that raid is kicking in before your sata driver so the devices never get detected.

Have you tried

mdadm -a --scan

After you have performed a reboot?

Steve

---

### Post by tonym on 2005-07-06
Some things to try:

Is your root partition on RAID and if so have you created an initrd file with the appropriate drivers.  If not call dpkg-reconfigre for your kernel package when RAID is working.

Check that the RAID partitions are type "FD" - RAID autodetect.

Delete /etc/mdadm/mdadm.conf.  It seems to cause more problems than it solves.

Add "sleep 5" at the start of /etc/init.d/checkfs.  This gives time for the /dev/mdx devices to be created before checkfs kicks in.

Are the modules needed for your sata controller being loaded?  Try adding lines to /etc/modules and /etc/mkinitrd/modules.  You'll need to run dpkg-reconfigure on your kernel modules when you change the latter.

---

