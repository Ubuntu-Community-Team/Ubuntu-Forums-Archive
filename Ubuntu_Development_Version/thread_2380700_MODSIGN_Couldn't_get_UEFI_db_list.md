---
title: "MODSIGN: Couldn't get UEFI db list"
date: 2017-12-20
forum: Ubuntu Development Version
---

### Post by calby on 2017-12-20
Hi,
I have installed Ubuntu and everything works as far as I can see, but I did get a error messages when I did reboot.
And I can find this in the log files.

Couldn't get size: 0x800000000000000e
MODSIGN: Couldn't get UEFI db list
Couldn't get size: 0x800000000000000e


I have a Lenovo Thinkpad T470s and I have disabled Secure boot in BIOS and I'm running UEFI only at the settings so "old" BIOS don't work, but I do have the Intel SGX on Software Controlled but I don't know if it's because of that?

Does someone know how to solve the issue?

---

### Post by oldos2er on 2017-12-20
Can you tell us which Ubuntu version you installed?

---

### Post by calby on 2017-12-20
Hi,
I did install Ubuntu 18.04.

It do looks like that this error message is appearing when I reboot the computer I can see it appear in the log files.

---

### Post by oldos2er on 2017-12-20
> **calby said:**
> I did install Ubuntu 18.04.

So moved to *Ubuntu Development Version*

---

### Post by corradoventu on 2017-12-21
[https://bugzilla.redhat.com/show_bug.cgi?id=1497559](https://bugzilla.redhat.com/show_bug.cgi?id=1497559)

---

### Post by steve233 on 2018-01-21
I am running Ubuntu Xenial 16.04.3 LTS with HWE. I began getting similar errors only after upgrading to kernel 4.13.0-26-generic. 

kernel: [    0.982630] Couldn't get size: 0x800000000000000e
kernel: [    0.982929] MODSIGN: Couldn't get UEFI db list
kernel: [    0.986380] Couldn't get size: 0x800000000000000e

The errors seem to be related to an attempt to import UEFI keys for Secure Boot.
I do not have Secure Boot enabled in my BIOS but do only boot in UEFI.
I have a SuperMicro board with American Megatrends BIOS Version 2.2
I was able to stop the errors simply by changing a setting in the BIOS from [Customized] to [Standard] for Secure Boot Mode.
The Customized setting allows you to modify the secure boot keys manually. The Standard just sets the default keys.
Note: This fixed my error even though I previously had Secure Boot [Disabled] in BIOS settings.

Security -> Secure Boot -> Secure Boot Mode -> [Standard]

Hope this can possibly help others.

---

### Post by danburgess on 2018-02-25
Steve!!! You're a lifesaver.  This worked.

Nice Job ;)

---

### Post by v-mishkovskyi on 2018-03-27
In my case the problem dissapired after I unplugged DVD-RW drive.

---

### Post by jcinpv on 2018-04-09
I'm having the same problem, but the hardware is a Mac Mini.
The bootable thumb drive (created in Ubuntu 16.04) works on one Mac Mini (newer) but not on another (older, cannot be upgraded to latest macOS - so I want to put Ubuntu on it. I've done this for an older MacBook Air).
That I know of, there's no way to access the boot rom.

---

### Post by spamless on 2018-04-16
I have discovered on my newly-set-up multiboot system that if I  install grub from one Linux but then I boot to a second Linux in the  menu list, I get the error message shown at the grub splash screen.  (However, Linux boots for me despite the error.) The error is not there  if I boot into the Linux from which I installed grub!

  I confirmed this: I re-installed grub from the second Linux. Now the  second Linux boots without the error, but the first Linux boots with the  error.
  So I could make make the error go away by reinstalling grub from the Linux that will boot first in the list by default.

---

### Post by agentk9 on 2018-09-30
Hey, I'm getting this same error. System Info: Macbook Pro 15" Late 2011 w/ i7, 8GB RAM, 500 GB SSD. Xubuntu 18.04. I'm trying to install xubuntu, but it won't boot into the installer, much less install the OS.

---

### Post by wildmanne39 on 2018-09-30
Hello and welcome to the forum agentk9, please start your own thread for support in the Apple Hardware sub-forum, 18.04 is no longer in development there for this thread is closed!

Thanks

---

