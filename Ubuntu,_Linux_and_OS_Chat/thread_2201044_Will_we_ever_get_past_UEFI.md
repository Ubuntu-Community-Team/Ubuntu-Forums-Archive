---
title: "Will we ever get past UEFI?"
date: 2014-01-22
forum: Ubuntu, Linux and OS Chat
---

### Post by xSCCMx on 2014-01-22
I'm not really asking for help but If I was to buy a new laptop, it would obviously have UEFI Secure Boot enabled. My question is will we ever be able to boot and install a Distro of our choice on our new laptops without special configuration in the UEFI settings?

---

### Post by oldos2er on 2014-01-22
Moved to Ubuntu, Linux & OS Chat.

---

### Post by oldfred on 2014-01-22
With secure boot you will always have to configure something.

But newest releases of grub2 & Linux kernels work on those systems that follow UEFI standards.

It just is some vendors do not follow UEFI standards and only boot Windows and major workaround then are required.

Even with BIOS, setting changes were often required for some systems.

 Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

---

### Post by buzzingrobot on 2014-01-22
Short answer: No.

UEFI, strictly as a modern replacement for the BIOS approach, is not a bad thing.

The "bad" showed up because it allows what MS calls Secure Boot. Checking to see if the boot process is being used as an attack vector is something that should be done. But, Microsoft's market position means its ordained implementation of secure booting is used by pretty much every vendor because Windows won't work otherwise. Hence, the inconvenience for Linux.

If you'll only be using Linux, look for a laptop that allows Secure Boot to be disabled.

---

### Post by oldfred on 2014-01-22
All standard 64 bit Windows will let you turn secure boot off as that is a Microsoft requirement. The issue is those vendors that modify UEFI to only boot Windows.

But now there is a new issue with some low cost systems. There are currently no Linux distributions with 32 bit UEFI.

 New Intel Atom - Nov 2013 x86 secure boot can be turned off, but only 32 bit UEFI which no one else has.
 Intel Atom SoC systems that ship with Windows 8/8.1 32-bit provide 32-bit UEFI-only firmware with no BIOS compatibility option (no CSM). In UEFI terms these systems are called Class 3 systems (this term is not specific to 32-bit), ie. UEFI-only with no BIOS CSM.
Windows with Atom 
[http://www.extremetech.com/computing/136276-intel-clover-trail-atom-chips-cannot-run-linux](http://www.extremetech.com/computing/136276-intel-clover-trail-atom-chips-cannot-run-linux)
W

---

### Post by The Cog on 2014-01-22
Is it possible to tell from a live CD/USB if a PC can boot linux. I'm guessing the answer is yes, but I'm wondering if it might make sense to walk into a store with a live USB and try on their display models.
What happens if secure boot doesn't like your boot code? Does it say anything on screen? Does it behave differently for USB boot and hard disk boot?

---

### Post by oldfred on 2014-01-22
Most new UEFI systems will boot Linux even with secure boot on as grub2's shim has the Microsoft signing key. 
I doubt that most stores would let you boot another system, as they would be afraid of modifications.

Some also require UEFI/BIOS settings to be changed. 

Often then the issues are Video drivers or with Ultrabooks how drive is formatted. Which would be or are the same issues with BIOS boot.

With my BIOS boot old system I have to have nomodeset or it just does not work. Similar issue with new systems if nVidia. And I have to change several default BIOS settings to have it work correctly.

---

### Post by 3rdalbum on 2014-01-23
> **oldfred said:**
> Most new UEFI systems will boot Linux even with secure boot on as grub2's shim has the Microsoft signing key.

You took the words right out of my mouth. I've installed Ubuntu on a PC with Secure Boot turned on. No dramas, it all worked as it should.

---

### Post by EnglishElectricAndy on 2014-01-23
While fiddling with UEFI specs is obviously a poor practice, what is most likely to cause dual-install issues is that wretched 'fast start-up' option buried deep in Windows 8 Control Panel>All Control Panel Items>Power Options>System Settings>Choose what the power button does. Enabled by default, it will trap the unwary user into believing a full shutdown has been accomplished when it hasn't.

---

### Post by The Cog on 2014-01-23
Thanks, oldfred and 3rdalbum. 
Actually, I have been known to just walk into a store and boot a USB stick on a display laptop before now, in order to run lshw. 
I resisted the temptation to install, or even to just leave Ubuntu running in RAM and walk away.

---

