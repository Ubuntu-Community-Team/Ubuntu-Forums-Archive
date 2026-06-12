---
title: "Enable KVM on Ubuntu 14"
date: 2019-04-10
forum: Virtualisation
---

### Post by teck.lah on 2019-04-10
Hi,

I have installed Ubuntu 14 on VirtualBox, but cannot enable the KVM. I have followed the instruction on [https://www.howtoforge.com/tutorial/kvm-on-ubuntu-14.04/](https://www.howtoforge.com/tutorial/kvm-on-ubuntu-14.04/). The VirtualBox is running on a Windows 10 machine and Virtualization Technology is already enabled in the BIOS.

$ kvm-ok
INFO: Your CPU does not support KVM extensions
INFO: For more detailed results, you should run this as root
HINT:   sudo /usr/sbin/kvm-ok
$ sudo kvm-ok
INFO: Your CPU does not support KVM extensions
KVM acceleration can NOT be used

Any advice on how I can get KVM to work? Thanks.

---

### Post by wildmanne39 on 2019-04-11
*Thread moved to **Virtualisation a more appropriate sub-forum**.*

---

### Post by deadflowr on 2019-04-11
You would  need to enable nested virtualization:
[https://docs.oracle.com/cd/E97728_01/F12470/html/nested-virt-support.html]("https://docs.oracle.com/cd/E97728_01/F12470/html/nested-virt-support.html")
in order to run a virtual machine within another virtual machine with hardware support.

---

### Post by teck.lah on 2019-04-11
Are you referring to the "Enable Nested VT-x/AMD-V" in VirtualBox System > Processor setting? For some reasons, it is being grey out in my setting. Thanks for sharing.

[ATTACH=CONFIG]283002[/ATTACH]

---

### Post by TheFu on 2019-04-11
> **teck.lah said:**
>  
Any advice on how I can get KVM to work? Thanks.

Any advice?
Sure, 
Wipe Windows.  Install Ubuntu onto the physical hardware. Install qemu-kvm, virt-manager, libvirt-bin.  Probably want openssh-server and fail2ban on the host machine too.

You can install Win10 into a virtual machine running under KVM on Ubuntu.

It might seem drastic, but it is another option for consideration.

However, support for Ubuntu 14.04 ends shortly, this month, so it would be a terrible idea to use that release at this point.  Need to use either 18.04 or 16.04 instead.  I installed a fresh KVM host this week with 16.04. Support for it last until 2021, April.

[https://wiki.ubuntu.com/Kernel/Support](https://wiki.ubuntu.com/Kernel/Support) has the specific support for specific kernel versions of specific Ubuntu releases.  All 3 have to line up for a system to be supported.

If you have an Intel CPU, looks like nested VT-x isn't supported by virtualbox. [https://www.virtualbox.org/manual/UserManual.html#nested-virt](https://www.virtualbox.org/manual/UserManual.html#nested-virt)
> Oracle VM VirtualBox supports nested virtualization on host systems that run AMD CPUs.

[https://forums.virtualbox.org/viewtopic.php?f=1&t=90831](https://forums.virtualbox.org/viewtopic.php?f=1&t=90831) is a discussion for vbox v6.0.0.

---

