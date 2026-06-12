---
title: "Ubuntu distros and its use on old revolving rust."
date: 2019-02-20
forum: Ubuntu, Linux and OS Chat
---

### Post by lammert-nijhof on 2019-02-20
The choice of a distro based on out-of-the-box appearance gets more and more irrelevant, basically you can give all distros the same layout on all desktops. I use mainly Mate and XFCE from Ubuntu and they look exactly the same on my PCs, Plank dock on the left, panel on the bottom and conky with all internals on the right. Sometimes I get confused and try to start Mousepad or Thunar from the sudo CLI in Mate. My choice is determined by the basics: reliability, memory usage and responsiveness/boot times and only that explains my choice for Mate and XFCE based on Ubuntu (all boringly reliable distros). 

I do not concentrate on the bling bling, but on performance, so I spend a lot of time using ZFS and BTRFS. I have automated my 2 sets of backups, which allows me to use striping (RAID-0) on all my revolving rust. I even stripe HDDs of different storage capacities (320, 500 and 1000 GB), throughput (78, 130 and 112 MB/s) and physical sizes (2.5" and 3.5") with these modern file systems. On both file systems I use compression NOT to save space, but to improve on speed (the number of IO OPS). 

My 1st 2008 desktop boots the virtual machines (VM) from compressed ZFS faster than the host is booting from ext4 on a SSD, because ZFS uses a 3-level storage hierarchy (memory cache; SSD cache and 3 striped HDDs). All my Linux VMs (XFCE to KDE, Gnome-3) boot in between 15 and 24 seconds from my 2008 HP dc5850. Reboots are ~10 seconds mainly from the memory cache (8 GB 800MHz DDR2 and a 4-core AMD Phenom II X4 B97 at 3.2 GHz).

My 2nd 2003 desktop with a Pentium 4 HT boots in 45 seconds from two old 40 GB striped and compressed IDE disks with BTRFS. In the past (2000-2005) I would go for a coffee booting such a machine. 

My 2012 i5 laptop with a 1 TB SSHD has improved too using ZFS and compression, the effects of a too small and too slow solid state cache of the Seagate SSHD are somewhat mitigated by a compression rate of 1.7 for virtual machines, so effectively I have now:
- 14 GB of cache instead of 8 GB and
- 340 MB/s throughput instead of  200 MB/s.

With help of to these 3 ancient PCs, there are number of stories to tell. Especially these ancient PCs clearly show the do's and dont's in using modern software. If you are interested, I tell those stories in a number of posts.

[LIST=1]
[*]How to install an Ubuntu based distro on striped compressed BTRFS disks (IDE or NVME). Problems with mixing BTRFS and EXT4 installations on the same PC. How I did it and what I would do differently now.
[*]How to install ZFS and use it for data and VM storage, how to determine memory and SSD caching space for a desktop. Tricks to display ZFS performances (hit-rates, cache and striped HDD throughput and size usage) in conky.
[*]Moving from one OS doing everything to a VM (or container?) for each main task and its results in performance and safety.
[*]Backup 15 VMs (250 GB) stored on zfs to an USB 2.0 disk in < ½ an hour and how it differs from data backup.
[*]A simple way to move your say 3 installed Hosts OSes (Virtualbox, QEMU/KVM and VMware) to ZFS, the remaining problems encountered.
[*]Optimize your laptop disk (SSD, SSHD or HDD) using zfs and how could it be done with btrfs.
[/LIST]

---

