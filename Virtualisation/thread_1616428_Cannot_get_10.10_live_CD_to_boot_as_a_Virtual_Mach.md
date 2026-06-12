---
title: "Cannot get 10.10 live CD to boot as a Virtual Machine"
date: 2010-11-08
forum: Virtualisation
---

### Post by The Foz on 2010-11-08
I have KVM (Kernel-Based Virtual Machine) installed on my main system, which is currently running 9.04. I use it extensively for running various VMs (Virtual Machines): an Ubuntu database and web-server, some Windows-XP VMs, and for trying out new releases and new packages. 

I recently downloaded both the 32 bit and 64 bit Desktop versions of Ubuntu 10.10, Neither of the live CDs will boot completely as a VM.

The CDs are both fine. I can boot a real physical PC with either disc.

Unfortunately, when I try to boot a VM using either version, they hang partway through the boot process (after the splash screen has been displayed, and them hidden again). It doesn't matter how long I wait; nothing happens. After a few minutes the optical disc drive goes idle, and there are no CPU cycles being used by the VM.

Does anyone have any idea why this is happening?

---

### Post by dcstar on 2010-11-11
> **The Foz said:**
> I have KVM (Kernel-Based Virtual Machine) installed on my main system, which is currently running 9.04. I use it extensively for running various VMs (Virtual Machines): an Ubuntu database and web-server, some Windows-XP VMs, and for trying out new releases and new packages. 

I recently downloaded both the 32 bit and 64 bit Desktop versions of Ubuntu 10.10, Neither of the live CDs will boot completely as a VM.

The CDs are both fine. I can boot a real physical PC with either disc.

Unfortunately, when I try to boot a VM using either version, they hang partway through the boot process (after the splash screen has been displayed, and them hidden again). It doesn't matter how long I wait; nothing happens. After a few minutes the optical disc drive goes idle, and there are no CPU cycles being used by the VM.

Does anyone have any idea why this is happening?

In a lot of VM environments only the latest versions are 10.10 compatible, you are using 9.04 and the KVM version with that may well not be 10.10 compatible.

---

### Post by The Foz on 2010-11-11
Hi David,

Thanks for the information.

Obviously, this situation is not ideal, as it undermines the ability to test a new O/S version before installing or upgrading.

I have anyway just upgraded my main system to 9.10 (9.04 support just ended), and I will try it again. Eventually I will upgrade to 10.something-or-other, but I am nervous as I had some problems with 10.04 on my laptop (had to re-install 9.10 to get it to work).

Regards,
David (yes, another David!)

---

### Post by dcstar on 2010-11-13
> **The Foz said:**
> Hi David,

Thanks for the information.

Obviously, this situation is not ideal, as it undermines the ability to test a new O/S version before installing or upgrading.
..........

Go to the KVM site and see what version supports 10.10 clients. When 10.10 first came out my VMware Player 3 version did not yet support it, I had to wait until VMware released a later version that did fully support 10.10 and now it is ok.

---

