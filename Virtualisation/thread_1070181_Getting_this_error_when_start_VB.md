---
title: "Getting this error when start VB"
date: 2009-02-14
forum: Virtualisation
---

### Post by Doug11 on 2009-02-14
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).

How do I set my permissions for this?

---

### Post by HotShotDJ on 2009-02-14
> **Doug11 said:**
> How do I set my permissions for this?System --> Administration -- Users & Groups

Unlock the dialog (press the "unlock" button) then click on "Manage Groups" -- find "vboxusers" in the list, click on it to select, then click on "Properties."  Check off all users that you want to allow to use virtualbox.  Do NOT check off root.  Click OK the close Groups settings and Users Settings.  You will need to log out and then log back in for the changes to take effect.

---

### Post by Doug11 on 2009-02-15
> **HotShotDJ said:**
> System --> Administration -- Users & Groups

Unlock the dialog (press the "unlock" button) then click on "Manage Groups" -- find "vboxusers" in the list, click on it to select, then click on "Properties."  Check off all users that you want to allow to use virtualbox.  Do NOT check off root.  Click OK the close Groups settings and Users Settings.  You will need to log out and then log back in for the changes to take effect.
Thanks,,finally got everything going great. Had a few conflicts cause there was something installed through repos and didnt go good with the version I got from the VB website. It even picks up my USB-serial adapter:):guitar:

---

