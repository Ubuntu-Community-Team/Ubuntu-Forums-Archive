---
title: "HP cciss / SmartArray strange perfomance problem"
date: 2009-11-14
forum: Server Platforms
---

### Post by mkutsevol on 2009-11-14
Hi All!
I have a HP ProLiant BL460c G5 with Smart Array E200i.
Two SAS 146Gb in RAID 1 or 0, tried both, the result differ slightly.

The problem is that when I copy a large file (or do dd if=/dev/cciss/c0d0 of=/dev/null bs=1M as a test) the disk is reading data for some time and then it just stops. In iostat it looks like that:

```

Device:         rrqm/s   wrqm/s     r/s     w/s    rMB/s    wMB/s avgrq-sz avgqu-sz   await  svctm  %util
cciss/c0d0    13603.00     0.00  672.00    0.00    55.80     0.00   170.07     2.12    3.15   1.46  98.00

Device:         rrqm/s   wrqm/s     r/s     w/s    rMB/s    wMB/s avgrq-sz avgqu-sz   await  svctm  %util
cciss/c0d0     7776.50     0.00  383.00    0.00    31.87     0.00   170.42     2.46    3.16   2.60  99.50

Device:         rrqm/s   wrqm/s     r/s     w/s    rMB/s    wMB/s avgrq-sz avgqu-sz   await  svctm  %util
cciss/c0d0        0.00     0.00    0.00    0.00     0.00     0.00     0.00     3.00    0.00   0.00 100.00

Device:         rrqm/s   wrqm/s     r/s     w/s    rMB/s    wMB/s avgrq-sz avgqu-sz   await  svctm  %util
cciss/c0d0        0.00     0.00    0.00    0.00     0.00     0.00     0.00     3.00    0.00   0.00 100.00

Device:         rrqm/s   wrqm/s     r/s     w/s    rMB/s    wMB/s avgrq-sz avgqu-sz   await  svctm  %util
cciss/c0d0        0.00     0.00    0.00    0.00     0.00     0.00     0.00     3.00    0.00   0.00 100.00

```Note, that %util =100 but rMB/s = 0!
And then after some time (up to 40 seconds!) is starts reading again.
In the end I have 6-9 MB/s average read perfomance.
Writing to disk is ok.
There is a described bug, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337419 ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337419")and [http://bugzilla.kernel.org/show_bug.cgi?id=13127](http://bugzilla.kernel.org/show_bug.cgi?id=13127) but changing read_ahead doesn't help me much. tried from 32 to 512.

uname -a
```
Linux vd001 2.6.31-15-server #50-Ubuntu SMP Tue Nov 10 15:50:36 UTC 2009 x86_64 GNU/Linux
```dmesg | grep Mem
```
[    0.000000] Memory: 33006764k/34340860k available (5305k kernel code, 788548k absent, 545548k reserved, 3012k data, 660k init)
```modinfo cciss | grep ^version:
```
version:        3.6.20
```Any ideas are appreciated. I ran out of them and my boss will kill me.
Please! Let's discuss it.

---

### Post by mkutsevol on 2009-11-15
I have to say that this performance degradation occurs in x86_64 kernel.
In ubuntu 9.10/i386 i managed to get 80/MBps playing with read_ahead - it's less than a half of array speed, but it doesn't stop reading, it just reads at 80 all the time.

---

### Post by beric on 2009-12-29
Hello can you please share with us with your conclusions. I'm having the same problem with 9.10 64bit

---

### Post by mkutsevol on 2009-12-30
I ended up in 9.04 x86_64.

---

