---
title: "Best way of combining SSD + HDD Dual-Boot Windows10-Linux"
date: 2019-05-09
forum: Ubuntu, Linux and OS Chat
---

### Post by avelarbio46 on 2019-05-09
Hello Everyone!

I have an HPC, for which windows 10 is necessary due to some software restritions to windows.
Also, we use a lot of linux for obvious reasons. 
So we want a dual-boot system, with 2TB HDD "bulk" storage and 1TB ssd with both systems on it.

Today we have a 1TB SSD plus a 2TB HDD, with no data on it.

We would use more space for Linux, but it might be usefull to have some large files that windows can access (big data).


What are you suggestions, not only to file formats, but partition sizes?

Checking, my BIOS is UEFI and Windows is not installed, but I have windows 10 PRO

---

### Post by oldfred on 2019-05-09
Newer UEFI/gpt or older BIOS/MBR?
If Windows pre-installed by vendor since 2012 and release of Windows 8, it will be UEFI. But users can still install in the old BIOS/MBR configuration for backwards compatibility. 

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

I prefer smaller system partitions for both Windows & Ubuntu, but Windows makes it difficult to make it small as many defaults still write data into the system.
I use 25 to 30GB for / (root) including /home inside / on SSD, but have all my data in a large ext4 data partition on HDD. I do not have Windows.
Back with XP I also had a shared NTFS data partition, but newer Windows now uses fast start up which sets hibernation flag and then Linux NTFS driver will not mount read/write. Make sure Windows fast start up is off whether UEFI or BIOS.

---

