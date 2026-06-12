---
title: "kvm/qemu errors"
date: 2007-12-04
forum: Virtualisation
---

### Post by infoomatic on 2007-12-04
Hi,

I use an Asus P5B Mainboard with an Intel Core 2 Duo 6600 (2,4GHz, 4MB Cache). I just want to set up various ubuntu VMs for testing. The BIOS uses the default settings (Virtualization enabled...), however I get some strange errors:

1.) When using kvm (modules loaded), i get: 
```
exception 13 (0)
rax 000000000000001f rbx 000000000006fffa rcx 000000000002fc25 rdx 0000000000000000
rsi 000000000006fffa rdi 0000000000051809 rsp 0000000000007bd6 rbp 000000000006ffe4
r8  0000000000000000 r9  0000000000000000 r10 0000000000000000 r11 0000000000000000
r12 0000000000000000 r13 0000000000000000 r14 0000000000000000 r15 0000000000000000
rip 000000000000145a rflags 00033046
cs 4004 (00040040/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ds 4004 (00040040/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
es 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ss 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
fs 0080 (00000800/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
gs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
tr 0000 (10850000/00002088 p 1 dpl 0 db 0 s 0 type b l 0 g 0 avl 0)
ldt 0000 (00000000/0000ffff p 1 dpl 0 db 0 s 0 type 2 l 0 g 0 avl 0)
gdt 40620/f
idt 0/3ff
cr0 60000010 cr2 0 cr3 0 cr4 0 cr8 0 efer 0
code: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Aborted (core dumped)
```

I found this: [http://kvm.qumranet.com/kvmwiki/Intel_Real_Mode_Emulation_Problems]("http://kvm.qumranet.com/kvmwiki/Intel_Real_Mode_Emulation_Problems")
 but without using the graphical boot I get the same error.

2.) Since the kqemu module is not much slower than kvm, I gave it a try. But with this module loaded I get kernel panics inside the VM (tried ubuntu server + desktop, gentoo, various bsds)

Can anyone help?

edit: I use Ubuntu Desktop 7.10 with all updates, currently I am using no acceleration and It's awfully slow!

---

