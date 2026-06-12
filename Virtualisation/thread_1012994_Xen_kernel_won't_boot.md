---
title: "Xen kernel won't boot"
date: 2008-12-16
forum: Virtualisation
---

### Post by djbon2112 on 2008-12-16
I'm running Ubuntu Server 8.10 and GRUB as my bootloader. I built and installed Xen 3.3 from source. It installed and everything, but I manually had to put the boot entries into menu.lst. The xen-3.3.gz and xen.gz files exist in my /boot folder, I have verified this. However, when I try to boot my Xen entry ("kernel /boot/xen.gz"), I get a GRUB Error 15: File not found. 

I can see no reason for this: I'm following the other entries (which all have /boot prefixed since I use only one ext3 partition for /), I have the right UUID for the partition, and I know the files exist and were installed. I've tried removing and reinstalling Xen twice, and also reinstalled GRUB twice to no avail. Does anyone have any light they could shine on the subject?

---

### Post by djbon2112 on 2008-12-16
After some more experimenting, I found something else that makes even less sense.

In a GRUB command line at boot, if I type:

root (hd0,1)
kernel /vmlinux

It works fine. Now, I created a symlink to the xen-3.3.gz images, called xen, in my root drive (much the way vmlinuz and initrd.img have symlinks in root). I do the same thing

root (hd0,1)
kernel /xen

And I get the Error 15 again. I can see ZERO logical reason for this, at all. Anyone?

---

### Post by djbon2112 on 2008-12-16
It turns out that Xen isn't supported in 8.10, from what I've read at least. I'm going to 8.04 LTS for the server, but not marking this thread as solved in case someone does have a solution.

---

### Post by Xepra on 2008-12-17
So, I just went through this as well, so perhaps I can shed light on the situation:

[http://cwshep.blogspot.com/2008/12/howto-ubuntu-intrepid-ibex-810-xen-dom0.html](http://cwshep.blogspot.com/2008/12/howto-ubuntu-intrepid-ibex-810-xen-dom0.html)


When you say you installed from sources, I am assuming you also compiled the last stable linux-xen 2.6.18?

Xen 3.3 is actually in the repositories for 8.10, it just doesn't include a dom0 compatible kernel.  This is very nice (well not as nice as including the kernel...) because it puts the xen 3.3 image in your /boot folder as well as sets up and configures all of the directories and xen tools like xen-create-image.

In that blog I also link to a bunch of stuff that is useful.  I think there are a couple not so obvious tidbits if you are familiar with xen, but not compiling xen kernels:  

First there are backend and frontend drivers; backend drivers are for dom0, frontend drivers are for domUs.

The xen linux bzImage is actually an ELF binary format, unlike vanilla linux kernels, but this should be transparent to you if you compile the kernel correctly.

The forward ported linux xen kernels don't necessarily come configured with Xen enabled, you have to make sure you configure the right options.

So basically the procedure is:

Install ubuntu-xen-server (or desktop)
Compile a dom0 compatible kernel
Modify Grub to boot the kernel
Fix little tidbits like the console='xvc0' thing.

Now there is something new called paravirt_ops.  My understanding of this, please correct me if I am wrong, is that it is a standard interface to run linux as a virtualized host on hypervisors, ie KVM or Xen, as well as run standalone?  Whatever it is, it is supposed to be included in all the recent kernels, including the kernels that ship with 8.10.

I tried running both the vanilla ubuntu 810 kernel as well as a custom compiled kernel from the latest source (with paravirt_ops enabled) and it did not work; neither would recognize the virtual block devices, or at least they didn't show up in /dev.

This sounds a lot more complicated than it is ;p

---

### Post by djbon2112 on 2008-12-19
I just got it working with 8.04, and frankly, I'd rather use the LTS release. Thanks for the help though!

---

