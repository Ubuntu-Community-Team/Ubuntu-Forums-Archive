---
title: "Problem running localapps in 10.04 LTSP clients"
date: 2010-12-08
forum: Server Platforms
---

### Post by Lost Fisherman on 2010-12-08
I've successfully built my server, and any fat or thin client that I connect to it boots wonderfully, with great response.
 
I've gone through this exercise because we need a more efficient way of testing computers before delivery to our customers. So, I'm trying to run Passmark's BurnInTest. I've run it before with previous versions (9.something, I think) and it worked well, but I needed to build a new server so we can test more computers concurrently, so I figured I'd get the latest release.
 
My problem occurs when I try to run BurnInTest - it must have root access to test the local USB, parallel, and serial ports, and the optical drive. For the previous iteration I used a script that dropped into a local xterm session, su'd to a root session, and called the BiT GUI. In this attempt, the same scripts, even when I single-step them manually, results in 'authentication failure' when the su is attempted.
 
I have enabled the root account and created a password for it in the chroot /opt/ltsp/i386, and rebuilt the image, multiple times, no joy.
 
Using ctrl-alt-F1 I can log in as root, and using dmesg I can see the USB device register when I connect it, so as far as I can tell the root account is alive and well, just not available in a local xterm session for some reason.
 
Any help at all would be appreciated.

---

### Post by Lost Fisherman on 2010-12-09
Bump
 
Anybody?
 
Bueller?
 
Bueller?

---

### Post by HugoSerrano on 2010-12-09
Hi!

You can add users to /etc/sudoers, or to admin group, so they have root privileges.

To access USB, the user need to be part of FUSE group.

Regards!

---

### Post by Lost Fisherman on 2010-12-09
Thanks Hugo, I'll add the default user to the admin and fuse groups.  Probably a better idea than trying to let a low-level tech have root access anyway.

---

### Post by HugoSerrano on 2010-12-09
If you only want to access to USB devices, the FUSE group should be enough. Adding it to admin is equally dangerous as giving root access.

---

### Post by Lost Fisherman on 2010-12-11
> **HugoSerrano said:**
> If you only want to access to USB devices, the FUSE group should be enough. Adding it to admin is equally dangerous as giving root access.

Didn´t work.  I am back to looking for a way of gaining root access in localapps.  Any ideas would be appreciated.

I´m almost ready to go back to v9, but I really want to use the latest ver if possible.

---

### Post by Lost Fisherman on 2010-12-17
Fixed - had to add the user id to sudoers.  BurnInTest still wants root access, so adding to fusers and admin groups wasn´t enough.

---

