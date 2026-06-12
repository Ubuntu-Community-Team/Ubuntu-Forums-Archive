---
title: "SecureBoot UEFI with Windows 8 and Grub 2"
date: 2013-07-08
forum: Ubuntu Development Version
---

### Post by EricKit on 2013-07-08
I'm not sure if this is the proper Forum for this, chose Ubuntu + 1 since I am running 13.10... but the question is mostly GRUB related.

I am dual booting Windows 8 and Ubuntu 13.10 with CSM On, UEFI On, and Secure Boot off.  I want to turn Secure Boot on.

With SecureBoot off:

I can boot to GRUB and launch Ubuntun 13.10
I can boot to GRUB and launch Windows 8

With SecureBoot on:

I can boot to Grub and launch Ubuntu 13.10
I can hit enter while booting to bring up boot options, F12 to pick a boot drive, and pick the Windows 8 OS.  It boots just fine.  If I wait for GRUB to launch, then pick any of the Windows 8 files it detected, it will not boot with Secure Boot (Just goes back to GRUB).  

Any ideas on how to get GRUB to work with Secure boot with this set-up?

Let me know what other information you need.  Thank you.
I have a Lenovo Twist, the boot file has it's own partition of 250MB with a mountpoint of /boot and EXT2.

---

### Post by oldfred on 2013-07-08
Best to see details. CSM and UEFI are different ways to boot. CSM or compatibility support module is really the old BIOS or legacy boot mode. Most systems cannot have both UEFI and CSM on at same time, but that may allow booting in either mode depending on what UEFI booting sees on hard drive. Or if efi partition found or MBR  found. 

Ubuntu can boot in any of three modes, BIOS/CSM/Legacy, UEFI, or UEFI with secure boot. But each requires different versions of grub. You use grub-pc with BIOS and grub-efi with UEFI. If secure boot grub adds a shim file with the Microsoft signing key and signed versions of the kernel are then also installed.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by EricKit on 2013-07-10
Nevermind, looks like a known bug.  Reference this [link]("http://falstaff.agner.ch/2012/12/18/ubuntu-12-10-and-windows-8-with-secure-boot-mode/") for more details.  Bug [#1091464]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464").

---

