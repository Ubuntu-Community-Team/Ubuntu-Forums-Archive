---
title: "&quot;Very big device. Trying to use READ CAPACITY(16)&quot; with 8TB HDDs and BTRFS"
date: 2018-03-02
forum: Server Platforms
---

### Post by Menion on 2018-03-02
[FONT=arial]Hi all
I have recently started to operate an array of 5x8TB HDD (WD RED) in RAID5 mode
The array is in an USB3.0 5 bay enclosure
The array seems to work ok, but with the time the dmesg is flooded by this log:

```
[[ 338.674673]("tel:%5B%20%20338.674673")] sd 0:0:0:0: [sda] Very big device. Trying to use READ
CAPACITY(16).
[[ 338.767184]("tel:%5B%20%20338.767184")] sd 0:0:0:1: [sdb] Very big device. Trying to use READ
CAPACITY(16).
[  338.989477] sd 0:0:0:3: [sdd] Very big device. Trying to use READ
CAPACITY(16).
[  339.301194] sd 0:0:0:4: [sde] Very big device. Trying to use READ
CAPACITY(16).
[  339.506579] sd 0:0:0:2: [sdc] Very big device. Trying to use READ
CAPACITY(16).
[  649.393340] sd 0:0:0:0: [sda] Very big device. Trying to use READ
CAPACITY(16).
[  650.129849] sd 0:0:0:1: [sdb] Very big device. Trying to use READ
CAPACITY(16).
[  650.379622] sd 0:0:0:3: [sdd] Very big device. Trying to use READ
CAPACITY(16).
[  650.524828] sd 0:0:0:4: [sde] Very big device. Trying to use READ
CAPACITY(16).
[  650.721615] sd 0:0:0:2: [sdc] Very big device. Trying to use READ
CAPACITY(16).

```

sda,sdb,sdc,sdd,sde as you can imagine are the HDDs in the array

Other info (note: there is also another single BTRFS array of 3 small
device that never print this log and my root filesystem is BTRFS as
well)

```
menion@Menionubuntu:/etc$ uname -a
Linux Menionubuntu 4.15.5-041505-generic #201802221031 SMP Thu Feb 22
15:32:28 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
menion@Menionubuntu:/etc$   btrfs --version
btrfs-progs v4.15.1
menion@Menionubuntu:/etc$ sudo btrfs fi show
[sudo] password for menion:
Label: none  uuid: 6db4baf7-fda8-41ac-a6ad-1ca7b083430f
        Total devices 1 FS bytes used 9.02GiB
        devid    1 size 27.07GiB used 11.02GiB path /dev/mmcblk0p3

Label: none  uuid: 931d40c6-7cd7-46f3-a4bf-61f3a53844bc
        Total devices 5 FS bytes used 5.47TiB
        devid    1 size 7.28TiB used 1.37TiB path /dev/sda
        devid    2 size 7.28TiB used 1.37TiB path /dev/sdb
        devid    3 size 7.28TiB used 1.37TiB path /dev/sdc
        devid    4 size 7.28TiB used 1.37TiB path /dev/sdd
        devid    5 size 7.28TiB used 1.37TiB path /dev/sde

Label: none  uuid: ba1e0d88-2e26-499d-8fe3-458b9c53349a
        Total devices 3 FS bytes used 534.50GiB
        devid    1 size 232.89GiB used 102.03GiB path /dev/sdh
        devid    2 size 232.89GiB used 102.00GiB path /dev/sdi
        devid    3 size 465.76GiB used 335.03GiB path /dev/sdj

menion@Menionubuntu:/etc$ sudo btrfs fi df /media/storage/das1
Data, RAID5: total=5.49TiB, used=5.46TiB
System, RAID5: total=12.75MiB, used=352.00KiB
Metadata, RAID5: total=7.00GiB, used=6.11GiB
GlobalReserve, single: total=512.00MiB, used=0.00B
menion@Menionubuntu:/etc$
```[/FONT]

[FONT=arial]I am not quite sure which subsystem is responsible of the issue, but I cannot believe that any 8TB HD with other filesystem show the error, but I really don't know where can I start to troubleshoot this[/FONT]

---

