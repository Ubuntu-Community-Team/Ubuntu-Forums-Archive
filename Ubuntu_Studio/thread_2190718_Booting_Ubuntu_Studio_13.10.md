---
title: "Booting Ubuntu Studio 13.10"
date: 2013-11-28
forum: Ubuntu Studio
---

### Post by dexfos on 2013-11-28
Installed Ubuntu Studio 13.10 (64-bt) on my system. When booting the only thing that shows up is a grub prompt "grub>". Seems like grub did not install properly. The content of the grub.cfg file is:

search.fs_uuid 15bd9413-dde1-4782-a844-e861c26979e1 root hd0,gpt4  
set prefix=($root)/boot/grub
configfile $prefix/grub.cfg

Any suggestions as to how to fix this problem?

TIA!

---

### Post by jejeman on 2013-11-28
Use the Live CD and reinstal GRUB.

---

### Post by dexfos on 2013-11-28
> **jejeman said:**
> Use the Live CD and reinstal GRUB.

Thanks jejeman, but I don't know how to install GRUB2, don't know its internals, and am doing my best to forget GRUB Legacy. I installed UbuntuStudio 13.10 on a 64-bit UEFI desktop. With UEFI, GRUB2 is unnecessary - all that is needed is the shim (if secure boot is enabled) and a kernel with the EFI stub compiled in. Turns out the EFI stub is compiled in the kernel used in 13.10. When I installed the system I selected the "Something Else" button in the "Installation Type" dialog so that I could choose partitions manually. I the past this has not been a problem (13.04), for 13.10 it is, as the installer does not create a valid grub.cfg in the EFI partition. I would call this an installer bug, probably already reported.

For anyone else who gets hosed by this the solution is simple, just boot directly to the kernel since the kernel is built with the EFI boot stub. Google "EFI boot stub" for details, it is a simple process. The down side is that when the kernel is updated you have to manually move the new kernel to the EFI partition and fixup the command line params if they change. PITA! Sometime in the next century or two the distros will figure out that GRUB2 is totally unnecessary relic on a UEFI platform...maybe...

---

### Post by fantab on 2013-11-29
Reinstall Ubuntu Studio or
Try these: [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

### Post by dexfos on 2013-11-29
> **fantab said:**
> Reinstall Ubuntu Studio or
Try these: [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

Multiple clean reinstalls were done before posting with the same result. The installer does not write the correct grub.cfg when manually selecting the installation partitions. Been using Studio for a few years, always manually configuring partitions with no problem until 13.10.

Thanks for the link to reinstall grub. As long as the kernel is compiled with the EFI boot stub, I'll just stick with kernel booting - I'm interested in running Linux, not the arcane and outdated GRUB2 which is a complete oxymoron on UEFI BIOS systems.

---

### Post by fantab on 2013-11-29
Post details of your machine's hardware, like RAM, CPU, Graphics etc...
Can you boot with live DVD/USB and post the output of:

```
sudo parted -l
sudo fidisk -l
```

Also go through this [Documentation]("https://help.ubuntu.com/community/UEFI") and [**Post**]("http://ubuntuforums.org/showthread.php?t=2147295&p=12657352#post12657352").

---

### Post by chkneater on 2013-12-01
[http://ubuntuforums.org/showthread.php?t=1769482&highlight=grub+restore](http://ubuntuforums.org/showthread.php?t=1769482&highlight=grub+restore)

This thread shows how to install a graphical tool that will fix your grub probs.

---

