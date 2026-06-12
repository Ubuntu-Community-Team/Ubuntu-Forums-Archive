---
title: "soft lockup - CPU#0 stuck for 61s"
date: 2011-02-10
forum: Server Platforms
---

### Post by Snowjoggs on 2011-02-10
If whenever I have too much I/O traffic (many downloads at once etc) on my system the system becomes unresponsive and the console spews out 

soft lockup - CPU#0 stuck for 61s
soft lockup - CPU#0 stuck for 61s
soft lockup - CPU#0 stuck for 61s

Here is what I have tried till now.

First to try disable APCI

I tried to do this by editing /etc/default/grub, adding this line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet noapic"
```then ran update-grub.
The problem remained after I rebooted.

The error occurs even if I use a disk connected to the onboard IDE or SATA, or even via SATA PCI cards.

Goggle results suggested turining off HT.
This is trickier because my crappy BIOS does not have this option. I tried updating to the latest one, but they have not included the option for some reason. I guess there is no way to turn off HT via ubuntu?

My motherboard is the GA-G31-ES2L (rev 1.x)

[http://www.gigabyte.com/products/product-page.aspx?pid=2889#ov](http://www.gigabyte.com/products/product-page.aspx?pid=2889#ov)

Any other things I could try?

Other infos

```

klingon@enterprise:~$ uname -a
Linux enterprise 2.6.32-28-server #55-Ubuntu SMP Mon Jan 10 23:57:16 UTC 2011 x86_64 GNU/Linux

``````
cat: /proc/: Is a directory
klingon@enterprise:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Celeron(R) CPU        E1500  @ 2.20GHz
stepping        : 13
cpu MHz         : 1200.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips        : 4400.10
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Celeron(R) CPU        E1500  @ 2.20GHz
stepping        : 13
cpu MHz         : 1200.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips        : 4400.01
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

``````

klingon@enterprise:~$ cat /proc/meminfo
MemTotal:        1012900 kB
MemFree:          793412 kB
Buffers:           23944 kB
Cached:            81468 kB
SwapCached:            0 kB
Active:            45104 kB
Inactive:          80700 kB
Active(anon):      20472 kB
Inactive(anon):     8804 kB
Active(file):      24632 kB
Inactive(file):    71896 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       2969592 kB
SwapFree:        2969592 kB
Dirty:                 4 kB
Writeback:             0 kB
AnonPages:         20388 kB
Mapped:            13856 kB
Shmem:              8888 kB
Slab:              18320 kB
SReclaimable:       8848 kB
SUnreclaim:         9472 kB
KernelStack:        1376 kB
PageTables:         4184 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3476040 kB
Committed_AS:     120308 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      567860 kB
VmallocChunk:   34359165488 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       10112 kB
DirectMap2M:     1028096 kB

``````

klingon@enterprise:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
03:01.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)

```

---

### Post by dtfinch on 2011-02-10
After the message "soft lockup - CPU#0 stuck for 61s", does it say which module it was stuck in? Maybe it'll say in /var/log/syslog, followed by a stack trace.

---

### Post by Snowjoggs on 2011-02-10
I solved it!!

Google is my friend :D

One guy suggested this

```
apt-get install intel-microcode microcode.ctl
```

The upgraded microcode where applied after a quick reboot and now its dead stable, no locks no matter how much I/O traffic I hit it with :D

---

