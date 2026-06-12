---
title: "Non-existent drive shows up: drive is part of a NAS Raid pair"
date: 2017-02-21
forum: Server Platforms
---

### Post by DaleAmon on 2017-02-21
I have a two blade servers on an Intel Modular server with storage coming from a
NAS and both machines are incorrectly showing the second drive of the raid pair.
Rather than get into loads of description, here are the important facts from lshw on
one of the two:

```
	*-disk:0
		description: SCSI Disk
		product: Multi-Flex
		vendor: Intel
		physical id: 0.0.0
		bus info: scsi@1:0.0.0
		logical name: /dev/sdb
		version: 0311
		serial: 4C2020200000000000000000907579A4970C595F
		size: 75GiB (80GB)
		capacity: 75GiB (80GB)
		capabilities: 15000rpm partitioned partitioned:dos
		configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=0008ac72
	*-disk:1
		description: SCSI Disk
		product: Multi-Flex
		vendor: Intel
		physical id: 0.1.0
		bus info: scsi@1:0.1.0
		logical name: /dev/sdc
		version: 0311
		serial: 4C2020200000000000000000907579A4970C595F
		size: 75GiB (80GB)
		capacity: 75GiB (80GB)
		capabilities: 15000rpm
		configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512

```

Note that /dev/sdc does not show in df, nor in blkid. There is an entry /dev/sdc but
any attempt to access it gives an error. This is an Enterprise class 'big iron' server
set up.

This confuses smartd and causes issues with upgrades of grub as well. Any ideas
of how to stop this?

---

### Post by DaleAmon on 2017-02-24
I finally stumbled upon the answer, so I will put the link here for others. Its not a bug, its a feature:

[http://www.linuxquestions.org/questions/blog/bittner-195120/multipath-on-debian-lenny-and-intel-modular-server-mfsys25-3072/](http://www.linuxquestions.org/questions/blog/bittner-195120/multipath-on-debian-lenny-and-intel-modular-server-mfsys25-3072/)

---

