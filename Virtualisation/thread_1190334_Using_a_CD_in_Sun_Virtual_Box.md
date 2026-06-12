---
title: "Using a CD in Sun Virtual Box"
date: 2009-06-17
forum: Virtualisation
---

### Post by artax33 on 2009-06-17
I am running 9.04 and XP on Sun VB for my iPod Touch.  I can't seem to get the CD to pass through to XP to import it on iTunes.  I am still a little new to both VB and Ubuntu.

---

### Post by nfox on 2009-06-17
You can go to Settings in VB with the guest powered off or at the top menu bar while it's running and select a CD-ROM drive or ISO image (only one at a time though) and even to enable passthrough (for burning CDs, etc.) 

The other route is to do what I do and have your host (Ubuntu) mount CDs to a folder (like set /etc/fstab to have the device mount on /media/cdrom0 for example) then map that as a shared folder and then browse to it in the guest. That gives me access to both drives at once. But you won't have autostart or anything since Windows will see it as a folder. But who cares about that anyways.

---

