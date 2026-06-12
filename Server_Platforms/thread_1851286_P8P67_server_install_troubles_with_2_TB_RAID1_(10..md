---
title: "P8P67 server install troubles with 2 TB RAID1 (10.04 or 11.04)"
date: 2011-09-28
forum: Server Platforms
---

### Post by electronico_nc on 2011-09-28
Hi all,

I have troubles with a new server install on a P8P67 motherboard.

As usually I wanted to install the 10.04.3 LTS version :
- The onboard NIC (Intel e1000) is not recognized by installer that says (after HD partitionning & soft RAID) "unable to install base files" (or something like that).
I think there is a problem with mdadm that needs postfix, but no NIC found ...

So decided to try 11.04 :
- NIC is well recognized :p
- They are 3 * 2 TB HDs that I want to be setup in RAID1 (1 spare) :
When it comes to the partition tool, I setup each partition as usually :
500 MB -> /boot (**here I can't setup the "boot" flag on partition**)
50 GB -> /
50 GB -> /var
1850 GB -> /home
16 GB -> swap
then make the RAID1 arrays on each (except swap) (md0, ..., md3)
installation goes OK up to the grub-install step :
- grub can't be installed on /dev/sda, neither on /dev/sdb, neither on /dev/sda1 or /dev/sda2 ...

I've tried the easiest way and only told installer to use only one complete HD.
Looking at the partitions on HD, there are :
- 1MB type:unknown flag:bios_grub
- 1.8TB type:ext4 mount-point:/
- 8GB type:swap

Thanks a lot for any help, as I'm a bit lost with this installation.

It isn't relative to BIOS, I've tried all versions from embedded 0105, to last stable 1704 and beta 1850.
There is no fake-raid configured on motherboard.

---

### Post by electronico_nc on 2011-09-28
About 11.04 install, the answer is :

- create a bios_grub partition, 1MB on each drive
- create partition for RAID as usually
- create software RAID

DO NOT CREATE A RAID WITH bios_grub PARTITIONS

---

