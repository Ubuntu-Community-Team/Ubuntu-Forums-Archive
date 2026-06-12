---
title: "my first raid (1)"
date: 2010-12-23
forum: Server Platforms
---

### Post by zander1013 on 2010-12-23
hi,

i have setup my first raid (a raid 1) using a pair of 4gb usb sticks.

i have followed the instructions here...
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

rather than use 10.04 alternate iso i have used the 10.10 alternate iso from a third usb stick.

i am at the point "Configuring the RAID". in step 7 of this section i have done as instructed for the ext4 partitions. i have left out the swap partitions (after all they were left out of the instruction). is this correct?

also the drives appear to be syncing as described in the instruction.

the installer has taken me back to the Partition Disks installer menu. the drives appear to still be syncing should i wait until their chatter has stopped before selecting "finish"?

so the questions are should i sync the swap spaces? and when should i select "finish" in the installer?

thank you.

---

### Post by zander1013 on 2010-12-23
well i have just followed the instructions given in the previous link. mostly all seems to be well <mostly>...

i am running 10.10 desktop on a netbook. i have installed mdadm. here is the result of mdadm -query ...

> af@jayne:~$ sudo mdadm --query --detail /dev/md*
[sudo] password for af: 
/dev/md0:
        Version : 00.90
  Creation Time : Thu Dec 23 11:32:19 2010
     Raid Level : raid1
     Array Size : 3687360 (3.52 GiB 3.78 GB)
  Used Dev Size : 3687360 (3.52 GiB 3.78 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Dec 23 12:04:56 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 74380809:d00ffa12:ef32bd85:f9dc5bba
         Events : 0.18

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
af@jayne:~$

please confirm if you can whats shown so far.

as i noted its my first raid.  things look okay here to me.

!!! i think all is well above !!!

i am having some difficulty following the instructions in "Booting from Degraded Disk" when i try to edit the file as directed i get...

> sudo edit /etc/initramfs-tools/conf.d/mdadm
Warning: unknown mime-type for "/etc/initramfs-tools/conf.d/mdadm" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"


!!! i used vi instead of edit and was able to edit the file. !!!

however!!! i was not able to boot to the drives as described in the link.

i am going to mark this thread as solved and start new ones for the particular issues that remain.

thank you.

---

