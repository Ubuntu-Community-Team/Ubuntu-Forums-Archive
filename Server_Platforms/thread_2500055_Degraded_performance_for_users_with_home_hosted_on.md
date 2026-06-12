---
title: "Degraded performance for users with /home hosted on NFS server"
date: 2024-08-20
forum: Server Platforms
---

### Post by xnobodyx on 2024-08-20
Hello,

Our setup has Ubuntu 22.04.4 desktops with */home* mounting from an Ubuntu 22.04.4 NFS server (storage in a zfs pool). Performance has degraded when logged in to any of the desktop machines, especially after opening processes that read/write to the home directory (web browsing, opening a terminal etc). This seems especially noticeable the first few minutes after logging in (nfs files are first accessed, but will continue happening on and off intermittently. The same issue happens across all desktops and desktop hardware tests have shown no issues. SSH logins to the desktops can take a while as well (perhaps due to checking keys in */home*)?

No noticeable entries appear in *journalctl *logs when these issues occur but perhaps looking at the wrong logs?

Created a test user on one of the machines, with a local home directory and the account doesn't seem to exhibit any performance issues.

The NFS server seems stable *- zfs status* shows all drives ONLINE and no repairs needed in the last scrub. Looking at *nfsstat* and *nfsiostat* doesn't show any glaring issues. Testing storage performance on the server seems alright as well.

Fileserver Details:

Linux fileserver 5.15.0-118-generic #128-Ubuntu SMP Fri Jul 5 09:28:59 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
IP Address: 10.10.60.1[I]

/etc/exports[/I]:
```
/tank/share       10.10.0.0/16(fsid=0,rw,async,no_root_squash,insecure,no_subtree_check)
```

Desktop Details:

Linux desktop1 6.8.0-40-generic #40~22.04.3-Ubuntu SMP PREEMPT_DYNAMIC Tue Jul 30 17:30:19 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
10.10.60.51 etc.

NFS entries in */etc/fstab*:
```
fileserver:/opt       /opt            nfs4    rw,nodev,soft 0 0
fileserver:/home      /home           nfs4    rw,nodev,soft 0 0
```

Will run some further tests/benchmarks but wanted to post the initial config to see if there were any thoughts or suggestions. any help is greatly appreciated, thanks

---

### Post by TheFu on 2024-08-20
Is other NFS storage slow too?
Are **getent** lookups slow?
Are DNS lookups slow?
Are any snaps being used?
Are the times all synchronized between all systems?
Is NFS4 with Kerberos being used?

For a long time, snaps broke when any NFS was used.  I found their workaround for HOME directories completely unacceptable - forcing NFS HOMEs to be mounted under /home is just foolish.  That removes many things that have been solved on Unix systems for decades from working.  Snaps need to allow HOME directories to be anywhere with local configuration, if LDAP isn't enough "proof" for where HOME directories should be allowed.  Whatever.  The Snap team has refused to move on this, breaking corporate installs of Ubuntu.  Nobody is forced to use Ubuntu after all. There are other distros without this issue.

Of course, your issue may have nothing at all to do with snaps, so perhaps that rant can be ignored.

---

### Post by xnobodyx on 2024-08-20
Thanks.

1. Yes, other NFS storage ( /opt ) appears slow as well.
2. No apparent getent issues (tried groups/networks/services)
3. DNS lookups don't seem to have any problem (dig)
4. Yes firefox is a snap
5. times appear to be synced (timesyncd syncing with ntp.ubuntu.com)
6. Kerberos is not being used, just NFS4

NFS home directories are being mounted in /home . (i did run into the snap issue when creating the local account with a local home directory not in /home/ for testing)

---

### Post by TheFu on 2024-08-20
Can you rule out ZFS as the problem?  Create a little ext4 data area and export that via NFS?
Do you have IO performance data that can be compared between local, ZFS and ext4 NFS storage?  Something like **fio** is commonly used for this.  Wouldn't hurt to compare NFS and rsync performance between the two systems too, just to get a feel for the difference in performance.  In theory, NFS without Kerberos should be much faster - probably to the network speed limit or to the storage speed limit if it is lower (non-SSD).

---

### Post by xnobodyx on 2024-08-20
will try all those tests, thanks

---

### Post by Tadaen_Sylvermane on 2024-08-21
I can't tell if this is a new deployment or not from your post. If you previously were on high speed local storage the answer is simple. If you are running your /home NFS share over Wifi it will be slower no matter what. Even a gigabit hard line will be noticeably slower than local storage ssd style. It can also be limited by the speed of the network uplink on the server itself. Even if you have 10gbit stuff around if the server is uploading a 1gb line then that is the best it will get.

Check for this type of thing before searching deeper I'd think. Way to look at it. Don't bother jumping to change the light bulb unless you make sure the light is plugged in first.

---

### Post by xnobodyx on 2024-08-21
thanks for the reminder. i should have mentioned that i suspect this might be a network level issue, but was worried i might have made an obvious mistake  with the NFS config. this is not a new deployment, the server and desktop config hasn't changed, but the desktops have moved to a new location. desktops and fileserver are using wired connections with 1Gb/s NICs. just did some testing from another server on the same rack as the fileserver and network speeds look fine there, but the desktop speeds aren't good at all. will investigate further.

running *iperf3 --client fileserver --bytes 2G *from the other server:

```
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec   114 MBytes   957 Mbits/sec    0    403 KBytes
[  5]   1.00-2.00   sec   112 MBytes   941 Mbits/sec    0    403 KBytes
[  5]   2.00-3.00   sec   112 MBytes   941 Mbits/sec    0    403 KBytes
[  5]   3.00-4.00   sec   112 MBytes   941 Mbits/sec    0    403 KBytes
[  5]   4.00-5.00   sec   112 MBytes   941 Mbits/sec    0    403 KBytes
[  5]   5.00-6.00   sec   112 MBytes   941 Mbits/sec    0    403 KBytes
[  5]   6.00-7.00   sec   112 MBytes   941 Mbits/sec    0    403 KBytes
[  5]   7.00-8.00   sec   112 MBytes   941 Mbits/sec    0    403 KBytes
[  5]   8.00-9.00   sec   112 MBytes   941 Mbits/sec    0    403 KBytes
[  5]   9.00-10.00  sec   112 MBytes   941 Mbits/sec    0    403 KBytes
```

and from one of the desktops (similar results on others as well):

```
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec   417 KBytes  3.42 Mbits/sec   31   1.41 KBytes
[  5]   1.00-2.00   sec   313 KBytes  2.56 Mbits/sec   36   2.83 KBytes
[  5]   2.00-3.00   sec   331 KBytes  2.71 Mbits/sec   24   1.41 KBytes
[  5]   3.00-4.00   sec  0.00 Bytes  0.00 bits/sec    2   1.41 KBytes
[  5]   4.00-5.00   sec  0.00 Bytes  0.00 bits/sec    0   1.41 KBytes
[  5]   5.00-6.00   sec   157 KBytes  1.29 Mbits/sec   22   1.41 KBytes
[  5]   6.00-7.00   sec   154 KBytes  1.26 Mbits/sec   27   1.41 KBytes
[  5]   7.00-8.00   sec  77.8 KBytes   637 Kbits/sec   12   1.41 KBytes
[  5]   8.00-9.00   sec  76.4 KBytes   625 Kbits/sec   17   1.41 KBytes
[  5]   9.00-10.00  sec   153 KBytes  1.25 Mbits/sec   17   2.83 KBytes
[  5]  10.00-11.00  sec   239 KBytes  1.96 Mbits/sec   33   1.41 KBytes
[  5]  11.00-12.00  sec   154 KBytes  1.26 Mbits/sec   11   1.41 KBytes
[  5]  12.00-13.00  sec  77.8 KBytes   637 Kbits/sec    7   2.83 KBytes
[  5]  13.00-14.00  sec  77.8 KBytes   637 Kbits/sec   20   2.83 KBytes
[  5]  14.00-15.00  sec   642 KBytes  5.26 Mbits/sec   44   1.41 KBytes
[  5]  15.00-16.00  sec  0.00 Bytes  0.00 bits/sec    1   1.41 KBytes
[  5]  16.00-17.00  sec   156 KBytes  1.28 Mbits/sec   24   1.41 KBytes
[  5]  17.00-18.00  sec   154 KBytes  1.26 Mbits/sec   13   2.83 KBytes
[  5]  18.00-19.00  sec   553 KBytes  4.53 Mbits/sec   59   1.41 KBytes
[  5]  19.00-20.00  sec   154 KBytes  1.26 Mbits/sec   18   1.41 KBytes
[  5]  20.00-21.00  sec   235 KBytes  1.92 Mbits/sec   25   1.41 KBytes
[  5]  21.00-22.00  sec   158 KBytes  1.30 Mbits/sec   38   1.41 KBytes
[  5]  22.00-23.00  sec   460 KBytes  3.77 Mbits/sec   44   2.83 KBytes
[  5]  23.00-24.00  sec   156 KBytes  1.27 Mbits/sec   29   1.41 KBytes
[  5]  24.00-25.00  sec   156 KBytes  1.27 Mbits/sec   15   2.83 KBytes
[  5]  25.00-26.00  sec  76.4 KBytes   625 Kbits/sec   12   1.41 KBytes
[  5]  26.00-27.00  sec   229 KBytes  1.88 Mbits/sec   32   2.83 KBytes
[  5]  27.00-28.00  sec   383 KBytes  3.14 Mbits/sec   46   1.41 KBytes
[  5]  28.00-29.00  sec  76.4 KBytes   625 Kbits/sec   14   1.41 KBytes
[  5]  29.00-30.00  sec   235 KBytes  1.92 Mbits/sec   21   1.41 KBytes
[  5]  30.00-31.00  sec  77.8 KBytes   637 Kbits/sec   11   1.41 KBytes
[  5]  31.00-32.00  sec   156 KBytes  1.27 Mbits/sec   23   2.83 KBytes
[  5]  32.00-33.00  sec  77.8 KBytes   637 Kbits/sec   11   1.41 KBytes
[  5]  33.00-34.00  sec   385 KBytes  3.15 Mbits/sec   49   2.83 KBytes
[  5]  34.00-35.00  sec   383 KBytes  3.14 Mbits/sec   40   1.41 KBytes
[  5]  35.00-36.00  sec   232 KBytes  1.90 Mbits/sec   25   2.83 KBytes
[  5]  36.00-37.00  sec   393 KBytes  3.22 Mbits/sec   48   2.83 KBytes
[  5]  37.00-38.00  sec   153 KBytes  1.25 Mbits/sec   23   1.41 KBytes
[  5]  38.00-39.00  sec   156 KBytes  1.27 Mbits/sec   14   2.83 KBytes
[  5]  39.00-40.00  sec  76.4 KBytes   626 Kbits/sec   17   2.83 KBytes
[  5]  40.00-41.00  sec   230 KBytes  1.89 Mbits/sec   35   1.41 KBytes
[  5]  41.00-42.00  sec   475 KBytes  3.89 Mbits/sec   41   1.41 KBytes
[  5]  42.00-43.00  sec   229 KBytes  1.88 Mbits/sec   32   1.41 KBytes
[  5]  43.00-44.00  sec   395 KBytes  3.23 Mbits/sec   40   1.41 KBytes
[  5]  44.00-45.00  sec   389 KBytes  3.19 Mbits/sec   44   4.24 KBytes
[  5]  45.00-46.00  sec   233 KBytes  1.91 Mbits/sec   27   1.41 KBytes
[  5]  46.00-47.00  sec   236 KBytes  1.93 Mbits/sec   36   1.41 KBytes
[  5]  47.00-48.00  sec   396 KBytes  3.24 Mbits/sec   44   1.41 KBytes
[  5]  48.00-49.00  sec   153 KBytes  1.25 Mbits/sec   20   2.83 KBytes
[  5]  49.00-50.00  sec   310 KBytes  2.54 Mbits/sec   31   2.83 KBytes
[  5]  50.00-51.00  sec  0.00 Bytes  0.00 bits/sec   11   1.41 KBytes
[  5]  51.00-52.00  sec   471 KBytes  3.86 Mbits/sec   39   1.41 KBytes
[  5]  52.00-53.00  sec   308 KBytes  2.52 Mbits/sec   33   1.41 KBytes
[  5]  53.00-54.00  sec   240 KBytes  1.97 Mbits/sec   32   1.41 KBytes
[  5]  54.00-55.00  sec   314 KBytes  2.57 Mbits/sec   27   1.41 KBytes
[  5]  55.00-56.00  sec   631 KBytes  5.17 Mbits/sec   50   1.41 KBytes
[  5]  56.00-57.00  sec   235 KBytes  1.92 Mbits/sec   18   2.83 KBytes
[  5]  57.00-58.00  sec   308 KBytes  2.53 Mbits/sec   32   1.41 KBytes
[  5]  58.00-59.00  sec   240 KBytes  1.97 Mbits/sec   25   2.83 KBytes
[  5]  59.00-60.00  sec   154 KBytes  1.26 Mbits/sec   20   1.41 KBytes
[  5]  60.00-61.00  sec   156 KBytes  1.27 Mbits/sec   16   1.41 KBytes
[  5]  61.00-62.00  sec   383 KBytes  3.14 Mbits/sec   37   2.83 KBytes
[  5]  62.00-63.00  sec   154 KBytes  1.26 Mbits/sec   16   1.41 KBytes
[  5]  63.00-64.00  sec   153 KBytes  1.25 Mbits/sec   19   2.83 KBytes
[  5]  64.00-65.00  sec   409 KBytes  3.35 Mbits/sec   45   1.41 KBytes
[  5]  65.00-66.00  sec   158 KBytes  1.30 Mbits/sec   20   1.41 KBytes
[  5]  66.00-67.00  sec   230 KBytes  1.89 Mbits/sec   25   2.83 KBytes
[  5]  67.00-68.00  sec   387 KBytes  3.17 Mbits/sec   32   1.41 KBytes
[  5]  68.00-69.00  sec  76.4 KBytes   625 Kbits/sec   17   1.41 KBytes
[  5]  69.00-70.00  sec   307 KBytes  2.51 Mbits/sec   30   1.41 KBytes
[  5]  70.00-71.00  sec   469 KBytes  3.85 Mbits/sec   55   1.41 KBytes
[  5]  71.00-72.00  sec   154 KBytes  1.26 Mbits/sec   26   1.41 KBytes
[  5]  72.00-73.00  sec   472 KBytes  3.87 Mbits/sec   53   1.41 KBytes
[  5]  73.00-74.00  sec   154 KBytes  1.26 Mbits/sec   17   1.41 KBytes
[  5]  74.00-75.00  sec   474 KBytes  3.88 Mbits/sec   58   1.41 KBytes
[  5]  75.00-76.00  sec   383 KBytes  3.14 Mbits/sec   39   1.41 KBytes
[  5]  76.00-77.00  sec   393 KBytes  3.22 Mbits/sec   63   1.41 KBytes
[  5]  77.00-78.00  sec   622 KBytes  5.10 Mbits/sec   63   1.41 KBytes
[  5]  78.00-79.00  sec   307 KBytes  2.51 Mbits/sec   31   2.83 KBytes
[  5]  79.00-80.00  sec  77.8 KBytes   636 Kbits/sec   10   1.41 KBytes
[  5]  80.00-81.00  sec  79.2 KBytes   649 Kbits/sec   15   1.41 KBytes
[  5]  81.00-82.00  sec   389 KBytes  3.19 Mbits/sec   35   1.41 KBytes
[  5]  82.00-83.00  sec  0.00 Bytes  0.00 bits/sec   17   1.41 KBytes
[  5]  83.00-84.00  sec   386 KBytes  3.16 Mbits/sec   43   1.41 KBytes
[  5]  84.00-85.00  sec   236 KBytes  1.93 Mbits/sec   36   1.41 KBytes
[  5]  85.00-86.00  sec   230 KBytes  1.89 Mbits/sec   17   2.83 KBytes
[  5]  86.00-87.00  sec   154 KBytes  1.26 Mbits/sec   23   1.41 KBytes
[  5]  87.00-88.00  sec   235 KBytes  1.92 Mbits/sec   21   1.41 KBytes
[  5]  88.00-89.00  sec  76.4 KBytes   626 Kbits/sec   14   1.41 KBytes
[  5]  89.00-90.00  sec   310 KBytes  2.54 Mbits/sec   39   1.41 KBytes
[  5]  90.00-91.00  sec   539 KBytes  4.41 Mbits/sec   41   1.41 KBytes
[  5]  91.00-92.00  sec  77.8 KBytes   637 Kbits/sec   11   1.41 KBytes
[  5]  92.00-93.00  sec  79.2 KBytes   648 Kbits/sec    7   1.41 KBytes
[  5]  93.00-94.00  sec   488 KBytes  4.00 Mbits/sec   55   1.41 KBytes
[  5]  94.00-95.00  sec   395 KBytes  3.23 Mbits/sec   39   1.41 KBytes
[  5]  95.00-96.00  sec   567 KBytes  4.65 Mbits/sec   57   2.83 KBytes
[  5]  96.00-97.00  sec   232 KBytes  1.90 Mbits/sec   29   2.83 KBytes
[  5]  97.00-98.00  sec   322 KBytes  2.64 Mbits/sec   27   1.41 KBytes
[  5]  98.00-99.00  sec   544 KBytes  4.46 Mbits/sec   48   2.83 KBytes
[  5]  99.00-100.00 sec  0.00 Bytes  0.00 bits/sec    2   1.41 KBytes
[  5] 100.00-101.00 sec   230 KBytes  1.89 Mbits/sec   24   2.83 KBytes
[  5] 101.00-102.00 sec   235 KBytes  1.92 Mbits/sec   22   1.41 KBytes
[  5] 102.00-103.00 sec   551 KBytes  4.52 Mbits/sec   45   1.41 KBytes
[  5] 103.00-104.00 sec   464 KBytes  3.80 Mbits/sec   47   2.83 KBytes
[  5] 104.00-105.00 sec   157 KBytes  1.29 Mbits/sec   16   1.41 KBytes
[  5] 105.00-106.00 sec   153 KBytes  1.25 Mbits/sec   20   1.41 KBytes
[  5] 106.00-107.00 sec   464 KBytes  3.80 Mbits/sec   46   1.41 KBytes
[  5] 107.00-108.00 sec   153 KBytes  1.25 Mbits/sec   32   1.41 KBytes
[  5] 108.00-109.00 sec   156 KBytes  1.27 Mbits/sec   20   1.41 KBytes
[  5] 109.00-110.00 sec   156 KBytes  1.27 Mbits/sec   23   1.41 KBytes
[  5] 110.00-111.00 sec   153 KBytes  1.25 Mbits/sec   15   1.41 KBytes
[  5] 111.00-112.00 sec   158 KBytes  1.30 Mbits/sec   18   2.83 KBytes
[  5] 112.00-113.00 sec  77.8 KBytes   637 Kbits/sec   13   1.41 KBytes
[  5] 113.00-114.00 sec   313 KBytes  2.56 Mbits/sec   36   2.83 KBytes
[  5] 114.00-115.00 sec  0.00 Bytes  0.00 bits/sec   11   1.41 KBytes
[  5] 115.00-116.00 sec  0.00 Bytes  0.00 bits/sec    1   1.41 KBytes
[  5] 116.00-117.00 sec   156 KBytes  1.28 Mbits/sec   15   1.41 KBytes
[  5] 117.00-118.00 sec   477 KBytes  3.91 Mbits/sec   50   2.83 KBytes
[  5] 118.00-119.00 sec   238 KBytes  1.95 Mbits/sec   32   1.41 KBytes
[  5] 119.00-120.00 sec   236 KBytes  1.93 Mbits/sec   25   1.41 KBytes
[  5] 120.00-121.00 sec  77.8 KBytes   637 Kbits/sec    8   1.41 KBytes
[  5] 121.00-122.00 sec  0.00 Bytes  0.00 bits/sec    2   1.41 KBytes
[  5] 122.00-123.00 sec  0.00 Bytes  0.00 bits/sec    0   1.41 KBytes
[  5] 123.00-124.00 sec  76.4 KBytes   626 Kbits/sec   15   2.83 KBytes
[  5] 124.00-125.00 sec   153 KBytes  1.25 Mbits/sec   14   1.41 KBytes
[  5] 125.00-126.00 sec  76.4 KBytes   625 Kbits/sec   21   1.41 KBytes
[  5] 126.00-127.00 sec   154 KBytes  1.26 Mbits/sec   13   2.83 KBytes
[  5] 127.00-128.00 sec   313 KBytes  2.56 Mbits/sec   38   1.41 KBytes
[  5] 128.00-129.00 sec  77.8 KBytes   637 Kbits/sec   18   1.41 KBytes
[  5] 129.00-130.00 sec   314 KBytes  2.57 Mbits/sec   24   1.41 KBytes
[  5] 130.00-131.00 sec   157 KBytes  1.29 Mbits/sec   24   1.41 KBytes
[  5] 131.00-132.00 sec  76.4 KBytes   625 Kbits/sec   15   1.41 KBytes
[  5] 132.00-133.00 sec   305 KBytes  2.50 Mbits/sec   33   2.83 KBytes
[  5] 133.00-134.00 sec   386 KBytes  3.16 Mbits/sec   41   2.83 KBytes
[  5] 134.00-135.00 sec   406 KBytes  3.32 Mbits/sec   43   1.41 KBytes
[  5] 135.00-136.00 sec   307 KBytes  2.51 Mbits/sec   33   2.83 KBytes
[  5] 136.00-137.00 sec   230 KBytes  1.89 Mbits/sec   29   1.41 KBytes
[  5] 137.00-138.00 sec   233 KBytes  1.91 Mbits/sec   33   1.41 KBytes
[  5] 138.00-139.00 sec   477 KBytes  3.90 Mbits/sec   39   1.41 KBytes
[  5] 139.00-140.00 sec   154 KBytes  1.26 Mbits/sec   27   2.83 KBytes
[  5] 140.00-141.00 sec   164 KBytes  1.34 Mbits/sec   25   1.41 KBytes
[  5] 141.00-142.00 sec   156 KBytes  1.27 Mbits/sec   26   1.41 KBytes
[  5] 142.00-143.00 sec   156 KBytes  1.27 Mbits/sec   14   1.41 KBytes
[  5] 143.00-144.00 sec   233 KBytes  1.91 Mbits/sec   32   1.41 KBytes
[  5] 144.00-145.00 sec   392 KBytes  3.21 Mbits/sec   37   2.83 KBytes
[  5] 145.00-146.00 sec   233 KBytes  1.91 Mbits/sec   26   1.41 KBytes
[  5] 146.00-147.00 sec   315 KBytes  2.58 Mbits/sec   29   1.41 KBytes
[  5] 147.00-148.00 sec   230 KBytes  1.89 Mbits/sec   29   1.41 KBytes
[  5] 148.00-149.00 sec  80.6 KBytes   660 Kbits/sec   25   1.41 KBytes
[  5] 149.00-150.00 sec  76.4 KBytes   625 Kbits/sec   16   1.41 KBytes
[  5] 150.00-151.00 sec   321 KBytes  2.63 Mbits/sec   30   1.41 KBytes
[  5] 151.00-152.00 sec  76.4 KBytes   625 Kbits/sec   14   1.41 KBytes
[  5] 152.00-153.00 sec   232 KBytes  1.90 Mbits/sec   22   1.41 KBytes
[  5] 153.00-154.00 sec  77.8 KBytes   637 Kbits/sec   11   1.41 KBytes
[  5] 154.00-155.00 sec  0.00 Bytes  0.00 bits/sec    1   1.41 KBytes
[  5] 155.00-156.00 sec  79.2 KBytes   649 Kbits/sec   11   1.41 KBytes
[  5] 156.00-157.00 sec  0.00 Bytes  0.00 bits/sec    1   1.41 KBytes
[  5] 157.00-158.00 sec  0.00 Bytes  0.00 bits/sec    0   1.41 KBytes
[  5] 158.00-159.00 sec  0.00 Bytes  0.00 bits/sec    1   1.41 KBytes
[  5] 159.00-160.00 sec  0.00 Bytes  0.00 bits/sec    0   1.41 KBytes
[  5] 160.00-161.00 sec  0.00 Bytes  0.00 bits/sec    0   1.41 KBytes
[  5] 161.00-162.00 sec  77.8 KBytes   638 Kbits/sec    9   1.41 KBytes
[  5] 162.00-163.00 sec  0.00 Bytes  0.00 bits/sec    2   1.41 KBytes
[  5] 163.00-164.00 sec  0.00 Bytes  0.00 bits/sec    1   1.41 KBytes
[  5] 164.00-165.00 sec  0.00 Bytes  0.00 bits/sec    1   1.41 KBytes
[  5] 165.00-166.00 sec  0.00 Bytes  0.00 bits/sec    0   1.41 KBytes
[  5] 166.00-167.00 sec  0.00 Bytes  0.00 bits/sec    0   1.41 KBytes
[  5] 167.00-168.00 sec  0.00 Bytes  0.00 bits/sec    0   1.41 KBytes
[  5] 168.00-169.00 sec  76.4 KBytes   626 Kbits/sec   15   1.41 KBytes
[  5] 169.00-170.00 sec   232 KBytes  1.90 Mbits/sec   31   1.41 KBytes
[  5] 170.00-171.00 sec   308 KBytes  2.53 Mbits/sec   32   4.24 KBytes
[  5] 171.00-172.00 sec   325 KBytes  2.66 Mbits/sec   47   1.41 KBytes
[  5] 172.00-173.00 sec   154 KBytes  1.26 Mbits/sec   21   1.41 KBytes
[  5] 173.00-174.00 sec  76.4 KBytes   625 Kbits/sec   12   1.41 KBytes
[  5] 174.00-175.00 sec  77.8 KBytes   637 Kbits/sec   11   2.83 KBytes
[  5] 175.00-176.00 sec   311 KBytes  2.55 Mbits/sec   34   1.41 KBytes
[  5] 176.00-177.00 sec   229 KBytes  1.88 Mbits/sec   29   1.41 KBytes
[  5] 177.00-178.00 sec   154 KBytes  1.26 Mbits/sec   17   1.41 KBytes
[  5] 178.00-179.00 sec   157 KBytes  1.29 Mbits/sec   18   1.41 KBytes
[  5] 179.00-180.00 sec   233 KBytes  1.91 Mbits/sec   32   2.83 KBytes
[  5] 180.00-181.00 sec   396 KBytes  3.24 Mbits/sec   49   1.41 KBytes
[  5] 181.00-182.00 sec  0.00 Bytes  0.00 bits/sec    9   1.41 KBytes
[  5] 182.00-183.00 sec   233 KBytes  1.91 Mbits/sec   25   1.41 KBytes
[  5] 183.00-184.00 sec   230 KBytes  1.89 Mbits/sec   31   1.41 KBytes
[  5] 184.00-185.00 sec  77.8 KBytes   637 Kbits/sec   14   1.41 KBytes
[  5] 185.00-186.00 sec   387 KBytes  3.18 Mbits/sec   35   2.83 KBytes
[  5] 186.00-187.00 sec   232 KBytes  1.90 Mbits/sec   31   1.41 KBytes
[  5] 187.00-188.00 sec  76.4 KBytes   625 Kbits/sec   14   2.83 KBytes
[  5] 188.00-189.00 sec   154 KBytes  1.26 Mbits/sec   20   1.41 KBytes
[  5] 189.00-190.00 sec  77.8 KBytes   637 Kbits/sec   20   2.83 KBytes
[  5] 190.00-191.00 sec  76.4 KBytes   625 Kbits/sec    5   1.41 KBytes
[  5] 191.00-192.00 sec  77.8 KBytes   637 Kbits/sec   19   2.83 KBytes
[  5] 192.00-193.00 sec  77.8 KBytes   637 Kbits/sec   16   1.41 KBytes
[  5] 193.00-194.00 sec   154 KBytes  1.26 Mbits/sec   21   2.83 KBytes
[  5] 194.00-195.00 sec   233 KBytes  1.91 Mbits/sec   24   1.41 KBytes
[  5] 195.00-196.00 sec   230 KBytes  1.89 Mbits/sec   30   1.41 KBytes
[  5] 196.00-197.00 sec   156 KBytes  1.27 Mbits/sec   32   1.41 KBytes
[  5] 197.00-198.00 sec  0.00 Bytes  0.00 bits/sec    6   1.41 KBytes
[  5] 198.00-199.00 sec   230 KBytes  1.89 Mbits/sec   24   1.41 KBytes
[  5] 199.00-200.00 sec  0.00 Bytes  0.00 bits/sec    7   1.41 KBytes
[  5] 200.00-201.00 sec  79.2 KBytes   649 Kbits/sec   10   2.83 KBytes
[  5] 201.00-202.00 sec  0.00 Bytes  0.00 bits/sec    7   1.41 KBytes
[  5] 202.00-203.00 sec  0.00 Bytes  0.00 bits/sec    2   1.41 KBytes
[  5] 203.00-204.00 sec  0.00 Bytes  0.00 bits/sec    0   1.41 KBytes
[  5] 204.00-205.00 sec  77.8 KBytes   638 Kbits/sec   11   2.83 KBytes
[  5] 205.00-206.00 sec   157 KBytes  1.29 Mbits/sec   22   2.83 KBytes
[  5] 206.00-207.00 sec   397 KBytes  3.26 Mbits/sec   45   1.41 KBytes
[  5] 207.00-208.00 sec   154 KBytes  1.26 Mbits/sec   19   2.83 KBytes
[  5] 208.00-209.00 sec   154 KBytes  1.26 Mbits/sec   17   1.41 KBytes
[  5] 209.00-210.00 sec  77.8 KBytes   637 Kbits/sec   16   1.41 KBytes
[  5] 210.00-211.00 sec   235 KBytes  1.92 Mbits/sec   27   1.41 KBytes
[  5] 211.00-212.00 sec   164 KBytes  1.34 Mbits/sec   26   1.41 KBytes
[  5] 212.00-213.00 sec  79.2 KBytes   649 Kbits/sec   15   2.83 KBytes
[  5] 213.00-214.00 sec  0.00 Bytes  0.00 bits/sec   12   1.41 KBytes
[  5] 214.00-215.00 sec   307 KBytes  2.52 Mbits/sec   39   1.41 KBytes
[  5] 215.00-216.00 sec  79.2 KBytes   649 Kbits/sec   13   1.41 KBytes
[  5] 216.00-217.00 sec   238 KBytes  1.95 Mbits/sec   33   1.41 KBytes
[  5] 217.00-218.00 sec   156 KBytes  1.27 Mbits/sec   15   1.41 KBytes
[  5] 218.00-219.00 sec   154 KBytes  1.26 Mbits/sec   26   2.83 KBytes
[  5] 219.00-220.00 sec   154 KBytes  1.26 Mbits/sec   16   1.41 KBytes
[  5] 220.00-221.00 sec   156 KBytes  1.27 Mbits/sec   24   1.41 KBytes
[  5] 221.00-222.00 sec   232 KBytes  1.90 Mbits/sec   27   1.41 KBytes
[  5] 222.00-223.00 sec   236 KBytes  1.93 Mbits/sec   33   2.83 KBytes
[  5] 223.00-224.00 sec   230 KBytes  1.89 Mbits/sec   35   1.41 KBytes
[  5] 224.00-225.00 sec   154 KBytes  1.26 Mbits/sec   30   1.41 KBytes
[  5] 225.00-226.00 sec   154 KBytes  1.26 Mbits/sec   22   1.41 KBytes
[  5] 226.00-227.00 sec  76.4 KBytes   625 Kbits/sec   15   1.41 KBytes
[  5] 227.00-228.00 sec  79.2 KBytes   649 Kbits/sec   10   1.41 KBytes
[  5] 228.00-229.00 sec  0.00 Bytes  0.00 bits/sec    1   1.41 KBytes
[  5] 229.00-230.00 sec  0.00 Bytes  0.00 bits/sec    0   1.41 KBytes
[  5] 230.00-231.00 sec  0.00 Bytes  0.00 bits/sec    1   1.41 KBytes
[  5] 231.00-232.00 sec  0.00 Bytes  0.00 bits/sec    0   1.41 KBytes
[  5] 232.00-233.00 sec  0.00 Bytes  0.00 bits/sec    0   1.41 KBytes
[  5] 233.00-234.00 sec  0.00 Bytes  0.00 bits/sec    8   1.41 KBytes
[  5] 234.00-235.00 sec   154 KBytes  1.26 Mbits/sec   18   1.41 KBytes
[  5] 235.00-236.00 sec   154 KBytes  1.26 Mbits/sec   24   2.83 KBytes
[  5] 236.00-237.00 sec  76.4 KBytes   626 Kbits/sec   15   1.41 KBytes
[  5] 237.00-238.00 sec  76.4 KBytes   625 Kbits/sec   18   2.83 KBytes
[  5] 238.00-239.00 sec  79.2 KBytes   648 Kbits/sec   16   1.41 KBytes
[  5] 239.00-240.00 sec   156 KBytes  1.28 Mbits/sec   24   1.41 KBytes
[  5] 240.00-241.00 sec  0.00 Bytes  0.00 bits/sec   11   2.83 KBytes
[  5] 241.00-242.00 sec   311 KBytes  2.55 Mbits/sec   36   1.41 KBytes
[  5] 242.00-243.00 sec   154 KBytes  1.26 Mbits/sec   31   2.83 KBytes
[  5] 243.00-244.00 sec  77.8 KBytes   637 Kbits/sec   13   2.83 KBytes
[  5] 244.00-245.00 sec   153 KBytes  1.25 Mbits/sec   18   1.41 KBytes
[  5] 245.00-246.00 sec  76.4 KBytes   625 Kbits/sec   25   1.41 KBytes
[  5] 246.00-247.00 sec   387 KBytes  3.17 Mbits/sec   28   2.83 KBytes
[  5] 247.00-248.00 sec  77.8 KBytes   637 Kbits/sec   20   1.41 KBytes
[  5] 248.00-249.00 sec  76.4 KBytes   625 Kbits/sec   13   1.41 KBytes
[  5] 249.00-250.00 sec  0.00 Bytes  0.00 bits/sec   10   1.41 KBytes
[  5] 250.00-251.00 sec   156 KBytes  1.28 Mbits/sec   16   1.41 KBytes
[  5] 251.00-252.00 sec   153 KBytes  1.25 Mbits/sec   17   1.41 KBytes
[  5] 252.00-253.00 sec   229 KBytes  1.88 Mbits/sec   31   2.83 KBytes
[  5] 253.00-254.00 sec  76.4 KBytes   625 Kbits/sec   15   1.41 KBytes
[  5] 254.00-255.00 sec   156 KBytes  1.27 Mbits/sec   21   1.41 KBytes
[  5] 255.00-256.00 sec   154 KBytes  1.26 Mbits/sec   32   2.83 KBytes
[  5] 256.00-257.00 sec  76.4 KBytes   625 Kbits/sec    9   1.41 KBytes
[  5] 257.00-258.00 sec   157 KBytes  1.29 Mbits/sec   21   1.41 KBytes
[  5] 258.00-259.00 sec  0.00 Bytes  0.00 bits/sec   14   1.41 KBytes
[  5] 259.00-260.00 sec  77.8 KBytes   637 Kbits/sec   14   1.41 KBytes
[  5] 260.00-261.00 sec   156 KBytes  1.27 Mbits/sec   22   1.41 KBytes
[  5] 261.00-262.00 sec   313 KBytes  2.56 Mbits/sec   42   1.41 KBytes
[  5] 262.00-263.00 sec   153 KBytes  1.25 Mbits/sec   24   1.41 KBytes
[  5] 263.00-264.00 sec   156 KBytes  1.27 Mbits/sec   24   1.41 KBytes
[  5] 264.00-265.00 sec  76.4 KBytes   626 Kbits/sec   15   2.83 KBytes
[  5] 265.00-266.00 sec  79.2 KBytes   649 Kbits/sec   15   1.41 KBytes
[  5] 266.00-267.00 sec  77.8 KBytes   637 Kbits/sec   13   1.41 KBytes
[  5] 267.00-268.00 sec   229 KBytes  1.88 Mbits/sec   30   1.41 KBytes
[  5] 268.00-269.00 sec  0.00 Bytes  0.00 bits/sec    1   1.41 KBytes
[  5] 269.00-270.00 sec  0.00 Bytes  0.00 bits/sec    0   1.41 KBytes
[  5] 270.00-271.00 sec  77.8 KBytes   638 Kbits/sec   14   1.41 KBytes
[  5] 271.00-272.00 sec   157 KBytes  1.29 Mbits/sec   28   2.83 KBytes
[  5] 272.00-273.00 sec   154 KBytes  1.26 Mbits/sec   24   2.83 KBytes
```

---

### Post by TheFu on 2024-08-21
So this is the 1-time that it really is a network issue?
Check the routing.  Perhaps someone in the network team made a mistake?

---

### Post by xnobodyx on 2024-09-03
turns out this was a networking issue after all. even though they are in the same building the fileserver and the desktops are on different switches with different fiber connections to the gateway. the fiber connection to the server switch is bad. thanks for all the posts and assistance.

---

