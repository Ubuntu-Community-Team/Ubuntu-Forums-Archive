---
title: "No window manager?"
date: 2008-12-14
forum: Server Platforms
---

### Post by ScottEChapman on 2008-12-14
So, I have installed the server edition, and it boots up in console command line mode

(sorry for being a big of a Linux noob)

But I was expecting to have some window manager running (gnome, kde, or something).

How do I fix this??

---

### Post by theozzlives on 2008-12-14
The server doesn't have GNOME, however, you can do:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by secondstage on 2008-12-14
At the command line you get type...
```
sudo apt-get install ubuntu-desktop
```
... Put in your password, and let it do its thing. Reboot, and it should automatically go into Gnome.


**Too late. My bad.**

---

### Post by howefield on 2008-12-14
If you intended to install the server edition to use it as a server, you might want to get a lighter window manager than gnome which you will get with ubuntu-desktop.

eg, xfce4. There are many others which won't eat so many processor cycles, although how much of a concern that is these days with processors being so fast and high end, I' not sure.

---

