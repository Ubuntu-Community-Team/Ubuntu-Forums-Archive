---
title: "GNOME Issue"
date: 2011-12-10
forum: Server Platforms
---

### Post by coolguy918 on 2011-12-10
I installed GNOME on my system per [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI). Problem is, now whenever I boot my server, it loads the desktop edition login screen and loads graphical desktop environments (even the terminal option isn't a true terminal). The server doesn't have a working port for a PS/2 mouse and I don't have a USB mouse to use with it, so my only option is to do all local work with only a keyboard. Because of this, I consider it a total waste of resources, and I want the original login screen (the text-based one) back without getting rid of GNOME (I still use VNC tunneled over SSH - DON'T JUDGE :P).

Is this possible? If so, how?

---

### Post by papibe on 2011-12-10
Hi coolguy918.

Without uninstalling anything change the grub config as follows:

Edit your grub file:
```
sudo nano /etc/default/grub
```

Locate these lines:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="text"
```
Change them to:
```
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="text"
```
Save the file. Then update grub:
```
sudo update-grub
```
Then restart:
```
sudo reboot
```
Hope it helps, and tell us how it goes.
Regards.

---

### Post by coolguy918 on 2011-12-17
> **papibe said:**
> Hi coolguy918.

Without uninstalling anything change the grub config as follows:

Edit your grub file:
```
sudo nano /etc/default/grub
```Locate these lines:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="text"
```Change them to:
```
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="text"
```Save the file. Then update grub:
```
sudo update-grub
```Then restart:
```
sudo reboot
```Hope it helps, and tell us how it goes.
Regards.
Still booting to the GNOME logon screen... any other suggestions?

---

### Post by papibe on 2011-12-17
Try removing gdm (GNOME Display Manager) from the services list:
```
sudo update-rc.d -f gdm remove
```
Regards.

---

### Post by coolguy918 on 2011-12-17
> **papibe said:**
> Try removing gdm (GNOME Display Manager) from the services list:
```
sudo update-rc.d -f gdm remove
```Regards.
No luck with this either...

If this helps: in order to try and diagnose the problem, I tried adding a beep to my GRUB config just to make sure update-grub was working. Uncommented the appropriate line, saved the config, and ran update-grub. It appeared to work until I actually tested it...restarted okay but no beep.

---

