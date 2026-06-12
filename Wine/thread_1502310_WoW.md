---
title: "WoW"
date: 2010-06-05
forum: Wine
---

### Post by Jasper_88 on 2010-06-05
OK I'm gonna try this again since it didn't seem to go very well at all last time. I'm having a few problems with playing WoW on Ubuntu 10.04 LTS. Im not sure if it's because Wine, or because the drivers but i have almost no images for my casts.

Whats going on with it?

---

### Post by asdfoo on 2010-06-05
which video card and drivers? which wine version?

---

### Post by Jasper_88 on 2010-06-06
Im noob to that, my graphics card is the one that came in my laptop, and i have the newest version of wine at the moment

---

### Post by pedro_orange on 2010-06-06
```
lspci |grep vga
```

Will tell you what video card you are running. Ensure you have installed the correct drivers.

Have you checked the Ubuntu WoW wiki page? 
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I presume you're running it with -opengl?

Pulseaudio is also an issue with Wine. Disable it before you run anything in wine.

---

### Post by asdfoo on 2010-06-06
> **Jasper_88 said:**
> Im noob to that, my graphics card is the one that came in my laptop, and i have the newest version of wine at the moment

this tells us nothing.  what you think is the newest version could be a year old.

open a terminal and type:

wine --version

It should say wine-1.2-rc2

to find out what video card you have, type:

glxinfo

---

