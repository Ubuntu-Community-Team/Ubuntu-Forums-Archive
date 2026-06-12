---
title: "Windows 7 won't boot after MBR change"
date: 2013-11-14
forum: Windows
---

### Post by jira.luis on 2013-11-14
I wanted to install Ubuntu on my new HP Pavilion dm6 and created a new partition with Windows. Windows made my new partition a virtual drive and this brings a lot of trouble with it how I now know. Anyways Ubuntu can't find the new partition and I look how I can get rid of it. Formatting my HDD wasn't an option so I got testdisk for Windows and added the virtual drive in the MBR.
Ubuntu can now find the partition and everything seems good, until I want to boot Windows again. I get a failure with a dialog that tells me to insert the Windowsdisc. So I insert the Windowsdisc and hope that I can fix my Windows, but it doesn't find anything to repair and is helpless.
I hope someone has an idea how to fix this.

Now I'm using Ubuntu 13.04 and I want to fix Windows 7.

Thank you already!

Sorry for my english

---

### Post by oldfred on 2013-11-14
Not sure what you mean by virtual drive for Windows?

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by jira.luis on 2013-11-14
This is a boot-info I created a week ago, is it ok? 
[http://paste.ubuntu.com/6302756/](http://paste.ubuntu.com/6302756/)

---

### Post by oldfred on 2013-11-14
Use gparted from Linux live installer and move boot flag back to sda1. That looks like a bootable Windows. That may let you boot Windows again.

I do not know why boot repair did not offer to install grub to MBR to boot Linux install on sda2.

The Linux NTFS driver is having all sorts of issues opening your sda3 NTFS partition. I doubt that is is RAID, but seems to need chkdsk at the minimum. You can only run chkdsk from Windows or from a Windows repairCD or flash drive.

---

