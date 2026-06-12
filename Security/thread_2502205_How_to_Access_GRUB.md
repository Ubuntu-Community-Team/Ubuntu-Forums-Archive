---
title: "How to Access GRUB"
date: 2024-11-05
forum: Security
---

### Post by snandy-the-snek on 2024-11-05
Hi,
I need to recover my account password (as it has special characters in it that cannot be typed on the first login screen) and am having trouble accessing GRUB. I've tried holding/pressing ESC, SHIFT, and DEL (one at a time), and none have worked. I am able to access BIOS if that matters. What else can I try to access GRUB or otherwise solve the problem? (I already checked the onscreen keyboard function and cannot find the required character.)

---

### Post by TheFu on 2024-11-05
There is no password recovery, as passwords are stored AFTER being 1-way encrypted.  It is the encrypted results that are compared, not the actual password a human types.

What this means is that you need to reset the password. There are lots of how-to guides to do this based on different situations, so google for _Ubuntu Password Reset_ and follow the guide that makes the most sense to you.  The grub screen should be displayed for at least 5 seconds between the BIOS and the OS launched image, unless someone changed the default time.  When that is shown, there should be 3+ lines on a black screen with white letters. The last option is "Advanced ....". Use the arrows to select that and go into maintenance mode when the next scree is shown.  From there, you can enter the **passwd {username}** command and change it.  Of course, this is dependent on YOUR startup settings and the actual release + flavor of Ubuntu installed.

[https://itsfoss.com/how-to-hack-ubuntu-password/](https://itsfoss.com/how-to-hack-ubuntu-password/) seems like what I'm trying to describe.

---

### Post by snandy-the-snek on 2024-11-05
I followed the tutorial you gave and it worked, thanks! I think the issue was that I wasn't pressing Shift fast enough after the BIOS splash screen came up.

---

