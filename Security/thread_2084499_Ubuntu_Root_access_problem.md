---
title: "Ubuntu Root access problem"
date: 2012-11-15
forum: Security
---

### Post by rickkos on 2012-11-15
I am having a problem while using Gnome on server 12.04 
When I run gksudo commands from the terminal that open any GUI's for system configuration I keep getting a window that pops up asking for a password but when I enter the admin password it tells me it is wrong?
 
An example is when running the Samba configuration GUI but this happens with any system configuration tools.
 
Please help if you can.

---

### Post by cortman on 2012-11-15
Your [gk]sudo password is the same as your user password, unless your user is not in sudoers.

---

### Post by Hungry Man on 2012-11-15
Your samba/ programs may be installed as a different user?

---

### Post by rickkos on 2012-11-15
> **cortman said:**
> Your [gk]sudo password is the same as your user password, unless your user is not in sudoers.
Okay, so how do I make a user a "sudo'er"?
 
Thanks for your help!

---

### Post by MG&amp;TL on 2012-11-15
> **rickkos said:**
> Okay, so how do I make a user a "sudo'er"?
 
Thanks for your help!
Login as a sudoer, then launch the 'users and groups' dialog, and make user X an administrator after "unlocking" the dialog.

---

