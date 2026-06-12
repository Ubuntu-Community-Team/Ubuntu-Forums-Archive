---
title: "Software raid5 with mdadm does not survive reboot"
date: 2005-05-12
forum: Server Platforms
---

### Post by vulture99 on 2005-05-12
Hello,

I set up software raid5 on an Ubuntu 5.04 box, server install, amd64.  The kernel was upgraded to 2.6.11-1-amd64-generic so that my Promise SATA controller would be detected.  Everything went well, except that the array doesn't survive a reboot!  After rebooting, there is no /dev/md0.  

I can't find any pertinent messages in dmesg output, other than a single md line:
   md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
Seems like md should be doing a lot more at boot time.

I have also tried the following after rebooting:

# mdadm --examine --brief --scan --config=partitions
Bus error
# mdadm --assemble --scan
mdadm: error opening /dev/md0: No such file or directory
# mdadm --assemble /dev/md0 /dev/sd[a-f]1
mdadm: error opening /dev/md0: No such file or directory

Can anyone give me a hand?  Maybe I just missed some important step...


1) Command used to create the array:
# mdadm -Cv /dev/md0 --chunk=64 --level=5 --parity=left-symmetric --spare-devices=1 --raid-devices=5 /dev/sd[a-f]1

2) # cat /proc/mdstat  showed array being created just fine

3) Verified array next morning:  # mdadm -D /dev/md0  It was created successfully.

4) Created mdadm.conf.  # mdadm --detail --scan >> /etc/mdadm/mdadm.conf  (added DEVICE line manually)
   DEVICE /dev/sd[a-f]1
   ARRAY /dev/md0 level=raid5 num-devices=5 spares=1 UUID=4e237259:e397c68d:bb6e92b9:a5f2d8c2
     devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sde1,/dev/sdf1

5) # mkfs -V -t xfs -f -d su=64k,sw=4 /dev/md0

6) # mkdir /mnt/raid

7) Edited /etc/fstab, adding line:   /dev/md0  /mnt/raid  xfs  defaults  1  2

8 ) # mount -a

9) # df -h  (verifed that raid volume was mounted...it was)

10) # dpkg-reconfigure mdadm  (reconfigured to start array automagically when machine is booted).

11) # reboot

---

### Post by alastair on 2005-05-15
I don't know. But it might be something to do with the Promise card and kernel 2.6.11. If you know the driver required for the card, perhaps add it to the /etc/modules file (to make sure it is loaded as early as possible). A guess though.

---

### Post by LordHunter317 on 2005-05-15
Without a complete boot log, there's no way to know.  Posting the output of lsmod and dmesg after a clean boot would be helpful.

But it sounds like the driver for the disks isn't being loaded, so the array can't autostart.

Can you access the individual disks?  If no, the chipset driver isn't loaded yet, and that's what's stopping you.  You need access to the disks before the array can run.

---

### Post by six6 on 2005-05-23
I have a nearly identical problem. I thought it was because the system wasn't loading the drivers for the sata before it tried initializing the raid. It does load the ide drivers, though, because it says something like "Can't create array (2/3) devices missing..." and I have two SATA disks and one PATA.

Anyway, how do I load the SATA drivers first? Somewhere in /etc/init.d/?

---

