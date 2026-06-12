---
title: "Return Code Indicates I can't run KVM; Can I run Virtualbox instead?"
date: 2016-07-26
forum: Virtualisation
---

### Post by SciGuy1872 on 2016-07-26
I was reading how to install KVM, and the first step is to make sure that the CPU supports hardware virtualization by entering the code:

```
anthony@anthony-Aspire-X1200:~$ egrep -c '(vmx|svm)' /proc/cpuinfo
0
```

The webpage states that the "0" that is returned means that the CPU doesn't support hardware virtualization.

Does this mean that I cannot do any virtualization, or just that I can't use KVM?  I'd like to use Virtualbox--they have a very nice tutorial.

I  am running Xenial 32-bit with 3GB of memory.
Thanks,
    Anthony

---

### Post by &amp;KyT$0P# on 2016-07-26
VirtualBox works best with hardware virtualization, but I don't think it's a requirement.
(I'm saying that just based on personal experience.  I've run VirtualBox inside VirtualBox VMs before.  Tried to use KVM inside a VirtualBox VM, but couldn't do it.)

What exactly computer do you have?  What are the specs on your computer?
Can you check your BIOS to see if hardware virtualization is available but just turned off?

---

### Post by siepo on 2016-07-26
Without hardware virtualization, VirtualBox can still run 32bits guests.

---

### Post by SciGuy1872 on 2016-07-26
I have an Acer Aspire X1200 160GB, 3GB memory, 32-bit, Nvidia GeForce 8200 (although when I go to Settings, the graphics is Gallium--when I first got this machine through Craig's List, I tried to change to the Nvidia driver, but after rebooting, the desktop appeared for a second, but then I lost all display; like I said, everything is perfect, the speed and everything, so I don't want to mess with being shut out).

I did go into BIOS just to make sure virtualization was enabled--it was.  But KVM still reports that the processor doesn't support virtualization, weird, right?  Oh well, as long as VB can still be used.

Thanks for the help all,
                           Anthony

---

### Post by &amp;KyT$0P# on 2016-07-26
You're welcome.

After initially setting up your first virtual machine, you can check if VirtualBox can make use of your hardware virtualization by going into the settings for the VM and checking what, if anything, is grayed out under "System".

---

