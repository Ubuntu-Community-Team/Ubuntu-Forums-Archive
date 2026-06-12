---
title: "kvm running windows xp sp3: corrupts file system on shutdown?"
date: 2009-07-02
forum: Server Platforms
---

### Post by jwatte on 2009-07-02
I'm attempting to set up a Windows XP virtual machine using KVM running on 8.04 LTS x64 or a Core 2 Duo (6550). I have updated all installed packages to the latest available as of a week ago.

I'm creating a 20 GB hard disk image with qemu-img, (on a file system that is managed by LVM, and in turn backed by a md0 soft mirror) and then starting the VM as follows:

#!/bin/sh
cd /var/kvm/wxp_build
kvm -m 1024M \
  -hda wxp_build.img \
  -usb -usbdevice tablet \
  -vnc :1 \
  -localtime \
  -net nic,model=virtio -net user \
  -redir tcp:5555::5555 \
  -daemonize \
  $*

When I install, I pass "-cdrom ../cdrom/wxp_sp3_installer.iso -boot d" to boot from the Windows install CD. The reboot as part of the install does not take down the VM, and does not cause any problems.

I can go through install just fine. I format the 20 GB image as NTFS, using slow format (not quick format).

I can download and install other things fine, too. However, when I shut down the virtual machine (using the Windows Shut Down command), and wait for the VNC connection to end, the (virtual) hard disk seems to get corrupt. When I boot again, one of three things happen:

1) The boot fails, because some necessary file has gotten corrupted.

2) The boot succeeds, but when I attempt to run something that I installed that worked fine before the shutdown, it doesn't work after the shutdown, with missing DLL errors or similar.

3) The boot kicks into CHKDSK, which finds tons and tons of NTFS file system corruption on the virtual hard disk image.

I've tried with both qcow2 and raw disk images, with the same results.

To my mind, it behaves as if the KVM process decides to exit as soon as the BIOS power-off signal comes, but the process keeps the hard disk write buffer in user-mode RAM, rather than immediately having passed it on to the kernel. Thus, when the process exits, whatever was buffered will not be committed to disk, and badness ensues. I'm not sure at all that this is what actually happens, but that's what it feels like. It could be some other kind of image corruption, too, but it's clearly related to actually powering off the virtual machine.

Btw: the same corruption happens if I kill the KVM while it's running (rather than do a "clean" shut-down). It's slightly more understandable under that situation, but not really -- NTFS is a journaling file system, and never has those corruption issues on my "native" Windows machines, even during power fail.

So... does anyone have a clue what could be causing this, and what I can do to fix it?

---

### Post by jwatte on 2009-07-02
I posted on the KVM mailing list, and got the following reply:

[INDENT]I warmly suggest updating to a later, much newer, KVM version. Specifically qcow2 format had corruption bugs similar to what described below.
Y.
[/INDENT]

Given that 8.04 is supposed to have long term support, is there any chance of getting a newer KVM rolled in, or do I need to go hand-crafting one for my system?

---

