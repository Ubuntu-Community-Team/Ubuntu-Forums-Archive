---
title: "Reinstalling Windows on Ubuntu"
date: 2014-01-31
forum: Windows
---

### Post by timpearce89 on 2014-01-31
On my laptop I currently have Ubuntu installed (which I installed via usb drive), however right now I have to reformat it back to windows for the time being until my machine gets fixed, luckily I already have a windows startup saved to another USB Drive!

The Issue:

Whenever I boot to the usb Drive to reinstall windows on the machine (or even to partition it) I get an error fairly quickly saying that "A required CD/DVD drive device driver is missing. If you have a driver floppy disk, CD, DVD or USB flash drive, please insert it now."

I used the Win7USB earlier today at work so I know that it is functioning normally, however when I try to update my drivers via Ubuntu it says everything is up to date and theres no more drivers needed. 

My question is that has anyone had this issue before? I know the CD drive works, I can get a Win7 Install Disk (but tomorrow is saturday and I REALLY don't want to drive to work and back for it) is there an easy fix or does anyone know what might be going wrong?

Any help will be greatly appreciated,

Thank You

---

### Post by oldfred on 2014-02-01
Windows will give all sorts of errors if it cannot see either a primary NTFS formatted partition with the boot flag to install into, or unallocated space with available primary partition(s). Default install of Windows 7 uses 2 primary partitions, one small 100MB boot and main install. But it will install to one NTFS partition.

Windows does not correctly see Linux partitions.

Is install a full install image and not an upgrade?

Did you boot in UEFI mode? Windows 7 needs updates to work with UEFI boot mode. 
And if Ubuntu is UEFI then drive is gpt partitioned and UEFI is only boot choice unless drive is totally erased.

---

