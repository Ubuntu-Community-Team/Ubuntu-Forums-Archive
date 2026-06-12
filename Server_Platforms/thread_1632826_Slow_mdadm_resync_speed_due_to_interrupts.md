---
title: "Slow mdadm resync speed due to interrupts?"
date: 2010-11-28
forum: Server Platforms
---

### Post by tgrimley on 2010-11-28
I recently upgraded my server from an AMD Opteron 165 dual core to a Xeon X3430 quad core & SUPERMICRO MBD-X8SIL-F-O.

I did a --grow --chunk=256 to increase my chunksize and rebuild is super slow.  I did this in a VM before to play around and it was no slower than a normal rebuild, so it seems to be related to the new hardware.  I think it might be an interrupt thing because the interrupts rescheduling look really high to me.. but I have nothing to compare it to.  8 Drives are on the rr2680 (v1.4 self compiled) and 1 is on the onboard SATA ports.  Any suggestions?  Is it safe to reboot during a chunk size change and switch with pci-E port the rr2680 is in?

Some other info:
Linux xxx 2.6.32-21-server #32-Ubuntu SMP Fri Apr 16 09:17:34 UTC 2010 x86_64 GNU/Linux
mdadm - v3.1.4 - 31st August 2010


```
tgrimley@xxx:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3955       2114       1841          0        160       1209
-/+ buffers/cache:        744       3211
Swap:        11629          0      11629
```


```
tgrimley@xxx:~$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 0.91
  Creation Time : Sat Aug 22 13:50:42 2009
     Raid Level : raid6
     Array Size : 9767559680 (9315.07 GiB 10001.98 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 7
  Total Devices : 9
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Nov 28 12:02:25 2010
          State : clean, recovering
 Active Devices : 7
Working Devices : 9
 Failed Devices : 0
  Spare Devices : 2

         Layout : left-symmetric
     Chunk Size : 128K

 Reshape Status : 57% complete
  New Chunksize : 256K

           UUID : 117232ce:f55876b7:9822568f:9ddc1a1a
         Events : 0.3308815

    Number   Major   Minor   RaidDevice State
       0       8      129        0      active sync   /dev/sdi1
       1       8      113        1      active sync   /dev/sdh1
       2       8      145        2      active sync   /dev/sdj1
       3       8       81        3      active sync   /dev/sdf1
       4       8        1        4      active sync   /dev/sda1
       5       8       33        5      active sync   /dev/sdc1
       6       8       97        6      active sync   /dev/sdg1

       7       8       65        -      spare   /dev/sde1
       8       8       49        -      spare   /dev/sdd1


```
```

tgrimley@xxx:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdg1[6] sde1[7](S) sdj1[2] sdi1[0] sdc1[5] sdf1[3] sdh1[1] sdd1[8](S) sda1[4]
      9767559680 blocks super 0.91 level 6, 128k chunk, algorithm 2 [7/7] [UUUUUUU]
      [===========>.........]  reshape = 57.9% (1131896832/1953511936) finish=3656.1min speed=3744K/sec

unused devices: <none>
```


```
tgrimley@xxx:~$ cat /proc/interrupts
           CPU0       CPU1       CPU2       CPU3
  0:         26          0          0       1077   IO-APIC-edge      timer
  1:          0          0          0          2   IO-APIC-edge      i8042
  3:          0          0          0     213197   IO-APIC-edge
  4:      82795      46234        949      89705   IO-APIC-edge
  5:      35945      94013        766      84974   IO-APIC-edge
  8:          0          0          0          1   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 12:          0          0          0          4   IO-APIC-edge      i8042
 16:    4659186          0  322957651       1231   IO-APIC-fasteoi   rr2680
 21:          0       1276         60          0   IO-APIC-fasteoi   ehci_hcd:usb1
 23:       7942      19795        142     117595   IO-APIC-fasteoi   ehci_hcd:usb2
 24:   18567834          0          0          0  HPET_MSI-edge      hpet2
 25:          0   11584272          0          0  HPET_MSI-edge      hpet3
 26:          0          0   31517059          0  HPET_MSI-edge      hpet4
 27:          0          0          0   29138775  HPET_MSI-edge      hpet5
 29:          0          0          0          0   PCI-MSI-edge      aerdrv
 30:          0          0          0          0   PCI-MSI-edge      aerdrv
 34:       1783     790778          0   56130140   PCI-MSI-edge      ahci
 35:         93    7419950          0          0   PCI-MSI-edge      eth1-rx-0
 36:    5102217         94          0          0   PCI-MSI-edge      eth1-tx-0
 37:          0          2          0          0   PCI-MSI-edge      eth1
NMI:          0          0          0          0   Non-maskable interrupts
LOC:         57         42         25          8   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
PND:          0          0          0          0   Performance pending work
RES:     242486     507369      37124       6580   Rescheduling interrupts
CAL:         67        113        116        121   Function call interrupts
TLB:      37806      28987      37664      25248   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:       1078       1078       1078       1078   Machine check polls
ERR:          3
MIS:          0

```

---

### Post by u.kron on 2010-12-08
Hi. I have the same problem and the same version of mdadm. But only use it under Gentoo.

I guess it`s a version problem. I have the another PC but with 3.0 version of mdadm and it`s makes a resync with 20MB/s speed.

I have`t tried this theory yet but I guess I will soon.

If you`ll find the solution - please post it here :]

---

### Post by u.kron on 2010-12-08
I had tried version 3.0 of mdadm and now it`s resync with 20MB/s
Anyway it`s tooo slow but I have no idea what can make work it faster..

---

### Post by Fafler on 2010-12-08
Try this:
```
echo "50000" > /proc/sys/dev/raid/speed_limit_min
```

On my system, the default minimum speed was 3000 kb/s.

---

### Post by u.kron on 2010-12-08
Thanks :]
On my it was 1000 but increasing it did`t made any changings on both PC :/

---

### Post by u.kron on 2010-12-09
Things that I had tried:

Installed the 3.0 version of mdadm.
Turn on the ACPI function in bios.
Added PCI SATA Controller.
Switched two of three HDD`s to the pci controller (I had a desire to switch all HDD`s but system just can`t boot in that case :/ ).
Disabled CONFIG_MULTICORE_RAID456 in Linux Kernel.

Now I have 35MB/s when raid make`s a resync and about 170MB/s with hdparm -Tt

Maybe there is more possibilities to improve the resync speed but I have`t found it yet.

---

