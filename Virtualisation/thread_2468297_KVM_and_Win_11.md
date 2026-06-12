---
title: "KVM and Win 11"
date: 2021-10-24
forum: Virtualisation
---

### Post by MAFoElffen on 2021-10-24
Someone tried telling me they were having troubles installing Windows 11 retail as a Virtual Machine...

That the install looked at hardare, so with hardware locks on TPM 2.0, and a minimum CPU requirement, that trying to run it on a Virtual Host that doesn't meet those requirements, was not possible, because the Virtual Host can only show through what capabilities it has... and that things could not be emulated, nor visualized for that to happen...

Well, here dispels the myth of that:

See attached screenshot

```

Device Name    WIN11-VM01
Processor         Intel Xeon E3112xx (sandy Bridge, IBRS update)  2.39 GHz (2 processors)
Product ID        00330-80000-00000-AA12EB8705EA7
System Type 64-bit operating system, x64-based processor
Pen or touch input is not available for this display

Edition Windows 11 Pro
Version 21H2
Installed on     10/24/2021
OS build          22000.194
Experience       Windows Feature Experience Pack 1000.22000.192.0

```
And the VIrt Host I did it on:
```

Host Device: Lenovo Thinkpad T520 type 4242
Host CPU: Intel® Core&#8482; i7-2760QM CPU @ 2.40GHz × 8 
Hardware TPM: 
mafoelffen@Mikes-ThinkPad-T520:~$ dmesg | grep -i tpm
[    0.478370] tpm_tis 00:05: 1.2 TPM (device-id 0x0, rev-id 78)
mafoelffen@Mikes-ThinkPad-T520:~$ [ -d $(ls -d /sys/kernel/security/tpm* 2>/dev/null | head -1) ] && \ echo "TPM available" || echo "TPM missing"
TPM available
mafoelffen@Mikes-ThinkPad-T520:~$ kvm --version
QEMU emulator version 4.2.1 (Debian 1:4.2-3ubuntu6.18)
Copyright (c) 2003-2019 Fabrice Bellard and the QEMU Project developers

```

In KVM, for the VM Guest, I am using UEFI w/ SecureBoot, and added a vTPM, before install... There are still a few tricks, but I did not touch the ISO file at all, except to use it through a certain manner.

Packages swtpm and swtpm-utils just got approval in Debian as a package last night... Code to it was updated 6 days ago, for the Debian Packaging. I am still running off the code from 6 months ago and it is running fine.

Here you go to those who have not embraced KVM. The friend who challenged me to this, is now "trying to do this same in ESXi on his below M$ required hardware Host... LOL

---

### Post by MAFoElffen on 2021-11-09
I know I posted this, but the Updates, two days ago were hard on this solution...

2 out of three machines ended up with broken apt systems because of updates. My KVM server was broken by swtpm and swtpm-tools, with unresolved dependency issues. Reconfiguring dpkg and trying to use apt to fix broken packages were unsuccessful. using apt to install/reinstall the two packages failed.

What did work was to remove/purge the two packages... Fix the apt system to finish the system updates. Then later install swtpm and swtpm-tools fresh and clean.

I recommended it indirectly, then it came up with this issue. I thought I better add this, for the just in cases of someone who had read the previous post.

---

