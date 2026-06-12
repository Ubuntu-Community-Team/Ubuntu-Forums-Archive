---
title: "Digital camera instalation help"
date: 2005-08-01
forum: Repositories &amp; Backports
---

### Post by Tymotey on 2005-08-01
I have a digital cameraand I want to intsll it..how can I? some help pls

---

### Post by MrCheese on 2005-08-01
[QUOTE=Tymotey]I have a digital cameraand I want to intsll it..how can I? some help pls[/QUOTE]

most reasonably recent cameras will be recognized by the system as a USB hard disk - if you open a root console (use your password when asked for a password).

Type "tail -f /var/log/messages" (hit return).  Plug the camera in & you should see the system detect the camera and ahsign it to a disk device (most likely /dev/sda1 unless you have SATA or scsi drives). If this goes ok, try running one of the digital photo apps which should pick up the camera & allow you to download the pics to a folder on your hard disk.

Hope this helps,

Paul.

---

### Post by Tymotey on 2005-08-01
thanks..it really worked... :)

---

### Post by Tymotey on 2005-08-01
thanks..it really worked... :)

---

