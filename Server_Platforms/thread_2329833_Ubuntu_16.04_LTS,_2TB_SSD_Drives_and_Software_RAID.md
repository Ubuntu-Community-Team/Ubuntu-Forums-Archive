---
title: "Ubuntu 16.04 LTS, 2TB SSD Drives and Software RAID5."
date: 2016-07-05
forum: Server Platforms
---

### Post by networkingguy2 on 2016-07-05
Good morning all, 

I have been working on this for about a week now and have decided to ask for a little help. 

My company has been utilizing Ubuntu LTS versions in their servers for an ELK stack over the course of the past year we have built 4 servers all using software RAID5 as the hardware raid built into the servers only uses RAID0, RAID1, or RAID10. This however is the first server we have used Ubuntu 16.04 LTS with. 

The specs of this server are as follows:
[LIST]
[*]1x SuperMicro SYS-1027R-WRFT+ "SuperServer"
[*]2x Intel Xeon E5-2650 V2 (LGA2011)
[*]12x Crucial 16GB DDR3-1866 RDIMM 1.5V CL13
[*]6x Samsung SSD 850 Pro 2TB Drives
[/LIST]

When I install Ubuntu, I configure a software raid 5 and select the 10tb raid partition created to install Ubuntu 16.04. When the install gets all the way to the end and attempts the grub install we receive an error that Grub could not being installed. When I click continue without grub, I get this error.

[img]http://i.imgur.com/cPWW5bk.png[/img]


When I have this error I attempt to manually boot into Ubuntu using “vmlinuz boot=/dev/md0p2” but it gives me a kernel panic.
 
I have done this a few times today, deleting the raid, recreating it, trying different options but no matter what I try, grub fails every single time. I am completely out of ideas.

[img]http://i.imgur.com/PVYjoam.jpg[/img]



I have discussed with my direct management the need for a hardware RAID necessity, but needless to say his requirements stand strong. Ubuntu 16.04 LTS and software RAID5. Can anyone assist?

---

### Post by darkod on 2016-07-05
Are you installing in bios mode or uefi mode? The mode in which ubuntu will install depends on how you boot the install media.

If you have usb stick for example and boot it in UEFI mode, it will try to install in UEFI mode.

But for that to work, you need small partition on each disk where you want grub installed, without any filesystem and with bios_grub flag set. I see on sda, sdb, sdc,etc you only have the big raid partition. No bios_grub partition.

This could be one of the reasons why grub doesn't install.

---

### Post by darkod on 2016-07-05
My mistake with the previous post. You need that small bios_grub partition if the disks have GPT tables. In such case the MBR is smaller and grub2 doesn't fit.

So, on all disks (because that's where grub is installed, not on the array), you need a small 1MiB partition with no filesystem (DO NOT format it) and with bios_grub flag set.

After that grub should install fine. All this is assuming you are using bios boot. If you want to use uefi boot you need EFI partition which is completely different thing.

---

### Post by networkingguy2 on 2016-07-05
When I went to set the 1MB partition with the bios_grub flag I am greeted with:
[img]http://i.imgur.com/Lj52oaP.jpg[/img]

Should I be taking the 1mb from the 1mb "Free Space" section of sdba for example?

---

### Post by darkod on 2016-07-05
Yes, the 1MB partition should be on sda, sdb, etc, on all physical disks. And you need to remove the biosgrub you have on the raid array shown on that picture. It will confuse the installer.

In fact, I think you better repartition everything. There is no sufficient free space on the disks to make 1MB partition now. I would also use this occasion to reconsider if you want one huge root of 10TB or smaller root partition/array in raid1 and then big raid5 array for the data.

I think it can work with that huge root but people usually don't do it that way.

The installer can be little off for precise partitioning, so you can use ubuntu desktop live cd, boot the machine with it in live mode, and use the terminal and parted to create the needed partitions. After that with the server installer you just create the software raid and you install. The partitions you need will already exist. That would be my recommendation...

---

### Post by networkingguy2 on 2016-07-05
Thank you for the reply. I am going to attempt the live CD method.

---

### Post by lukeiamyourfather on 2016-07-05
ZFS would be better suited than md for this. Like darkod said, you need a UEFI or boot partition that isn't part of the RAID if you go that route.

---

