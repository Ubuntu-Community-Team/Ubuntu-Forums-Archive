---
title: "Creating a virtual image from an existing hard ubuntu installation"
date: 2010-05-03
forum: Virtualisation
---

### Post by gartss on 2010-05-03
Hi all,

I would be very interested in creating a virtual image which will be a copy of my existing ubuntu hard installation (which is not virtual).
I wonder if VirtualBox or VMware (or others) are capable of doing such a thing. I tried googling some but didn't find any answer easily, or any topic on that
So just to know if someone already did this, or just asked himself the question :-)

Many thanks and have a nice day !
Gartss

---

### Post by benderisgreat on 2010-05-03
The way i would do is to create an image file using dd or qemu-img big enough to hold your installation. Then partition it with fdisk (and set up lvm if you use it) as you have your installation.
Install grub on the image. Make filesystems on your partitions/logical volumes. Boot from a live cd, mount your existing installation and the image. Then rsync the files from your installation into the target. If your fstab uses UUIDs you should check the uuids of the target because it/they will be different  and change it in your target's fstab. I think your installation should then be bootable and virtualizable with any fully virtualizing software, though i only have experience with kvm and xen.

---

### Post by HermanAB on 2010-05-04
Yes, you can - however, it is so easy to install Ubuntu from scratch that it is probably not worth the trouble, since copying it will take much longer than re-installing it in the VM.

---

### Post by uberlinuxnerd on 2010-05-04
> **HermanAB said:**
> Yes, you can - however, it is so easy to install Ubuntu from scratch that it is probably not worth the trouble, since copying it will take much longer than re-installing it in the VM.

I agree with this, having had experience doing it. P2V is a pain on linux and I would say re-install and copy what every you need over. Further more Synaptic markings maybe of some use to you after a reinstall.

e.g. Export markings on old physical machine and import them on the new virtual machine.

---

### Post by gartss on 2010-05-04
Hi all,

Thanks for answers.
Thank you benderisgreat, I think your solution may work.
However I totally agree with all remarks :-)
Personally I would do the same (install from scratch and reinstall everything).
I asked the question for a totally unexperienced scientist (one of my colleague) that has its linux installation with all its home-made programs and stuff, since 10 years ... He never upgraded anything and he is afraid of a hardware system crash :-) And he **** me off !
So he asked me for a solution, and I do not want to spend a week to help him upgrade all its stuff. That's actually why I asked myself for a virtualization solution, so he could keep its old system in a virtual image.

Thanks again for suggestions.

---

### Post by lmarmisa on 2010-05-05
You can use Clonezilla for creating a partition/disk image from your hard Ubuntu installation and recovering it to a virtual disk (for example, with VirtualBox):

[http://clonezilla.org/](http://clonezilla.org/)

Clonezilla works great, but I do not know if this migration will be successful.

Best regards,

Luis

---

### Post by gartss on 2010-05-05
Thank you ! it will better fill my needs, and a lot easier.

---

