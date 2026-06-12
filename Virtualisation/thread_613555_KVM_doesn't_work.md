---
title: "KVM doesn't work"
date: 2007-11-15
forum: Virtualisation
---

### Post by maxalken on 2007-11-15
I am trying to install a ubuntu server guest on KVM. if I load kvm-intel, I get core dumped

> jerry@shuttle:~$ kvm -m 750 -cdrom /home/DATA/images/ubuntu-7.10-server-amd64.iso -boot d vmware/ubuntu.img 
exception 6 (0)
rax 0000000000000469 rbx 0000000000800001 rcx 0000000000004300 rdx 0000000000000000
rsi 000000000005961d rdi 000000000005961c rsp 00000000fffaa9cc rbp 000000000000200c
r8  0000000000000000 r9  0000000000000000 r10 0000000000000000 r11 0000000000000000
r12 0000000000000000 r13 0000000000000000 r14 0000000000000000 r15 0000000000000000
rip 000000000000b04b rflags 00033006
cs 4143 (00041430/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ds 4004 (00040040/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
es 4004 (00040040/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ss 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
fs 3002 (00030020/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
gs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
tr 0000 (2f650000/00002088 p 1 dpl 0 db 0 s 0 type b l 0 g 0 avl 0)
ldt 0000 (00000000/0000ffff p 1 dpl 0 db 0 s 0 type 2 l 0 g 0 avl 0)
gdt 40920/47
idt 0/ffff
cr0 60000010 cr2 0 cr3 0 cr4 0 cr8 0 efer 0
code: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Aborted (core dumped)


If I use -no-kvm -no-acpi options, the KVM guest becomes so slow that the text installer can't even install grub, and get stuck there forever

---

### Post by maxalken on 2007-11-15
I found the answer here [http://kvm.qumranet.com/kvmwiki/Guest_Support_Status#head-c39a7e5b9f7ffdae4e3ae443710e3333b4e20bc7](http://kvm.qumranet.com/kvmwiki/Guest_Support_Status#head-c39a7e5b9f7ffdae4e3ae443710e3333b4e20bc7)

Ubuntu 7.10 can't work as a guest. So it's Ubuntu's bug!?

---

### Post by ubuntu_demon on 2007-11-15
I have also an "exception 6" (I tried 7.10 desktop) when creating the image with KVM.

I'm creating the image with KQEMU and I'm planning to try it both with KVM and KQEMU (if that's possible).

---

### Post by ansicplusplus on 2007-11-17
Hy,

I have gutsy running almost perfectly under KVM. I used the same procedure as I posted here for feisty ([Link]("http://ubuntuforums.org/showthread.php?t=444904")). 
You just have to get the corresponding images for gutsy.

Yours, ansicplusplus

---

### Post by ubuntu_demon on 2007-11-18
I'm using KVM on an image created with QEMU.

---

