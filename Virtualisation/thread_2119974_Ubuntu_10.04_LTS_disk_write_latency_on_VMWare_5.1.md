---
title: "Ubuntu 10.04 LTS disk write latency on VMWare 5.1"
date: 2013-02-25
forum: Virtualisation
---

### Post by boxsterra on 2013-02-25
Hello, [FONT=Times New Roman]we've had this nagging performance issue on our performance benchmark[/FONT]
[FONT=Times New Roman]rack since installing Ubuntu 10.04 LTS OS on it. We've narrowed it down to a write latency issue when writing to the 12-disk array on the DL-380. The write latency on Ubuntu almost 10 times worse the amount seen with Solaris OS.[/FONT]
 
[FONT=Times New Roman]In a typical 1/2 hour load traffic run we'll get these results:[/FONT]
 
[FONT=Times New Roman]VMWare 5.1 on a HP DL-380 w/12-disk array[/FONT]
[FONT=Times New Roman]"Virtual Disk Perf Chart"[/FONT]
[FONT=Times New Roman]Solaris OS (ZFS):[/FONT]
[FONT=Times New Roman]Write Latency Max: 40 msec Average: 6.1 msec[/FONT]
 
[FONT=Times New Roman]Ubuntu OS (ext4):[/FONT]
[FONT=Times New Roman]Write Latency Max: 296 msec Average: 54 msec[/FONT]
 
[FONT=Times New Roman][FONT=Times New Roman]The HP DL-380 The 12-disk array is configured as a single LUN RAID1+0 with a total capacity of 3.27TB. The Ubuntu is provisioned to use about 1.4TB of this for writing objects during the load test. The disk file system is currently configured with ext4, noatime.[/FONT]
 
[FONT=Times New Roman]Has anyone else experienced really bad write latency running Ubuntu OS in VMWare? [/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Times New Roman]What is the preferred disk file system people are using for performance on Ubuntu OS? Has anyone had better luck running XFS or even ZFS file systems?[/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Times New Roman]Thanks[/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Times New Roman]Gary[/FONT][/FONT]

---

