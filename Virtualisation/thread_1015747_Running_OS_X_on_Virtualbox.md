---
title: "Running OS X on Virtualbox?"
date: 2008-12-19
forum: Virtualisation
---

### Post by Jonne on 2008-12-19
I'm running Ubuntu on an iMac (because I like Ubuntu better), and I was wondering if anyone has found a way to run OS X in Virtualbox. I found another thread on that, but it was closed because apparently it's illegal to run OS X on anything other than macs (whether that's actually enforceable is another discussion, which I'd like to avoid here).

So, has anyone managed to either run the existing OS X install on a mac or a new virtual machine in virtualbox?

Note that running OS X in virtualbox *is* legal if you do it on Apple hardware, which is what I'll be doing, so please don't close this thread like you did with the other one.

I got so far for now:
ran
```
sudo usermod -a -G disk username
```
logged out and back in again
then:
```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/osx.vmdk -rawdisk /dev/sda2-register
```
which creates a vmdk file
then I created a new virtual machine in the wizard (I picked FreeBSD as the OS)
But when i try to boot it I get 'FATAL: No Bootable medium Found! System Halted', which is probably because OS X doesn't boot from a BIOS.

Anyone know a way of bypassing that?

---

### Post by medley on 2008-12-19
> **Jonne said:**
> I'm running Ubuntu on an iMac (because I like Ubuntu better), and I was wondering if anyone has found a way to run OS X in Virtualbox. I found another thread on that, but it was closed because apparently it's illegal to run OS X on anything other than macs (whether that's actually enforceable is another discussion, which I'd like to avoid here).

So, has anyone managed to either run the existing OS X install on a mac or a new virtual machine in virtualbox?

Note that running OS X in virtualbox *is* legal if you do it on Apple hardware, which is what I'll be doing, so please don't close this thread like you did with the other one.

I got so far for now:
ran
```
sudo usermod -a -G disk username
```
logged out and back in again
then:
```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/osx.vmdk -rawdisk /dev/sda2-register
```
which creates a vmdk file
then I created a new virtual machine in the wizard (I picked FreeBSD as the OS)
But when i try to boot it I get 'FATAL: No Bootable medium Found! System Halted', which is probably because OS X doesn't boot from a BIOS.

Anyone know a way of bypassing that?

My suspicion is that OS X probably won't run well, if at all, in VBox because the VBox graphics driver doesn't seem to support the 3D functions needed for transparency, etc. Unless there is some stripped down configuration for the OS X desktop, you likely won't be able to get the composite effects you'll need. I say that based on the fact that I can't use the advanced visual effects available in KDE4 working in VBox because of the simple gfx driver VBox exposes to the guest OS. Of course, I could be wrong and would be interested to hear otherwise.

Good luck.

---

### Post by tsphere on 2008-12-20
You can't run OSx on virtualbox, but you can in kvm/qemu, which actually use hardware virtualization and so runs very fast.
There is a guide here:
[http://alex.csgraf.de/self/?qemu/](http://alex.csgraf.de/self/?qemu/)
A link to an installation guide is there.

I can tell you a bit more about it, pm me if you want to discuss it more, I think they (rightfully) frown on discussing these matters here as they're of disputed legality.

---

### Post by Jonne on 2008-12-20
I'll check out the qemu/kvm route, but one problem with that is that you can't have both Virtualbox and KVM installed at the same time (right?). I don't have unlimited hardware (if I did, i wouldn't be looking at virtualization ;) )

anyway, I'll be gone for a couple of weeks, so I'll try it then.

---

