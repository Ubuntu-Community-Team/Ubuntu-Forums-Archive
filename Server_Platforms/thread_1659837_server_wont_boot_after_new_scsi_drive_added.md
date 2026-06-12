---
title: "server wont boot after new scsi drive added"
date: 2011-01-04
forum: Server Platforms
---

### Post by igorm80 on 2011-01-04
hi,

i have a dell server with existing hw raid running fine.
as soon as I create an additional raid on the controller with new disks, the system wont boot anymore. It falls through to initramfs stating that it can not find root.

this seems that the LUN's get reshuffled, and hence my
root (hd0,1) with real_root=/dev/sda1 does not work anymore.

Under initramfs shell, if i check my /dev/sd* devices, I do see that my 'used-to-be' sda1, sda2, sda5 has moved to sdc1, sdc2, sdc5 (i have not had a chance to partition my new raid), and the new raid I believe appears as a single /dev/sda device.

Now if on the next reboot I try to edit my grub to root into
/dev/sdc1 partition (as seen from previous boot), same thing happens - initramfs shell.

Can someone please lend me a hand figuring this out?

Thanks!

---

### Post by samosamo on 2011-01-04
What evidence do you have that the LUNs are changing?  If they are, you should look into using UUID's instead of explicitly specifying the disk device.

[http://www.unixtutorial.org/2008/05/ubuntu-uuid-how-to/](http://www.unixtutorial.org/2008/05/ubuntu-uuid-how-to/)

---

### Post by igorm80 on 2011-01-04
regarding the lun changes, that was only a supposition - 

simply by looking in the /dev/ after failed boot under initramfs. with the new disk in place, i get

sda
sdc
sdc1
sdc2
sdc5

With only a single disk with normal bootup, i get
sda
sda1
sda2
sda5

---

### Post by BlueVark on 2011-01-06
I will help bump this back to the top because I am having a similar problem.  About 25% of the time my server won't boot because it can't find the boot drive.  I changed to Fstab to use all UUID and still have the problem. 

Anybody have any ideas what could be causing this?

---

### Post by jeybee on 2011-02-15
Anyone figured this out?

I have the same problem.


My setup:
Ubuntu 10.04 LTS
Dell PowerEdge2800 server, 2 scsi disks in raid (mirroring), and one SIL3114 (4-port sata) controller with 4x2TB hdd's.
This worked fine..;)
But when I installed 3 more SIL3114 sata controllercards (yes, I have 4 PCI cards) the server normally halts during boot:cry:
At first boot, the server halts with the initramfs shell. when i type -reboot- the next time it usually starts fine but not always - sometimes I need to reboot 2-3 times before it starts normally. Then it works fine until next restart..

Any suggestions?

---

