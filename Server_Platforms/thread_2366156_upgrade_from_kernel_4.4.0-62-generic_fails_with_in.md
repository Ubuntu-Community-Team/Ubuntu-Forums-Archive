---
title: "upgrade from kernel 4.4.0-62-generic fails with initramsf"
date: 2017-07-14
forum: Server Platforms
---

### Post by mpgk-marsoft on 2017-07-14
Hi,
I have a 64 bit server running version 16.04.1 LTS and kernel 4.4.0-62-generic
I am having issues with qemu invoking oom-killer and crashing out some of my host VMs.
Some Googling gave results that suggested this is an issue with this kernel version so on a backup server I tried to update the kernel.
I ran apt-get upgrade and the upgrade process hangs at...
update-initramfs: Generating /boot/initrd.img-4.4.0-83-generic


In a separate shell I have tried update-initramfs -u -v and the process stops on
"Calling hook cryptroot"


In my /boot/ directory I now have a file initrd.img-4.4.0-83-generic.new which is 0Kb in size.


I do not have any encrypted volumes.

I run 'dpkg --configure -a' and it hangs on
'update-initramfs: Generating /boot/initrd.img-4.4.0-83-generic'

It will stay like this forever so I have to crash out of this and an unable to do any updates.

If I run killall dpgk and re-run the above commands it gets to the same point each time where it hangs.

Please can anyone suggest how I can get round this error and complete the upgrade.
Any advice is gratefully welcomed.
Kind regards
Max

---

### Post by Bashing-om on 2017-07-14
mpgk-marsoft; Hello; Welcome to the forum :)

Not much yet to go on .
1st up is do we have operational headroom to install additional kernels ?
what shows :
```

df -h

```Where we need about 300 Mb of available space.

Next then is what kernel packages are installed?
```

dpkg -l | grep linux-
ls -al /boot

```
The end goal here is to get up on the latest kernel:
> 
sysop@x1604:~$ uname -r
4.4.0-83-generic


Show us the results of :
```

sudo apt update
sudo apt full-upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
See then where we go from here.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by mpgk-marsoft on 2017-07-17
Hi.
Many thanks for your help.
Free space:
```

df-h
Filesystem                                 Size  Used Avail Use% Mounted on
udev                                        63G     0   63G   0% /dev
tmpfs                                       13G   19M   13G   1% /run
/dev/mapper/vg0-lv_root                    190G  4.7G  176G   3% /
tmpfs                                       63G   92K   63G   1% /dev/shm
tmpfs                                      5.0M     0  5.0M   0% /run/lock
tmpfs                                       63G     0   63G   0% /sys/fs/cgroup
/dev/sda1                                  511M  3.4M  508M   1% /boot/efi
cgmfs                                      100K     0  100K   0% /run/cgmanager/fs
/dev/mapper/mpath-dx100-IsoArchive-part1   148G   66G   75G  47% /mnt/IsoArchive
/dev/mapper/mpath-dx100-New-testing-part1  442G  318G  103G  76% /mnt/testing-new
tmpfs                                       13G     0   13G   0% /run/user/1000

```

Kernel packages installed:
```

dpkg -l | grep linux-
ii  linux-base                          4.0ubuntu1                                   all          Linux image base package
ii  linux-firmware                      1.157.11                                     all          Firmware for Linux kernel drivers
ii  linux-headers-4.4.0-31              4.4.0-31.50                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic      4.4.0-31.50                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-45              4.4.0-45.66                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-45-generic      4.4.0-45.66                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-53              4.4.0-53.74                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-53-generic      4.4.0-53.74                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-57              4.4.0-57.78                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic      4.4.0-57.78                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-62              4.4.0-62.83                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-62-generic      4.4.0-62.83                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-83              4.4.0-83.106                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-83-generic      4.4.0-83.106                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic               4.4.0.83.89                                  amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-31-generic        4.4.0-31.50                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic        4.4.0-45.66                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-53-generic        4.4.0-53.74                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-57-generic        4.4.0-57.78                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-62-generic        4.4.0-62.83                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-83-generic        4.4.0-83.106                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic  4.4.0-31.50                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-45-generic  4.4.0-45.66                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-53-generic  4.4.0-53.74                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-57-generic  4.4.0-57.78                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-62-generic  4.4.0-62.83                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-83-generic  4.4.0-83.106                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                4.4.0-83.106                                 amd64        Linux Kernel Headers for development
ii  linux-signed-generic                4.4.0.83.89                                  amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-4.4.0-31-generic 4.4.0-31.50                                  amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-45-generic 4.4.0-45.66                                  amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-53-generic 4.4.0-53.74                                  amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-57-generic 4.4.0-57.78                                  amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-62-generic 4.4.0-62.83                                  amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-83-generic 4.4.0-83.106                                 amd64        Signed kernel image generic
ii  linux-signed-image-generic          4.4.0.83.89                                  amd64        Signed Generic Linux kernel image

```

```

ls -al /boot
total 298668
drwxr-xr-x  4 root root     4096 Jul  4 15:29 .
drwxr-xr-x 23 root root     4096 Jul  3 10:39 ..
-rw-r--r--  1 root root  1240067 Jul 13  2016 abi-4.4.0-31-generic
-rw-r--r--  1 root root  1242701 Oct 19  2016 abi-4.4.0-45-generic
-rw-r--r--  1 root root  1243479 Dec  2  2016 abi-4.4.0-53-generic
-rw-r--r--  1 root root  1243800 Dec 10  2016 abi-4.4.0-57-generic
-rw-r--r--  1 root root  1244118 Jan 18 15:59 abi-4.4.0-62-generic
-rw-r--r--  1 root root  1246511 Jun 26 20:45 abi-4.4.0-83-generic
-rw-r--r--  1 root root   189558 Jul 13  2016 config-4.4.0-31-generic
-rw-r--r--  1 root root   189760 Oct 19  2016 config-4.4.0-45-generic
-rw-r--r--  1 root root   189877 Dec  2  2016 config-4.4.0-53-generic
-rw-r--r--  1 root root   189991 Dec 10  2016 config-4.4.0-57-generic
-rw-r--r--  1 root root   190047 Jan 18 15:59 config-4.4.0-62-generic
-rw-r--r--  1 root root   190356 Jun 26 20:45 config-4.4.0-83-generic
drwx------  3 root root     4096 Jan  1  1970 efi
drwxr-xr-x  5 root root     4096 Jul  3 15:10 grub
-rw-r--r--  1 root root 37383212 Jul  3 15:10 initrd.img-4.4.0-31-generic
-rw-r--r--  1 root root 37886882 Jul  3 15:10 initrd.img-4.4.0-45-generic
-rw-r--r--  1 root root 37937061 Jul  3 15:10 initrd.img-4.4.0-53-generic
-rw-r--r--  1 root root 37942595 Jul  3 15:09 initrd.img-4.4.0-57-generic
-rw-r--r--  1 root root 37944246 Jul  3 15:09 initrd.img-4.4.0-62-generic
-rw-r--r--  1 root root        0 Jul 15 00:13 initrd.img-4.4.0-83-generic.new
-rw-------  1 root root  3866473 Jul 13  2016 System.map-4.4.0-31-generic
-rw-------  1 root root  3869895 Oct 19  2016 System.map-4.4.0-45-generic
-rw-------  1 root root  3874377 Dec  2  2016 System.map-4.4.0-53-generic
-rw-------  1 root root  3875329 Dec 10  2016 System.map-4.4.0-57-generic
-rw-------  1 root root  3875553 Jan 18 15:59 System.map-4.4.0-62-generic
-rw-------  1 root root  3883887 Jun 26 20:45 System.map-4.4.0-83-generic
-rw-------  1 root root  7047504 Jul 13  2016 vmlinuz-4.4.0-31-generic
-rw-------  1 root root  7049432 Oct 22  2016 vmlinuz-4.4.0-31-generic.efi.signed
-rw-------  1 root root  7054208 Oct 19  2016 vmlinuz-4.4.0-45-generic
-rw-------  1 root root  7056120 Oct 22  2016 vmlinuz-4.4.0-45-generic.efi.signed
-rw-------  1 root root  7065648 Dec  2  2016 vmlinuz-4.4.0-53-generic
-rw-------  1 root root  7067576 Dec 20  2016 vmlinuz-4.4.0-53-generic.efi.signed
-rw-------  1 root root  7067152 Dec 10  2016 vmlinuz-4.4.0-57-generic
-rw-------  1 root root  7069080 Dec 21  2016 vmlinuz-4.4.0-57-generic.efi.signed
-rw-------  1 root root  7070992 Jan 18 15:59 vmlinuz-4.4.0-62-generic
-rw-------  1 root root  7072920 Feb  3 13:53 vmlinuz-4.4.0-62-generic.efi.signed
-rw-------  1 root root  7092720 Jun 26 20:45 vmlinuz-4.4.0-83-generic
-rw-------  1 root root  7094648 Jul  3 10:40 vmlinuz-4.4.0-83-generic.efi.signed

```


Then:
```

sudo apt update


WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


Hit:1 http://gb.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [578 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [559 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [505 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [488 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages [14.9 kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages [14.0 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [145 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages [129 kB]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [74.8 kB]
Fetched 2,814 kB in 6s (426 kB/s)
Reading package lists...
Building dependency tree...
Reading state information...
7 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

And
```

sudo apt full-upgrade


WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



```

I hope this helps.
Many thanks
Max

---

### Post by mpgk-marsoft on 2017-07-17
A bit more information about my hardware setup.
This is a FUJITSU PRIMERGY RX2510 M22 x Intel(R) Xeon(R) CPU E5-2620 v4 @ 2.10GHz (8 cores in each processor)
RAM 128GB
Swap 11GB


This is a host server for approx 30 VMs (mix of Windows and Linux servers and workstations)
QEMU is using 64GB of the total of 128GB

We have plenty of spare RAM so I cannot see my initial Out of Memory issue as actually being out of memory.
I have also included the syslog showing the output for the OOM incident below in case this helps:

```

Jul 13 21:21:11 server kernel: [7601521.772315] qemu-system-x86 invoked oom-killer: gfp_mask=0x26000c0, order=2, oom_score_adj=0
Jul 13 21:21:11 server kernel: [7601521.772322] qemu-system-x86 cpuset=emulator mems_allowed=0-1
Jul 13 21:21:11 server kernel: [7601521.772332] CPU: 15 PID: 30526 Comm: qemu-system-x86 Tainted: G        W       4.4.0-62-generic #83-Ubuntu
Jul 13 21:21:11 server kernel: [7601521.772335] Hardware name: FUJITSU PRIMERGY RX2510 M2/D3279-H1, BIOS V5.0.0.11 R1.7.0 for D3279-H1x                     04/21/2016
Jul 13 21:21:11 server kernel: [7601521.772338]  0000000000000286 00000000093bb360 ffff8801519abaf0 ffffffff813f7c63
Jul 13 21:21:11 server kernel: [7601521.772342]  ffff8801519abcc8 ffff88102a8a1c00 ffff8801519abb60 ffffffff8120ad4e
Jul 13 21:21:11 server kernel: [7601521.772346]  0000000000000015 0000000000000000 ffff8820357d2f00 ffff880bff851c00
Jul 13 21:21:11 server kernel: [7601521.772350] Call Trace:
Jul 13 21:21:11 server kernel: [7601521.772361]  [<ffffffff813f7c63>] dump_stack+0x63/0x90
Jul 13 21:21:11 server kernel: [7601521.772369]  [<ffffffff8120ad4e>] dump_header+0x5a/0x1c5
Jul 13 21:21:11 server kernel: [7601521.772376]  [<ffffffff81390c14>] ? apparmor_capable+0xc4/0x1b0
Jul 13 21:21:11 server kernel: [7601521.772383]  [<ffffffff811926c2>] oom_kill_process+0x202/0x3c0
Jul 13 21:21:11 server kernel: [7601521.772386]  [<ffffffff81192ae9>] out_of_memory+0x219/0x460
Jul 13 21:21:11 server kernel: [7601521.772392]  [<ffffffff81198a5d>] __alloc_pages_slowpath.constprop.88+0x8fd/0xa70
Jul 13 21:21:11 server kernel: [7601521.772396]  [<ffffffff81198e56>] __alloc_pages_nodemask+0x286/0x2a0
Jul 13 21:21:11 server kernel: [7601521.772401]  [<ffffffff81198f0b>] alloc_kmem_pages_node+0x4b/0xc0
Jul 13 21:21:11 server kernel: [7601521.772408]  [<ffffffff8107ea5e>] copy_process+0x1be/0x1b70
Jul 13 21:21:11 server kernel: [7601521.772415]  [<ffffffff811c1543>] ? handle_mm_fault+0xbc3/0x1820
Jul 13 21:21:11 server kernel: [7601521.772423]  [<ffffffff811036f7>] ? do_futex+0x107/0x540
Jul 13 21:21:11 server kernel: [7601521.772426]  [<ffffffff810805a0>] _do_fork+0x80/0x360
Jul 13 21:21:11 server kernel: [7601521.772433]  [<ffffffff810910ef>] ? sigprocmask+0x6f/0xa0
Jul 13 21:21:11 server kernel: [7601521.772436]  [<ffffffff81080929>] SyS_clone+0x19/0x20
Jul 13 21:21:11 server kernel: [7601521.772444]  [<ffffffff818385f2>] entry_SYSCALL_64_fastpath+0x16/0x71
Jul 13 21:21:11 server kernel: [7601521.772447] Mem-Info:
Jul 13 21:21:11 server kernel: [7601521.772457] active_anon:8613912 inactive_anon:2561790 isolated_anon:0
Jul 13 21:21:11 server kernel: [7601521.772457]  active_file:253319 inactive_file:20093382 isolated_file:0
Jul 13 21:21:11 server kernel: [7601521.772457]  unevictable:31167 dirty:704072 writeback:29263 unstable:0
Jul 13 21:21:11 server kernel: [7601521.772457]  slab_reclaimable:707348 slab_unreclaimable:261557
Jul 13 21:21:11 server kernel: [7601521.772457]  mapped:18045 shmem:9329 pagetables:41405 bounce:0
Jul 13 21:21:11 server kernel: [7601521.772457]  free:148686 free_pcp:0 free_cma:0
Jul 13 21:21:11 server kernel: [7601521.772463] Node 0 DMA free:13316kB min:8kB low:8kB high:12kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15992kB managed:15900kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Jul 13 21:21:11 server kernel: [7601521.772471] lowmem_reserve[]: 0 1757 64218 64218 64218
Jul 13 21:21:11 server kernel: [7601521.772477] Node 0 DMA32 free:252604kB min:1228kB low:1532kB high:1840kB active_anon:354708kB inactive_anon:364440kB active_file:124kB inactive_file:124kB unevictable:1616kB isolated(anon):0kB isolated(file):0kB present:1920252kB managed:1839632kB mlocked:1616kB dirty:4kB writeback:0kB mapped:312kB shmem:1148kB slab_reclaimable:672460kB slab_unreclaimable:85320kB kernel_stack:6864kB pagetables:632kB unstable:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Jul 13 21:21:11 server kernel: [7601521.772485] lowmem_reserve[]: 0 0 62461 62461 62461
Jul 13 21:21:11 server kernel: [7601521.772490] Node 0 Normal free:133352kB min:43716kB low:54644kB high:65572kB active_anon:27141800kB inactive_anon:4481708kB active_file:626280kB inactive_file:29382908kB unevictable:38808kB isolated(anon):0kB isolated(file):0kB present:65011712kB managed:63960676kB mlocked:38808kB dirty:46940kB writeback:0kB mapped:56152kB shmem:28156kB slab_reclaimable:1159628kB slab_unreclaimable:457356kB kernel_stack:11424kB pagetables:64980kB unstable:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Jul 13 21:21:11 server kernel: [7601521.772498] lowmem_reserve[]: 0 0 0 0 0
Jul 13 21:21:11 server kernel: [7601521.772502] Node 1 Normal free:195472kB min:45152kB low:56440kB high:67728kB active_anon:6959140kB inactive_anon:5401012kB active_file:386872kB inactive_file:50990496kB unevictable:84244kB isolated(anon):0kB isolated(file):0kB present:67108864kB managed:66057592kB mlocked:84244kB dirty:2769344kB writeback:117052kB mapped:15716kB shmem:8012kB slab_reclaimable:997304kB slab_unreclaimable:503552kB kernel_stack:9536kB pagetables:100008kB unstable:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Jul 13 21:21:11 server kernel: [7601521.772509] lowmem_reserve[]: 0 0 0 0 0
Jul 13 21:21:11 server kernel: [7601521.772513] Node 0 DMA: 1*4kB (U) 0*8kB 2*16kB (U) 3*32kB (U) 2*64kB (U) 0*128kB 1*256kB (U) 1*512kB (U) 0*1024kB 2*2048kB (UM) 2*4096kB (M) = 13316kB
Jul 13 21:21:11 server kernel: [7601521.772529] Node 0 DMA32: 2060*4kB (UME) 3571*8kB (UME) 2908*16kB (UME) 1950*32kB (UMEH) 978*64kB (UMH) 272*128kB (UMH) 27*256kB (H) 5*512kB (H) 0*1024kB 0*2048kB 0*4096kB = 252616kB
Jul 13 21:21:11 server kernel: [7601521.772544] Node 0 Normal: 32272*4kB (UMEH) 941*8kB (UMEH) 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 136616kB
Jul 13 21:21:11 server kernel: [7601521.772555] Node 1 Normal: 44018*4kB (UMEH) 2622*8kB (UMEH) 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 197048kB
Jul 13 21:21:11 server kernel: [7601521.772567] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=1048576kB
Jul 13 21:21:11 server kernel: [7601521.772569] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
Jul 13 21:21:11 server kernel: [7601521.772571] Node 1 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=1048576kB
Jul 13 21:21:11 server kernel: [7601521.772573] Node 1 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
Jul 13 21:21:11 server kernel: [7601521.772575] 20382113 total pagecache pages
Jul 13 21:21:11 server kernel: [7601521.772577] 23445 pages in swap cache
Jul 13 21:21:11 server kernel: [7601521.772580] Swap cache stats: add 541987737, delete 541964292, find 438258469/644757883
Jul 13 21:21:11 server kernel: [7601521.772582] Free swap  = 0kB
Jul 13 21:21:11 server kernel: [7601521.772583] Total swap = 11718652kB
Jul 13 21:21:11 server kernel: [7601521.772585] 33514205 pages RAM
Jul 13 21:21:11 server kernel: [7601521.772587] 0 pages HighMem/MovableOnly
Jul 13 21:21:11 server kernel: [7601521.772588] 545755 pages reserved
Jul 13 21:21:11 server kernel: [7601521.772589] 0 pages cma reserved
Jul 13 21:21:11 server kernel: [7601521.772591] 0 pages hwpoisoned
Jul 13 21:21:11 server kernel: [7601521.772592] [ pid ]   uid  tgid total_vm      rss nr_ptes nr_pmds swapents oom_score_adj name
Jul 13 21:21:11 server kernel: [7601521.772606] [  746]     0   746    24254     8892      52       3      902             0 systemd-journal
Jul 13 21:21:11 server kernel: [7601521.772610] [  799]     0   799    25742      463      19       3       27             0 lvmetad
Jul 13 21:21:11 server kernel: [7601521.772614] [  814]     0   814    11201      765      21       3      187         -1000 systemd-udevd
Jul 13 21:21:11 server kernel: [7601521.772618] [ 2434]   100  2434    25081      543      19       3       30             0 systemd-timesyn
Jul 13 21:21:11 server kernel: [7601521.772621] [ 2650]     0  2650    77162      424      20       4      563             0 lxcfs
Jul 13 21:21:11 server kernel: [7601521.772624] [ 2652]   107  2652    10801      813      27       3      104          -900 dbus-daemon
Jul 13 21:21:11 server kernel: [7601521.772627] [ 2663]     0  2663     7252      553      19       3       42             0 cron
Jul 13 21:21:11 server kernel: [7601521.772630] [ 2665]   104  2665    64100      620      28       4      341             0 rsyslogd
Jul 13 21:21:11 server kernel: [7601521.772633] [ 2667]     0  2667     6511      423      18       3       45             0 atd
Jul 13 21:21:11 server kernel: [7601521.772636] [ 2676]     0  2676     7470      237      19       3        0             0 cgmanager
Jul 13 21:21:11 server kernel: [7601521.772639] [ 2700]     0  2700    68971     1055      37       3      117             0 accounts-daemon
Jul 13 21:21:11 server kernel: [7601521.772642] [ 2718]     0  2718     1100      294       7       3        9             0 acpid
Jul 13 21:21:11 server kernel: [7601521.772645] [ 2791]     0  2791     8848      681      20       3     1736             0 systemd-logind
Jul 13 21:21:11 server kernel: [7601521.772648] [ 3124]     0  3124    69272      736      38       3      107             0 polkitd
Jul 13 21:21:11 server kernel: [7601521.772651] [ 3146]     0  3146    16380      755      36       3      152         -1000 sshd
Jul 13 21:21:11 server kernel: [7601521.772655] [ 3159]     0  3159     1306      425       8       3       12             0 iscsid
Jul 13 21:21:11 server kernel: [7601521.772658] [ 3160]     0  3160     5129     2574      15       3        0           -17 iscsid
Jul 13 21:21:11 server kernel: [7601521.772677] [16365]     0 16365     4966      469      14       3       65             0 irqbalance
Jul 13 21:21:11 server kernel: [7601521.772680] [16690]   112 16690    12496      367      27       3       98             0 dnsmasq
Jul 13 21:21:11 server kernel: [7601521.772683] [16901]   112 16901    12496      272      28       3       98             0 dnsmasq
Jul 13 21:21:11 server kernel: [7601521.772686] [16902]     0 16902    12489        1      27       3       95             0 dnsmasq
Jul 13 21:21:11 server kernel: [7601521.772689] [17084]   112 17084    12496      372      28       3       97             0 dnsmasq
Jul 13 21:21:11 server kernel: [7601521.772692] [17263]   112 17263    12496      386      27       3       98             0 dnsmasq
Jul 13 21:21:11 server kernel: [7601521.772694] [17442]   112 17442    12496      356      27       3       98             0 dnsmasq
Jul 13 21:21:11 server kernel: [7601521.772697] [17952]  1000 17952    12147     1496      28       3      284             0 systemd
Jul 13 21:21:11 server kernel: [7601521.772700] [17956]  1000 17956    15878        0      34       3     1053             0 (sd-pam)
Jul 13 21:21:11 server kernel: [7601521.772703] [18107]  1000 18107    22162     2963      50       4    12528             0 tmux
Jul 13 21:21:11 server kernel: [7601521.772706] [18113]  1000 18113     5658      459      16       3      479             0 bash
Jul 13 21:21:11 server kernel: [7601521.772709] [18280]     0 18280    13237      494      32       3      149             0 sudo
Jul 13 21:21:11 server kernel: [7601521.772712] [18382]     0 18382    13071      466      30       3      107             0 su
Jul 13 21:21:11 server kernel: [7601521.772715] [18383]     0 18383     6002      893      17       3      605             0 bash
Jul 13 21:21:11 server kernel: [7601521.772717] [18798]     0 18798    48453      500      49       4      184          -900 virtlogd
Jul 13 21:21:11 server kernel: [7601521.772721] [21398]     0 21398    26726      557      51       3      464             0 sendmail-mta
Jul 13 21:21:11 server kernel: [7601521.772724] [ 2039]  1000  2039     5658      351      17       3      479             0 bash
Jul 13 21:21:11 server kernel: [7601521.772727] [23493]   111 23493   553726    54242     567       6    81317             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772732] [26162]     0 26162   351716      768      81       6     3086             0 snapd
Jul 13 21:21:11 server kernel: [7601521.772735] [19044]     0 19044    29924      242      45       3        0          -900 virtlockd
Jul 13 21:21:11 server kernel: [7601521.772738] [19115]     0 19115   715569     3994     210       6     8497             0 libvirtd
Jul 13 21:21:11 server kernel: [7601521.772741] [21289]     0 21289    13237      271      30       3      150             0 sudo
Jul 13 21:21:11 server kernel: [7601521.772743] [28861]     0 28861    13071      227      31       3      107             0 su
Jul 13 21:21:11 server kernel: [7601521.772746] [28871]     0 28871     5981      873      16       3      433             0 bash
Jul 13 21:21:11 server kernel: [7601521.772749] [ 9715]     0  9715     3410      322      11       3       63             0 mdadm
Jul 13 21:21:11 server kernel: [7601521.772752] [31589]   115 31589     8875      237      22       3      149             0 rpc.statd
Jul 13 21:21:11 server kernel: [7601521.772755] [31592]     0 31592    11940      458      28       3      104             0 rpcbind
Jul 13 21:21:11 server kernel: [7601521.772757] [31811]  1000 31811     5659      231      17       3      480             0 bash
Jul 13 21:21:11 server kernel: [7601521.772760] [32333]     0 32333    13237      275      31       3      150             0 sudo
Jul 13 21:21:11 server kernel: [7601521.772763] [32548]     0 32548    13071      236      31       3      107             0 su
Jul 13 21:21:11 server kernel: [7601521.772766] [32549]     0 32549     6002      602      18       3      485             0 bash
Jul 13 21:21:11 server kernel: [7601521.772768] [15204]  1000 15204     5659      250      15       3      480             0 bash
Jul 13 21:21:11 server kernel: [7601521.772771] [15502]     0 15502    13237      251      32       3      150             0 sudo
Jul 13 21:21:11 server kernel: [7601521.772774] [15664]     0 15664    13071      239      31       3      106             0 su
Jul 13 21:21:11 server kernel: [7601521.772776] [15665]     0 15665     6000      489      17       3      612             0 bash
Jul 13 21:21:11 server kernel: [7601521.772779] [26831]  1000 26831     5659      237      16       3      480             0 bash
Jul 13 21:21:11 server kernel: [7601521.772782] [26941]     0 26941    13237      271      30       3      149             0 sudo
Jul 13 21:21:11 server kernel: [7601521.772785] [27717]     0 27717    13071      254      30       3      106             0 su
Jul 13 21:21:11 server kernel: [7601521.772788] [27718]     0 27718     5971      265      16       3      791             0 bash
Jul 13 21:21:11 server kernel: [7601521.772791] [16855]     0 16855     6066      265      18       4      527             0 nano
Jul 13 21:21:11 server kernel: [7601521.772794] [17222]  1000 17222     5659      216      16       3      481             0 bash
Jul 13 21:21:11 server kernel: [7601521.772797] [17382]     0 17382    13237      254      32       3      150             0 sudo
Jul 13 21:21:11 server kernel: [7601521.772799] [17507]     0 17507    13071      226      30       3      106             0 su
Jul 13 21:21:11 server kernel: [7601521.772802] [17508]     0 17508     5949      512      17       3      615             0 bash
Jul 13 21:21:11 server kernel: [7601521.772805] [ 2660]     0  2660     6062      352      17       3      499             0 nano
Jul 13 21:21:11 server kernel: [7601521.772808] [29154]  1000 29154     5660      405      16       3      480             0 bash
Jul 13 21:21:11 server kernel: [7601521.772810] [29319]     0 29319    13238      395      32       3      149             0 sudo
Jul 13 21:21:11 server kernel: [7601521.772813] [29558]     0 29558    13072      344      31       3      106             0 su
Jul 13 21:21:11 server kernel: [7601521.772816] [29559]     0 29559     5700      475      17       3      521             0 bash
Jul 13 21:21:11 server kernel: [7601521.772820] [ 1555]   111  1555  2351888   912738    2401      12   145630             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772823] [ 5673]   111  5673  1131516   242334    1262       8   285390             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772826] [ 6107]   111  6107  1789401    85474     832      10   180301             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772829] [ 6597]   111  6597  1553812   677006    1931       9   125801             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772832] [ 8814]   111  8814  2357093   859643    2342      12   169514             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772835] [ 8944]   111  8944  1794141   469905    1298      11    55631             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772838] [ 9209]   111  9209  1409360   477185    1411       9    63893             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772842] [ 9587]     0  9587     6228      427      19       3      687             0 nano
Jul 13 21:21:11 server kernel: [7601521.772845] [23692]     0 23692    84493      919     161       3      573             0 smbd
Jul 13 21:21:11 server kernel: [7601521.772848] [23693]     0 23693    82472      266     152       3      578             0 smbd
Jul 13 21:21:11 server kernel: [7601521.772850] [23696]     0 23696    84468      519     154       3      562             0 smbd
Jul 13 21:21:11 server kernel: [7601521.772853] [23780]     0 23780    61093      841     116       3      390             0 nmbd
Jul 13 21:21:11 server kernel: [7601521.772857] [ 1018]     0  1018     6292      510      18       3      729             0 nano
Jul 13 21:21:11 server kernel: [7601521.772859] [ 9919]     0  9919     6293      510      19       3      729             0 nano
Jul 13 21:21:11 server kernel: [7601521.772863] [18907]   111 18907  3296045  2506999    5635      17   138823             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772866] [22378]     0 22378     5964      872      16       3       68             0 nano
Jul 13 21:21:11 server kernel: [7601521.772870] [ 9533]     0  9533     3986      370      12       3       12             0 agetty
Jul 13 21:21:11 server kernel: [7601521.772873] [23711]   111 23711  1325629   157601     843       8   115133             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772876] [30526]   111 30526  1500496   261973     846       9    11664             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772879] [22168]   111 22168  1794945    67719     918      10   236605             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772883] [ 1736]   111  1736  1246039    26906     445       8    49225             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772886] [ 8371]   111  8371  1421929   151860    1074       9   253413             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772889] [25486]   111 25486  1760135   281997     881      10     5366             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772892] [ 8320]   111  8320  1208369    63320     439       8    14264             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772895] [15981]   111 15981  1507982    38789     501      10    45822             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772899] [25823]     0 25823   984933    12071     106       6        0         -1000 multipathd
Jul 13 21:21:11 server kernel: [7601521.772914] [28932]   111 28932  3778957  2714270    6748      18   460055             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772917] [ 2369]     0  2369   984614     7551      99       7        0         -1000 multipathd
Jul 13 21:21:11 server kernel: [7601521.772920] [ 4340]     0  4340   984622     7617      99       7        0         -1000 multipathd
Jul 13 21:21:11 server kernel: [7601521.772925] [13170]     0 13170     6798      684      16       3        0             0 screen
Jul 13 21:21:11 server kernel: [7601521.772928] [13172]     0 13172     3133      756      11       3        0             0 clone_ext_vms.s
Jul 13 21:21:11 server kernel: [7601521.772931] [15015]   111 15015  1702370    26705     517      10    75114             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772934] [17093]     0 17093     6798      699      17       3        0             0 screen
Jul 13 21:21:11 server kernel: [7601521.772937] [17094]     0 17094     3133      755      11       3        0             0 clone_int_vms.s
Jul 13 21:21:11 server kernel: [7601521.772940] [18731]   111 18731  1542275    31111     513       9    69146             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772943] [ 1348]     0  1348    56751     5931      93       3        0             0 python
Jul 13 21:21:11 server kernel: [7601521.772946] [15380]     0 15380    56751     5968     101       3        0             0 python
Jul 13 21:21:11 server kernel: [7601521.772950] [22424]     0 22424     1128      189       7       3        0             0 sh
Jul 13 21:21:11 server kernel: [7601521.772953] [22425]     0 22425     1874      522       9       3        0             0 dd
Jul 13 21:21:11 server kernel: [7601521.772955] [22637]     0 22637     1128      191       8       3        0             0 sh
Jul 13 21:21:11 server kernel: [7601521.772958] [22638]     0 22638     1874      529      10       3        0             0 dd
Jul 13 21:21:11 server kernel: [7601521.772961] [  494]   111   494  1118467   795558    1774       7     5489             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772965] [ 9701]   111  9701   352659   143019     465       4      377             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772968] [15505]   111 15505   352163   143958     466       4       45             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772971] [22555]   111 22555   352677   143166     468       4      551             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772974] [30719]   111 30719   352163   136182     468       5     8139             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772978] [ 2810]   111  2810   352402   143455     469       5      366             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772981] [12145]   111 12145   483261   273350     728       5     1164             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772984] [19814]   111 19814   482971   266878     721       5     3868             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772987] [26246]   111 26246   352145   138118     467       5     6142             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772990] [30428]   111 30428   321183   111064     407       4       62             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772993] [ 4157]   111  4157   319631   110301     401       4       28             0 qemu-system-x86
Jul 13 21:21:11 server kernel: [7601521.772999] Out of memory: Kill process 28932 (qemu-system-x86) score 88 or sacrifice child
Jul 13 21:21:11 server kernel: [7601521.773461] Killed process 28932 (qemu-system-x86) total-vm:15115828kB, anon-rss:10846296kB, file-rss:10784kB
Jul 13 21:21:13 server kernel: [7601522.914294] virbr1: port 3(vnet4) entered disabled state
Jul 13 21:21:13 server kernel: [7601522.918014] device vnet4 left promiscuous mode
Jul 13 21:21:13 server kernel: [7601522.918021] virbr1: port 3(vnet4) entered disabled state
Jul 13 21:21:13 server kernel: [7601522.977653] br_int: port 2(vnet3) entered disabled state
Jul 13 21:21:13 server kernel: [7601522.980919] device vnet3 left promiscuous mode
Jul 13 21:21:13 server kernel: [7601522.980922] br_int: port 2(vnet3) entered disabled state
Jul 13 21:21:13 server libvirtd[19115]: internal error: End of file from monitor
Jul 13 21:21:13 server virtlogd[18798]: End of file while reading data: Input/output error
Jul 13 21:21:13 server kernel: [7601523.277770] audit: type=1400 audit(1499977273.477:7810): apparmor="STATUS" operation="profile_remove" profile="unconfined" name="libvirt-95871028-9a96-0fe0-0b2a-b1d1252ffa6a" pid=28069 comm="apparmor_parser"
Jul 13 21:21:14 server systemd[1]: dev-disk-by\x2dlabel-System\x5cx20Reserved.device: Dev dev-disk-by\x2dlabel-System\x5cx20Reserved.device appeared twice with different sysfs paths /sys/devices/virtual/block/dm-4 and /sys/devices/virtual/block/dm-107
Jul 13 21:21:14 server systemd[17952]: dev-disk-by\x2dlabel-System\x5cx20Reserved.device: Dev dev-disk-by\x2dlabel-System\x5cx20Reserved.device appeared twice with different sysfs paths /sys/devices/virtual/block/dm-4 and /sys/devices/virtual/block/dm-107
Jul 13 21:23:39 server sm-mta[727]: v6DJ3dUt024808: Warning: program /usr/sbin/sensible-mda unsafe: No such file or directory
Jul 13 21:23:39 server sm-mta[727]: v6DJ3dUt024808: SYSERR(root): Cannot exec /usr/sbin/sensible-mda: No such file or directory
Jul 13 21:23:39 server sm-mta[726]: v6DJ3dUt024808: to=<root@server.domain.local>, delay=01:20:00, xdelay=00:00:00, mailer=local, pri=750000, dsn=4.0.0, stat=Operating system error



```

---

### Post by Bashing-om on 2017-07-17
mpgk-marsoft; Well, well .

Mind you I may not see all there is to this story, but, What I do see is that we are missing the " linux-image-generic" file . Gotta have it !

```

sudo apt install --reinstall linux-image-generic

```
> 
Description: Generic Linux kernel image
 This package will always depend on the latest generic kernel image
 available.


Also of mind as this is a server application with a lot going on .. inodes ?
Not having addresses for data can cause all kinds of errors, no ?
```

df -i

```


[INDENT][INDENT]2 steps forward
[/INDENT][/INDENT]

---

### Post by mpgk-marsoft on 2017-07-18
Hi [COLOR=#000000]Bashing-om,

Your assistance has been great.

Followed your instructions.
[/COLOR]```
root@server:/var/lib/dpkg/updates# apt install --reinstall linux-image-generic
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```
Then ran:
```

root@server:/var/lib/dpkg/updates# dpkg --configure -a
Setting up initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-83-generic
```[COLOR=#000000]
Where it hangs.
I run update-initramfs -u -v which provides plenty of output (not included as output exceeds file size limit for uploading). Upshot is, this command stops on ```
Calling hook cryptroot
```

I then ran ps -ef | grep initram and killed all initramfs processes.
Once again ran: [/COLOR]apt install --reinstall linux-image-generic
```

root@server:/var/lib/dpkg/updates# apt install --reinstall linux-image-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-headers-4.4.0-45 linux-headers-4.4.0-45-generic linux-headers-4.4.0-53
  linux-headers-4.4.0-53-generic linux-headers-4.4.0-57 linux-headers-4.4.0-57-generic linux-image-4.4.0-31-generic linux-image-4.4.0-45-generic
  linux-image-4.4.0-53-generic linux-image-4.4.0-57-generic linux-image-extra-4.4.0-31-generic linux-image-extra-4.4.0-45-generic
  linux-image-extra-4.4.0-53-generic linux-image-extra-4.4.0-57-generic linux-signed-image-4.4.0-31-generic linux-signed-image-4.4.0-45-generic
  linux-signed-image-4.4.0-53-generic linux-signed-image-4.4.0-57-generic snap-confine
Use 'apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 1 reinstalled, 0 to remove and 7 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/2,288 B of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 229411 files and directories currently installed.)
Preparing to unpack .../linux-image-generic_4.4.0.83.89_amd64.deb ...
Unpacking linux-image-generic (4.4.0.83.89) over (4.4.0.83.89) ...
Setting up initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-generic (4.4.0.83.89) ...
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-83-generic

```
At this stage I again checked the output of [COLOR=#000000]ps -ef | grep initram
[/COLOR]```
root@server:~# ps -ef | grep initram
root     10103     1  0 10:39 ?        00:00:00 /bin/sh /usr/share/initramfs-tools/hooks/cryptroot
root     10108 10103  0 10:39 ?        00:00:00 /bin/sh /usr/share/initramfs-tools/hooks/cryptroot
root     10988 10900  0 10:40 pts/9    00:00:00 /usr/bin/dpkg --status-fd 57 --configure initramfs-tools:all linux-image-generic:amd64
root     10993 10988  0 10:40 pts/9    00:00:00 /bin/sh /var/lib/dpkg/info/initramfs-tools.postinst triggered update-initramfs
root     10994 10993  0 10:40 pts/9    00:00:00 /bin/sh /usr/sbin/update-initramfs -u
root     11002 10994  0 10:40 pts/9    00:00:00 /bin/sh /usr/sbin/mkinitramfs -o /boot/initrd.img-4.4.0-83-generic.new 4.4.0-83-generic
root     14044 11002  0 10:40 pts/9    00:00:00 /bin/sh /usr/share/initramfs-tools/hooks/cryptroot
root     14327 14044  0 10:40 pts/9    00:00:00 /bin/sh /usr/share/initramfs-tools/hooks/cryptroot
root     14331 14327  0 10:40 pts/9    00:00:00 /bin/sh /usr/share/initramfs-tools/hooks/cryptroot
root     14995   918  0 10:41 pts/4    00:00:00 grep --color=auto initram

```

[COLOR=#000000]I killed the last descendant of [/COLOR]/bin/sh /usr/sbin/mkinitramfs -o /boot/initrd.img-4.4.0-83-generic.new 4.4.0-83-generic ```
kill -9 14331
``` and the output of apt install --reinstall linux-image-generic then advanced so:
```

Killed
cryptsetup: FAILURE: could not determine configuration for vg0-lv_root

```
Checked ps -ef again and again killed the last descendant and the apt install output advanced again:
```

Killed
cryptsetup: FAILURE: could not determine configuration for vg0-lv_swap

```
Ran the reinstall command again and this time it appears to have completed.
```

root@server:/var/lib/dpkg/updates# apt install --reinstall linux-image-generic                                                                                   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-headers-4.4.0-45 linux-headers-4.4.0-45-generic linux-headers-4.4.0-53
  linux-headers-4.4.0-53-generic linux-headers-4.4.0-57 linux-headers-4.4.0-57-generic linux-image-4.4.0-31-generic linux-image-4.4.0-45-generic
  linux-image-4.4.0-53-generic linux-image-4.4.0-57-generic linux-image-extra-4.4.0-31-generic linux-image-extra-4.4.0-45-generic
  linux-image-extra-4.4.0-53-generic linux-image-extra-4.4.0-57-generic linux-signed-image-4.4.0-31-generic linux-signed-image-4.4.0-45-generic
  linux-signed-image-4.4.0-53-generic linux-signed-image-4.4.0-57-generic snap-confine
Use 'apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 1 reinstalled, 0 to remove and 7 not to upgrade.
Need to get 0 B/2,288 B of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 229411 files and directories currently installed.)
Preparing to unpack .../linux-image-generic_4.4.0.83.89_amd64.deb ...
Unpacking linux-image-generic (4.4.0.83.89) over (4.4.0.83.89) ...
Setting up linux-image-generic (4.4.0.83.89) ...
root@server:/var/lib/dpkg/updates# 

```



If I now run the commands you originally requested I get:
```

root@server:/var/lib/dpkg/updates# dpkg -l | grep linux-
ii  linux-base                          4.0ubuntu1                                   all          Linux image base package
ii  linux-firmware                      1.157.11                                     all          Firmware for Linux kernel drivers
ii  linux-headers-4.4.0-31              4.4.0-31.50                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic      4.4.0-31.50                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-45              4.4.0-45.66                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-45-generic      4.4.0-45.66                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-53              4.4.0-53.74                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-53-generic      4.4.0-53.74                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-57              4.4.0-57.78                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic      4.4.0-57.78                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-62              4.4.0-62.83                                  all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-62-generic      4.4.0-62.83                                  amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-83              4.4.0-83.106                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-83-generic      4.4.0-83.106                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic               4.4.0.83.89                                  amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-31-generic        4.4.0-31.50                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic        4.4.0-45.66                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-53-generic        4.4.0-53.74                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-57-generic        4.4.0-57.78                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-62-generic        4.4.0-62.83                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-83-generic        4.4.0-83.106                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic  4.4.0-31.50                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-45-generic  4.4.0-45.66                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-53-generic  4.4.0-53.74                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-57-generic  4.4.0-57.78                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-62-generic  4.4.0-62.83                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-83-generic  4.4.0-83.106                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                 4.4.0.83.89                                  amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                4.4.0-83.106                                 amd64        Linux Kernel Headers for development
ii  linux-signed-generic                4.4.0.83.89                                  amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-4.4.0-31-generic 4.4.0-31.50                                  amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-45-generic 4.4.0-45.66                                  amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-53-generic 4.4.0-53.74                                  amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-57-generic 4.4.0-57.78                                  amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-62-generic 4.4.0-62.83                                  amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-83-generic 4.4.0-83.106                                 amd64        Signed kernel image generic
ii  linux-signed-image-generic          4.4.0.83.89                                  amd64        Signed Generic Linux kernel image

```
and
```

root@server:/var/lib/dpkg/updates# ls -al /boot
total 335184
drwxr-xr-x  4 root root     4096 Jul 18 11:24 .
drwxr-xr-x 23 root root     4096 Jul  3 10:39 ..
-rw-r--r--  1 root root  1240067 Jul 13  2016 abi-4.4.0-31-generic
-rw-r--r--  1 root root  1242701 Oct 19  2016 abi-4.4.0-45-generic
-rw-r--r--  1 root root  1243479 Dec  2  2016 abi-4.4.0-53-generic
-rw-r--r--  1 root root  1243800 Dec 10  2016 abi-4.4.0-57-generic
-rw-r--r--  1 root root  1244118 Jan 18 15:59 abi-4.4.0-62-generic
-rw-r--r--  1 root root  1246511 Jun 26 20:45 abi-4.4.0-83-generic
-rw-r--r--  1 root root   189558 Jul 13  2016 config-4.4.0-31-generic
-rw-r--r--  1 root root   189760 Oct 19  2016 config-4.4.0-45-generic
-rw-r--r--  1 root root   189877 Dec  2  2016 config-4.4.0-53-generic
-rw-r--r--  1 root root   189991 Dec 10  2016 config-4.4.0-57-generic
-rw-r--r--  1 root root   190047 Jan 18 15:59 config-4.4.0-62-generic
-rw-r--r--  1 root root   190356 Jun 26 20:45 config-4.4.0-83-generic
drwx------  3 root root     4096 Jan  1  1970 efi
drwxr-xr-x  5 root root     4096 Jul  3 15:10 grub
-rw-r--r--  1 root root 37383212 Jul  3 15:10 initrd.img-4.4.0-31-generic
-rw-r--r--  1 root root 37886882 Jul  3 15:10 initrd.img-4.4.0-45-generic
-rw-r--r--  1 root root 37937061 Jul  3 15:10 initrd.img-4.4.0-53-generic
-rw-r--r--  1 root root 37942595 Jul  3 15:09 initrd.img-4.4.0-57-generic
-rw-r--r--  1 root root 37944246 Jul  3 15:09 initrd.img-4.4.0-62-generic
-rw-r--r--  1 root root 37389652 Jul 18 11:24 initrd.img-4.4.0-83-generic
-rw-------  1 root root  3866473 Jul 13  2016 System.map-4.4.0-31-generic
-rw-------  1 root root  3869895 Oct 19  2016 System.map-4.4.0-45-generic
-rw-------  1 root root  3874377 Dec  2  2016 System.map-4.4.0-53-generic
-rw-------  1 root root  3875329 Dec 10  2016 System.map-4.4.0-57-generic
-rw-------  1 root root  3875553 Jan 18 15:59 System.map-4.4.0-62-generic
-rw-------  1 root root  3883887 Jun 26 20:45 System.map-4.4.0-83-generic
-rw-------  1 root root  7047504 Jul 13  2016 vmlinuz-4.4.0-31-generic
-rw-------  1 root root  7049432 Oct 22  2016 vmlinuz-4.4.0-31-generic.efi.signed
-rw-------  1 root root  7054208 Oct 19  2016 vmlinuz-4.4.0-45-generic
-rw-------  1 root root  7056120 Oct 22  2016 vmlinuz-4.4.0-45-generic.efi.signed
-rw-------  1 root root  7065648 Dec  2  2016 vmlinuz-4.4.0-53-generic
-rw-------  1 root root  7067576 Dec 20  2016 vmlinuz-4.4.0-53-generic.efi.signed
-rw-------  1 root root  7067152 Dec 10  2016 vmlinuz-4.4.0-57-generic
-rw-------  1 root root  7069080 Dec 21  2016 vmlinuz-4.4.0-57-generic.efi.signed
-rw-------  1 root root  7070992 Jan 18 15:59 vmlinuz-4.4.0-62-generic
-rw-------  1 root root  7072920 Feb  3 13:53 vmlinuz-4.4.0-62-generic.efi.signed
-rw-------  1 root root  7092720 Jun 26 20:45 vmlinuz-4.4.0-83-generic
-rw-------  1 root root  7094648 Jul  3 10:40 vmlinuz-4.4.0-83-generic.efi.signed

```


Also, you asked for output for inodes.
```

root@server:/var/lib/dpkg/updates# df -i
Filesystem                                  Inodes  IUsed    IFree IUse% Mounted on
udev                                      16479238   3127 16476111    1% /dev
tmpfs                                     16484255   4756 16479499    1% /run
/dev/mapper/vg0-lv_root                   12640256 258949 12381307    3% /
tmpfs                                     16484255     33 16484222    1% /dev/shm
tmpfs                                     16484255      8 16484247    1% /run/lock
tmpfs                                     16484255     18 16484237    1% /sys/fs/cgroup
/dev/sda1                                        0      0        0     - /boot/efi
cgmfs                                     16484255     14 16484241    1% /run/cgmanager/fs
/dev/mapper/mpath-dx100-IsoArchive-part1   9830400     37  9830363    1% /mnt/IsoArchive
/dev/mapper/mpath-dx100-New-testing-part1 29425664     43 29425621    1% /mnt/testing-new
tmpfs                                     16484255      4 16484251    1% /run/user/1000

```

Having skipped the 2 cryptroot problems by killing the processes do you think my system will be stable to reboot?
Is this likely to occur again?
Best wishes
Max

---

### Post by Bashing-om on 2017-07-18
mpgk-marsoft; Hey !

You do good work .. and all looks pretty good to me .
> 
ii  linux-image-generic                 4.4.0.83.89

Is there a reason that you are keeping all those old kernels ?
Follow the package managers advisement to remove ?? What will it matter in the long term ?
What is the current booting kernel :
```

uname -r

```
Let's consider at a convenient time to re-boot this server and see what results .
Bear in mind I have no experience with encryption and do not know what to make if the reports of cryptsetup: FAILURE: .
I do "assume" that the controlling config files to bring up the file systems are off-line at this time.

We see here what is and then look at the production machine.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by mpgk-marsoft on 2017-07-19
Hi Bashing-om,

As all seemed good I went for a reboot and all went well.
And now:
```

root@server:~# uname -r
4.4.0-83-generic

```

Still don't know what was the problem with the cryptsetup, especially as these drives are not encrypted.
I guess I'll have to be vigilant in the future when I next have to upgrade the kernel and bear this experience in mind.

At a convenient time I will push my VMs onto the backup server and make sure they all work fine and then I can upgrade the production machine as well.

Thank you so much for your assistance.
Best wishes
Max

---

### Post by Bashing-om on 2017-07-19
mpgk-marsoft: Good deal !

Forward progress .

If this matter of this thread is satisfied :
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]see what we can do the next time around
[/INDENT]

---

