---
title: "Cant open Virtualbox machines"
date: 2017-10-25
forum: Virtualisation
---

### Post by linuxyogi on 2017-10-25
When I try to open a 64Bit vbox machine I get this 

```
Failed to open a session for the virtual machine openbsd.

VT-x is disabled in the BIOS for all CPU modes (VERR_VMX_MSR_ALL_VMX_DISABLED).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: ConsoleWrap
Interface: IConsole {872da645-4a9b-1727-bee2-5585105b9eed}


```

Where exactly in UEFI/Bios can I find this option ?

Using Asus H110 motherboard.

Does my CPU  support this feature ? How to check ?

---

### Post by linuxyogi on 2017-10-25
Found it in UEFI as Intel Virtualization technology. Sorry for the confusion.

---

### Post by TheFu on 2017-10-25
64-bit VMs require vt-x or amd-v support.  Not all CPUs or BIOS support these.  Look in the manual for the motherboard and look on the CPU vendor website (or google it) for the CPU virtualization support.  Very low end CPUs often do not have this ability.

There is also a command - **kvm-ok** - run that.

```
$ kvm-ok 
INFO: /dev/kvm exists
KVM acceleration can be used

```

But if you are using virtualbox, that command probably cannot/should not be loaded.  Having multiple hypervisors on a system is a not-so-good idea. They can conflict.

[https://www.howtogeek.com/213795/how-to-enable-intel-vt-x-in-your-computers-bios-or-uefi-firmware/](https://www.howtogeek.com/213795/how-to-enable-intel-vt-x-in-your-computers-bios-or-uefi-firmware/) is another how-to.


So ... SOLVED?   Please mark the thread as solved.

---

### Post by linuxyogi on 2017-10-25
@[**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685") 

I have enabled vt-x in bios/uefi. Installing OpenBSD 64Bit atm.

Thanks.

---

