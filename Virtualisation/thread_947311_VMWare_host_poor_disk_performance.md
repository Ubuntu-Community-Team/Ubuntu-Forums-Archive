---
title: "VMWare host poor disk performance"
date: 2008-10-14
forum: Virtualisation
---

### Post by Xianath on 2008-10-14
Hi all,

I am experiencing extremely poor HDD performance when resuming virtual machines. Here are some stats:

Dual C2D Xeon 5160 @3.04GHz, 4GB RAM
Ubuntu Server 8.04 LTS 64-bit

```

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.57    0.00    7.41   23.05    0.00   68.97

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda              58.80     1.50  455.70    9.20  2604.00    82.00    11.56     6.97   15.10   1.28  59.30

ppopov@faiella:~$ w
 12:46:00 up 20 days, 21:02,  1 user,  load average: 2.15, 2.07, 1.22
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
ppopov   pts/0    10.191.10.36     12:41    0.00s  0.03s  0.00s w

```

This box is currently doing nothing but resuming a VMWare box (on VMWare Server 1.05). Why the load average and high I/O times? For comparison, here's how it looks with the VMWare guest already restored:

```

ppopov@faiella:~$ sudo hdparm -t -T /dev/sda
/dev/sda:
 Timing cached reads:   6502 MB in  2.00 seconds = 3252.93 MB/sec
 Timing buffered disk reads:  196 MB in  3.03 seconds =  64.60 MB/sec

ppopov@faiella:~$ dd if=/dev/zero of=/var/lib/vmware/machines/temp bs=1048576 count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 52.279 s, 20.5 MB/s

```

Has anyone seen such an issue?

Thanks,
Peter

---

### Post by Xianath on 2008-10-28
The guest disks were badly fragmented (auto-grow does that). Defragmenting helped a lot, though just for a while. I guess I'll have to migrate them over to physical partitions to avoid fragmentation, and switch to XFS to deal with fragmentation (hopefully the new UPS will hold its own this time)

---

