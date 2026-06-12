---
title: "Ubuntu server and SAN problems"
date: 2009-11-16
forum: Server Platforms
---

### Post by alfaceor on 2009-11-16
Hi people

I have a SAN(Storage Area Network) solution from IBM
- 2 Blades Chasis
- 1 Extern Storage 4.9 TB (RAID 5)
- Each Blade have a 146GB (RAID 1)

When the installation began this is how recognize the devices
```


SCSI1 (0,0,0) (sda) - 5.0 TB IBM 1726-4xx FAStT
	pri/log	   5.0 TB FREE SPACE
SCSI2 (0,0,0) (sdb) - 5.0 TB IBM 1726-4xx FAStT

SCSI4 (1,1,0) (sdc) - 146.0 GB LSILOGIC Logical Volume
	pri/log	   146.0 GB FREE SPACE

```

SCSI1 and SCSI2 are the same this is because we have 2 fiber channel for high avaibility (2 fiber channel for each chasis to the storage)

Then finish the installation
And in boot time
```

_Grub_
Error 21: Selected disk does not exist

```

So, i change the root (hd1,0) by root (hd0,0) and then start to boot. But i have errors like this

```

*loading hardware drivers ...
Buffer I/O error on device sdc, logical block 0
Buffer I/O error on device sdc, logical block 0 
Buffer I/O error on device sdc, logical block 0 
ldm_validate_partition_table(): Disk read failed
Buffer I/O error on device sdc, logical block 0
Buffer I/O error on device sdc, logical block 3
Buffer I/O error on device sdc, logical block 2
... 

```

After that i install multipath-tools, mdamd, kpartx
```

$ sudo multipath -d
sdc: checker msg is  "directio checker reports path is down"
create 360050.......20d LSILOGIC, logical volume
[size=136G][features=0][hwhandler=0]
\_ round-robin 0 [prio=1][undef]
 \_ 0:1:1:0 sda 8:0 [undef][ready]

```

Well after that i try to reinstall and i get this in the partition table
 
```

SCSI1 (0,0,0) (sda) - 5.0 TB IBM 1726-4xx FAStT
	#5 logical       600.3 GB 	ext3
		pri/log	   4.4 TB	FREE SPACE
SCSI2 (0,0,0) (sdb) - 5.0 TB IBM 1726-4xx FAStT
SCSI4 (1,1,0) (sdc) - 146.0 GB LSILOGIC Logical Volume
	#1 primary	140.0 GB B ext3
	#5 logical	  6.0 GB F swap  swap

```

FIRST PROBLEM
So what happen?! The installation just take 600 GB instead the 5TB. I don't understand why?

SECOND PROBLEM
I need a howto for the configuration of the multipath i don't found at google

I hope you guys can helpme

P.D.:Sorry my english is very bad.

---

### Post by ion-ral on 2010-03-13
if that's what I think you have a SAN controller LSI RDAC and you have to use this handler (rdac) but can not tell you how you set up during the installation, I read around how to do it but I've yet to try it (next week!) then I say, in the meantime please follow this link:

[http://blog.loftninjas.org/2008/06/13/debian-dell-md3000i-dm_multipath-and-path-checking/](http://blog.loftninjas.org/2008/06/13/debian-dell-md3000i-dm_multipath-and-path-checking/)

---

