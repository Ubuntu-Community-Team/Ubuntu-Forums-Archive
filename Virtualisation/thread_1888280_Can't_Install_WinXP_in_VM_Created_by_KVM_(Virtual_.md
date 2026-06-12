---
title: "Can't Install WinXP in VM Created by KVM (Virtual Machine Manager)"
date: 2011-11-28
forum: Virtualisation
---

### Post by ganymede7 on 2011-11-28
[SIZE=3]Used KVM to create virtual machine in Ubuntu 10.04.  All goes well until very last step for installing XP.  I then get an error message as follows: 
[I]     Booting from CD-Rom
     Boot failed:could not read from CDROM (Code 0003)
     No bootable device

[/I]The CD-ROM was chosen in the boot options as the boot device.  I thought at first that perhaps the Win XP install disk was bad, though unlikely.  I created a brand new boot disk for Linux Mint, booted to a live session.  The OS installed without incident and things ran just fine.  So I go back to virtual machine manager and create a virtual machine for Linux Mint.  Same error message as with XP.  Does anyone have an idea why the software isn't reading the install disc?   I suppose I could do the install from and ISO file.   How do I delete the two virtual machines that I've created?

Yes, I checked to make sure that my CPU supports hardware virtualization.  And I am a member of the KVM group and the *libvirtd *group.  Would really appreciated some help with this.
[/SIZE]

---

### Post by buntudawg on 2011-11-29
Hi.

It isn't clear to me from your post if you have actually added the CD/DVD drive to your VM Guest?

If not, there should be options along the lines (I'm a bit fuzzy) of

Add Hardware -> Storage

---

### Post by BC59 on 2011-11-29
You can create an image .iso from your WinXP CD and try to mount it from KVM.

```
dd if=/dev/cdrom of=WinXP.iso
``` then try to find the WinXP.iso in the temp folder.


I don't know why you have to use KVM. I use always VirtualBox and never had problems.

---

