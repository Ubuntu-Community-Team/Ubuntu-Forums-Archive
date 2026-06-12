---
title: "Getting Windows from hard drive partition to virtual machine"
date: 2008-08-29
forum: Virtualisation
---

### Post by bieber on 2008-08-29
Little bit of a problem, I was wondering if anyone could help.  I'm on a laptop that's running 8.04, but there's still a little Windows partition with the Vista install that came with the machine.  I've copied the partition to a file in my home directory with dd, but it doesn't seem to be usable with Qemu-launcher: I'm guessing this is because there's no boot-loader on the partition, but how do I get one onto it?  Also, is there a way to transfer it to an image format that will only take up as much space as is actually used on the partition? (I'm looking at a 20GB file holding an 8GB file system right now).  I'm also using a Core 2 Duo, and I have KVM installed, but is it going to be used if I'm launching Qemu with Qemu-launcher?  If not, what would be a better solution?

---

### Post by HermanAB on 2008-08-30
The easy way is to use a tool from VMware.  The other way is to google for a guide.  There are a few.

In essence, you have to ensure that you have installed some generic SCSI, display and ethernet drivers, before you copy the partition to a VM disk using dd.

H.

---

