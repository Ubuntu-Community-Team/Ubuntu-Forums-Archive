---
title: "Unable to Mount Guest Additions"
date: 2013-03-27
forum: Virtualisation
---

### Post by DaGamer12345 on 2013-03-27
I'm not necessarily new to Ubuntu in any way (I've virtualized it since Karmic Koala), but this is the first time I've tried installing Guest Additions in Virtualbox.
When I go to my Computer section, it DOES show a CD/DVD drive. But I cannot mount it in any way. Here's what I get when I try to mount it:
[IMG]http://i.imgur.com/PciUXwv.png[/IMG]
Any tips on trying to fix it? I try to do cd /media/ in Terminal, then do ls, but nothing comes up.
Please help.[RIGHT]-DaGamer12345[/RIGHT]

---

### Post by CharlesA on 2013-03-29
Have you mounted the guest addition ISO in virtualbox before trying to access the cd drive?

---

### Post by DaGamer12345 on 2013-03-29
Of course I have. I go up to Devices > Install Guest Additions, then I try to access the drive. Nothing comes up on the desktop/launcher, and Terminal does not recognize it. I'm not that inexperienced...

---

### Post by CharlesA on 2013-03-29
No need to get offended. :)

Try mounting the iso manually in VBox.

---

### Post by DaGamer12345 on 2013-03-29
When I do that, I get "mount point /media/cdrom does not exist".
Apparently it is not even recognizing that there is a CD in the drive.

EDIT: Apparently the Guest Additions .iso was broken. Downloaded the .iso in Ubuntu, mounted it and installed it. Works now.

---

### Post by CharlesA on 2013-03-29
Weird. Glad you got it working at least. :)

---

