---
title: "can't get GUI in ubuntu server 9.04"
date: 2009-09-20
forum: Server Platforms
---

### Post by benzslr123 on 2009-09-20
i just installed 32 bit ubuntu server on my desktop computer, upon logging in i type the commands
```

sudo apt-get update

```
and then
```

sudo apt-get install ubuntu-desktop

```
to which i get the reply "E: couldn't find package ubuntu-desktop"

am i doing something wrong? any advice?
and yes i understand there are drawbacks to having a GUI on a server, but unfortunately its necessary at this time. thank you for your help.

---

### Post by Iowan on 2009-09-21
See if [this]("https://help.ubuntu.com/community/ServerGUI") one helps.  Yes, it starts with the "you don't need it" arguments, but details follow.

---

### Post by stlsaint on 2009-09-21
> **benzslr123 said:**
> i just installed 32 bit ubuntu server on my desktop computer, upon logging in i type the commands
```

sudo apt-get update

```
and then
```

sudo apt-get install ubuntu-desktop

```
to which i get the reply "E: couldn't find package ubuntu-desktop"

am i doing something wrong? any advice?
and yes i understand there are drawbacks to having a GUI on a server, but unfortunately its necessary at this time. thank you for your help.

for the gnome gui use this
sudo apt-get install gnome-desktop-environment

also you may want to look into web interface ie web-admin

---

### Post by okivash on 2009-09-21
I did this exact same process but I ran the following and it worked perfectly....

```
sudo apt-get install xorg gnome-core gdm
```It then finished install and booted into the GUI login desktop. The first time I did this it complained about not having the proper Human Theme file and defaulted to the flowery one... After logging in, I started Synaptic and searched the the Human-Theme, installed it and rebooted... Everything worked great after that!

Okivash

---

