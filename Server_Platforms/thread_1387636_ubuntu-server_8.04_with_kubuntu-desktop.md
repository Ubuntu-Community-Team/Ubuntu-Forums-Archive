---
title: "ubuntu-server 8.04 with kubuntu-desktop"
date: 2010-01-22
forum: Server Platforms
---

### Post by maammar on 2010-01-22
I have installed ubuntu-server 8.04 with kubuntu-desktop To facilitate the configuration.
I want now to remove kubuntu-desktop,how can i do that without lost any package in the server (sun-java-jdk,mysql,apache2.....)

I have tested

[PHP]apt-get remove kubuntu-desktop[/PHP]but Nothing happens

---

### Post by maammar on 2010-01-23
pls help

---

### Post by nyu2007 on 2010-01-23
Hi,

I am confused about your issue. How can you install ubuntu 8.04 with kubuntu-desktop??

Regards,
NyU

---

### Post by d3v1150m471c on 2010-01-23
If you don't have another desktop manager installed, like xfce or gnome, i wouldn't remove kde. That's just asking to run everything out of a terminal screen...possibly worse, unless that's your goal...

anyways...**from a different desktop manager**
```

sudo aptitude remove kubuntu-desktop && sudo apt-get autoclean && sudo apt-get autoremove

```

---

### Post by maammar on 2010-01-23
> **nyu2007 said:**
> Hi,

I am confused about your issue. How can you install ubuntu 8.04 with kubuntu-desktop??

Regards,
NyU

after installation of ubuntu-server

from  kubuntu alternate cd or internet 

[PHP]apt-get install kubuntu-desktop[/PHP]

---

### Post by maammar on 2010-01-23
> **d3v1150m471c said:**
> If you don't have another desktop manager installed, like xfce or gnome, i wouldn't remove kde. That's just asking to run everything out of a terminal screen...possibly worse, unless that's your goal...

anyways...**from a different desktop manager**
```

sudo aptitude remove kubuntu-desktop && sudo apt-get autoclean && sudo apt-get autoremove

```
I don't have any other desktop manager installed

---

### Post by nyu2007 on 2010-01-23
I found this thread
Hope to help you
[http://ubuntuforums.org/showthread.php?t=870455](http://ubuntuforums.org/showthread.php?t=870455)

Regards,
NyU

---

