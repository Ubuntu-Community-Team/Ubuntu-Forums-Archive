---
title: "Virtualization out-of-the-box"
date: 2010-03-04
forum: Server Platforms
---

### Post by smeerbartje on 2010-03-04
Hi guys, I was wondering what the possibilities are with Ubuntu Server 9.10 64 bit regarding virtualization. Currently I'm running a home server with VMWARE server 2.0 running two VMs: Windows XP and a 'development' server (also ubuntu). Main problem is that I don't like vmware; it often needs 're-configuration' and I prefer a native solution.

But what native solutions are available? According [this page]("http://www.ubuntu.com/products/whatisubuntu/serveredition/technologies/virtualization"), we have KVM. But here are some questions:

[LIST=1]
[*]Is my motherboard/processor compatible with KVM? I have a Intel DQ35JO motherboard with a Intel Core2Duo (E7300) processor.
[*]Do I need to activate the virtualization stuff in the BIOS?
[*]Are there VERY simple how-to's available which show how to create a Virtual Machine running -for example- Windows XP?
[/LIST]

Thanks!

---

### Post by spynappels on 2010-03-04
This is probably not the answer you want, but using a bare metal hypervisor such as VMWare ESXi (free) is often a better option. This uses less resources tha an underlying OS and any that I have run are rock solid, rarely, if ever, needing reconfiguration. And you can probably run your existing VMs on it.

---

### Post by smeerbartje on 2010-03-05
> **spynappels said:**
> This is probably not the answer you want, but using a bare metal hypervisor such as VMWare ESXi (free) is often a better option. This uses less resources tha an underlying OS and any that I have run are rock solid, rarely, if ever, needing reconfiguration. And you can probably run your existing VMs on it.

Thanks for your answer, but this indeed is not the answer I want :). My primary OS (Ubuntu server) runs a lot of services I need every day: web, mysql, transmission, sabnzb, etc. Every now and then I want to start a virtual machine (Windows XP or ubuntu server dev) for test purposes. This can be once a month or something. Therefore I don't think it's efficient to use ESXi as a host, since the usage of VMs is not that big.

---

### Post by kiranmurari on 2010-03-05
Hi smeerbartje,

> 1. Is my motherboard/processor compatible with KVM? I have a Intel DQ35JO motherboard with a Intel Core2Duo (E7300) processor.You can check if your machine has hardware virtualization support by the following command:
```
$ cat /proc/cpuinfo | grep vmx
```If hardware virtualization is supported, it is represented with vmx flag for Intel processors and svm flag for AMD processors in /proc/cpuinfo.

In case your machine does not support hardware virtualization, you can use qemu.

> 2. Do I need to activate the virtualization stuff in the BIOS?Once the above command returns a valid flag, then you need to check your BIOS settings for enabling virtualization.

> 3. Are there VERY simple how-to's available which show how to create a Virtual Machine running -for example- Windows XP?The following links might be helpful in understanding virtualization and on how to create a virtual machine on ubuntu server.
[https://help.ubuntu.com/9.10/serverguide/C/libvirt.html](https://help.ubuntu.com/9.10/serverguide/C/libvirt.html)
[https://help.ubuntu.com/9.10/serverguide/C/jeos-and-vmbuilder.html](https://help.ubuntu.com/9.10/serverguide/C/jeos-and-vmbuilder.html)
[https://help.ubuntu.com/community/Installation/QemuEmulator](https://help.ubuntu.com/community/Installation/QemuEmulator)
[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

Let me know if you have any questions in specific.

---

### Post by smeerbartje on 2010-03-05
> **kiranmurari said:**
> Hi smeerbartje,

You can check if your machine has hardware virtualization support by the following command:
```
$ cat /proc/cpuinfo | grep vmx
```If hardware virtualization is supported, it is represented with vmx flag for Intel processors and svm flag for AMD processors in /proc/cpuinfo.

In case your machine does not support hardware virtualization, you can use qemu.

Once the above command returns a valid flag, then you need to check your BIOS settings for enabling virtualization.

The following links might be helpful in understanding virtualization and on how to create a virtual machine on ubuntu server.
[https://help.ubuntu.com/9.10/serverguide/C/libvirt.html](https://help.ubuntu.com/9.10/serverguide/C/libvirt.html)
[https://help.ubuntu.com/9.10/serverguide/C/jeos-and-vmbuilder.html](https://help.ubuntu.com/9.10/serverguide/C/jeos-and-vmbuilder.html)
[https://help.ubuntu.com/community/Installation/QemuEmulator](https://help.ubuntu.com/community/Installation/QemuEmulator)
[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

Let me know if you have any questions in specific.

Thanks; I will check on short term.

---

### Post by miguel.antonio.168 on 2010-03-05
[FONT=Arial][SIZE=3]agree with you on KVM, we are currently using it in our server running 4 virtual pc's serving remote branches and find it pretty stable. been using it for 3 years now and no hiccups so far. 

just installed another server with KVM also in it to handle our main office and this machine will also act as our alternate server in the event of failure of the machine handling our branches' virtual pc.
 
our server is a quad core phenom with 8 gig mem running on ubuntu 64. much responsive and easier to manage compared to virtualbox which we tried to use first for a few months until we discovered KVM.

i believe you're on the right path with KVM.

good luck...
[/SIZE][/FONT]

---

### Post by tlsarles on 2010-03-05
Seriously, VMWare ESX IS the answer you want. It installs straight to the machine without a host OS, so that you can reboot any of the VM/Host OS's without one being reliant on the other. This is definitely the way to go.... As long as you have a modern CPU that has virtualization extensions, the performance hit is basically a non-issue.

of course, if you hardly use the VM's like you say.... then I would just stick with what your doing... or KVM, but I think VMWare is easier to use. If you don't want to reconfigure every time you get a new kernel or a VMWare update, then use an APT repository rather than manually installing VMWare.

---

### Post by smeerbartje on 2010-03-05
> **tlsarles said:**
> Seriously, VMWare ESX IS the answer you want. It installs straight to the machine without a host OS, so that you can reboot any of the VM/Host OS's without one being reliant on the other. This is definitely the way to go.... As long as you have a modern CPU that has virtualization extensions, the performance hit is basically a non-issue.

of course, if you hardly use the VM's like you say.... then I would just stick with what your doing... or KVM, but I think VMWare is easier to use. If you don't want to reconfigure every time you get a new kernel or a VMWare update, then use an APT repository rather than manually installing VMWare.

Thanks, what exactly do you mean with 'use an APT repository'?

---

### Post by bruno9779 on 2010-03-05
> **smeerbartje said:**
> Thanks, what exactly do you mean with 'use an APT repository'?

He means that if you install binaries, of from source, some updates will break your installation. If you install from a repository, then the upgrade shouldn't break anything.

I have found this old link, you may want to have a look:

[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

---

