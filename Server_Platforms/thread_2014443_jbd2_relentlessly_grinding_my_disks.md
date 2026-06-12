---
title: "jbd2 relentlessly grinding my disks"
date: 2012-07-01
forum: Server Platforms
---

### Post by ziggo0 on 2012-07-01
Fresh install of Ubuntu Server 12.04 LTS. Completely updated with apt-get update;apt-get upgrade -y;apt-get dist-upgrade -y. ```
root@nas:~# uname -r
3.2.0-26-generic
```Freshly created mdadm raid6 array with 8x2TB disks.
 ```
mdadm --verbose --create /dev/md0 --assume-clean --level=raid6 --raid-devices=8 /dev/sd[abcdefgh]1
```ext4 partition created with

```
mkfs.ext4 -m 0 /dev/md0
```Mounted with noatime & barrier=0. I used dstat to monitor hard disk usage when I noticed 1024kb/1Mb is constantly being written to the array. This is strange because there is nothing on it and no processes actively using it. I checked iotop and iostat to see what was going on, jbd2 is constantly writing to all the disks for no reason. 

```
root@nas:~# iostat
Linux 3.2.0-26-generic (nas)    07/01/2012      _x86_64_        (2 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.01    0.04    8.07    1.09    0.00   90.78

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda              87.53     22952.77       258.64 1965548515   22148179
sdb              69.69     22956.48       258.65 1965866335   22149711
sdc              81.86     22947.08       257.21 1965061481   22026359
sdd              86.78     22941.53       256.91 1964585771   22000403
sde              63.51     22949.12       258.31 1965235776   22120235
sdf              76.66     22949.06       258.26 1965230414   22115823
md0              10.64         0.09       943.55       7458   80800300
sdg             132.80     22943.42       259.23 1964748196   22199139
sdh             134.83     22947.22       259.57 1965072963   22228463
sdi               0.18         2.26         4.18     193865     358268

``````

Total DISK READ:       0.00 B/s | Total DISK WRITE:    1041.98 K/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND
 3258 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.12 % [jbd2/md0-8]
    1 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % init
    2 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kthreadd]
    3 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/0]
    5 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/u:0]

``````

Total DISK READ:       0.00 B/s | Total DISK WRITE:    1026.25 K/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND
 3258 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.12 % [jbd2/md0-8]
    1 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % init
    2 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kthreadd]

``````

Total DISK READ:       0.00 B/s | Total DISK WRITE:    1026.35 K/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND
 3258 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.37 % [jbd2/md0-8]
    1 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % init
    2 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kthreadd]
    3 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/0]

```

I've tried mounting it with no special options, just noatime, etc...didn't change anything. I also tried a 'fix' I found googling the subject...disabling the journal. This really isn't an option as the array isn't meant for performance but bulk network accessible storage. I disabled it to test to see if that fixed it and jbd2 still kept writing...after reboots and remounts it didn't change. What other information do I need to provide to figure out this issue? I really need to get this array back into use...but I'm not gonna use it while all the disks are being written to constantly for no reason.

---

### Post by rubylaser on 2012-07-02
I just built a 8 disk RAID6 mdadm array on Ubuntu 12.04 Server array in Virtualbox, without any special mount options and without the --assume-clean option and I don't see reads/writes to the array without me causing it (or from the initial sync action).

```
root@test:~# uname -r
3.2.0-26-generic

```

```
mdadm --create --verbose /dev/md0 --level=6 --raid-devices=8 /dev/sd[bcdefghi]1
```

```
mkfs.ext4 -b 4096 -E stride=128,stripe-width=768 -m 0 /dev/md0
```
```
mkdir /storage
```
```
cat /etc/fstab | grep /dev/md0
/dev/md0        /storage            ext4        defaults        0        0
```

```
iotop -a -p $(sed 's, , -p ,g' <<<`pgrep "_raid|_resync|jbd2"`)
```

```
Total DISK READ:       0.00 B/s | Total DISK WRITE:       0.00 B/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND                                       
  235 be/3 root          0.00 B     32.00 K  0.00 %  0.00 % [jbd2/sda1-8]
 8013 be/4 root          0.00 B      0.00 B  0.00 %  0.00 % [md0_raid6]
 8054 be/3 root          0.00 B      0.00 B  0.00 %  0.00 % [jbd2/md0-8]

```

Both of your iotop examples don't show any activity on your mdadm array.  If if was being written to, it would have a write value in it's row like this.

```
Total DISK READ:       0.00 B/s | Total DISK WRITE:      27.95 K/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND                                       
  287 be/3 root          0.00 B    152.00 K  0.00 %  0.02 % [jbd2/sda1-8]
  721 be/3 root          0.00 B     **[COLOR="Red"]84.02 M[/COLOR]**  0.00 %  0.02 % [jbd2/md0-8]
  274 be/4 root          0.00 B      0.00 B  0.00 %  0.00 % [md0_raid6]

```

^ I caused this using dd to write a small testfile to the array like this.

```
dd if=/dev/zero of=/storage/testfile.out bs=1M count=100
```

To my eyes, both your example and mine both seem to be working as intended.  Please let me know if you think I have not interrupted your results correctly :)

As a sidebar, why did you use the assume-clean flag when you where creating your new array?  This will obviously prevent a sync action, but you want a new array to be in sync from the beginning, that's the whole point of disk parity.

---

### Post by ziggo0 on 2012-07-03
I was beginning to think my assume clean flag had something to do with it. I was trying to skip the inital resync for testing purposes (erasing superblocks, recovering file systems etc) and I never deviated from that. I'll go ahead and re-create the array without assume clean, let it resync and see if that makes any changes. Thanks for your reply & testing!

---

### Post by rubylaser on 2012-07-03
Sounds good, keep me posted on your results.

---

### Post by ziggo0 on 2012-07-17
Apologizes for taking so long to update this. One of the disks was on the way out and took a crap during the resync process. Got the replacement in yesterday and it just finished resyncing - formatted like above and jbd2 is still hitting the array. Not really sure why or how to track down what's making it think it should - any suggestions or ideas now that we have the resync thing out of the way?

---

### Post by rubylaser on 2012-07-17
Can you post your top, iostat and iotop results without doing anything on the array?

---

### Post by ziggo0 on 2012-07-17
When watching top, I'm often seeing kworker/0:1 kworker/1:1 etc, md0_raid6, ext4lazyinit jump to the top of the list.

```

top - 12:35:09 up 11:21,  1 user,  load average: 0.26, 0.28, 0.30
Tasks:  93 total,   1 running,  92 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.5%sy,  0.0%ni, 98.3%id,  1.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   3977896k total,   888872k used,  3089024k free,   102316k buffers
Swap:  1048572k total,        0k used,  1048572k free,   348420k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
  305 root      20   0     0    0    0 S    0  0.0   1:27.30 md0_raid6
    1 root      20   0 24324 2248 1268 S    0  0.1   0:00.59 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S    0  0.0   0:00.60 ksoftirqd/0
    5 root      20   0     0    0    0 S    0  0.0   0:00.33 kworker/u:0
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0
    7 root      RT   0     0    0    0 S    0  0.0   0:00.10 watchdog/0
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1
   10 root      20   0     0    0    0 S    0  0.0   0:00.37 ksoftirqd/1
   12 root      RT   0     0    0    0 S    0  0.0   0:00.08 watchdog/1
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset
   14 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 kdevtmpfs
   16 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns
   17 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:1
   18 root      20   0     0    0    0 S    0  0.0   0:00.08 sync_supers
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default
   20 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd
   22 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff
   23 root      20   0     0    0    0 S    0  0.0   0:00.04 khubd
   24 root       0 -20     0    0    0 S    0  0.0   0:00.00 md
   26 root      20   0     0    0    0 S    0  0.0   0:00.00 khungtaskd
   27 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0
   28 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd
   29 root      39  19     0    0    0 S    0  0.0   0:00.00 khugepaged
   30 root      20   0     0    0    0 S    0  0.0   0:00.00 fsnotify_mark
   31 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea
   32 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto
   40 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld
   41 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0
   42 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_1
   43 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_2
   44 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_3
   48 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_4
   49 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_5
   52 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_6
   53 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_7
   75 root       0 -20     0    0    0 S    0  0.0   0:00.00 devfreq_wq
   79 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_8
   80 root      20   0     0    0    0 S    0  0.0   0:01.26 usb-storage
  263 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_9
  269 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_10
  313 root      20   0     0    0    0 S    0  0.0   0:07.73 kworker/0:2
  322 root      20   0     0    0    0 S    0  0.0   0:00.09 jbd2/sdi1-8
  323 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit
  434 root      20   0 17936 1448  484 S    0  0.0   0:00.08 upstart-udev-br
  437 root      20   0 21744 1512  760 S    0  0.0   0:00.05 udevd
  532 root      20   0 21708 1044  320 S    0  0.0   0:00.00 udevd
  533 root      20   0 21708 1024  300 S    0  0.0   0:00.00 udevd
  587 root       0 -20     0    0    0 S    0  0.0   0:00.00 ttm_swap
  662 root       0 -20     0    0    0 S    0  0.0   0:00.00 kpsmoused
 1082 root      20   0 23344 1352 1004 S    0  0.0   0:00.00 vsftpd
 1144 root      20   0 15180  412  192 S    0  0.0   0:00.00 upstart-socket-
 1162 root      20   0     0    0    0 S    0  0.0   0:00.82 jbd2/md0-8
 1163 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit
 1164 root      20   0     0    0    0 S    0  0.0   0:13.70 ext4lazyinit

``````

root@nas:~# iostat
Linux 3.2.0-26-generic (nas)    07/17/2012      _x86_64_        (2 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.07    0.01    0.15    0.48    0.00   99.29

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda               4.44        68.36       164.75    2802392    6754112
sdb               6.56        71.50       164.74    2931074    6753740
sdc               6.22        63.71       163.82    2611648    6715892
sdd               6.01        59.07       163.55    2421584    6704900
sde               6.36        65.32       164.59    2677799    6747340
sdf               6.32        65.27       164.51    2675690    6744360
md0              15.87        36.07       595.70    1478549   24421128
sdg               5.12        60.64       165.21    2486068    6772836
sdh               5.23        63.76       165.58    2613855    6787880
sdi               0.37         5.71         6.72     234229     275592

``````

Total DISK READ:       0.00 B/s | Total DISK WRITE:    1026.20 K/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND
 1162 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.05 % [jbd2/md0-8]
    1 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % init
    2 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kthreadd]
    3 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/0]
    5 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/u:0]
    6 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [migration/0]
    7 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [watchdog/0]
    8 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [migration/1]
   10 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/1]
   12 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [watchdog/1]
   13 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [cpuset]
   14 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [khelper]
   15 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kdevtmpfs]
   16 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [netns]
   17 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/u:1]
   18 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [sync_supers]
   19 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [bdi-default]
   20 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kintegrityd]
   21 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kblockd]
   22 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ata_sff]
   23 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [khubd]
   24 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [md]
   26 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [khungtaskd]
   27 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kswapd0]
   28 be/5 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksmd]
   29 be/7 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [khugepaged]
   30 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [fsnotify_mark]
   31 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ecryptfs-kthrea]
   32 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [crypto]
   40 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kthrotld]
   41 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [scsi_eh_0]
   42 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [scsi_eh_1]
   43 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [scsi_eh_2]
   44 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [scsi_eh_3]
   48 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [scsi_eh_4]
   49 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [scsi_eh_5]
   52 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [scsi_eh_6]
   53 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [scsi_eh_7]
 1082 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % vsftpd
   75 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [devfreq_wq]
   79 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [scsi_eh_8]
   80 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [usb-storage]
 1144 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % upstart-socket-bridge --daemon
  532 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % udevd --daemon
  533 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % udevd --daemon
 1668 be/4 ziggo0      0.00 B/s    0.00 B/s  0.00 %  0.00 % sshd: ziggo0@pts/0
 1669 be/4 ziggo0      0.00 B/s    0.00 B/s  0.00 %  0.00 % -bash
 1163 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ext4-dio-unwrit]
 1164 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ext4lazyinit]
 1167 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [jbd2/sdg2-8]
 1168 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ext4-dio-unwrit]
 1475 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % console-kit-daemon --no-daemon
  662 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kpsmoused]
 1181 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % smbd -F
 1195 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % smbd -F
 1196 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % nmbd -D
 1208 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % sshd -D
 1213 be/4 messageb    0.00 B/s    0.00 B/s  0.00 %  0.00 % dbus-daemon --system --fork --activation=upstart
 1223 be/4 syslog      0.00 B/s    0.00 B/s  0.00 %  0.00 % rsyslogd -c5
 2538 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/1:1]
 1228 be/4 syslog      0.00 B/s    0.00 B/s  0.00 %  0.00 % rsyslogd -c5
 1229 be/4 syslog      0.00 B/s    0.00 B/s  0.00 %  0.00 % rsyslogd -c5

```

---

### Post by ziggo0 on 2012-07-19
To update this - it's finally stopped. After much research I finally came across a tid bit of information stating that when you format an ext4 partition it's basically a 'quick' format...and over time it slowly 'formats' the rest of the drive. For large volumes like mine (12TB) it can take an extensive amount of time. It finally seems to be done and things are back to normal...i'll update this if I get any more new.

---

### Post by jickerson on 2012-08-25
> **ziggo0 said:**
> To update this - it's finally stopped. After much research I finally came across a tid bit of information stating that when you format an ext4 partition it's basically a 'quick' format...and over time it slowly 'formats' the rest of the drive. For large volumes like mine (12TB) it can take an extensive amount of time. It finally seems to be done and things are back to normal...i'll update this if I get any more new.


I just ran into the same problem. How long did it take for your array to finish the process?

---

### Post by szafran on 2012-09-24
> **jickerson said:**
> I just ran into the same problem. How long did it take for your array to finish the process?

Same here. But I have 2 x 11TB filesystems. How soon can I expect the disk grinding to be over?

---

