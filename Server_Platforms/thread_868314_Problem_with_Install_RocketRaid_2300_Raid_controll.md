---
title: "Problem with Install RocketRaid 2300 Raid controller"
date: 2008-07-23
forum: Server Platforms
---

### Post by saint818 on 2008-07-23
I am using Ubuntu 8.0.4 and the kernel version of 2.6.24-16-server on my system and using 1 SATA drives as a storage.

Recently, I bought 4 more SATA Disks made by the Seagate and Rocketraid 2300 Raid controller which could add 4 more SATA drives to store more data.

After I install the controller and the open source driver from Highpoint Tech (since there was no driver for Ubuntu), the system boots up with all 5 hard drives (1 is connected to the board directly, 4 are connected to the controller).

However, 1 of 4 disk drives which connected to the controller does not work properly; it keeps throwing the following error

ata3.00: Exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata3.00: cmd c8/00:00:00fe:00/00:00:00:00:00/e0 tag 0 dma 131072
in
ata3.00: status: {DRDY }

I am not sure that this problem is caused by

1. not properly installed controller?

2. not properly compiled and loaded driver?

3. a kernel bug?

If any1 knows how to install the RocketRaid 2300 raid controller, please let me know how to do it.

thanks in advance

---

### Post by wirelessmonkey on 2008-07-23
looks more like a problem with the drive than with the raid controller...

OTOH, I have 3 RocketRaid SATA Controllers that I have never been able to get working in any Linux distros, IMO highpoint just kinda sucks.

---

### Post by TomB19 on 2009-03-28
I want to add a 4 x 1.5 TB Seagate software raid to my Kubuntu 8.10 AMD64 system.  I don't care about hardware raid as I really like software raid on linux.

The system has 6 SATA ports on the MB but they are consumed by another 6 drive SATA raid.  I've also got a 2 port eSATA card based on the Marvel chipset, I think.

I'm considering the Highpoint RocketRAID 2300.  I like that it takes a single PCIe slot and has 4 internal ports.

I don't want to fool around with closed source drivers.

If I don't care about their soft/hardware raid, will Kubuntu 8.10 see the RR2300 connected drives without installing Highpoint's driver?  I'm guessing it will see the drives as plain old /dev/sdX devices.

Thanks!

---

### Post by windependence on 2009-03-28
> **wirelessmonkey said:**
> looks more like a problem with the drive than with the raid controller...

OTOH, I have 3 RocketRaid SATA Controllers that I have never been able to get working in any Linux distros, IMO highpoint just kinda sucks.
X2. I have one of their junky controllers here new in the box if anyone wants to buy it. I have never been able to get their stuff to work right either and they are pricey. 

Tom, you can get a controller cheap that Linux will recognize. You have to also get out of that Windoze mode. You don't need to load all kinds of funky driver stuff in Linux. Most times, the drivers are built in to the kernel. I don't usually load their driver unless it doesn't work without it, and then I'd rather not.

-Tim

---

