---
title: "Meaning of Secure Boot if I can boot Debian with it?"
date: 2015-06-12
forum: The Cafe
---

### Post by kagashe on 2015-06-12
I installed Debian 8.1 on one partition and while installing I disabled the Secure Boot. I could reboot with Debian's Boot Loader only with Secure Boot disabled.

While updating Ubuntu 15.04 I got kernel update and its Boot Loader picked up the entry of Debian installation.

Now I can boot Debian from Ubuntu Boot Loader with Secure Boot on.

It means that Secure Boot is only for the Grub Boot Loader provided by Ubuntu.

Kamalakar

---

### Post by sudodus on 2015-06-12
If I understand it correctly, there is a 'licensed' file provided by Ubuntu, that allows further booting (into whatever you point to with grub).

---

### Post by Copper Bezel on 2015-06-12
Oh ... wow, really? That's handy. I thought Secure Boot required a signed kernel.

---

### Post by oldfred on 2015-06-12
It also was my understanding that kernel also had to be signed. But I see some installs with both kernels. So maybe Debian had both but you were booting with grub not shim(signed grub) and then signed grub from Ubuntu's os-prober only picked up signed versions from Debian??

Just to see what versions are installed where.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by grahammechanical on 2015-06-12
This is the Ubuntu security team's explanation of how Ubuntu handles secure boot

[https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)
> 
In order to boot on the widest range of systems, Ubuntu uses the following chain of trust: 


[LIST=1]
[*]Microsoft  signs Canonical's 'shim' 1st stage bootloader with their 'Microsoft  Corporation UEFI CA'. When the system boots and Secure Boot is enabled,  firmware verifies that this 1st stage bootloader (from the 'shim-signed'  package) is signed with a key in DB (in this case 'Microsoft  Corporation UEFI CA') 
[*]The  second stage bootloader (grub-efi-amd64-signed) is signed with  Canonical's 'Canonical Ltd. Secure Boot Signing' key. The shim 1st stage  bootloader verifies that the 2nd stage grub2 bootloader is properly  signed. 
[*]The  2nd stage grub2 bootloader boots an Ubuntu kernel (as of 2012/11, if  the kernel (linux-signed) is signed with the 'Canonical Ltd. Secure Boot  Signing' key, then grub2 will boot the kernel which will in turn apply  quirks and call ExitBootServices. If the kernel is unsigned, grub2 will  call ExitBootServices before booting the unsigned kernel) 

[/LIST]


Note  the last sentence in section 3. So, with Ubuntu we get a signed first  stage Grub boot loader and a signed second stage Grub boot loader as  well as a signed kernel. I think on your system the Ubuntu Grub is  loading an unsigned Debian Linux kernel because the Ubuntu developers  did not include a lockout in the second stage Grub boot loader.

> before booting the unsigned kernel

> **IMPORTANT:** Canonical's Secure Boot implementation is  primarily about hardware-enablement and this page focuses on how to test  Secure Boot for common hardware-enablement configurations, not for  enabling Secure Boot to harden your system. If you want to use Secure  Boot as a security mechanism, an appropriate solution would be to use  your own keys (optionally enrolling additional keys, see above) and  update the bootloader to prohibit booting an unsigned kernel. Future  releases of Ubuntu may make this easier.

Regards.

---

### Post by sudodus on 2015-06-12
With ***secure boot turned off*** I can even boot Ubuntu 12.04 LTS in UEFI mode (the original one, not 12.04.2) via grub and iso, according to these links

Post #7. [Multiboot pendrive system for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302264#post13302264")

Post #8. [Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302278#post13302278")

I just checked that it really works in my Toshiba laptop.

It booted and is running now from **ubuntu-12.04-desktop-i386.iso** with the kernel 3.2.0-23-generic-pae.

-o-

But when ***secure boot is turned on***, this grub and iso system does not even reach the grub menu, instead there is a message 'Boot failure: a proper digital signature was not found ...'

I can boot Ubuntu from a pendrive cloned from **ubuntu-14.04.2-desktop-amd64.iso** with secure boot. So obviously there is checking in my computer. Thanks oldfred and grahammechanical      for the details about secure boot, how it might allow booting a kernel without signature and why :-)
                        
> Canonical's Secure Boot implementation is  primarily about  hardware-enablement ... not for  enabling Secure  Boot to harden your system.

---

### Post by Copper Bezel on 2015-06-12
Ehh. So having Secure Boot enabled in Ubuntu ... isn't actually really a secure boot. 

Bummer. I don't think I want to go through the steps involved in, like, rebuilding grub to use it properly. = /

---

### Post by kagashe on 2015-06-13
> **grahammechanical said:**
> This is the Ubuntu security team's explanation of how Ubuntu handles secure boot

[https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)

Note  the last sentence in section 3. So, with Ubuntu we get a signed first  stage Grub boot loader and a signed second stage Grub boot loader as  well as a signed kernel. I think on your system the Ubuntu Grub is  loading an unsigned Debian Linux kernel because the Ubuntu developers  did not include a lockout in the second stage Grub boot loader.

Regards.Thanks for the explanation. Before installing Debian I was wondering I had to disable Secure Boot permanently but thanks to Ubuntu I don't have to.

Kamalakar

---

### Post by kagashe on 2015-06-13
> **Copper Bezel said:**
> Ehh. So having Secure Boot enabled in Ubuntu ... isn't actually really a secure boot. 

Bummer. I don't think I want to go through the steps involved in, like, rebuilding grub to use it properly. = /It is Secure Boot if you are using Ubuntu. For distro-hoppers it is not. But there is an option for me to use my own keys to sign the Debian kernel. For those who are interested:
[Managing EFI Boot Loaders for Linux: Dealing with Secure Boot]("http://www.rodsbooks.com/efi-bootloaders/secureboot.html")

On [Archlinux people are doing it]("https://bbs.archlinux.org/viewtopic.php?id=191056").

Kamalakar

---

### Post by Copper Bezel on 2015-06-13
Fair enough. Thanks for the info. = ]

---

### Post by kagashe on 2015-06-14
> **oldfred said:**
> It also was my understanding that kernel also had to be signed. But I see some installs with both kernels. So maybe Debian had both but you were booting with grub not shim(signed grub) and then signed grub from Ubuntu's os-prober only picked up signed versionDebian does not have signed version of kernel, not even grub.

Kamalakar

---

