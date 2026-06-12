---
title: "firmware update"
date: 2012-07-02
forum: Server Platforms
---

### Post by Hadesdarklord on 2012-07-02
Did the recent firmware update pushed out by Ubuntu impact Grub?

After applying the update (2.6.32-41-generic-pae kernel) my grub install was hosed.

Using a 10.04LTS rescue disk to reinstall grub has had NO EFFECT.

I can shell into the server, using the shell from the Live CD, but I cannot start the OS.

Everything was just fine until i restarted to apply the kernel update.

Very disappointed...

---

### Post by Cheesehead on 2012-07-02
Firmware updates are usually kernel modules. Changes to the kernel (including modules) will trigger update-initramfs and update-grub.

Did you have a custom kernel before? Or special grub settings?

When you boot, does the system fail before or after the grub screen? Is there any error message?

---

### Post by Hadesdarklord on 2012-07-03
Standard 10.04LTS 32bit install

The update in question contained the standard linux kernel and kernel headers, but also an update titled linux-firmware.

Grub just crashes.  I believe it may have written additional information to my raid array (running a 50 with a hot-spare),

I even re-installed fresh, and grub crashes.

just sits there at

grub>

---

