---
title: "Running a physical drive as a KVM and dual-boot"
date: 2012-02-28
forum: Virtualisation
---

### Post by solomonson on 2012-02-28
I have an install of Windows 7 on a separate hard drive from Ubuntu.  I want to boot into it from Ubuntu as a KVM.  I would rather not clone the drive and make it virtual.  I want to work with the physical drive and allow the possibility to continue to boot directly into Windows if needed.

I am able to add /dev/sdb as a drive to a KVM and I see the boot manager for Windows and the fancy four color logo spinning around.  Then, it blue screens and tries to reboot again.  Inserting a Windows disk and trying repair doesn't seem to help.  I installed all of the KVM Windows 7 signed drivers onto the Windows partition.

Has anyone been able to create a dual-use partition that can dual-boot and run as a KVM?

---

### Post by zeljkojagust on 2012-03-01
Windows 7 are currently installed with your on-board disk controller drivers and when you try to boot them in KVM the driver changes to one KVM if offering, and that's the reason of the blue screen. Unfortunately Windows do not have an option to use "generic" disk drivers option that can be selected during the install like Ubuntu has an that leads to your problem.

Although this is a very interesting topic and I will definitely look in to it. First thing I will try is to install a fresh Ubuntu on an LVM enabled disk than run a Windows installation trough KVM also using LVM and than will try to reboot the machine and boot Windows. Will let you know what was the outcome.

---

