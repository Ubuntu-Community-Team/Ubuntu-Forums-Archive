---
title: "Hardware Virtulisation (Spesficly KVM) not working"
date: 2008-01-25
forum: Virtualisation
---

### Post by neoncode on 2008-01-25
I've been trying to get hardware virtulisation working, and whenver I try to run KVM I get

```

monolith@monolith-desktop:~/Disk Images$ sudo qemu-system-x86_64 -cdrom "KDE4 0.0.12.iso"
[sudo] password for monolith:
exception 13 (33)
rax 0000000000000600 rbx 0000000000800000 rcx 0000000000000000 rdx 000000000000b163
rsi 0000000000055821 rdi 000000000005581d rsp 00000000fffaf454 rbp 000000000000200c
r8  0000000000000000 r9  0000000000000000 r10 0000000000000000 r11 0000000000000000
r12 0000000000000000 r13 0000000000000000 r14 0000000000000000 r15 0000000000000000
rip 00000000000001bc rflags 00033006
cs 4004 (00040040/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ds 4004 (00040040/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
es 4004 (00040040/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ss 5381 (00053810/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
fs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
gs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
tr 0000 (fffbd000/00002088 p 1 dpl 0 db 0 s 0 type b l 0 g 0 avl 0)
ldt 0000 (00000000/0000ffff p 1 dpl 0 db 0 s 0 type 2 l 0 g 0 avl 0)
gdt 40914/47
idt 0/ffff
cr0 60000010 cr2 0 cr3 0 cr4 0 cr8 0 efer 0
code: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 --> ff ff ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Aborted (core dumped)


```

I'm useing a compiled version of KVM-60 on Kubuntu 7.10 (as per [this]("http://www.howtoforge.com/using-kvm-on-ubuntu-gutsy-gibbon") guide, thus the strange command, but the repo version returns the same result.)

In terms of hardware I have an Intel Core 2 Duo E6600 CPU and an Asus P5N32-E SLi motherboard with an nForce 680i chipset. Hardware Virtulisation support is enabled in BIOS. 

cpuinfo shows...

```
monolith@monolith-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 2400.094
cache size      : 4096 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4803.16
clflush size    : 64

```

I also have "kvm" and "kvm_intel" in my /etc/modules file, and my kernel version is...

```
monolith@monolith-desktop:~$ uname -r
2.6.22-14-386

```


Can anyone offer any advice as to why it isn't working? If you need me to provide more information about my system I can.

---

