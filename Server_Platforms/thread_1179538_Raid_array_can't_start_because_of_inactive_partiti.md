---
title: "Raid array can't start because of inactive partitions in VMware environment"
date: 2009-06-05
forum: Server Platforms
---

### Post by dcdyd on 2009-06-05
I am using server 904 as guest in VMware Workstation environment. The host is Windows 7.
 
I set 4 virtual disks using VMware and these 4 disks can be seen in Ubuntu as /sd{b-e}. I used mdadm to create a raid6 array using these 4 disks. Everything went fine until I restart Ubuntu.
 
After ths OS is rebooted, the raid array doesn't comeup automatically. If I use mdadm --assemble --scan, sometimes the array can start with 2 or 3 out of fur disks. Some time the array can't be re-assembed because of more than 3 disks are inactive. 
 
This happens for both 32bit and 64bit server OS. I also tried to use WIndows 2003 as host and the behavior is the same.
 
By the way, I tried Fedora v10, the symptom didn't show up. At the beginning I thought that it may be VMware issue and I posted the question in VMware forum. However I was told to check the Ubuntu forum and may be this is Ubuntu issue.

---

