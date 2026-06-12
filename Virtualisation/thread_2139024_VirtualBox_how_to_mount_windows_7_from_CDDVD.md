---
title: "VirtualBox how to mount windows 7 from CD/DVD?"
date: 2013-04-25
forum: Virtualisation
---

### Post by Laynetrain on 2013-04-25
First post\\:D/

I installed VirtualBox software on Ubuntu.  I have a Windows 7 Professional 64bit DVD that my friend at work gave me - it's wicked shiny.  I want to run Windows 7 64bit as a VM using VirtualBox software running on Ubuntu 12.10 (or whatever the latest version is).  I add a new VM using the VM Wizard.  I give it 666MB RAM and 50GB storage, while using all the other default settings.


I knowingly start the VM in anticipation of it not working and get this message:[INDENT]"[/INDENT]
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
"


I assume it's because I have not actually "installed" the Windows 7 OS.  From what I gather you do this using the OS "install" CD/DVD or from an ISO file.  


So how do I use the DVD to enable this VM?

---

### Post by midnightramen on 2013-04-30
this is just a quick reply, but the windows 7 dvd probably has nothing to do with why the VM is not running. It seems like the vboxdrv module isn't loaded, which could be resolved using the "sudo /etc/init.d/vboxdrv setup" command at a terminal prompt, or possibly reinstalling VirtualBox. If the module is correctly loaded, the command "lsmod" should show a bunch of vbox modules, such as vboxpci ,etc. 

Typically, I have had the most success with the virtualbox installs from the official oracle website at [www.virtualbox.org](www.virtualbox.org) instead of the virtualbox ose version that can be found on the ubuntu apt-get repositories.

---

### Post by coldraven on 2013-04-30
Check that your hardware supports virtualisation.
[http://www.cyberciti.biz/faq/linux-xen-vmware-kvm-intel-vt-amd-v-support/](http://www.cyberciti.biz/faq/linux-xen-vmware-kvm-intel-vt-amd-v-support/)

---

