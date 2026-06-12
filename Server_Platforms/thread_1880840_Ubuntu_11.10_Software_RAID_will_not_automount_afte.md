---
title: "Ubuntu 11.10 Software RAID will not automount after reboot."
date: 2011-11-14
forum: Server Platforms
---

### Post by aimwin on 2011-11-14
Hardware
Intel Main Board DH67BL, RAM 3.8GB
2 x SSD 60 GB 
2 x Hard Disk 2 TB => Raid1, DATA

This first part of RAID is generated using Alternate CD Ubuntu 11.10
The 2 x SSD 60GB
First of 55 GB on both SSD used for RAID1.=> MD0
the last 5 GB on both SSD are used for SWAP, non raid.

They started Ubuntu at reboot not problems.

This DATA parts are created by using "Disk Utility" GUI from Desktop.
(This 2TB RAID was created by Alternate CD at the first time, but due to bugs in kernel 3.0.0-12 on external USB drives, wreck the RAID by freezing server and I have to turn off AC power to the server. After upgrade to pre-released 3.0.0-13 kernel and all updates. I used Disk Utility to repartitioning and configure RAID 1)

The 2TB pair.
First 200GB of both 2TB Disk is used as non Raid DATA.
The rest were divided into 3 raid MD1 (100GB), MD2(300GB), MD3(1400GB).

All functions works fine, testing by hot plug removing the one half of the pair, data is still accessible and intact.

The only problem is it will not automount RAID.

instead it has a message saying the raid was not mounted and to press S to skip it. 

We need to press this twice and then it loads Ubuntu. 

Any ideas on a fix to this?

---

### Post by darkod on 2011-11-14
Have you checked what /etc/fstab says? Which entries exist?

Since the raid was recreated later with disk utility I don't think that puts an entry in /etc/fstab automatically. The original entry from the alternate installer might be there but if you reformatted the raid the UUIDs might be different now, or something along those lines.

---

### Post by aimwin on 2011-11-16
> **darkod said:**
> Have you checked what /etc/fstab says? Which entries exist?

Since the raid was recreated later with disk utility I don't think that puts an entry in /etc/fstab automatically. The original entry from the alternate installer might be there but if you reformatted the raid the UUIDs might be different now, or something along those lines.

Thank you for that suggestion, I thought that is the case,
I will look into that and will report it back here.

---

### Post by aimwin on 2011-11-22
Thanks for the advice, please give me more on below problems after I degraded the RAID.

but after googled a lot on subjects,

I have decide to do a new Altenate CD ubuntu 11.10 installation.
md0 for /root and /boot, md1 for swap and md2 for data.

Yes both Raids worked fine now I had reboot many times and it won't break.
Auto Started and clean.

I post below for references to others who are facing the same problems.

==============>> from /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=ba894259-b1a3-44fa-90d7-069d4258a147 /               ext4    errors=remount-ro 0       1
# swap was on /dev/md1 during installation
UUID=65e1a073-0eea-4653-af0d-8f8e2b3452f0 none            swap    sw              0       0

=======> and from /etc/mdadm/mdadm.conf
# definitions of existing MD arrays
ARRAY /dev/md/2 metadata=1.2 UUID=bb7bf0d5:202d9427:2eed99c7:29af942e name=Rubuntu:2
ARRAY /dev/md/0 metadata=1.2 UUID=00db16b7:690bde40:febd1eaf:7b9c41ab name=Rubuntu:0
ARRAY /dev/md/1 metadata=1.2 UUID=96571ff1:b89db656:7020f9f7:4bb35005 name=Rubuntu:1

But I test the RAID by pulling off 2 hard disk which is half of md0/md1 and md2.

I can easily repair md2 once I put back the removed hard disk.
Just use "Disk Utility", click unmount, stop RAID, and repair function, (GUI)

But I can't find a way to repair the boot-root md0 and the swap md1.
It is degraded and I try a few methods include 
[http://en.wikipedia.org/wiki/Mdadm](http://en.wikipedia.org/wiki/Mdadm)

we have to unmount the drive before we can repair it.
but it is being used as boot/root is in md0 and swap is md1.

Is there any way to re assemble the md0/md1 without have to zero both drive and reinstall the whole lot all over again.

Thanks in advance.

---

### Post by rubylaser on 2011-11-22
You'll need to use the command line to re-assemble your array.  Also, your /etc/mdadm/mdadm.conf file looks wrong.  But, I'd like to see output from these commands first before recommending anything.

```
mdadm --detail --scan
```

And, 
```
mdadm -E /dev/sd[ab]1
```
```
mdadm -E /dev/sd[ab]2
```
```
mdadm -E /dev/sd[ab]5
```

---

### Post by aimwin on 2011-11-30
Thank You rubylaser and darkod

Sorry my Intel-Server Board is "corrupted",
I have to sent it for warranty claim.

Bios Chip is Dead, it will not boot, but If used usb-Intel-Bios,
then it will boot with usb-bios.

That happen after a very successful Alternate CD Ubuntu 11.10 Raid Installation. 
On reboot, the bios chip is dead, won't boot.

I was joking (still think more than a joke though) with Intel Technical staff that, when I received the server board back, I will do it exact again and see if Alternate CD has a virus that can destroy Intel Bios Chip or not.

So I will find alternative board and will redone the RAID again in the next few days, since it will be more than 10 days before I will get the server board back.

Thanks for your response for the moment.

---

