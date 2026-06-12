---
title: "which virtual machine software to use?"
date: 2008-08-21
forum: Virtualisation
---

### Post by syxbit on 2008-08-21
I've read the sticky's, but they don't really list pro's and con's
could anyone make any recommendations between these?

XEN, KVM, VirtualBox, VMWare, Qemu.

From what I've read, VMWare is the only non OSS.

---

### Post by petedct on 2008-08-21
I can’t give you a comprehensive list of the pros and cons but from my experience VirtualBox is simple to install and set up. I use it mainly for trying out other Linux distros and for running tax software in XP. After reading around the web I felt that the others would take more work to install and setup. VirtualBox is available in the Ubuntu repos minus a few goodies like USB support. If you want to try out USB support than that version can be had at the [VirtualBox web site]("http://www.virtualbox.org/wiki/Editions"). Cheers!! :)

---

### Post by jayson.rowe on 2008-08-21
Hi Syxbit,
They all have their advantages and dis-advantages. It's best to try a few and stick with one that you like (especially important once you get some machines built).

I'll try to lay out some of the differences for you:

XEN:
Awesome platform for virtualizing servers on servers. I do not reccomend XEN for desktop use. First, it requires a different kernel than the standard Ubuntu kernel, which makes proprietary drivers (if you need them) a royal pain. If going with XEN, I reccomend setting up a CLi only server, loading the XEN kernel and going from there. At work I use XEN all day long - using Citrix XenServer Enterprise (which is based on CentOS 5). Xen gives you the ability to "Paravirtualize" an OS (Paravirtualization means the Guest OS knows it's being virtulized) allowing for enhanced (near bare-metal speed) performance. Also, in XEN, to virtualize a Windows OS you must have Hardware Virtulization support in your CPU (and also be enabled in the BIOS). Xen uses the Linux host OS and QEMU to handle I/O.

KVM:
KVM is unique and new to the virtualization world. Using QEMU to handle I/O and loading itself into the Kernel (as a module) it in turn basically turns Linux into a Hypervisor. KVM is very easy to maintatin through kernel revisions (Ubuntu builds KVM modules with each release) so you don't have to worry about breakage. KVM is fast and powerful, just not as easy to use as say VMware or VirtualBox, but easier to handle than XEN. KVM must have Hardware Virtualization support in the host CPU to run any OS.

VirtualBox:
Sun's VirtualBox (previously Innotek) is a great tool, and is more comparable to VMware than either XEN or KVM. The GUI is very intuitive, but is written in QT, so looks very ugly by default on a GNOME desktop unless you have many KDE libraries and themes loaded. VirtualBox is very fast, and can make use of Hardware Virtualization, but doesn't need it to run. There are also two versions of VirtualBox - there is VirtualBoxOSE (Open Source Edition) which is available in the Ubuntu repositories), and the propritery version available from Sun's website. The main difference is that the version from Sun has proprietry drivers built in, however, you can download the Guest Additions ISO to install them into your guests in the OSE Edition.

VMWare:
There are 3 basic versions of VMWare you will deal with on Linux. First (and most simple) is VMWare Player. Player doesn't allow you to create images, but you can download many images online, load them up and play them. VMware Workstation is geared towards the Workstation, is very fast, but is not available for free (costs about $190 per workstation). VMWare Server is "based" on VMWare Workstation 4.5 (current workstation version is 6 and has had many improvements since 4.5). The biggest difference between Server and Workstation is that in Server, Virtual machines can be set to start up and shutdown with the Host OS basically acting like Daemons. VMware server is availble for free. The current version is 1.0.6, but VMware Server 2 is availible as a pre-release, and is based on VMWare Workstation 6, and like 6 supports paravirutalizing Linux OSes that have the VMX flag compiled in the kernel (ever version of Ubuntu since 7.04 has supported this) and makes for a VERY fast Linux virtual. 
Speedwise, VMWare server can be very fast, and only requires Hardware Virtualization to run x86_64 operating systems (even on an x86_64 host).

QEMU:
The slowest of the bunch, and can be complicated to set up machines (using the command line), however there is a GUI program called QEMULator that makes this easier. QEMU is full emulation of a processor, and is quite slow (think around 30% of native speed). I generally wouldn't reccomend messing with QEMU unless you have a specific reason to do so, however as I mentioned before, both XEN and KVM utilize QEMU to some extent to handle I/O for their virtual machines.

I know these are brief descriptions, but hopefully this will give you at least a general idea of the differences.

If it matters to you, although I use XEN at work, I have VMWare Workstation on my PC at work, and at home I have a Ubuntu Server that isn't running X that I have VMWare Server on running 10 Virtual Machines, and I simply connect to it from my desktop using the VMWare Server Console. I've toyed with VirtualBox and KVM some at home as well, but none have given me a compelling reason to switch.

---

### Post by syxbit on 2008-08-22
great info.
thanks
i've used VMWare a few times, cause i like the pre-done images.
i'm trying out VirtualBox. It's not as good as VMWare (the simple share folders isn't working for me), but it's OSS, and decent

---

