---
title: "BU, then Wipe Win Partition from Inside Xubuntu, Restore Win7 in VM"
date: 2016-02-23
forum: Virtualisation
---

### Post by Rick St. George on 2016-02-23
Have Xubuntu v14.04 on Laptop with 4 GB Ram, 300 GB HD; Dual boot with Win7.

Would  like to wipe Win7 partition, install Virtual Box in Xubuntu, and  Restore Win7 into VBox. Have good experience with VBox on Desktop  running WinXP and trading software!  But it has 16 GB Ram, with 2GB  dedicated to VM. I'm thinking on my laptop, 2GB (1/2 memory) and 50 GB  HD space will work. 

Does this sound plausible? And if so, after Backup of Win7, how can I reclaim the full disk for use within Xubuntu? 

Thanks,
Rick

---

### Post by Bucky Ball on 2016-02-23
You'll need a licensed copy of a Win ISO or install media to install in Virtualbox. Not sure you can 'clone' a partition as a virtual machine. Not that I've heard of. (Although you could try cloning the partition and creating an ISO with Clonezilla then booting that as the virtual guest OS.)

Despite all this, you are looking at splitting that 4Gb between the host OS and the guest OS. Not sure that 2Gb each, particularly with a recent Ubuntu, is going to be adequate. I would say give it a shot. You'll soon find out.

---

### Post by Rick St. George on 2016-02-24
Thanks Bucky ... I would be using CloneZilla to do a Backup of Win7, then Restore it into the VirtualBox under Xubuntu! Does it have to be an ISO? And is there a function within Xubuntu that will format the old Win partition?

Thanks!

---

### Post by Rick St. George on 2016-02-24
By looking at another post, I looked at CPUINFO and found to instance of vt-x, so I don't think my BIOS / Laptop is capable. Here's the output ...

```

steve-o:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz
stepping    : 6
microcode    : 0x60c
cpu MHz        : 800.000
cache size    : 6144 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips    : 5053.74
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz
stepping    : 6
microcode    : 0x60c
cpu MHz        : 800.000
cache size    : 6144 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips    : 5053.74
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

Since the Win7 is a 64 bit version, I may just keep it as a DUAL Boot system, so Win7 will operate using the full RAM. Just hate monitoring MS from making my machine upgrade to Win10. Those people are NASTY. But I will toy with the idea of installing VBox and using an old WinXP so I can run my Trading Software that ONLY runs on a windows OS. That's what I did with my Desktop. 

Or better yet, Wipe the Win Partition, EXPORT the VM (w/WinXP) from the Desktop and IMPORT to the Laptop. That would work Right? Now How do I Format the Win Partition from inside of Xubuntu? And what to do about GRUB Dual Boot???

Thanks!
Rick

---

### Post by Rick St. George on 2016-02-24
In answer to my last question ... I found the following Link, So Case closed ... Thanks everyone!
For the benefit of anyone with this issue ... follow these steps.
[https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)

---

