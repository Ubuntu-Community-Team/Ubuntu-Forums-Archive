---
title: "Running VMWare workstation player on top of workstation player"
date: 2020-10-26
forum: Virtualisation
---

### Post by pablosl on 2020-10-26
Hello,

So I'm currently running an Ubuntu 20.4 VM on top of Windows 10 using workstation player, I'm using this VM to run GNS3 for network virtualization. Now, GNS3 uses a VM to run certain type of images (qemus for example) so I installed workstation player on the Ubuntu to run the VM, however whenever I try to start said VM, I get the regular warning of reduced performance for running workstation player on a VM, but after that the program crashes. Did any of you had this kind of issues?

thanks and regards!

---

### Post by TheFu on 2020-10-26
Is "nested virtualization" enabled?  That's the key word.
Have you validated the image file?
Do other OSes run under the nested virtualization?
It could be that GNS expects very specific device names and the VM configuration isn't providing that. If so, fix the configuration.
If you have a QEMU VM, why not use QEMU directly?  

I haven't used VMware Workstation in over 20 yrs and have never used Win10, so cannot say anything else to check.

---

### Post by pablosl on 2020-10-26
So, nested virtualization is enabled by default in this ova, disabling didn't change things tho. This Ubuntu host is running under nested virtualization, GNS3 does expect a specific setup yes, this ova is from GNS3's site, apparently to emulate certain devices it needs the qemu version of firmware and to run qemu it needs this VM running in the background. 
Maybe I should try the VirtualBox version of this VM

---

### Post by TheFu on 2020-10-26
You've lost me.  QEMU is an emulator in software for almost any hardware CPUs available.  I have no idea how VMware Workstation handles that, since qemu is a separate package to be installed.  I don't know if qemu supports OVA files or not.  I haven't touched any OVA files in about 8 yrs. I'm not that trusting, but I suppose there's little choice with GNS3.  Hopefully, they upgraded the internal Ubuntu from the unsupported 14.04 release they've been using a long time.  Too long.

---

### Post by pablosl on 2020-10-27
Sorry, I mean .qcow2 version of firmware which runs on qemu

---

### Post by TheFu on 2020-10-27
If the guestOS is 64-bit, you'll want to use KVM+QEMU so the hardware accel features are available. Straight qemu is seldom used by anyone, unless they need to support CPUs like MIPS.

There is a tool, qemu-img, which will convert .qcow2 files into a bunch of other formats - vdi, vmdk, etc.

---

