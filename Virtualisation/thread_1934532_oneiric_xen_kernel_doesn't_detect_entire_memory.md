---
title: "oneiric xen kernel doesn't detect entire memory"
date: 2012-03-02
forum: Virtualisation
---

### Post by mikemowgli on 2012-03-02
Dear forum,

I've got a Ubuntu Oneiric 11.10 x86_64 laptop. I installed the Xen hypervisor on it. Then I boot on the adapted kernel from Grub.

When booting on the regular kernel, I can see, and use, the whole physical memory (2GB). But when I boot on Xen kernel, mx box just sees 860MB, or sometimes 837MB.

Please find below some useful outputs. As you can see, some commands (xm dmesg, xm info) return the correct amount of memory (2GB) while others return the truncated amount (free, /proc/meminfo, lshw). My laptop is a Dell Vostro 1700.

Any help appreciated, as I'm currently computing the aerodynamics of my computer for a flight starting from the second floor window :)

```
mb@lt-mb:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           860        838         22          0          4        119
-/+ buffers/cache:        713        146
Swap:         2044        611       1433
```




```
mb@lt-mb:~$ sudo xm dmesg
(XEN) Xen version 4.1.1 (Ubuntu 4.1.1-2ubuntu4.1) (zulcss@ubuntu.com) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) Tue Oct 11 07:31:13 UTC 2011
(XEN) Bootloader: GRUB 1.99-12ubuntu5
(XEN) Command line: placeholder
(XEN) Video information:
(XEN)  VGA is text mode 80x25, font 8x16
(XEN)  VBE/DDC methods: none; EDID transfer time: 0 seconds
(XEN)  EDID info not retrieved because no DDC retrieval method detected
(XEN) Disc information:
(XEN)  Found 1 MBR signatures
(XEN)  Found 1 EDD information structures
(XEN) Xen-e820 RAM map:
(XEN)  0000000000000000 - 000000000009f000 (usable)
(XEN)  000000000009f000 - 00000000000a0000 (reserved)
(XEN)  0000000000100000 - 000000007fe6d800 (usable)
(XEN)  000000007fe6d800 - 0000000080000000 (reserved)
(XEN)  00000000f4000000 - 00000000f8000000 (reserved)
(XEN)  00000000fec00000 - 00000000fec10000 (reserved)
(XEN)  00000000fed18000 - 00000000fed1c000 (reserved)
(XEN)  00000000fed20000 - 00000000fed90000 (reserved)
(XEN)  00000000feda0000 - 00000000feda6000 (reserved)
(XEN)  00000000fee00000 - 00000000fee10000 (reserved)
(XEN)  00000000fff00000 - 0000000100000000 (reserved)
(XEN) System RAM: 2046MB (2095152kB)
(XEN) ACPI: RSDP 000FBBF0, 0024 (r2 DELL  )
(XEN) ACPI: XSDT 7FE6F200, 005C (r1 DELL    M08     27D8010E ASL        61)
(XEN) ACPI: FACP 7FE6F09C, 00F4 (r4 DELL    M08     27D8010E ASL        61)
(XEN) ACPI: DSDT 7FE6F800, 565E (r2 INT430 SYSFexxx     1001 INTL 20050624)
(XEN) ACPI: FACS 7FE7E000, 0040
(XEN) ACPI: HPET 7FE6F300, 0038 (r1 DELL    M08            1 ASL        61)
(XEN) ACPI: APIC 7FE6F400, 0068 (r1 DELL    M08     27D8010E ASL        47)
(XEN) ACPI: MCFG 7FE6F3C0, 003E (r16 DELL    M08     27D8010E ASL        61)
(XEN) ACPI: SLIC 7FE6F49C, 0176 (r1 DELL    M08     27D8010E ASL        61)
(XEN) ACPI: BOOT 7FE6EFC0, 0028 (r1 DELL    M08     27D8010E ASL        61)
(XEN) ACPI: SSDT 7FE6D9BC, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
(XEN) Domain heap initialised
(XEN) Processor #0 6:15 APIC version 20
(XEN) Processor #1 6:15 APIC version 20
(XEN) IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
(XEN) Enabling APIC mode:  Flat.  Using 1 I/O APICs
(XEN) Table is not found!
(XEN) Using scheduler: SMP Credit Scheduler (credit)
(XEN) Detected 2193.996 MHz processor.
(XEN) Initing memory sharing.
(XEN) I/O virtualisation disabled
(XEN) ENABLING IO-APIC IRQs
(XEN)  -> Using new ACK method
(XEN) Platform timer is 14.318MHz HPET
(XEN) Allocated console ring of 16 KiB.
(XEN) VMX: Supported advanced features:
(XEN)  - APIC MMIO access virtualisation
(XEN)  - APIC TPR shadow
(XEN)  - Virtual NMI
(XEN)  - MSR direct-access bitmap
(XEN) HVM: ASIDs disabled.
(XEN) HVM: VMX enabled
(XEN) Brought up 2 CPUs
(XEN) *** LOADING DOMAIN 0 ***
(XEN)  Xen  kernel: 64-bit, lsb, compat32
(XEN)  Dom0 kernel: 64-bit, PAE, lsb, paddr 0x1000000 -> 0x1e42000
(XEN) PHYSICAL MEMORY ARRANGEMENT:
(XEN)  Dom0 alloc.:   0000000074000000->0000000078000000 (458958 pages to be allocated)
(XEN)  Init. ramdisk: 000000007d3f0000->000000007f9ff800
(XEN) VIRTUAL MEMORY ARRANGEMENT:
(XEN)  Loaded kernel: ffffffff81000000->ffffffff81e42000
(XEN)  Init. ramdisk: ffffffff81e42000->ffffffff84451800
(XEN)  Phys-Mach map: ffffffff84452000->ffffffff848056f0
(XEN)  Start info:    ffffffff84806000->ffffffff848064b4
(XEN)  Page tables:   ffffffff84807000->ffffffff84830000
(XEN)  Boot stack:    ffffffff84830000->ffffffff84831000
(XEN)  TOTAL:         ffffffff80000000->ffffffff84c00000
(XEN)  ENTRY ADDRESS: ffffffff81ad0200
(XEN) Dom0 has maximum 2 VCPUs
(XEN) Scrubbing Free RAM: .done.
(XEN) Xen trace buffers: disabled
(XEN) Std. Loglevel: Errors and warnings
(XEN) Guest Loglevel: Nothing (Rate-limited: Errors and warnings)
(XEN) Xen is relinquishing VGA console.
(XEN) *** Serial input -> DOM0 (type 'CTRL-a' three times to switch input to Xen)
(XEN) Freed 224kB init memory.
```

```
mb@lt-mb:~$ sudo xm info
host                   : lt-mb
release                : 3.0.0-14-generic
version                : #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011
machine                : x86_64
nr_cpus                : 2
nr_nodes               : 1
cores_per_socket       : 2
threads_per_core       : 1
cpu_mhz                : 2193
hw_caps                : bfebfbff:20100800:00000000:00000940:0000e3bd:00000000:00000001:00000000
virt_caps              : hvm
total_memory           : 2046
free_memory            : 1047
free_cpus              : 0
xen_major              : 4
xen_minor              : 1
xen_extra              : .1
xen_caps               : xen-3.0-x86_64 xen-3.0-x86_32p hvm-3.0-x86_32 hvm-3.0-x86_32p hvm-3.0-x86_64 
xen_scheduler          : credit
xen_pagesize           : 4096
platform_params        : virt_start=0xffff800000000000
xen_changeset          : unavailable
xen_commandline        : placeholder
cc_compiler            : gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 
cc_compile_by          : zulcss
cc_compile_domain      : ubuntu.com
cc_compile_date        : Tue Oct 11 07:31:13 UTC 2011
xend_config_format     : 4
```

Here's the entry of grub I'm booting on:

```
submenu "Xen 4.1-amd64" {
menuentry 'Ubuntu GNU/Linux, avec Xen 4.1-amd64 et Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os --class xen {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set=root d63ef959-4f10-4350-89ad-18d0e5fa764b
        echo    'Chargement de Xen 4.1-amd64 ...'
        multiboot       /boot/xen-4.1-amd64.gz placeholder
        echo    'Chargement de Linux 3.0.0-14-generic ...'
        module  /boot/vmlinuz-3.0.0-14-generic placeholder root=UUID=d63ef959-4f10-4350-89ad-18d0e5fa764b ro  quiet splash
        echo    'Chargement du disque mémoire initial ...'
        module  /boot/initrd.img-3.0.0-14-generic
```

```
mb@lt-mb:~$ cat /proc/meminfo 
MemTotal:         881056 kB
MemFree:           35060 kB
Buffers:            9152 kB
Cached:           111324 kB
SwapCached:       123908 kB
Active:           450840 kB
Inactive:         201812 kB
Active(anon):     396472 kB
Inactive(anon):   139924 kB
Active(file):      54368 kB
Inactive(file):    61888 kB
Unevictable:        2916 kB
Mlocked:            2916 kB
SwapTotal:       2094076 kB
SwapFree:        1468272 kB
Dirty:                80 kB
Writeback:             0 kB
AnonPages:        461060 kB
Mapped:            48528 kB
Shmem:              2276 kB
Slab:              69704 kB
SReclaimable:      42424 kB
SUnreclaim:        27280 kB
KernelStack:        4368 kB
PageTables:        31832 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2534604 kB
Committed_AS:    3826972 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      138916 kB
VmallocChunk:   34359592928 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:     2095540 kB
DirectMap2M:           0 kB
```

```
mb@lt-mb:~$ lshw
[...]
     *-memory
          description: System memory
          physical id: 0
          size: 860MiB
[...]
```

```
mb@lt-mb:~$ uname -a
Linux lt-mb 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by mikemowgli on 2012-03-02
!!!SKIP THIS MESSAGE, PROBLEM STILL NOT SOLVED!!!

Ok, this has been solved using the "dom0_mem=2G" option in the kernel grub line.

I had to add this line into /etc/default/gurb:
GRUB_CMDLINE_XEN_DEFAULT="dom0_mem=2G"

and then run update-grub

Now the system detects the 2GB of mem.

Dear people from the future, I hope this will be helpful for you, as I found very few references to this wierd behavior.

cheers,

mike

---

### Post by mikemowgli on 2012-03-02
Sorry, this wasn't solved at all. I thought it was solved because the kernel crashed when I passed the "dom0_mem=2G" option. So my laptop rebooted automatically and used the default grub entry which is the ordinary stock kernel, which detects all my memory


So the problem is still there... any clue, people?

---

