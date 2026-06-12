---
title: "/etc/inittab Not found !"
date: 2008-09-23
forum: Server Platforms
---

### Post by asel_ on 2008-09-23
Hi , the file /etc/inittab not found ! in ubuntu server , I want to use this file to enable/desable Xwindows , please help ! I installed xwindow and gnome GUI and it now run every time I start ubuntu ,I want to disable xwindow !

---

### Post by mike1821 on 2008-09-23
From what I know Debian based systems like Ubuntu are not using an inittab file.

Instead of that you can decide about the start up scripts using the update-rc.d command.

In order to start/stop the "Gnome GUI" you can remove the gdm script from the starting list.

Try,

```
man update-rc.d
```

---

### Post by kevdog on 2008-09-23
The last version of Ubuntu to contain an inittab file was Feisty.

---

### Post by asel_ on 2008-09-23
> **kevdog said:**
> The last version of Ubuntu to contain an inittab file was Feisty.
So I want any thing to do it (i.e like Fedora Core)

---

### Post by asel_ on 2008-09-23
> **mike1821 said:**
> From what I know Debian based systems like Ubuntu are not using an inittab file.

Instead of that you can decide about the start up scripts using the update-rc.d command.

In order to start/stop the "Gnome GUI" you can remove the gdm script from the starting list.

Try,

```
man update-rc.d
```
Sorry ,But I find it too difficult :(

---

### Post by asel_ on 2008-09-23
Ok , My Question is : How to enable text mode ? Thnx

---

### Post by mike1821 on 2008-09-23
Then I suppose the simplest way to do that is to go

System/Administration/Services

and uncheck the gdm service (Graphical login manager)

I believe this will do the job

---

