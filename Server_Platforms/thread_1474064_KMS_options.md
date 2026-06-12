---
title: "KMS options"
date: 2010-05-05
forum: Server Platforms
---

### Post by Chav on 2010-05-05
The machine is using the inteldrmfb and running Ubuntu 10.04.

I need to keep the vga port active even when the machine is started without a monitor connected. 
Adding "GRUB_CMDLINE_LINUX_DEFAULT=...video=VGA-1:e..." to /etc/default/grub  accomplishes that. 

I also need to set the resolution to 640x480. 
video=VGA-1:640x480@60 works for that. 

I'm stumped as to how I can accomplish both at the same time. I tried adding "option i915 video=VGA-1:e" and "option video=VGA-1:640x480@60" to /etc/modprobe.d/i915-kms.conf, but that switches to a the EFI VGA frame buffer device which slows my writes out to the framebuffer. 

Thank you for your time.

---

### Post by Chav on 2010-05-06
I have a work around that involves disabling KMS. 

edit /etc/initramfs-tools/modules
add
fbcon
i915

make sure i915 isn't blacklisted in /etc/modprobe.d/blacklist-framebuffer

sudo update-initramfs -u -k all

edit /etc/default/grub
add
i915.modeset=0

sudo update-grub

This still switches to EFI VGA but the writes to the framebuffer are on par with inteldrmfb.

---

