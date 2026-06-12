---
title: "Kubuntu 12.04 cannot hibernate"
date: 2012-01-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by SeijiSensei on 2012-01-23
I have an ASUS 1201n EEEpc that would hibernate correctly in Kubuntu 10.10 and 11.10.  In 12.04 it fails to hibernate at all.  Neither closing the lid nor choosing "Hibernate" from the menu puts the machine into hibernation.  Instead it remains powered up with the screen dimmed but not turned off.  Pressing a key in this state brings up the dialog box to unlock the session however.

If you turn off the power in this state, then turn it back on, you return to the BIOS screen followed by the grub menu, just as if I had selected "Shutdown" from the main menu except that the power is never turned off.

This is an upgrade from 11.10, not a fresh installation, if that matters.

---

### Post by donniezazen on 2012-01-23
I don't even have hibernation option in Ubuntu.

---

### Post by cariboo on 2012-01-23
@donniezazen, have you looked at System Settings->Power? That's where I set hibernation/suspend behavior.

---

### Post by donniezazen on 2012-01-24
> **cariboo907 said:**
> @donniezazen, have you looked at System Settings->Power? That's where I set hibernation/suspend behavior.

Yes, hibernation is grayed out.

---

### Post by u2nTu on 2012-02-22
Thanks to Dima on askubuntu for _[the solution]("http://askubuntu.com/questions/94754/how-to-modify-policykit-to-allow-hibernation-in-upower")_, echoed here:[INDENT]1. Create the following file:```
sudo nano /etc/polkit-1/localauthority/50-local.d/com.ubuntu.desktop.pkla
```2. Paste this text into it:```
[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
```3. Reboot, select 'normal boot' from grub menu that comes up, and be patient.
[/INDENT]Works in Ubuntu (amd/64), and apparently all 12.04 distros.

For further reading as to why hibernate is disabled by default (yes, this is intentional), see _[the bug thread]("https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/812394")_.

Hope this helps others who, like me, come here thinking, 'WTF, NO HIBERNATE?'


**EDIT:**
Thanks also to dino99 for the note on swap. 2 GB ***is*** insufficient, though 3 GB works great for me. But if the disk is large, why squeeze it? Rule of thumb is to set swap space = RAM size.

---

### Post by dino99 on 2012-02-22
and remember to set the swap partition at least with 4 Gib to get a working hibernation.

---

