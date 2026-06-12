---
title: "debootstrap with server, custom packages only???"
date: 2005-06-20
forum: Server Platforms
---

### Post by mweisser on 2005-06-20
Hello,

i managed to install ubuntu linux on a remote server using debootstrap. The result was a working ubuntu installation BUT also with all desktop related software like Xorg, Gnome, etc...

Is is possible to install ubuntu via debootstrap but only with the "CUSTOM", "SERVER" package selection ???  

Thanks
Michael

---

### Post by xurizaemon on 2007-03-12
I used this:
```

sudo debootstrap --arch i386 dapper /media/ubuntu-dapper http://nz.archive.ubuntu.com/ubuntu

```
and got a fairly minimal system (surprised to see ALSA in there, but apart from that ...)

---

