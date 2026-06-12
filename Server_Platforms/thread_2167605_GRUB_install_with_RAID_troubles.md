---
title: "GRUB install with RAID troubles"
date: 2013-08-14
forum: Server Platforms
---

### Post by brighty22 on 2013-08-14
Hi,

In preparation for a new build, I installed Ubuntu Server 12.04.2 x64 on a VM, and did a clean install over it to see how things coped (not so well, apparently).

Right at the end of the clean install, "Executing 'grub-install /dev/sda' failed", so I'm now trying to fix the boot loader.

I'm essentially walking though [these instructions]("https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot"). I've booted into a 12.04.2 x64 desktop live CD, installed mdadm, and run the following. To clarify, /dev/md0 is the root partition, and /dev/md1 is /boot.

```

root@ubuntu:~# mdadm --assemble --scan
mdadm: /dev/md/0 has been started with 4 drives.
mdadm: /dev/md/1 has been started with 4 drives.
mdadm: /dev/md/2 has been started with 4 drives.
mdadm: /dev/md/3 has been started with 4 drives.
mdadm: /dev/md/4 has been started with 4 drives.
root@ubuntu:~# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [raid1] 
md4 : active raid5 sda7[0] sdd7[3] sdc7[2] sdb7[1]
      7276032 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      
md3 : active raid5 sda6[0] sdd6[3] sdc6[2] sdb6[1]
      287232 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      
md2 : active raid5 sda5[0] sdd5[3] sdc5[2] sdb5[1]
      142848 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      
md1 : active raid1 sda2[0] sdd2[3] sdc2[2] sdb2[1]
      97152 blocks super 1.2 [4/4] [UUUU]
      
md0 : active raid5 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      23419392 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>
root@ubuntu:~# mount /dev/md0 /mnt
root@ubuntu:~# mkdir /mnt/boot
root@ubuntu:~# mount /dev/md1 /mnt/boot
root@ubuntu:~# mkdir /mnt/run
root@ubuntu:~# for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
root@ubuntu:~# chroot /mnt
root@ubuntu:/# grub-install /dev/sda
/usr/sbin/grub-probe: error: no mapping exists for `md1'.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```

I'm no Ubuntu expert, and after searching around am still not sure what's causing this, but if (before chrooting) I run grub-install --root-directory=/mnt [/dev/sda through /dev/sdd], it succeeds, but then update-grub fails with "/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)."

```

root@ubuntu:~# fdisk -l


Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders, total 20971520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002419b


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    15624191     7811072   fd  Linux raid autodetect
/dev/sda2   *    15624192    15818751       97280   fd  Linux raid autodetect
/dev/sda3        15820798    20969471     2574337    5  Extended
/dev/sda5        15820800    15917055       48128   fd  Linux raid autodetect
/dev/sda6        15919104    16111615       96256   fd  Linux raid autodetect
/dev/sda7        16113664    20969471     2427904   fd  Linux raid autodetect


Disk /dev/sdb: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders, total 20971520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003ed07


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    15624191     7811072   fd  Linux raid autodetect
/dev/sdb2   *    15624192    15818751       97280   fd  Linux raid autodetect
/dev/sdb3        15820798    20969471     2574337    5  Extended
/dev/sdb5        15820800    15917055       48128   fd  Linux raid autodetect
/dev/sdb6        15919104    16111615       96256   fd  Linux raid autodetect
/dev/sdb7        16113664    20969471     2427904   fd  Linux raid autodetect


Disk /dev/sdc: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders, total 20971520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00057b11


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048    15624191     7811072   fd  Linux raid autodetect
/dev/sdc2   *    15624192    15818751       97280   fd  Linux raid autodetect
/dev/sdc3        15820798    20969471     2574337    5  Extended
/dev/sdc5        15820800    15917055       48128   fd  Linux raid autodetect
/dev/sdc6        15919104    16111615       96256   fd  Linux raid autodetect
/dev/sdc7        16113664    20969471     2427904   fd  Linux raid autodetect


Disk /dev/sdd: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders, total 20971520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006f466


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048    15624191     7811072   fd  Linux raid autodetect
/dev/sdd2   *    15624192    15818751       97280   fd  Linux raid autodetect
/dev/sdd3        15820798    20969471     2574337    5  Extended
/dev/sdd5        15820800    15917055       48128   fd  Linux raid autodetect
/dev/sdd6        15919104    16111615       96256   fd  Linux raid autodetect
/dev/sdd7        16113664    20969471     2427904   fd  Linux raid autodetect


Disk /dev/md0: 24.0 GB, 23981457408 bytes
2 heads, 4 sectors/track, 5854848 cylinders, total 46838784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x00000000


Disk /dev/md0 doesn't contain a valid partition table


Disk /dev/md1: 99 MB, 99483648 bytes
2 heads, 4 sectors/track, 24288 cylinders, total 194304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/md1 doesn't contain a valid partition table


Disk /dev/md2: 146 MB, 146276352 bytes
2 heads, 4 sectors/track, 35712 cylinders, total 285696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x00000000


Disk /dev/md2 doesn't contain a valid partition table


Disk /dev/md3: 294 MB, 294125568 bytes
2 heads, 4 sectors/track, 71808 cylinders, total 574464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x00000000


Disk /dev/md3 doesn't contain a valid partition table


Disk /dev/md4: 7450 MB, 7450656768 bytes
2 heads, 4 sectors/track, 1819008 cylinders, total 14552064 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x00000000


Disk /dev/md4 doesn't contain a valid partition table

```

Does anyone have any suggestions? Thanks in advance!

---

### Post by oldfred on 2013-08-14
I do not know RAID, but do know you install grub to the root of the RAID not the MBR of the drive. If doing the grub install manually you mount the / (root) partition (and /boot if separate partition) and install to the RAID volume. Example shows p1 as first partition and VOLUME_0 as RAID volume

 "fakeRaid" with nVidia
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0[COLOR=#ff0000]p1[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

Boot-Repair will automatically do it in most cases.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

