---
title: "HOWTO: Reinstall GRUB if you're using LVM"
date: 2009-12-06
forum: Tutorials
---

### Post by ThomasTC on 2009-12-06
Every time I reinstall Windows, it overwrites my boot sector, and I need to reinstall it from the Ubuntu live CD to recover my dual-boot system. However, since my Ubuntu install is inside an LVM partition, this is not very straightforward. Here's how to do it.

I'm assuming some experience with the command prompt, but since you're apparently running LVM, you're not a total beginner.

[list=1]
[*]Start from the Ubuntu CD and open a terminal.
[*]Install LVM:
```
sudo apt-get install lvm2
```
[*]Find the name of the volume group:
```
sudo vgdisplay
```
[*]Make the volume group available:
```
sudo vgchange -ay name-of-vg
```
[*]Mount the root and boot file systems, and bind the dev file system:
```
sudo mkdir foo
sudo mount /dev/name-of-vg/name-of-root-lv foo
sudo mount /dev/name-of-boot-partition foo/boot
sudo mount -obind /dev foo/dev
```
[*]Change to the root of your system:
```
sudo chroot foo
```
[*]Drop into the GRUB prompt:
```
sudo grub
```
[*]Install the GRUB MBR (assuming that (hd0) is your boot drive and (hd0,0) your boot partition):
```
root (hd0,0)
setup (hd0)
```
[*]Reboot and have your boot menu back!
[/list]

---

### Post by bwana on 2010-10-31
Re step 8:
root (hd0,0)
setup (hd0)

How can I find out where my boot/grub partition is in grub-speak ?
I've got 1 disk: /dev/sda
I've got 1 volume group on /dev/sda1: vg20
The volume group contains 3 logical volumes (active):
/dev/vg20/m_boot
/dev/vg20/m_root
/dev/vg20/m_swap
I can mount them without any issues (when using live cd)..

- My boot partition (containing grub) is /dev/vg20/m_boot
ls -la /dev/vg20/m_boot shows:
/dev/vg20/m_boot -> ../dm-0

I cant figure out what root (in grub) should be set to.
Any ideas ? (note: root (sd0,1), root (sd0,2) root (sd0,3) gives me "Error 23: Error while parsing number"

Any ideas ?

---

### Post by kahgfakhjsf on 2012-09-08
At the step where I typed in setup(hd0) I got

> setup (hd0)
Checking if "/boot/grub/stage1" exists... no
Checking if "/grub/stage1 exists... no
Error 27: Unrecognized command

What went wrong? I'm on Debian.

---

