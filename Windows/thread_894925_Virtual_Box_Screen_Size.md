---
title: "Virtual Box Screen Size"
date: 2008-08-19
forum: Windows
---

### Post by L815 on 2008-08-19
I'm using Virtual Box from Sun (not the OSS version), and every OS I boot always has a screen resolution larger than my screen. 

I tried to edit the screen resolution inside the OS, but there are no options.

Anyone know what's going on?

---

### Post by fiddledd on 2008-08-20
In linux you can set the screen size using vboxmanage. I've not used the command in Windows but the command is in the C:\Program Files\Sun\xVM VirtualBox folder. So run cmd.exe and type "C:\Program Files\Sun\xVM VirtualBox\VBoxManage setextradata global GUI/MaxGuestResolution width,height" replace the width/height with your desired resolution. That should do it.

---

