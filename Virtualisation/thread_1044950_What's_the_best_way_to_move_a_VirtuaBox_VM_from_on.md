---
title: "What's the best way to move a VirtuaBox VM from one PC to another?"
date: 2009-01-19
forum: Virtualisation
---

### Post by diablo75 on 2009-01-19
I am wanting to move a VM that contains Windows XP from one PC running Ubuntu to another Ubuntu PC, both of which have the latest version of Virtualbox installed.  How should this be done?

---

### Post by jrusso2 on 2009-01-20
Why not just copy the operating system images and reinstall virtual box on that other PC?

---

### Post by thomasr on 2009-01-20
Just copying a virtualbox .vdi almost always results in a corrupted file for me aas does vbox clone command. The best way I have found is to zip it and copy the zipped file and then unzip it.

---

### Post by HotShotDJ on 2009-01-20
> **thomasr said:**
> Just copying a virtualbox .vdi almost always results in a corrupted file for me aas does vbox clone command. The best way I have found is to zip it and copy the zipped file and then unzip it.I've not had that experience.  I simply drag the .vdi file to a USB hard drive, then drag the .vdi file onto the new hard drive.  It has worked every time for me.

---

### Post by Ein2015 on 2009-01-21
Perhaps get an MD5 sum and do checks before and after transfer?

But basically transfer the .vdi file just like you would a text document.  :)

---

### Post by diablo75 on 2009-03-08
Unfortunately when I tried to do this (twice now, ensuring that the source vdi was from a machine that was "Powered Off"), I got the attached error message while Windows booted up.  The error does not occur when booting up into safemode.  Any suggestions?

---

### Post by albandy on 2009-03-08
VirtualBox version should be the same in both machines and disk image size should be fixed.

clone your vdi file with VBoxManage

---

### Post by diablo75 on 2009-03-08
Cool, I'll try using VBoxManage to clone the vdi.  It is a dynamic volume so hopefully that doesn't cause a problem.  Thanks for the help!

---

### Post by diablo75 on 2009-03-10
I tried to use VBoxManage as instructed above, and got the following problems right off the bat (username has been changed)

```
user@hostname:~/.VirtualBox/VDI$ VBoxManage clonevdi ./XP\ 101.vdi ~/XP101backup.vdi
VirtualBox Command Line Management Interface Version 2.1.4
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

[!] FAILED calling a->virtualBox->OpenHardDisk2(src, srcDisk.asOutParam()) at line 369!
[!] Primary RC  = VBOX_E_IPRT_ERROR (0x80BB0005) - Runtime subsystem error
[!] Full error info present: true , basic error info present: true 
[!] Result Code = VBOX_E_IPRT_ERROR (0x80BB0005) - Runtime subsystem error
[!] Text        = Could not get the storage format of the hard disk '/home/user/.VirtualBox/XP 101.vdi' (VERR_FILE_NOT_FOUND)
[!] Component   = HardDisk2, Interface: IHardDisk2, {ed6e2525-c2fd-42a4-917a-7a9045ac9e15}
[!] Callee      = IVirtualBox, {339abca2-f47a-4302-87f5-7bc324e6bbde}

```

This was on a virtual machine running XP that had been completely shut down via the start menu... so it wasn't running in other words.  I'm not sure what to make out of the above output.  Any ideas?

---

### Post by albandy on 2009-03-11
> **diablo75 said:**
> I tried to use VBoxManage as instructed above, and got the following problems right off the bat (username has been changed)

```
user@hostname:~/.VirtualBox/VDI$ VBoxManage clonevdi ./XP\ 101.vdi ~/XP101backup.vdi
VirtualBox Command Line Management Interface Version 2.1.4
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

[!] FAILED calling a->virtualBox->OpenHardDisk2(src, srcDisk.asOutParam()) at line 369!
[!] Primary RC  = VBOX_E_IPRT_ERROR (0x80BB0005) - Runtime subsystem error
[!] Full error info present: true , basic error info present: true 
[!] Result Code = VBOX_E_IPRT_ERROR (0x80BB0005) - Runtime subsystem error
[!] Text        = Could not get the storage format of the hard disk '/home/user/.VirtualBox/XP 101.vdi' (VERR_FILE_NOT_FOUND)
[!] Component   = HardDisk2, Interface: IHardDisk2, {ed6e2525-c2fd-42a4-917a-7a9045ac9e15}
[!] Callee      = IVirtualBox, {339abca2-f47a-4302-87f5-7bc324e6bbde}

```

This was on a virtual machine running XP that had been completely shut down via the start menu... so it wasn't running in other words.  I'm not sure what to make out of the above output.  Any ideas?

I think you're not in the correct folder:
Virtualbox says that can't found /home/user/.VirtualBox/XP 101.vdi and as I read in your command-line you are using ~/.VirtualBox/VDI

---

### Post by diablo75 on 2009-03-11
> **albandy said:**
> I think you're not in the correct folder:
Virtualbox says that can't found /home/user/.VirtualBox/XP 101.vdi and as I read in your command-line you are using ~/.VirtualBox/VDI

Hmmm... I know I was in the right folder... perhaps it's because that vdi filename has a space in it, and I had to use tab-completion to figure out how to type it in properly (to keep Bash happy).

I'll remove the space and give it another shot sometime later today.

---

### Post by gene_x on 2009-03-20
same error here.

I works after I use the full path to files:

[email]user@server:~/.Virtua[/email]lBox/VDI$ VBoxManage clonevdi ~/.VirtualBox/VDI/winxp.vdi ~/.VirtualBox/VDI/winxp2.vdi

---

### Post by ggeldenhuys on 2009-05-21
> **diablo75 said:**
> I tried to use VBoxManage as instructed above, and got the following problems right off the bat

There is a regression bug in VirtualBox 2.1.x. For the clone command to work, you need to specify the full path (from the root of your harddrive) to the source VDI file. That will solve your problem. I experienced this same issue 30 minutes ago under Linux.

---

