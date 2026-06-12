---
title: "Xen broke my Ubuntu"
date: 2008-05-17
forum: Virtualisation
---

### Post by SoyChulo on 2008-05-17
I just installed Xen via CL and when it said to reboot I did. The result was my kernel of choice in Grub was changed from Ubuntu 8.08, kernel 2.6.24-17 to Xen 3.2/ Ubuntu 8.04 kernel 2.6.24-17-xen.

When I choose that option as it is the only one I'm forced to watch all of the devices load.  The it says offending process: init.  Then strange sequence of lines with the prefix of [xx.xxxxxx])x=escalating number values).  This goes through hundreds and hundreds of these lines then nothing, it hangs and fails to boot into Ubuntu at all.

How can I recover my Ubuntu?  Xen is a piece of crap as far as I'm concerned.  Should have stuck with VB or VMWare.

Please help.:confused:

And it deleted my recovery kernel option too!

---

### Post by lex1 on 2008-05-18
[http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories](http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories)

---

### Post by bradmkjr on 2008-05-19
Xen is not a desktop virtualization platform such as VMware workstation, VMware Player or Virtualbox or even Qemu. It is designed to be on a dedicated server, which is access remotely, not via a gui interface. VMware server will run on a system with a gui interface, but you are putting a huge additional burden on a system running a gui and virtual machines.

I'm sorry to hear that your system no longer boots into GDM/KDM/XDM, but anytime you are swapping out kernels that is a risk you take. I'm unsure why you deleted your recovery kernel, as that might have allowed you to get back in and fix some issues. I think you might be able to do some careful reconstruction from the command line on a boot cd to get your kernel recovered.

This video may help
[http://www.youtube.com/watch?v=f8y29gqX9SU](http://www.youtube.com/watch?v=f8y29gqX9SU)


Bradford Knowlton
[http://x86Virtualization.com/](http://x86Virtualization.com/)

---

### Post by SoyChulo on 2008-05-22
I was able to use a Knoppix Live CD and go in and restore a menu.lst backup that I had.  This restored all of the previous kernels to my boot menu.  If I look the xen kernel images are still on my partition but do not show up on my boot screen as it wasn't there when the backup menu.lst was created.

Is it possible to remove xen or delete the files associated with it?  Everything is running great now and I don't want to mess it up.

I never removed the recovery kernels.  The Xen installation created a menu.lst that showed only the XEN altered kernel and my XP image.  It took the liberty of removing the previous kernels from the boot menu even thought they were still present on the machine.

The recovery was suprisingly much easier than anticipated, but XEN is still installed just not accessible as it isn't an option to boot into at present.

Thanks.

---

