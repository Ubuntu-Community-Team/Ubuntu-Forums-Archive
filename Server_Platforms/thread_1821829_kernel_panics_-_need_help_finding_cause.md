---
title: "kernel panics - need help finding cause"
date: 2011-08-09
forum: Server Platforms
---

### Post by markolonius on 2011-08-09
Hello! I keep getting kernel panics on my Ubuntu Server I have setup, but can't figure out why they happen.  I need help figuring out what causes the panic before I can find a way to fix it.  Attached you will find a screenshot of the stack trace after the kernel panic, also dmesg, dmesg.0, and kern.log.

some specs:

```
$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: CentaurHauls
cpu family	: 6
model		: 10
model name	: VIA Esther processor 1500MHz
stepping	: 9
cpu MHz		: 1496.127
cache size	: 128 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge cmov pat clflush acpi mmx fxsr sse sse2 tm nx up pni rng rng_en ace ace_en ace2 ace2_en phe phe_en pmm pmm_en
bogomips	: 2992.25
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 32 bits virtual
power management:

```

```
$ cat /proc/meminfo 
MemTotal:        1994552 kB
MemFree:         1855336 kB
Buffers:           27500 kB
Cached:            72232 kB
SwapCached:            0 kB
Active:            50516 kB
Inactive:          65748 kB
Active(anon):      17140 kB
Inactive(anon):     2184 kB
Active(file):      33376 kB
Inactive(file):    63564 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       1117192 kB
HighFree:        1025432 kB
LowTotal:         877360 kB
LowFree:          829904 kB
SwapTotal:       2027516 kB
SwapFree:        2027516 kB
Dirty:                40 kB
Writeback:             0 kB
AnonPages:         16544 kB
Mapped:            13772 kB
Shmem:              2800 kB
Slab:              13980 kB
SReclaimable:       8980 kB
SUnreclaim:         5000 kB
KernelStack:         720 kB
PageTables:         1016 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3024792 kB
Committed_AS:     120880 kB
VmallocTotal:     122880 kB
VmallocUsed:        5176 kB
VmallocChunk:     115004 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       12280 kB
DirectMap2M:      901120 kB

```

I thought it had something to do with acpi so i turned it off in the bios and also have this in my /etc/default/grub file (this was added automatically from installation)

GRUB_CMDLINE_LINUX="acpi=off noapic nolapic"

But I still get these kernel panics.  I also thought it had something to do with my hard drives but I've done a scan and no bad blocks anywhere.  If someone could tell me instructions on how to scan properly with e2fsck would be awesome.  Otherwise I used manufacture software.

Any other ideas on how to figure what causes these panics from the logs or screenshot?  If there is any other info you need to help just ask!

Thanks.  The help would be really appreciated.

---

