---
title: "Black Screen After Changing Display Resolution"
date: 2018-08-23
forum: Virtualisation
---

### Post by souzaalexuo on 2018-08-23
After changing Lubuntu 18.04 display resolution and rebooting, I will get only a black screen after logging on.

I've tried adding "GRUB_GFXPAYLOAD_LINUX=1280x800" (or other resolutions such as 800x600) to /etc/default/grub file, following this [https://askubuntu.com/questions/351585/black-screen-after-login-lubuntu](https://askubuntu.com/questions/351585/black-screen-after-login-lubuntu) but it didn't work.

"xrandr" will give me "Can't open display".

Does anybody have any idea how to troubleshoot this? (I'm new to Linux)

---

### Post by Autodave on 2018-08-23
A little info on your system may help: especially what video card do you hae, did you install any driver for it, and where did you get the driver from?

---

### Post by souzaalexuo on 2018-08-23
I'm running Lubuntu 18.04 (x64) as a Virtual Box machine on Windows 7 (x64).

Intel® HD Graphics 4000.

I didn't install any driver for it.

---

### Post by souzaalexuo on 2018-08-23
This VM is just a test to me and I could just reinstall the whole thing, but I'd like to take this as an opportunity to learn more. Although I don't understand why Lubuntu couldn't just "not let me" change the resolution to an unsupported one or at least warn me about it.

---

### Post by wildmanne39 on 2018-08-23
*Thread moved to **Virtualisation for a more appropriate fit**.*

---

### Post by jorlando on 2019-01-04
Delete this file:

~/.config/autostart/lxrandr-autostart.desktop

reboot.

Now retry other resolutions, only press SAVE if the new resolution tests ok (the 15 seconds warning, etc)

If by accident you lose your desktop just remove lxrandr-autostart.desktop and reboot again.

---

### Post by souzaalexuo on 2019-01-04
> **jorlando said:**
> Delete this file:

~/.config/autostart/lxrandr-autostart.desktop

reboot.

Now retry other resolutions, only press SAVE if the new resolution tests ok (the 15 seconds warning, etc)

If by accident you lose your desktop just remove lxrandr-autostart.desktop and reboot again.

Tank you, jorlando, but I've already deleted the VM.

---

