---
title: "HIMEM / HIGHMEM / PAE - help"
date: 2006-04-17
forum: Server Platforms
---

### Post by neild on 2006-04-17
Hello

I have the following:
A8N-SLI Premium 
AMD64 X2 4200+
4GB Ram (4x1GB)
2x Seagate 400GB SATA (3Gps) in linux RAID1 configuration
Using Breezy AMD64 Server Image

I have been battling for sometime now trying to get around this kernel panic whenever you enable H/W or S/W Memory remapping in the ASUS bios.
I am using currently using kernel image 2.6.12-10-amd54-k8-smp.

I read on this forum that the server kernel image has support enabled for 64G Ram but I can't find this image anywhere. 
I have also done a " cat /boot/config-2.6.12* |grep MEM " to try and find the HIGHMEM or HIMEM string but neither are listed. The only things that show are as follows:
CONFIG_SHMEM=y
# CONFIG_TINY_SHMEM is not set
CONFIG_DISCONTIGMEM=y
CONFIG_BLK_DEV_UMEM=m
CONFIG_W1_SMEM=m

I then recompiled the kernel using a HOWTO on this forum hoping to find an option in the menuconfig that would allow me to select 64G but could not find it anywhere. 
I then checked the .config file to see if it was hiding in there but it wasnt, so I am a bit stuck now as where and how I get the 64G option enabled.

I intend to use this machine for VMware Server so I would really like to get all the memory that I am entitled to so my vmware server can be happy.

I call on all the wise gurus to please help before I drive myself mad....

Kind Regards,

Neil

---

### Post by netpython on 2007-07-03
Hi,

You should install the server kernel. In addition you can use noexec=on noexec32=on  on the grub kernel line so you have a non executable stack with amd64 CPU's.

---

