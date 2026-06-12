---
title: "Kernel 3.8.0-10 won't boot"
date: 2013-03-05
forum: Ubuntu Development Version
---

### Post by chenriques on 2013-03-05
I've just update RR to kernel 3.8.0-10 but for the first time my laptop can't boot with this kernel.
Went to Advance Options and booted with 3.8.0-9.

---

### Post by ventrical on 2013-03-05
Works ok here but I haven't tried on the laptop yet.

---

### Post by craig10x on 2013-03-05
After i got the update for that kernel today, when i re-booted into 13.04 a window came up that i was in low graphics mode...i shut down and booted into 12.10 instead (i am dual booting) and i got the normal screen but it mentioned about some errors...i had it fix the errors and booted into 12.10 fine, then re-started and booted into 13.04 and it came up perfect again!  (good thing i had the dual boot...i wasn't sure what to do with the options given me on that low graphics mode window)....

So, it must have done something to the grub bootloader that needed straightening out...I have a recent toshiba laptop, by the way...

---

### Post by chenriques on 2013-03-05
I have an ASUS N56VZ laptop, and this is the first 3.8 kernel that I have problems with :/

---

### Post by jinjorge on 2013-03-05
seeing the same thing on xubuntu. Was able to boot with 3.8.0.9 but not 3.8.0.10

---

### Post by pqwoerituytrueiwoq on 2013-03-05
it boots here, still having my backlight issue though
using my laptop
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1138168](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1138168)

---

### Post by cole.mickens on 2013-03-05
My MBA 2012 does not boot with the -10 kernel as well. I'm checking my desktop in the next half hour.

edit: Weird.... with the -10 kernel, dosfsck tries to run. If I skip it, it's fine. But the -9 kernel doesn't try to run dosfsck.

A bit weird...

---

### Post by raccoonone on 2013-03-05
Same problem here, with a MBP Retina. 3.8.0-10 won't boot at all, 3.8.0-9 still boots although the graphics driver is now messed up :/ (nvidia proprietary won't load)

---

### Post by cole.mickens on 2013-03-05
3.8.0-10 will not boot on my desktop at all. Not with nvidia, not with nouvareu. Is it possibly getting hung up on my BTRFS array?

---

### Post by raccoonone on 2013-03-05
> **cole.mickens said:**
> 3.8.0-10 will not boot on my desktop at all. Not with nvidia, not with nouvareu. Is it possibly getting hung up on my BTRFS array?

I'm not using btrfs, just standard Ubuntu 13.04 install

---

### Post by Harry33 on 2013-03-06
Have you tried the latest kernel linux (3.8.0-11.20) in RR, which will soon hit the repos.
You can find it manually from here:

[https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-11.20](https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-11.20)

---

### Post by PJs Ronin on 2013-03-06
I've got 3.8.0-10 (64 bit) up and running in a VM (on my desktop) no probs... in fact the Launcher transparency is now finally working too.

---

### Post by cole.mickens on 2013-03-06
Yup, my desktop still doesn't boot with -11.

Last thing I get is:

```

Begin: Running /scripts/init-bottom ... done.
[] EXT4-fs (sda2) remounted. Opts: errors=remount-ro
[] device fsid .... devid 2 transid 241333 /dev/sdc
[] btrfs: disk space caching is enabled

```

Hitting CTRL+ALT+DEL causes
```

alsa-store main process terminated with status 19.
plymouth-upstart-bridge main process termined with status 1

```

er... and it sits here for an inordinate amount of time... like, time enough for me to slowly type this message with some accuracy. and then a bunch of stuff happens too fast to see and it reboots [with a caveat, see below]

Is ALSA the source of problems? For now, back to -9. Are there bugreports for this issue??



Also... Grub has a VERY irritating problem. I have "quiet nosplash" but when the boot hangs like this, when it restarts and I choose "Ubuntu" again, I can't see squat. Nothing. Just a purple screen. What a pain. Is this a special Nvidia problem, that's my guess. Gotta love propreitary software, the biggest impediment to a much more seamless linux experience. (Or if I manually choose -9 without powering off my box, I get "Loading Linux 3.8.9-90-generic... \n Loading intial ramdisk... " and the next thing I see is Plasma KDE taking forever to load because of some PulseAudio issue (and KMix is annoying) both of which should be fixed soon with 4.10.1.

---

### Post by dino99 on 2013-03-06
that issue is probably related to btrfs; why have you made that choice as ext4 tests are better ?

you'd remove "quiet splash" from the grub:

```
sudo gedit /etc/default/grub
```

then run:

```
sudo update-grub
```

and you seems to test lot of non genuine ubuntu default choice, like vanilla kernel. So you might understand its at your own risk and be ready to fix the possible issue(s) by digging errors inside the logs and then using dbg to narrow down the problem before reporting it on Launchpad.

---

### Post by cole.mickens on 2013-03-06
Huh?

I know how to remove "quiet nosplash", I put them there to debug the boot problems, and because it looks dumb anyway because of nvidia's mucking with the tty resolution.

Also, I don't have a problem with Grub either, it's that the normal output isn't written to the screen after a reboot unless the power is manually cycled. I'm pretty sure that has to do with initialization stuff that nvidia does. For example, I was having a specific issue switching between nvidia and nouvareu because, for me, I had to manually power off to switch. I was told that this was expected, that nvidia has an amount of voodoo in it.

Also, that issue is not present on my Intel laptop which is exhibiting differnet boot problems (it says it's doing a dos-fsck, but it's not... it just sits there forever and the only FAT I have is the EFI partition... another bug related to EFI on Macs, possibly.

Finally, I chose BTRFS because it makes sense for me. I have a 64GB SSD used for my OS, apps, and Code (to compile fast). The rest of my home dir, movies, pictures, and music reside on a BTRFS array configured as RAID10 (you can change RAID levels at any time and BTRFS will rebalance them for you). So, I had 12TB and now I have 6TB of multiply redundant storage for my home dir and media. My home dir is also backed up and I have an old copy of my media I can restore from in case of catastrophic failure. Let me know if you have any questions about it :)

Also, I've been using BTRFS all through out 12.10 and 3.8.0-{1-9}. Also, other people that don't have BTRFS are experiencing the exact same issue. I'm not convinced either way, but BTRFS isn't that automatically cause of alarm in my mind.

PPPS, my read and writes are noticably fast in this configuration too, for obvious reasons.

---

### Post by jinjorge on 2013-03-06
3.8.0.11 is not booting on my computer either.  Does anyone know if a bug has been filed for this issue on launchpad?

also, what information would should we share that will help get to the bottom of this issue?

Thanks.

---

### Post by anca-emanuel on 2013-03-06
^ Please tell us what PC do you have, (and lspci and lsusb)

---

### Post by jinjorge on 2013-03-06
> **anca-emanuel said:**
> ^ Please tell us what PC do you have, (and lspci and lsusb)

Here you go.

cat /proc/cpuinfo
```

$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 20
model        : 1
model name    : AMD E-350 Processor
stepping    : 0
microcode    : 0x5000028
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat hw_pstate npt lbrv svm_lock nrip_save pausefilter
bogomips    : 3200.01
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate


processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 20
model        : 1
model name    : AMD E-350 Processor
stepping    : 0
microcode    : 0x5000028
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat hw_pstate npt lbrv svm_lock nrip_save pausefilter
bogomips    : 3200.01
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate



```

lspci

```
$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:15.2 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 2)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller



```

lsusb

```
$ lsusb
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 004 Device 003: ID 413c:1002 Dell Computer Corp. Keyboard Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 004: ID 413c:2002 Dell Computer Corp. SK-8125 Keyboard



```

---

### Post by John_Swing on 2013-03-06
Same here, 3.8.0-10 and 3.8.0-11 won't boot on my computer while everything worked fine from 3.8-rc3 until 3.8.0-9 included.

---

### Post by chenxiaolong on 2013-03-06
Same problem here. I extracted the initramfs for 3.8.0-9-generic and 3.8.0-10-generic and "diff -Nru" 'ed them. There's no difference other than the newer kernel modules, so this is obviously a kernel issue.

I have a Lenovo W520 booting from an ext4 partition.

```
~ [ cat /proc/cmdline                                                  ] 6:38 PM
BOOT_IMAGE=/boot/vmlinuz-3.8.0-9-generic root=UUID=64f4b8ed-fc14-4cb3-9b91-ae97e235a881 ro noapic crashkernel=384M-2G:64M,2G-:128M quiet splash
```

```
~ [ cat /proc/cpuinfo                                                  ] 6:39 PM
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 42
model name      : Intel(R) Core(TM) i7-2720QM CPU @ 2.20GHz
stepping        : 7
microcode       : 0x28
cpu MHz         : 800.000
cache size      : 6144 KB
physical id     : 0
siblings        : 8
core id         : 0
cpu cores       : 4
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips        : 4385.66
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 42
model name      : Intel(R) Core(TM) i7-2720QM CPU @ 2.20GHz
stepping        : 7
microcode       : 0x28
cpu MHz         : 800.000
cache size      : 6144 KB
physical id     : 0
siblings        : 8
core id         : 0
cpu cores       : 4
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips        : 4385.66
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 6
model           : 42
model name      : Intel(R) Core(TM) i7-2720QM CPU @ 2.20GHz
stepping        : 7
microcode       : 0x28
cpu MHz         : 800.000
cache size      : 6144 KB
physical id     : 0
siblings        : 8
core id         : 1
cpu cores       : 4
apicid          : 2
initial apicid  : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips        : 4385.66
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 6
model           : 42
model name      : Intel(R) Core(TM) i7-2720QM CPU @ 2.20GHz
stepping        : 7
microcode       : 0x28
cpu MHz         : 800.000
cache size      : 6144 KB
physical id     : 0
siblings        : 8
core id         : 1
cpu cores       : 4
apicid          : 3
initial apicid  : 3
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips        : 4385.66
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 4
vendor_id       : GenuineIntel
cpu family      : 6
model           : 42
model name      : Intel(R) Core(TM) i7-2720QM CPU @ 2.20GHz
stepping        : 7
microcode       : 0x28
cpu MHz         : 800.000
cache size      : 6144 KB
physical id     : 0
siblings        : 8
core id         : 2
cpu cores       : 4
apicid          : 4
initial apicid  : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips        : 4385.66
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 5
vendor_id       : GenuineIntel
cpu family      : 6
model           : 42
model name      : Intel(R) Core(TM) i7-2720QM CPU @ 2.20GHz
stepping        : 7
microcode       : 0x28
cpu MHz         : 800.000
cache size      : 6144 KB
physical id     : 0
siblings        : 8
core id         : 2
cpu cores       : 4
apicid          : 5
initial apicid  : 5
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips        : 4385.66
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 6
vendor_id       : GenuineIntel
cpu family      : 6
model           : 42
model name      : Intel(R) Core(TM) i7-2720QM CPU @ 2.20GHz
stepping        : 7
microcode       : 0x28
cpu MHz         : 800.000
cache size      : 6144 KB
physical id     : 0
siblings        : 8
core id         : 3
cpu cores       : 4
apicid          : 6
initial apicid  : 6
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips        : 4385.66
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 7
vendor_id       : GenuineIntel
cpu family      : 6
model           : 42
model name      : Intel(R) Core(TM) i7-2720QM CPU @ 2.20GHz
stepping        : 7
microcode       : 0x28
cpu MHz         : 800.000
cache size      : 6144 KB
physical id     : 0
siblings        : 8
core id         : 3
cpu cores       : 4
apicid          : 7
initial apicid  : 7
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips        : 4385.66
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:
```

```
~ [ lspci                                                              ] 6:40 PM
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
0d:00.0 System peripheral: Ricoh Co Ltd PCIe SDXC/MMC Host Controller (rev 08)
0e:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
```

```
~ [ lsusb                                                              ] 6:40 PM
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 004: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 005: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 001 Device 006: ID 04f2:b217 Chicony Electronics Co., Ltd Lenovo Integrated Camera (0.3MP)
Bus 002 Device 003: ID 17ef:1003 Lenovo Integrated Smart Card Reader
```

By the way, I can't see the kernel messages, even if I remove "quiet splash" from the command line because of some UEFI framebuffer issue.

---

### Post by raccoonone on 2013-03-06
One clue here. I'm using EFI on my retina macbook, and notice some EFI related errors in recovery mode. Is anyone else using EFI?

---

### Post by alphacrucis2 on 2013-03-06
No problems here with 3.8.0.10 or 11. Hardware is Lenovo T520 with Optimus disabled. It has BIOS not UEFI and I'm using one of the proprietary Nvidia drivers. Sounds like the problem might be specific to certain hardware or maybe UEFI boot is the problem.

---

### Post by chenxiaolong on 2013-03-06
Yeah, I'm booting via UEFI. With the W520 being identical with the T520 (except for the graphics card), UEFI could very well be the problem.

EDIT: Looking at Ubuntu's git kernel commit log, the only major change that could potentially affect the boot process would be the rebasing to version 3.8.2. I'm going to compile a vanilla version of kernel 3.8.2 and see if that boots.

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-raring.git;a=log](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-raring.git;a=log)

---

### Post by cole.mickens on 2013-03-06
EFI boot on MBA2012 === hang on msdos fsck (which is dumb, the only FAT I have is the EFI partition

UEFI boot on my desktop === hang with alsa error-exiting and taking plymouth with it (see the error messages above).

I sure hope base linux-3.8.2 didn't regress this much... kind of a big deal for it neither of my ubuntu machines to boot...

---

### Post by raccoonone on 2013-03-07
Did anyone file a bug on this yet? Couldn't find a report when I looked just now

---

### Post by chenxiaolong on 2013-03-07
Just finished compiling vanilla 3.8.2 - same problem. It looks like this is an upstream kernel issue :(

---

### Post by raccoonone on 2013-03-07
> **chenxiaolong said:**
> Just finished compiling vanilla 3.8.2 - same problem. It looks like this is an upstream kernel issue :(

:( Did you file a bug report?

---

### Post by chenxiaolong on 2013-03-07
> **raccoonone said:**
> :( Did you file a bug report?

Not yet. I have to go to sleep now (1 AM here :P). Tomorrow, I'll compile 3.8.1 to see if the issue still exists. If 3.8.1 is fine, I'll do a git bisect until I find the exact commit that broke everything.

EDIT: Vanilla 3.8.1 works fine. I'm going to do a git bisect. This will take a while...

EDIT2: Narrowed the range a bit: 364 commits left to check (about 9 bisects)

---

### Post by cole.mickens on 2013-03-07
Thanks for taking the time to do the bisect!

---

### Post by Harry33 on 2013-03-08
The newest kernel in RR repos is now 3.8.0-12.21 (based on 3.8.2).
This will soon hit the repos.

Here:
[https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-12.21](https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-12.21)

---

### Post by chenxiaolong on 2013-03-08
> **cole.mickens said:**
> Thanks for taking the time to do the bisect!

No problem :)

The bisect revealed the two git commits that broke the boot process (same as what Seth found here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1146988](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1146988)).

I haven't tested it yet, but 3.8.0-12.21 reverts those two patches, so that update should get things working again :)

EDIT: Actually, only one commit is broken: da27a24383b2b10bf6ebd0db29b325548aafecb4

If anyone is building the kernel from git, just run

```
git checkout -b efi-reverts
git revert da27a24383b2b10bf6ebd0db29b325548aafecb4
```

or from a tarball

```
wget -q -O - 'https://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/patch/?id=da27a24383b2b10bf6ebd0db29b325548aafecb4' | patch -p1 -R
```

---

