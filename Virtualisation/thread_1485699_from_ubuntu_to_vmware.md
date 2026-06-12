---
title: "from ubuntu to vmware"
date: 2010-05-17
forum: Virtualisation
---

### Post by Franz01 on 2010-05-17
I have a ubuntu server and I have just installed a vmware package in a Win box.

Now I'd like to transfer the ubuntu server to the Win vmware installation.

Could you advice me?
So far I had a look at Clonezilla and, if I understand well, I could create a image file from the server and then boot the vmware with CloneZilla, copying the image to the disk... but please let me know whether I'm doing it the right way.... shall I use tar or dd instead?

Thank you.

---

### Post by ilovelinux33467 on 2010-05-17
if you mean to convert P2V (Physical to Virtual) you could always use vmware's own tool: VMware Converter

---

### Post by Franz01 on 2010-05-17
> **ilovelinux33467 said:**
> if you mean to convert P2V (Physical to Virtual) you could always use vmware's own tool: VMware Converter

Actually I cannot access the ubuntu server from my PC, where I have wmware installed.

But I can add a USB device to ubuntu. That's why I was thinking to copy from the server HD to the usb in some way... and then come back to my PC...

---

### Post by Franz01 on 2010-05-18
> **ilovelinux33467 said:**
> if you mean to convert P2V (Physical to Virtual) you could always use vmware's own tool: VMware Converter

Ok, it seems that vmware provides a bootable CD for cold migration of linux boxes...

---

