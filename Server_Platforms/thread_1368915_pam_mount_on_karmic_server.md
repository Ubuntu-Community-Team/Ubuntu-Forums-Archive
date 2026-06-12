---
title: "pam_mount on karmic server"
date: 2009-12-31
forum: Server Platforms
---

### Post by mcgrmic2 on 2009-12-31
I have a home server running 9.10 with VLM and Samba configured. I can mount the shared "drives" on my desktops just fine, but I would like to configure them to be automounted at login (and umounted at logout) while maintaining security for users individual files using pam_mount or similair. However, I do remember reading something about pam_mount not working with karmic. Anybody else have experience with this or any input? Thank you

mcgrmic

---

### Post by mcgrmic2 on 2010-01-01
Anybody have any experience in this?

---

### Post by reader4 on 2010-01-21
Does this help?

[http://ubuntuforums.org/showthread.php?t=1375653&highlight=mount+share+user&page=2](http://ubuntuforums.org/showthread.php?t=1375653&highlight=mount+share+user&page=2)

Mine is working if I use the username explicitly.  So far I haven't been able to get the user="%(USER)" specification to work.

---

