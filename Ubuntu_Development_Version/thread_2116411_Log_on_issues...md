---
title: "Log on issues.."
date: 2013-02-15
forum: Ubuntu Development Version
---

### Post by Baldrick_NZ on 2013-02-15
Using 13.04, Gnome 3.6, has anyone else noticed that just before the GDM login screen arrives, the system just hangs?

It gets to the purple Ubuntu screen with five red dots under the Ubuntu logo, then has the mouse icon similar to the hour glass and goes no further.

It seems the only way to remedy the prob is to do a hard restart and hope that it works better next time. 

What's the best way to trouble shoot something like this?

Thanks in advance..

EDIT: Just changed to LightDM, seems to work better. So might be an issue between the hand over between start-up & GDM?

---

### Post by dino99 on 2013-02-16
you simply need to boot without "quiet splash" to get the verbose mode, and see what are the boot comments.

---

### Post by cariboo on 2013-02-16
The only thing I've really noticed, that setting a background picture in grub, my boot time seems to take longer. It's not enough for me to bother investigating, though, as instead of the login screen being up and waiting when I start the system up in the morning, and go get a cup of coffee, it now is just loading the login screen when I get back.

---

### Post by zika on 2013-02-17
> **cariboo907 said:**
> The only thing I've really noticed, that setting a background picture in grub, my boot time seems to take longer. It's not enough for me to bother investigating, though, as instead of the login screen being up and waiting when I start the system up in the morning, and go get a cup of coffee, it now is just loading the login screen when I get back.It allows You to enjoy chosen picture longer...

---

