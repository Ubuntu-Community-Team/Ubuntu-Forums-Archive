---
title: "Ubuntu 16.10 Virtualization"
date: 2016-10-15
forum: Virtualisation
---

### Post by theshady1 on 2016-10-15
Trying to run 16.10 in a VM. I have downloaded 16.10 x64 and have tried to run it with both VMWare Workstation and VirtualBox. I am able to install the OS on VMware and Virtualbox,after successful install the OS fails to boot. VMWare spits out and error message:The CPU has been disabled by the guest operating system. Power off or rest the virtual machine. and Oracle: Fatal! Could not read from the boot medium.System halted.
I have several virtual machines setup/configured on my machine (under VMWare)and all seem to run perfectly fine. Several are other Ubuntu machines. Trying to find out why 16.10 wont run. Please advise.

---

### Post by rbmorse on 2016-10-17
Can't help except to say I see exactly the same problem here.  16.4 Gnome works fine on the same hardware/VMware Workstation 12.5 installation.

---

### Post by vipex2 on 2016-10-18
Here the same problem, I've found a workaround that I've posted here:
[https://answers.launchpad.net/ubuntu/+question/402993](https://answers.launchpad.net/ubuntu/+question/402993)

Anyway the OS remain laggy and unstable.

---

### Post by theshady1 on 2016-10-26
This is just very odd. I have run nearly every version of Ubuntu since 12.04 (out of the box)in a VM without any issue. Any plans for some sort of update to resolve this? Looks like many others are now seeing the same issue.

---

### Post by T.J. on 2016-10-26
I can't give you a specific solution because I do not have enough information.  VmWare is very version specific in what support they offer for guests. Unless they say they support 16.10 with your version of Vmware, I simply advise that you do not use 16.10.   According to what I have read on the subject, Vmware will shut down virtual processors when it hits an instruction to the virtual processor that it does not support; which means you will probably continue to encounter problems until Vmware officially supports Ubuntu 16.10. 

 My final solution to these kinds of support problems was to migrate over to KVM, because KVM is supported by the same community that works on the Linux kernel. I'm glad I switched, and I'll never go back.

---

### Post by theshady1 on 2016-10-28
I did attempt with VBox as well to make sure that its not just VMware with the issue. KVM? I dont follow.

---

### Post by T.J. on 2016-10-28
> **theshady1 said:**
> I did attempt with VBox as well to make sure that its not just VMware with the issue. KVM? I dont follow.


Kvm is yet another virtualization solution supported directly in the Linux kernel.  Itconsists of qemu (provided by the Qemu project) &#8211; which is a  hardware emulator; and a set of kernel modules (from the Linux kernel project) to provide paravirtualization support. If you are running Linux, you can pretty much use it.  It has several advantages over Vmware or VirtualBox.  Since it is completely open and maintained by the Linux kernel and the Qemu project, new versions are always supported by Canonical/Ubuntu.  It can do things that Vmware and VirtualBox can't &#8211; such as provide support for operating systems that use ARM and other processor types.  It can do just about everything that Vmware can, including PCI passthrough.  RedHat, Canonical and a few others provide commercial support for it.

It has a similar design to Vmware and definitely better than VirtualBox.  I'd say that it performs better than both, especially in terms of time spent &#8211; but that is my opinion.

I use it to host Windows 7 with full DirectX support using a second video card for passthrough &#8211; in other words, Windows programming and gaming.  For what I do, KVM is a perfect replacement for Vmware's Workstation.  I refuse to use either Oracle's VirtualBox or Vmware Server or Workstation ever again.  KVM has saved me massive headaches over the other two.

Here is an example of someone using KVM to run Windows with full DX support.  I believe they are playing Battlefield 4 on the left monitor.  My setup is quite similar.

[https://www.youtube.com/watch?v=N9QwDmYBRgg](https://www.youtube.com/watch?v=N9QwDmYBRgg)

---

### Post by kevdog on 2016-10-29
What's your host operating machine?  Did you try 16.04?  I just installed Ubuntu 16.04 within Vbox this week and the installation was pretty smooth with a Mac El Capitan host.

---

### Post by T.J. on 2016-10-29
> **kevdog said:**
> What's your host operating machine?  Did you try 16.04?  I just installed Ubuntu 16.04 within Vbox this week and the installation was pretty smooth with a Mac El Capitan host.

On the off chance you are asking me, I use a personally modified version of Debian 8.  I love the Ubuntu community, but I have always found Ubuntu itself to be a bit too unstable and under-maintained for my own use.  I'd think you would be stuck with VirtualBox or Parallels on a Mac.

---

### Post by theshady1 on 2016-11-10
> **kevdog said:**
> What's your host operating machine?  Did you try 16.04?  I just installed Ubuntu 16.04 within Vbox this week and the installation was pretty smooth with a Mac El Capitan host.

W10 x64. 16.04 runs fine (both desktop and server variants). This is why it seems to be an issue with 16.10. As stated prior, I have run every Ubuntu release in a VM since 12.04 without any issue.
Might just stick with 16.04 and await 17.04 release.

---

### Post by theshady1 on 2016-12-02
It appears that the issue has now been resolved. There is an updated kernel 4.8.0-28.30 that addresses this issue. I was able to get 16.10 up and running with the latest version of Vbox (as of this posting). I was able to find a bug report that addresses this issue further in much detail as found here:[https://bugs.launchpad.net/ubuntu/yakkety/+source/linux/+bug/1630774/comments/11](https://bugs.launchpad.net/ubuntu/yakkety/+source/linux/+bug/1630774/comments/11)

---

