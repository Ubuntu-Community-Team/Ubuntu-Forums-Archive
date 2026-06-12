---
title: "CPU Issue"
date: 2008-11-13
forum: Server Platforms
---

### Post by Vegan on 2008-11-13
My Linux box has a Pentium 3 CPU and it has 512 KB of L2 cache, but when I ran

dmesg

it showed only 256 KB which under reports the value.

[    0.010766] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.010778] CPU: L2 cache: 256K
[    0.010817] Checking 'hlt' instruction... OK.
[    0.050966] SMP alternatives: switching to UP code
[    0.070058] Freeing SMP alternatives: 11k freed
[    0.070073] ACPI: Core revision 20080609
[    0.072213] ACPI: Checking initramfs for custom DSDT
[    1.051872] ACPI: setting ELCR to 0200 (from 0e00)
[    1.060158] weird, boot CPU (#0) not listedby the BIOS.
[    1.060167] SMP motherboard not detected.
[    1.070000] SMP disabled
[    1.070000] Brought up 1 CPUs
[    1.070000] Total of 1 processors activated (1324.40 BogoMIPS).
[    1.070000] CPU0 attaching sched-domain:

---

### Post by CrucifiedEgo on 2008-11-13
what are the specs of your CPU?  is it a slot 1 or socket 370?  the s-code would be useful as well.  Also, have you tried something like cpu-z on windows to confirm?  There were pentium IIIs with both 256 and 512K of L2.

---

### Post by y@w on 2008-11-13
You can cat /proc/cpuinfo to get the exact model. Like CrucifiedEgo said, some came with 256K and others with 512K. If it is indeed supposed to be 512K that probably means there's something wrong with the cache. Was this a question, or are you just making a statement?

---

### Post by Vegan on 2008-11-13
The CPU is slot 1, and it is marked on the top as 667/133 512KB, this machine is a real IBM and came with Windows 2000 and NT 4 disks. I used FreeBSD on it until I adopted Ubuntu. Windows recognized the CPU properly. The machine has the web server on it, so not able to run Windows programs on it.

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 3
cpu MHz         : 662.205
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
bogomips        : 1324.41
clflush size    : 32
power management:

---

### Post by y@w on 2008-11-13
According to Wikipedia, the Coppermine only had 256K of L2 Cache. Not sure it was marked that way..
[http://en.wikipedia.org/wiki/Pentium_III#Coppermine_.280.18_.C2.B5m.29](http://en.wikipedia.org/wiki/Pentium_III#Coppermine_.280.18_.C2.B5m.29)

---

### Post by CrucifiedEgo on 2008-11-13
I have to imagine that's a counterfit CPU.  no coppermine 667 came with 512K as far as I can tell... unless it's an ES.  is it slot 1 or socket 370?  And, yeah, the S-code would still be awesome, something like SL3XN (667/133 coppermine s370) or SL3XL(667/133 coppermine slot 1)

---

### Post by y@w on 2008-11-13
I've actually heard before that the only difference between some of the older Pentium-class processors and the Celeron equivalents was that some of the L2 cache didn't work when tested so they slapped a Celeron sticker on. Perhaps something like that is happening?

---

### Post by Vegan on 2008-11-13
My PC is the IBM 300 GL 6563 and according to the CPU markings and the manual the CPU is a Pentium 3 with 512 KB L2 cache. This is not their cheap model, its their workstation/server model. :mad:

The 300 GL came with a range of configurations, I have one of the higher desktop models. I also have the manuals for the machine. IBM did not use Celerons in their better machines.

It runs fine, for example when I updated phpBB today it was faster than downloading the backups. The rate determining step was the LAN which is 100 (WRT54G).

The machine originally had 128 MB of RAM, I upped it to 768 MB now.

The CPU is a Pentium III running at 667 MHz with a FSB of 133.

I going to see if I can find a faster CPU for the box, bound to be something floating around a junk box somewhere.

---

