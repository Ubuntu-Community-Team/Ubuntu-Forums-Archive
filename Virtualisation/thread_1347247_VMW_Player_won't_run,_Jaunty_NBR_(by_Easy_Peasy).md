---
title: "VMW Player won't run, Jaunty NBR (by Easy Peasy)"
date: 2009-12-06
forum: Virtualisation
---

### Post by beloved88 on 2009-12-06
my specs are as follows:
HPMINI1101 Atom N280, 2GB mem, 32GB SSD, 
Easy Peasy 1.5 (it's basically jaunty nbr with ext4 and custom kernel)
Kernel Version: 2.6.30.5-ep0

I'm trying to install VMWare Player v.3.0
I've been able to install it, and i can creat VMs but when i try to play the VM it tells me this:
Error: "Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded."
"Failed to initialize monitor device."
"The virtual machine is busy."

I've tried a variety of things posted on other threads, but nothing seems to work.
I've tried a couple of the vmware-any-any-update (115 and 117), and when i run runme.pl it spits this back at me:

"Unknown VMware version 1 is installed. This installer supports only version 2 
and 3.

Execution aborted."

There were also a couple of fixes dealing with vmware-config nder usr/bin, but that file is not even there.

what i understand, it's a patch needed, but i can't find it.  is there something else i've missed?

---

### Post by beloved88 on 2009-12-06
other thing, i can't seem to use ANY virtualization software.  Vitualbox, which i just installed, spits this out when i try to turn a machine on.
"Please install the virtualbox-ose-source package and the appropriate
     headers, most likely  linux-headers-.
     You will not be able to start VMs until this problem is fixed.
VBoxSDL: Error -1908 in suplibOsInit!
VBoxSDL: VERR_VM_DRIVER_NOT_INSTALLED
VBoxSDL: Tip! Make sure the kernel module is loaded. It may also help to reinstall VirtualBox."

When i try to to any of the above, aptitude, apt-get, and synaptic package manager (GUI) tell me i'm up to date on everything... what to do?

---

### Post by beloved88 on 2009-12-06
dumb solution.  I haven't ever rebooted my computer, it just cycles between suspend and normal.  I've updated my headers and all and have never rebooted my machine.  I unistalled all my virtualization stuff and rebooted, and reinstalled it, no problems at all, thanks anyway

---

### Post by fjgaude on 2009-12-06
Well, it's  nice that as we learn new things we are grateful. Peace settles in.

---

