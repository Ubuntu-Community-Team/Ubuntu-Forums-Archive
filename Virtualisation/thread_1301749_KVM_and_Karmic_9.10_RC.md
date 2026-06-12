---
title: "KVM and Karmic 9.10 RC"
date: 2009-10-26
forum: Virtualisation
---

### Post by fjgaude on 2009-10-26
Installed kvm and virt-mgr from theUbuntu repros. Everything went as planned. Then installed WinXP SP1 from cdrom. Then updated to SP3 which took hours because of slowness of downloads and updates.

Had troubles with mouse and size of screen. So I used a CLI to reboot the guest:

frank@sunshine:~$ kvm -vga std -hda /var/lib/libvirt/images/WinXP.img -boot c -m 2048 &

That worked well... but, but I could no longer use virt-mgr. It looks to load the image from /dev/sr1 and not from hda. Anyone have an idea how to correct this so I can use virt-mgr to mange the image?

---

### Post by fjgaude on 2009-10-26
Turns out virt-mgr always requires you to have a CD in the drive, as it looks for something in /dev/sr1 as the block device.

KVM is very slow using virt-mgr to run the VM, but is almost alright using the command line... lots more learning required to figure out how to get any quickness out of KVM, mouse, and low CPU usage.

---

