---
title: "windows xp"
date: 2016-12-05
forum: Windows
---

### Post by pete1977x on 2016-12-05
I use Xubuntu. I wanted to try and install Windows XP on the side so I put the CD(with product key) in my cd tray and did the F12 thing and tried to boot up from the CD drive. After a few seconds
it just booted Xubuntu. I thought it would ask me to install XP and then ask for the product key etc. But it didnt do anything except boot Ubuntu.
Why didnt it boot XP??

---

### Post by ian-weisser on 2016-12-05
Did you tell your system's BIOS to boot from the CD drive?

Er, you do realize that XP will promptly overwrite Xubuntu and all your data?

---

### Post by DuckHook on 2016-12-05
You also realize that XP is long dead, unsupported, a malware black hole, and a disaster waiting to happen?

It is difficult to help in general with little to no information, like HW specs for example. For the kind of info that would be useful, please look at the link in my sig: *How to Ask for Help*

---

### Post by ajgreeny on 2016-12-05
You could also be using a UEFI mode which is a non-starter for XP, I believe.

Try using a virtual machine if you have resources that will allow you to do so; I run XP-SP3 as a VM in VirtualBox very successfully for one specific job, ie updating my TomTom SatNav, so it is essential that I can get onto the web to do that. 

A VM, however, also gives the added advantage that I can keep a snapshot of a known clean version, so should my XP become corrupted by virus or malware, I simply start next time with the clean snapshot.

---

### Post by pete1977x on 2016-12-05
Is Virtual Box a pay thing online???? Could I use it for Nexus Root Toolkit??

---

### Post by ian-weisser on 2016-12-05
Sometimes and No.

---

### Post by DuckHook on 2016-12-05
@OP

*ian's* response is pithy and gets to the heart of the matter, but perhaps you might appreciate a broader overview:

As in anything in life, there is no magic bullet. VMs are amazing things, but they are not pixie dust and magic wands.

In your case, the idea behind a VM would be that you run Windows inside a box within Linux. This means that you have to install some legal version of Windows into the VM after you install Ubuntu. *ajgreeny*'s point is that XP would be less dangerous within a VM than as a standalone install (say, configured as a dual boot) because one of the advantages of a VM is that it allows one to revert to an earlier pristine snapshot of the OS, thus nuking whatever malware may have infected the OS through use and exposure to the big bad Internet. But, no, a VM by itself is incapable of running Nexus Root Toolkit. It needs Windows.

VirtualBox is free for personal use. It is also free even for commercial use in its basic form. However, commercial use of its more advanced features requires payment.

You may wish to read up further on the nature, usage and nuances of VMs and especially VirtualBox with the following:

[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
[https://help.ubuntu.com/community/VirtualMachines](https://help.ubuntu.com/community/VirtualMachines)
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

