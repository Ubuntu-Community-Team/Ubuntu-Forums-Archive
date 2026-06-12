---
title: "KVM fails to boot Windows 7 and Vista guests"
date: 2010-01-07
forum: Virtualisation
---

### Post by SATA on 2010-01-07
KVM Fails to boot Windows 7 and and Windows Vista, after installation has completed, garbage is displayed on screen (See images 06 and 07).

Windows XP installs and works fine

I have included images 03, 04 and 05 to show that installation goes fine, Just first boot (and all others after it) fail.

When the garbage in figures 06 and 07 are on screen, CPU usage skyrockets

When win vista boots, kvm is invoked with the following arguments:
```

ryan@kgb:~/Desktop$ ps ax | grep vista
 9550 ?        Rl     0:10 /usr/bin/kvm -cpu core2duo -S -M pc-0.11 -m 1024 -smp 1 -name winvista -uuid 0581038a-73fd-96cb-7206-5644a5f5d3ba -monitor unix:/var/run/libvirt/qemu/winvista.monitor,server,nowait -localtime -boot d -drive file=/var/lib/libvirt/images/winvista.img,if=ide,index=0 -drive file=/dev/sr0,if=ide,media=cdrom,index=2 -net nic,macaddr=54:52:00:1f:45:22,vlan=0,name=nic.0 -net tap,fd=18,vlan=0,name=tap.0 -serial pty -parallel none -usb -usbdevice tablet -vnc 0.0.0.0:1,password -k en-us -vga cirrus -soundhw es1370

```This is the CPU my system is running:
```

ryan@kgb:~/Desktop$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     E8300  @ 2.83GHz
stepping        : 6
cpu MHz         : 2826.051
cache size      : 6144 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips        : 5652.10
clflush size    : 64
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     E8300  @ 2.83GHz
stepping        : 6
cpu MHz         : 2826.051
cache size      : 6144 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips        : 5652.41
clflush size    : 64
power management:

```
KVM Version:
```

ryan@kgb:~/Desktop$ dpkg -l | grep kvm
ii  kvm                                   1:84+dfsg-0ubuntu16+0.11.0+0ubuntu6.3   dummy transitional pacakge for qemu-kvm
ii  kvm-pxe                               5.4.3+dfsg-0.2ubuntu2                   PXE ROM's for KVM
ii  qemu-kvm                              0.11.0-0ubuntu6.3                       Full virtualization on i386 and amd64 hardware
ii  qemu-kvm-extras                       0.11.0-0ubuntu6.3                       fast processor emulator binaries for non-x86 architectures

```

---

### Post by SATA on 2010-01-10
Kernel:
```

ryan@kgb:~$ uname -a
Linux kgb 2.6.31-17-generic-pae #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 i686 GNU/Linux

```KVM:
```

QEMU PC emulator version 0.11.0 (qemu-kvm-0.11.0), Copyright (c) 2003-2008 Fabrice Bellard
```

---

### Post by tuxic73 on 2010-02-14
> **SATA said:**
> Kernel:
```

ryan@kgb:~$ uname -a
Linux kgb 2.6.31-17-generic-pae #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 i686 GNU/Linux

```KVM:
```

QEMU PC emulator version 0.11.0 (qemu-kvm-0.11.0), Copyright (c) 2003-2008 Fabrice Bellard
```

I'm having the exact same problem. No solution yet, tried everything. Now waiting for an update o kvm, maybe solves the problem.

---

### Post by SATA on 2010-02-14
Its got to be KVM,

Probably not the kernel as it has done it throughout all the updates.

I tried installing KVM on Jaunty to see if it would work in the meantime with the exact same results.

---

### Post by tuxic73 on 2010-02-14
I tried Lucid beta (alternative install cd) in the meantime, everything works with that. I tried windows 7 and windows 2008 server. Both boot fine, Very strange. I couldn't figure out the version of KVM shipped with Lucid, but it seems a KVM problem indeed.

---

### Post by tuxic73 on 2010-02-14
small update: startging from the console with the -no-kvm switch causes the boot process to go further, except windows crashes and reboots. Just for you to try as well

kvm -m 1024 /dev/RAID/win2008 -no-kvm -vnc :1

---

### Post by SATA on 2010-02-14
> **tuxic73 said:**
> small update: startging from the console with the -no-kvm switch causes the boot process to go further, except windows crashes and reboots. Just for you to try as well

kvm -m 1024 /dev/RAID/win2008 -no-kvm -vnc :1

Yeah I had tried that, And i got no further.
I've upgraded the machine to Lucid

---

### Post by tuxic73 on 2010-02-14
Did Lucid work for you?

---

### Post by SATA on 2010-02-14
> **tuxic73 said:**
> Did Lucid work for you?

Still installing, I'll let you know.

---

### Post by SATA on 2010-02-14
> **tuxic73 said:**
> Did Lucid work for you?


Only with -no-kvm on Lucid with Vista Guest (Which is an improvement to not booting at all)

---

### Post by SATA on 2010-02-15
Okay,

Running KVM with -no-kvm runs fine (Althrough hogs all the CPU)

Something about when NTLDR is loaded on Vista causes the machine to spaz and KVM returns the following:

```

ryan@kgb:~/Desktop$ sudo kvm -enable-kvm -m 1024 /var/lib/libvirt/images/winvista.img
kvm: unhandled exit 80000021
kvm_run returned -22

```

Getting Closer.... But not close enough

---

### Post by SATA on 2010-02-16
> **SATA said:**
> Okay,

Running KVM with -no-kvm runs fine (Althrough hogs all the CPU)

Something about when NTLDR is loaded on Vista causes the machine to spaz and KVM returns the following:

```

ryan@kgb:~/Desktop$ sudo kvm -enable-kvm -m 1024 /var/lib/libvirt/images/winvista.img
kvm: unhandled exit 80000021
kvm_run returned -22

```Getting Closer.... But not close enough

Same behaviour with Windows 7

---

### Post by r0mmie on 2010-04-03
I have the same issue, has anyone found a solution yet?

I can't use the -no-kvm argument either:

```
$ qemu-system-x86_64 -no-kvm -m 2047 -hdd vm1.img
Aborted
```

```

$ qemu-system-x86_64 -m 2047 -hdd vm1.img
kvm: unhandled exit 80000021
kvm_run returned -22
```

Basically, I have no way to use qemu/kvm for windows 7/Vista

---

### Post by ipso_frato on 2010-05-03
This happened to me, but it appeared to be an issue with the Windows installation, where the MBR wasn't created correctly.

I used KVM to boot off the Windows 7 CD again, and went to repair, then fixed the MBR as per this URL:

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Everything worked fine after that.

---

### Post by SATA on 2010-05-14
> **ipso_frato said:**
> This happened to me, but it appeared to be an issue with the Windows installation, where the MBR wasn't created correctly.

I used KVM to boot off the Windows 7 CD again, and went to repair, then fixed the MBR as per this URL:

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Everything worked fine after that.

Dude,

YOU ARE A LEGEND!

Fixed both hosts.

---

