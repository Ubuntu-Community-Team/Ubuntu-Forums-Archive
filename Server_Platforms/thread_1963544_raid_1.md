---
title: "raid 1"
date: 2012-04-22
forum: Server Platforms
---

### Post by Gareth_2007 on 2012-04-22
evening all,

right ive just bought 2 brand new 3tb seagate drives for my server and i'm looking to run raid 1. I've never set up a raid before so i have a few questions... Do i just need to configure it in the raid controller or will i need to configure it in ubuntu as well? do the dives need to be formatted before creating the raid? I'm running ubuntu server 11.10 and i will be doing a fresh install

cheers

---

### Post by darkod on 2012-04-22
You can use the fakeraid (bios raid), but if running only ubuntu you can also use software raid which many people prefer.

In case of software raid you do not configure anything in the raid controller, and the SATA mode in bios should be set to AHCI, not RAID. The raid is configured on OS level.

Will the OS be on the array too, or on a third disk?

---

### Post by Gareth_2007 on 2012-04-23
hi darkod thanks for the reply.

i was planning on running the os on the array, or would it be better to run it on a 3rd drive?

---

### Post by darkod on 2012-04-23
I would put it on the array because even if one disk dies, the server will still keep on running.
If the OS is on a third disk and it dies, it stops working until you sort that out.

Since this is a server and you probably don't plan to dual boot, I would use mdadm and software raid to create the RAID1 array. Note that for 3TB you will need to use GPT partition table on the disks.

The idea is simple:
1. Start the server installation. When you reach the partitioning step select Manual.
2. Create one single partition taking whole of the 3TB disk with type Linux RAID. Do the same on the other disk.
3. Above the partitions list, select the Configure Software raid option. That will ask you what level or raid you want (RAID1), the number of devices (2), and to select the devices (partitions) to be used. Note that you select with Space, not Enter. Press Space and watch a small mark to appear that you have selected the partitions to be used. When you create the device it will appear in the partitions list as separate device.
4. Create the root, swap, and any other partitions you want onto this raid device.
5. Continue with the installation.

---

### Post by Gareth_2007 on 2012-04-23
thank you for the help. i'll start it tomorrow and let you know how it goes

---

### Post by a2j on 2012-04-23
If more than 2 partitions needed (swap+1more), I'd use LVM over RAID1. You should be OK with putting OS on that array. Grub should be installed on both drives. You can use *mdadm* to accomplish your task.

---

