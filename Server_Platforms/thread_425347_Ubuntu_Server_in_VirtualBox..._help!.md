---
title: "Ubuntu Server in VirtualBox... help!"
date: 2007-04-27
forum: Server Platforms
---

### Post by hise0001 on 2007-04-27
Hi,
Hi,

I've installed VirtualBox on my 32-bit Fiesty Desktop.  I want to setup up a test environment running 32-bit Edgy Server in a virtual box.

I've successfully installed Edgy Server in a virtual box.  Upon starting the virtual machine, I reach grub.  When grub tries to launch the edgy server I receive a repeated string of messages saying...

"Unknown interrupt or fault at EIP 00000060 c0100295 00000294"

Does anyone have any input as to what's going on?

I'm guessing VirtualBox doesn't like having a boot loader in the boot sector of a virtual disk, so I tried to find a way to install edgy server without installing grub but couldn't.

Thanks in advance for your help.

--Hise

---

### Post by hise0001 on 2007-05-04
bump!

---

### Post by IcemanV9 on 2007-05-05
Unfortunately, it is a known bug. It is related to the race condition in the kernel 2.6.18+. So, it has nothing to do with grub.

---

### Post by hise0001 on 2007-05-10
Doh!

oh well maybe soon.

Thanks for the reply.

--Hise

---

