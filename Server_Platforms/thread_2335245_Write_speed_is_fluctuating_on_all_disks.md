---
title: "Write speed is fluctuating on all disks"
date: 2016-08-26
forum: Server Platforms
---

### Post by speed... on 2016-08-26
Hi all,

I have some problems with my write speed on all disks.
First of all some informations:
- New to Ubuntu :)
- Ubuntu 16.04.1 LTS
- ProLiant MicroServer Gen8 (819185-421)
- Intel(R) Celeron(R) CPU G1610T @ 2.30GHz
- 4GB RAM
- 4 disks (1x 300GB, 3x 2TB Western Digital Red, 2 of the 2TB disks are new)
- Fresh installation on new server, it occurs since the beginning

When I copy something to the server via samba from a Win10 Pc the speed  is fluctuating from 110 MB/s to 5-6 MB/s. In the example I copied 18  Files with ca 3 GB.
[ATTACH=CONFIG]270878[/ATTACH]
The other way (from server to client) the speed is constant at 110 MB/s.

The same thing happens when I copy something via rsync localy on the server.
Copy from "Disk1" to "Disk2" via rsync -> fluctuating from 5 to 100 MB/s
Copy from "Disk1" to "OS Disk" via rsync -> fluctuating from 5 to 100 MB/s
Copy from "OS Disk" to "Disk 1" via rsync -> fluctuating from 5 to 100 MB/s


When I check iotop during the copy process, I saw that kworker and jbd2 use 99% of I/O eveytime when the transfer rate is going down
[IMG]https://s4.postimg.io/ha35sq1nh/Disk2.jpg[/IMG]

My fstab.conf:
```
/dev/mapper/srv01--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=219329f1-bb1c-4226-bde5-702b80657af8 /boot           ext2    defaults        0       2
/dev/mapper/srv01--vg-swap_1 none            swap    sw              0       0
/dev/sdb /data/movies                                     ext4  errors=remount-ro 0 1
/dev/sdc /data/data                                       ext4  errors=remount-ro 0 1
/dev/sdd1 /data/backup                                    ext4  errors=remount-ro 0 1
```

I tried to mount the disk with the "commit=600" option and than it works  much better. No fluctuations but during the copy process after 30-40%  the speed goes down from 100 MB/s to 50 MB/s (2,5 GB, 14 Files).  Checking with iotop the kworker process is again using the disk with  99%.

With the old server that I had before the write speed was always around 100 MB/s. Somebody has an idea what could be the cause?

Thank you and when you need additional info let me know :smile:

Best
Speed

---

### Post by Graham_Willis on 2016-08-27
1. Can you boot your machine from live CD of a completely different Linux distribution, then mount the disks and check what the results of the copying tests will be then? It'd allow us to figure out at once if the problem lies with the OS or with the disks.
2. When you're using **commit **option of **mount** command - after how many minutes the speed of write operation goes down? **commit** says **mount** after what time it should actually write data to the disk. So perhaps the observed initial boost in performance isn't a real boost, but the progress indicator shows that because the first part of the copy procedure (which can be copying data to the memory) indeed goes fast. And then when the real write is attempted, it (possibly) throttles.
3. What's the speed of the write and read operations when using **dd**, are fluctuations also observed? Check this using the following commands (with the first you'll create the test file). Of course try manipulating parameters:

**dd if=/dev/zero of=file bs=1024k count=180**
[B]dd if=file of=/dev/null bs=1024k

[/B]4. What's the speed of write operation when you're copying a file from the same disk to the same disk? Fluctuations observed? On the old server did you perform write operations among different disks?
5. Have you tried performing **fsck **on your disks (**if you allow it to make repairs you must unmount the disk on which checking will be performed earlier, otherwise you'll lose your data**)? No errors reported? It's rather unlikely that filesystems would be damaged on all of them, but who knows.

---

### Post by speed... on 2016-08-30
Sorry for the late response.

2. The write speed goes down after 5-8 seconds.

I will try the other tests the next days.

---

### Post by speed... on 2016-09-03
Sorry again for the late response, I was a bit busy in the last day. Here the results of the tests. Please let me know if I have to do further tests.

1. I tried with a live cd from Linux mint and it seems that the same thing happens. The copy process freeze for 2-3 seconds every 500 MB, copy speed was 50-60 MB/s (MKV file with 5,7 GB)

3.
```
dd if=/dev/zero of=test.mkv bs=1024k count=180
180+0 records in
180+0 records out
188743680 bytes (189 MB, 180 MiB) copied, 2.91832 s, 64.7 MB/s
```
```
dd if=/dev/zero of=test.mkv bs=1024k count=1800
1800+0 records in
1800+0 records out
1887436800 bytes (1.9 GB, 1.8 GiB) copied, 31.8955 s, 59.2 MB/s
```
```
dd if=test.mkv of=/dev/null bs=1024k
1800+0 records in
1800+0 records out
1887436800 bytes (1.9 GB, 1.8 GiB) copied, 0.458885 s, 4.1 GB/s
```
```
dd if=test.mkv of=/dev/null bs=1024M
1+1 records in
1+1 records out
1887436800 bytes (1.9 GB, 1.8 GiB) copied, 0.914059 s, 2.1 GB/s
```

4. Yes, I can observe the same fluctuations. 2 of the actual disks are the same that worked well with the old server

5.
```
fsck /dev/sdb
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/sdb: clean, 3747/122101760 files, 452258855/488378646 blocks
```
```
fsck /dev/sdc
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
Setting free inodes count to 122096831 (was 122096833)
Setting free blocks count to 455146951 (was 456339209)
/dev/sdc: clean, 4929/122101760 files, 33231695/488378646 blocks
```
```
fsck /dev/sdd1
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/sdd1: clean, 7558/67108864 files, 30588111/268435456 blocks
```

It seems that it depends from the hardware, not from the OS. Maybe you have some suggestion what I can do to fix this.

Thank you in advanced

/Edit: P.S. I found this [manual]("https://www.linuxserver.io/index.php/2015/03/24/hp-proliant-microserver-gen8-g1610t-setting-up-a-linux-home-server/") in the internet and I saw that, during step 3, I selected "Enable Sata Legacy support" and not "Enable Sata AHCI support". Could this be the problem?

---

### Post by speed... on 2016-09-04
I changed the selection from **Legacy **mode to **AHCI **mode in the bios. After correction the /etc/fstab file its working now.
The speed is again around 100 MB/s.
Thank you very much for you patience and the support.:D

---

