---
title: "System lockup starting chromium-browser [edit:soft lockup]"
date: 2018-04-21
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2018-04-21
I have this old dell server, probably around a 2010 model
I popped a old MSI Nvidia GT 210 in it
It has a pair of old 3Ghz dual core hyperthreaded processors 8 THREADS
not really a high end server now days but it does work for a power hungery desktop
is there a known reason chromium-browser would not work on this hardware?

When i say locks up i mean you see the gtk2 window border from chromium then the os locks up (REISUB is not usuable)

```
me@Precision-WorkStation-490:~$ cat /proc/meminfo 
MemTotal:        8165796 kB
MemFree:         6918556 kB
MemAvailable:    7394472 kB
Buffers:           46792 kB
Cached:           616304 kB
SwapCached:            0 kB
Active:           733244 kB
Inactive:         322892 kB
Active(anon):     364736 kB
Inactive(anon):    18204 kB
Active(file):     368508 kB
Inactive(file):   304688 kB
Unevictable:          48 kB
Mlocked:              48 kB
SwapTotal:       8392700 kB
SwapFree:        8392700 kB
Dirty:               164 kB
Writeback:             0 kB
AnonPages:        392972 kB
Mapped:           305620 kB
Shmem:             19284 kB
Slab:              84028 kB
SReclaimable:      48220 kB
SUnreclaim:        35808 kB
KernelStack:        6656 kB
PageTables:        24732 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    12475596 kB
Committed_AS:    2452436 kB
VmallocTotal:   34359738367 kB
VmallocUsed:           0 kB
VmallocChunk:          0 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
ShmemHugePages:        0 kB
ShmemPmdMapped:        0 kB
CmaTotal:              0 kB
CmaFree:               0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      172072 kB
DirectMap2M:     8214528 kB
me@Precision-WorkStation-490:~$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 6
model name    : Intel(R) Xeon(TM) CPU 3.00GHz
stepping    : 4
microcode    : 0x2
cpu MHz        : 2000.000
cache size    : 2048 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts nopl cpuid pni dtes64 monitor ds_cpl vmx est cid cx16 xtpr pdcm lahf_lm pti tpr_shadow
bugs        : cpu_meltdown spectre_v1 spectre_v2
bogomips    : 5985.06
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 15
model        : 6
model name    : Intel(R) Xeon(TM) CPU 3.00GHz
stepping    : 4
microcode    : 0x2
cpu MHz        : 2000.000
cache size    : 2048 KB
physical id    : 1
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 4
initial apicid    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts nopl cpuid pni dtes64 monitor ds_cpl vmx est cid cx16 xtpr pdcm lahf_lm pti tpr_shadow
bugs        : cpu_meltdown spectre_v1 spectre_v2
bogomips    : 5985.18
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 15
model        : 6
model name    : Intel(R) Xeon(TM) CPU 3.00GHz
stepping    : 4
microcode    : 0x2
cpu MHz        : 2000.000
cache size    : 2048 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts nopl cpuid pni dtes64 monitor ds_cpl vmx est cid cx16 xtpr pdcm lahf_lm pti tpr_shadow
bugs        : cpu_meltdown spectre_v1 spectre_v2
bogomips    : 5985.06
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 15
model        : 6
model name    : Intel(R) Xeon(TM) CPU 3.00GHz
stepping    : 4
microcode    : 0x2
cpu MHz        : 2000.000
cache size    : 2048 KB
physical id    : 1
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 6
initial apicid    : 6
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts nopl cpuid pni dtes64 monitor ds_cpl vmx est cid cx16 xtpr pdcm lahf_lm pti tpr_shadow
bugs        : cpu_meltdown spectre_v1 spectre_v2
bogomips    : 5985.18
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 4
vendor_id    : GenuineIntel
cpu family    : 15
model        : 6
model name    : Intel(R) Xeon(TM) CPU 3.00GHz
stepping    : 4
microcode    : 0x2
cpu MHz        : 2000.000
cache size    : 2048 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts nopl cpuid pni dtes64 monitor ds_cpl vmx est cid cx16 xtpr pdcm lahf_lm pti tpr_shadow
bugs        : cpu_meltdown spectre_v1 spectre_v2
bogomips    : 5985.06
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 5
vendor_id    : GenuineIntel
cpu family    : 15
model        : 6
model name    : Intel(R) Xeon(TM) CPU 3.00GHz
stepping    : 4
microcode    : 0x2
cpu MHz        : 2000.000
cache size    : 2048 KB
physical id    : 1
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 5
initial apicid    : 5
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts nopl cpuid pni dtes64 monitor ds_cpl vmx est cid cx16 xtpr pdcm lahf_lm pti tpr_shadow
bugs        : cpu_meltdown spectre_v1 spectre_v2
bogomips    : 5985.18
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 6
vendor_id    : GenuineIntel
cpu family    : 15
model        : 6
model name    : Intel(R) Xeon(TM) CPU 3.00GHz
stepping    : 4
microcode    : 0x2
cpu MHz        : 2000.000
cache size    : 2048 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts nopl cpuid pni dtes64 monitor ds_cpl vmx est cid cx16 xtpr pdcm lahf_lm pti tpr_shadow
bugs        : cpu_meltdown spectre_v1 spectre_v2
bogomips    : 5985.06
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 7
vendor_id    : GenuineIntel
cpu family    : 15
model        : 6
model name    : Intel(R) Xeon(TM) CPU 3.00GHz
stepping    : 4
microcode    : 0x2
cpu MHz        : 2000.000
cache size    : 2048 KB
physical id    : 1
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 7
initial apicid    : 7
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts nopl cpuid pni dtes64 monitor ds_cpl vmx est cid cx16 xtpr pdcm lahf_lm pti tpr_shadow
bugs        : cpu_meltdown spectre_v1 spectre_v2
bogomips    : 5985.18
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

me@Precision-WorkStation-490:~$ nvidia-smi -q

==============NVSMI LOG==============

Timestamp                           : Sat Apr 21 18:16:06 2018
Driver Version                      : 340.106

Attached GPUs                       : 1
GPU 0000:07:00.0
    Product Name                    : GeForce 210
    Product Brand                   : GeForce
    Display Mode                    : N/A
    Display Active                  : N/A
    Persistence Mode                : Disabled
    Accounting Mode                 : N/A
    Accounting Mode Buffer Size     : N/A
    Driver Model
        Current                     : N/A
        Pending                     : N/A
    Serial Number                   : N/A
    GPU UUID                        : GPU-8fb016a6-7ec5-3837-32e1-a8c27a668b01
    Minor Number                    : 0
    VBIOS Version                   : 70.18.49.00.00
    MultiGPU Board                  : N/A
    Board ID                        : N/A
    Inforom Version
        Image Version               : N/A
        OEM Object                  : N/A
        ECC Object                  : N/A
        Power Management Object     : N/A
    GPU Operation Mode
        Current                     : N/A
        Pending                     : N/A
    PCI
        Bus                         : 0x07
        Device                      : 0x00
        Domain                      : 0x0000
        Device Id                   : 0x0A6510DE
        Bus Id                      : 0000:07:00.0
        Sub System Id               : 0x80941462
        GPU Link Info
            PCIe Generation
                Max                 : N/A
                Current             : N/A
            Link Width
                Max                 : N/A
                Current             : N/A
        Bridge Chip
            Type                    : N/A
            Firmware                : N/A
    Fan Speed                       : N/A
    Performance State               : P8
    Clocks Throttle Reasons         : N/A
    FB Memory Usage
        Total                       : 1023 MiB
        Used                        : 93 MiB
        Free                        : 930 MiB
    BAR1 Memory Usage
        Total                       : N/A
        Used                        : N/A
        Free                        : N/A
    Compute Mode                    : Default
    Utilization
        Gpu                         : N/A
        Memory                      : N/A
        Encoder                     : N/A
        Decoder                     : N/A
    Ecc Mode
        Current                     : N/A
        Pending                     : N/A
    ECC Errors
        Volatile
            Single Bit            
                Device Memory       : N/A
                Register File       : N/A
                L1 Cache            : N/A
                L2 Cache            : N/A
                Texture Memory      : N/A
                Total               : N/A
            Double Bit            
                Device Memory       : N/A
                Register File       : N/A
                L1 Cache            : N/A
                L2 Cache            : N/A
                Texture Memory      : N/A
                Total               : N/A
        Aggregate
            Single Bit            
                Device Memory       : N/A
                Register File       : N/A
                L1 Cache            : N/A
                L2 Cache            : N/A
                Texture Memory      : N/A
                Total               : N/A
            Double Bit            
                Device Memory       : N/A
                Register File       : N/A
                L1 Cache            : N/A
                L2 Cache            : N/A
                Texture Memory      : N/A
                Total               : N/A
    Retired Pages
        Single Bit ECC              : N/A
        Double Bit ECC              : N/A
        Pending                     : N/A
    Temperature
        GPU Current Temp            : 41 C
        GPU Shutdown Temp           : N/A
        GPU Slowdown Temp           : N/A
    Power Readings
        Power Management            : N/A
        Power Draw                  : N/A
        Power Limit                 : N/A
        Default Power Limit         : N/A
        Enforced Power Limit        : N/A
        Min Power Limit             : N/A
        Max Power Limit             : N/A
    Clocks
        Graphics                    : N/A
        SM                          : N/A
        Memory                      : N/A
    Applications Clocks
        Graphics                    : N/A
        Memory                      : N/A
    Default Applications Clocks
        Graphics                    : N/A
        Memory                      : N/A
    Max Clocks
        Graphics                    : N/A
        SM                          : N/A
        Memory                      : N/A
    Clock Policy
        Auto Boost                  : N/A
        Auto Boost Default          : N/A
    Compute Processes               : N/A

me@Precision-WorkStation-490:~$ 
```
edit: it opened without the propitary nvidia driver
edit: log files post #3

---

### Post by mc4man on 2018-04-21
If you are using the snap version of chromium then the stable snapd core version may still have an issue if it hasn't been upgraded.
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1760444](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1760444)

---

### Post by pqwoerituytrueiwoq on 2018-04-21
***This is a clean install

Managed to get it to happen using firefox
keyboard is useless, but holy crap SSH is working, for some reason i can not kill pid 1330
```
me@Precision-WorkStation-490:~$ kill 1330
me@Precision-WorkStation-490:~$ kill -9 1330
me@Precision-WorkStation-490:~$ top

top - 19:18:17 up 24 min,  2 users,  load average: 6.04, 4.97, 2.97
Tasks: 180 total,   6 running, 110 sleeping,   0 stopped,   0 zombie
%Cpu(s): 10.6 us,  6.2 sy,  0.0 ni, 81.4 id,  1.8 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  8165796 total,  6881788 free,   575588 used,   708420 buff/cache
KiB Swap:  8392700 total,  8392700 free,        0 used.  7494508 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                            
 1330 me        20   0 2404616 503264 171768 R 100.0  6.2  16:40.39 Web Content                                                        
 2121 me        20   0   51648   3936   3300 R  16.7  0.0   0:00.05 top                                                                
   78 root      20   0       0      0      0 I   5.6  0.0   0:19.08 kworker/5:1                                                        
   79 root      20   0       0      0      0 I   5.6  0.0   0:20.66 kworker/6:1                                                        
    1 root      20   0  225260   8948   6632 S   0.0  0.1   0:03.44 systemd                                                            
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd                                                           
    4 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/0:0H                                                       
    5 root      20   0       0      0      0 I   0.0  0.0   0:00.37 kworker/u16:0                                                      
    6 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 mm_percpu_wq                                                       
    7 root      20   0       0      0      0 S   0.0  0.0   0:00.09 ksoftirqd/0                                                        
    8 root      20   0       0      0      0 I   0.0  0.0   0:05.20 rcu_sched                                                          
    9 root      20   0       0      0      0 I   0.0  0.0   0:00.00 rcu_bh                                                             
   10 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 migration/0                                                        
   11 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 watchdog/0                                                         
   12 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/0                                                            
   13 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/1                                                            
   14 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/1                                                         
   15 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 migration/1  
```

edit: looking at dmesg (line 920 and up), is my cpu unstable, maybe the psu is failing or a cap is going bad

---

