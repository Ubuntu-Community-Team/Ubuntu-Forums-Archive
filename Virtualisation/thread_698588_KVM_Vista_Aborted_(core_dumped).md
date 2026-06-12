---
title: "KVM: Vista Aborted (core dumped)"
date: 2008-02-16
forum: Virtualisation
---

### Post by lancerocke on 2008-02-16
On the step that say "Installing Windows Vista" in [this tutorial]("https://help.ubuntu.com/community/KVM") I get this error.
```
danny@danny-desktop:~$ kvm -m 1000 -cdrom /dev/cdrom1 -boot d -net nic,model=rtl8139 -net nic,model=ne2k_pci windows-vista.img
unhandled vm exit: 0xb
rax 0000000000000002 rbx 0000000000000001 rcx 000000004742444b rdx fffff80009948680
rsi fffff800091e2f70 rdi fffff800099ff550 rsp fffff8000b26ae20 rbp 0000000000000005
r8  0000000000000000 r9  fffff80009d071e0 r10 fffff8000984fe20 r11 fffff80009958960
r12 fffff800091e2f00 r13 fffff800099ff500 r14 0000000000000000 r15 fffff8000b26afc0
rip fffff80009c01d71 rflags 00000082
cs 0010 (00000000/00000000 p 1 dpl 0 db 0 s 1 type b l 1 g 0 avl 0)
ds 002b (00000000/ffffffff p 1 dpl 3 db 1 s 1 type 3 l 0 g 1 avl 0)
es 002b (00000000/ffffffff p 1 dpl 3 db 1 s 1 type 3 l 0 g 1 avl 0)
ss 0000 (00000000/ffffffff p 0 dpl 0 db 0 s 0 type 0 l 0 g 0 avl 0)
fs 0053 (00000000/00003c00 p 1 dpl 3 db 1 s 1 type 3 l 0 g 0 avl 0)
gs 0060 (fffff80009949700/0000ffff p 1 dpl 0 db 0 s 1 type 3 l 0 g 0 avl 0)
tr 0040 (fffff8000b264070/00000067 p 1 dpl 0 db 0 s 0 type b l 0 g 0 avl 0)
ldt 0000 (00000000/ffffffff p 0 dpl 0 db 0 s 0 type 0 l 0 g 0 avl 0)
gdt fffff8000b263000/6f
idt fffff8000b263070/fff
cr0 e0050031 cr2 0 cr3 2c5000 cr4 6a0 cr8 2 efer d01
Aborted (core dumped)
danny@danny-desktop:~$ 


```Any ideas?

---

### Post by Tails9 on 2008-02-19
I suggest you search Google for 'unhandled vm exit KVM vista'.
Are you trying to install 64-bit Vista?

Out of curiosity, why are you installing Vista?

---

### Post by PmDematagoda on 2008-02-19
This thread has been moved to the Virtualisation section.

---

