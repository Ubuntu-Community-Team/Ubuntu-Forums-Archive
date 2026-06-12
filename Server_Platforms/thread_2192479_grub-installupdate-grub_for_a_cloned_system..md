---
title: "grub-install/update-grub for a cloned system."
date: 2013-12-08
forum: Server Platforms
---

### Post by DiagonalArg on 2013-12-08
Hey all, quick question.  I'm cloning a system (cp -ax from one raid mirror to a second), where the second system (but not the first) is on LVM over LUKS.  To install grub, do I have to do anything more than:

(1) Modify mdadm.com, crypttab and fstab and then (2) grub-install to both disks followed by update-grub?  Will grub automatically know about the LVM?

Thx
/DA

---

### Post by oldfred on 2013-12-09
You probably have to add the lvm2 driver.
I would think grub & kernels, then have to have the separate /boot partition outside of the encryption as that is what a standard install is. Grub may work with LVM, but if it is encrypted it cannot be inside it.

Grub remembers where to reinstall and that may be correct.
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by DiagonalArg on 2013-12-11
@oldFred - thanks for your input.  Yes, I understand that grub [edit: I mean /boot] will have to be outside of the LUKS container (on RAID).

I've been trying to learn grub/initramfs & understand the booting process (in outline at least, I'm not competent to understand it all).  I see that /boot/grub has an lvm.mod driver, which would allow core.img to access a logical volume (if necessary to get to /boot).  On the other hand, it seems that for the linux kernel to get to a lv, the script lvm2 must be present in /usr/share/initrafs-tools/hooks (not quite sure what that script does).  Is that right, or is there some way to use that lvm.mod driver?  Do you know?

---

