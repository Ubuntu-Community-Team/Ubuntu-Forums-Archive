---
title: "Advice on partitions for Dual boot? 128 GB SSD + 1 TB HDD + 500 GB HDD."
date: 2014-02-17
forum: Ubuntu, Linux and OS Chat
---

### Post by Daniel_Rollins on 2014-02-17
Hi all,

Completely new to Ubuntu and Linux in general and would like to try it out. I am still beholden to Windows for a few reasons so I'd like some advice on how to structure my partitions, for dual booting. As stated in the thread title, I have a 128 GB SSD that I'll use as a Windows 8 and Ubuntu dual boot drive, however I'm not sure how to structure my other drives.

I mainly use my PC for gaming. Any games that can be run natively on Linux, I will try to do so. I do have an SLI system but am not sure what the support for it is like on Linux. For this reason, I'd like a decent size Windows partition - just in case. I'll also need a partition for general data (Music, Documents, Downloads) that I will Symlink to in Linux.

My plan was as follows:

128 GB SSD
  - 68 GB NTFS for Windows 8
  - 20 GB ext4 for '/'
  - 48 GB ext4 for '/home'

500 GB
  - All NTFS for Windows-specific applications

1 TB HDD
  - 650 GB NTFS for general data (symlinked in linux)
  - 350 GB ext4 for Linux-specific applications

Can any of you see any potential problems with set up? Any optimisations you'd make to file system structure?

Many thanks,

Dan

---

### Post by oldfred on 2014-02-17
On my 64GB SSD I have two / (root) partitions. One my working install that uses about 11GB of the about 28GB and a space for next install. I include /home inside my / as I have all data on my rotating drive. 
I still have some data in my shared NTFS when I still booted XP, and all new data goes into my Linux formatted shared data as I also have several other installs on my rotating drive for testing and want that data to also be shared.

My /home is about 2GB and the vast majority of that 2GB is .wine. Actual settings in /home are very small. Any app that starts to use some space gets that data moved to data partition.
I try to configure every hard drive to be fully bootable without any other drive. If other drive fails then I may get errors about swap or data not mounting, but can still boot. And if main boot drive fails I have another (maybe older, but periodically updated) that I can boot and have access to same data and current Firefox & Thunderbird profiles.

       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive. With SSD now I only keep a somewhat current install on older rotating drives.

---

