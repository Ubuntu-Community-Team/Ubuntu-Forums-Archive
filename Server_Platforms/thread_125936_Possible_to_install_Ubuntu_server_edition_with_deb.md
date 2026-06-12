---
title: "Possible to install Ubuntu server edition with debootstrap?"
date: 2006-02-05
forum: Server Platforms
---

### Post by fbn on 2006-02-05
Hi,

I don't see a way to install the Ubuntu server edition for Breezy with debootstrap, only warty, hoary and breezy are available.

Will there be an debootstrap option for Dapper Drake server edition?

---

### Post by LordHunter317 on 2006-02-05
Whatda mean?  Ubuntu server is esentially just the base system plus giving the installer the ability to install extra kernels.  Deboostraping breezy and then not installing anything should give you the base system, least I'm pretty certain of that.

---

### Post by fbn on 2006-02-05
Why are there two images (ubuntu & ubuntu-server) if it's just the same?

---

### Post by diebels on 2006-02-05
[QUOTE=fbn]Why are there two images (ubuntu & ubuntu-server) if it's just the same?[/QUOTE]
You don't get the whole cd-image installed when you debbootstrap.

The server images has less gui and more server packages. Also some server kernels i think.

---

