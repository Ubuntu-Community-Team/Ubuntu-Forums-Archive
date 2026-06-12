---
title: "Conflict with kernel module"
date: 2011-12-07
forum: Virtualisation
---

### Post by Brad wilkinson on 2011-12-07
I'm running a Phenom x6 with 8gig of RAM and Ubuntu 10.04LTS. AMD-v (or whatever it is called) is turned on.

So i took the advice from this thread [URL="http://ubuntuforums.org
/showthread.php?t=1686936"]_[COLOR="Blue"][64 bit] Virtualisation of WinXP[/COLOR]_[/URL] and un-installed the KVM/QEMU packages then installed the VirtualBox packages from the repos.

It all worked wonderfully. I created a new VM, installed winXP SP3, loaded my A/V software and downloaded all the updates (105) for windows without any problems. was very happy and went to bed thinking I could start getting in to all my old games that I cannot get to run in WINE/play-on-linux. I shut down the guest using the graceful shutdown in VirtualBox (no cold shutdown).

Then I rebooted the host machine.

Bad move apparently.

so now when I start a VM in VirtualBox, I get the folowing error message:

Failed to open a session for the virtual machine VirtualXP1.
AMD-V is being used by another hypervisor. (VERR_SVM_IN_USE).
VirtualBox can't enable the AMD-V extension. Please disable the KVM kernel extension, recompile your kernel and reboot (VERR_SVM_IN_USE).

So do I have to reinstall the kernel now?

I'm just using the latest kernel out of the repos - nothing funny at all.

and why did it work the first time I used it but now it's telling me there is a bit of the KVM package left in the kernel making things difficult?

---

### Post by Dedoimedo on 2011-12-07
Does this help you - it should:
[http://www.dedoimedo.com/computers/kvm-virtualbox.html](http://www.dedoimedo.com/computers/kvm-virtualbox.html)

Dedoimedo

---

### Post by Brad wilkinson on 2011-12-12
Yes, yes it does help.

Thank you very much.

---

