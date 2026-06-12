---
title: "No separate login option for flashback session"
date: 2018-01-16
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2018-01-16
Just giving todays daily build a spin and after installing I installed gnome-panel which still pulls in all the depends needed to run a flashback session. But after logging out there was no option to select flashback as a session - only Ubuntu and Ubuntu + Xorg. I was pleasantly surprised though to find that once logging back into the standard Ubuntu session I was running flashback.

Good enough for me, for now, but I'm certain that behavior needs to be corrected long before we reach Beta stage. I haven't even checked yet to see what window manager is actually running in that session, or even what happens after a reboot. Just thought i'd give a shout out. I've been away so long I have a lot of re-learning to do. I assume that Ubuntu is now running GDM?

---

### Post by mc4man on 2018-01-16
When installing a new session gdm3 needs a reboot (unlike lightdm where a log out sufficed.
(- with gdm3 - when in doubt, reboot

---

### Post by kansasnoob on 2018-01-16
> **mc4man said:**
> When installing a new session gdm3 needs a reboot (unlike lightdm where a log out sufficed.
(- with gdm3 - when in doubt, reboot

I see, thanks. I wonder if all new sessions added always appear at the top of the list? That would appear to be the reason that the newly added flashback session loaded from login even though Ubuntu was selected. After reboot flashback appears at the top of the list.

---

### Post by mc4man on 2018-01-16
> **kansasnoob said:**
> I see, thanks. I wonder if all new sessions added always appear at the top of the list? That would appear to be the reason that the newly added flashback session loaded from login even though Ubuntu was selected. After reboot flashback appears at the top of the list.
Not sure, I'd think alphabetically would be most likely. When I've added unity-session it's at the bottom..

---

