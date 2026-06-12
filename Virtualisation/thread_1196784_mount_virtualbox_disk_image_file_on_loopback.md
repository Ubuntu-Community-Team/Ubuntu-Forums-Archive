---
title: "mount virtualbox disk image file on loopback"
date: 2009-06-25
forum: Virtualisation
---

### Post by anonmars on 2009-06-25
I'm trying to mount a VirtualBox disk image file on loopback so I can browse the file system, etc. from within my host OS:

sudo mount testimage.vdi ~/.VirtualBox/HardDisks/test -t ext3 -o loop

But when I run that it says "wrong fs type." I presume that's because the testimage.vdi file isn't ext3, though the file system inside it is...

Am I misunderstanding this? Or do I just need to specify the right file system type, and if so, what?

Thanks.

---

### Post by juancarlospaco on 2009-06-25
Its not RAW format, you have to convert it to RAW format, an you can mount and browse,
but you have to re-convert to VBOX format to use it again, 
its not very safe for data integrity versus daily usage.

Maybe a better option is to use Qemu+KQemu it can run on RAW format, and mount it directly,
KVM support it too, and its a better technology, a nice GUI to KVM is Convirt 1.0

---

### Post by anonmars on 2009-06-25
> **juancarlospaco said:**
> Its not RAW format, you have to convert it to RAW format, an you can mount and browse,
but you have to re-convert to VBOX format to use it again, 
its not very safe for data integrity versus daily usage.

Maybe a better option is to use Qemu+KQemu it can run on RAW format, and mount it directly,
KVM support it too, and its a better technology, a nice GUI to KVM is Convirt 1.0
What about a Xen disk image?

---

### Post by juancarlospaco on 2009-06-25
But you already have KVM in the Kernel, 
Xen its an independent microkernel, 
it makes your actual system like a virtual machine.

---

### Post by anonmars on 2009-06-25
> **juancarlospaco said:**
> But you already have KVM in the Kernel, 
Xen its an independent microkernel, 
it makes your actual system like a virtual machine.
Yes but KVM requires hardware support.

---

### Post by anonmars on 2009-06-25
> **anonmars said:**
> I'm trying to mount a VirtualBox disk image file on loopback so I can browse the file system, etc. from within my host OS:

sudo mount testimage.vdi ~/.VirtualBox/HardDisks/test -t ext3 -o loop

But when I run that it says "wrong fs type." I presume that's because the testimage.vdi file isn't ext3, though the file system inside it is...

Am I misunderstanding this? Or do I just need to specify the right file system type, and if so, what?

Thanks.
A Xen image worked, I changed the type to auto.

---

