---
title: "XEN Guest Swap partition problem"
date: 2015-04-09
forum: Virtualisation
---

### Post by sklpr on 2015-04-09
Hello all, 

I am trying to configure a domU guest for Xen Hypervisor [HVM - mode - > fully virtualized] , so I follow every instruction on this  [guide!]("http://www.virtuatopia.com/index.php/Building_a_Xen_Virtual_Guest_Filesystem_using_Logical_Volume_Management_%28LVM%29")

Xen Hypervisor is directly installed on hardware drive */dev/sdd4* with right partitions (with LVM partition for guests) as mentioned on official Ubuntu website

But I am a bit confused about the mkswap command in order to ***"Configure the Swap Partition for the Xen Guest System"*** 

// *sda* is a hard-drive with Ubuntu - desktop installed (my primary OS) 
// and *sdd* is another hard-drive has XEN dom0 (installed on Ubuntu Server 12.04.5) and LVM for guests 

**-- fdisk - l** output for sda and sdd:

[http://i58.tinypic.com/30wwl5e.jpg]("http://i58.tinypic.com/30wwl5e.jpg")

[http://i57.tinypic.com/5y7qtf.jpg]("http://i57.tinypic.com/5y7qtf.jpg")

**-- cat /etc/fstab ** output :

[http://i60.tinypic.com/2yp0jye.jpg]("http://i60.tinypic.com/2yp0jye.jpg")

**-- swapon -s** output :

[http://i58.tinypic.com/zksx2c.jpg]("http://i58.tinypic.com/zksx2c.jpg")

The error I get when i am trying to : mkswap /dev/sdd2 is : **Device or resource busy**

So if I try to unmount /dev/sdd2 will it fix it or i will mess up the system and I will have to format and re-install it again ? ? :-/

Please ask me if you need further information about my system or problem.. 

Thanks in advance !

---

