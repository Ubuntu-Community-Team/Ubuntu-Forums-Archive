---
title: "card reader issues"
date: 2009-01-19
forum: System76 Support
---

### Post by gpstar on 2009-01-19
I am having issues with the built in card reader on my bonobo laptop.

Been trying to copy files off/on and deleting them on a SD cards and I get i/o errors and corrupted files. I've tried different SD and SDHC cards, same thing. Sometimes I get lucky and the files get copied over, other times they wont or they get corrupted.

it's a new bonobo model as of october 2008 running Hardy 8.04

---

### Post by thomasaaron on 2009-01-19
Please post some of the errors.

---

### Post by gpstar on 2009-01-19
```
Jan 17 18:49:53 gpstar kernel: [ 8141.482192] mmc0: new SD card at address b368
Jan 17 18:49:53 gpstar kernel: [ 8141.482295] mmcblk0: mmc0:b368 SD    1997312KiB 
Jan 17 18:49:53 gpstar kernel: [ 8141.482325]  mmcblk0: p1
Jan 17 18:51:45 gpstar kernel: [ 8194.230053] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:51:45 gpstar kernel: [ 8194.230058]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:51:45 gpstar kernel: [ 8194.230060]     File system has been set read-only
Jan 17 18:51:45 gpstar kernel: [ 8194.236868] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:51:45 gpstar kernel: [ 8194.236872]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:18 gpstar kernel: [ 8207.049187] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:18 gpstar kernel: [ 8207.049192]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:18 gpstar kernel: [ 8207.049215] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:18 gpstar kernel: [ 8207.049216]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:20 gpstar kernel: [ 8207.891624] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.891630]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:20 gpstar kernel: [ 8207.891637] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.891638]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:20 gpstar kernel: [ 8207.891784] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.891785]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:20 gpstar kernel: [ 8207.891792] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.891793]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:20 gpstar kernel: [ 8207.891839] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.891840]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:20 gpstar kernel: [ 8207.891847] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.891848]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:20 gpstar kernel: [ 8207.891871] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.891872]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:20 gpstar kernel: [ 8207.891880] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.891881]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:20 gpstar kernel: [ 8207.891976] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.891978]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:20 gpstar kernel: [ 8207.891986] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.891987]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:20 gpstar kernel: [ 8207.892035] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.892037]     invalid access to FAT (entry 0x0000f8f9)
Jan 17 18:52:20 gpstar kernel: [ 8207.892046] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.892047]     invalid access to FAT (entry 0x0000f8f9)
Jan 17 18:52:20 gpstar kernel: [ 8207.892175] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.892177]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:20 gpstar kernel: [ 8207.892188] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.892189]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:20 gpstar kernel: [ 8207.892242] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.892243]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:20 gpstar kernel: [ 8207.892254] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.892255]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:20 gpstar kernel: [ 8207.892282] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.892283]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:20 gpstar kernel: [ 8207.892295] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:20 gpstar kernel: [ 8207.892296]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:28 gpstar kernel: [ 8210.482457] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:28 gpstar kernel: [ 8210.482462]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:28 gpstar kernel: [ 8210.482561] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:28 gpstar kernel: [ 8210.482563]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:28 gpstar kernel: [ 8210.482688] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:28 gpstar kernel: [ 8210.482689]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:38 gpstar kernel: [ 8213.354144] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:38 gpstar kernel: [ 8213.354150]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:38 gpstar kernel: [ 8213.354251] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:38 gpstar kernel: [ 8213.354252]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:52:38 gpstar kernel: [ 8213.354378] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:52:38 gpstar kernel: [ 8213.354379]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:53:08 gpstar kernel: [ 8237.543692] FAT: Filesystem panic (dev mmcblk0p1)
Jan 17 18:53:08 gpstar kernel: [ 8237.543698]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jan 17 18:53:08 gpstar kernel: [ 8237.543700]     File system has been set read-only
Jan 17 18:53:24 gpstar kernel: [ 8245.156180] mmc0: card b368 removed

```

---

### Post by thomasaaron on 2009-01-20
Looks like it's choking on the filesystem. There are a lot of posts out there that discuss those errors. But no real solutions.

Try downloading Partition Editor...

sudo apt-get install gparted

...and reformatting it. I'd use either an ext3 or a fat32 filesystem.

---

### Post by gpstar on 2009-01-21
thanks, seems reformatting the cards in ubuntu with gparted did the trick.

---

