---
title: "Weird unity launcher glitch on login."
date: 2013-03-23
forum: Ubuntu Development Version
---

### Post by georgelappies on 2013-03-23
Hi all

I have chnaged my unity launcher icon's size to 32. However as soon as Iogin the launcher still has an icon size of the default big size for a second or so before changing to the smaller size.

This distracting behaviour is not present in 12.04 or 12.10.

---

### Post by dino99 on 2013-03-23
there are some changes about decoration made in the background, and major bug fix releases both for compiz & unity will landing in a few days. Hopes to see less issue then.

have you a .local/..../compiz.desktop ?  If ccsm has been used, then save the changes with:  ```
compiz --replace ccp &
``` otherwise they may be lost on the next logout/in

---

### Post by grahammechanical on 2013-03-23
> **georgelappies said:**
> Hi all

I have chnaged my unity launcher icon's size to 32. However as soon as Iogin the launcher still has an icon size of the default big size for a second or so before changing to the smaller size.

This distracting behaviour is not present in 12.04 or 12.10.

I also have seen this behaviour. Unity is loading default settings and then bringing in user configuration settings.

---

### Post by cariboo on 2013-03-23
> **grahammechanical said:**
> I also have seen this behaviour. Unity is loading default settings and then bringing in user configuration settings.

I've got the launcher icon size set to 28px, via ccsm, and I see the same behaviour on startup.

---

### Post by mc4man on 2013-03-23
> **grahammechanical said:**
> I also have seen this behaviour. Unity is loading default settings and then bringing in user configuration settings.

I believe this is only the icon size setting. So when unity starts the launcher icon size is set to '48px', then if the user has switched from the default, (which happens to be 48) then that value is used & the icons are resized. If the user hasn't changed from the default then the launcher is not resized.

(what the actual default size is of the launcher icons is somewhat irrelevant, other than the defacto default is 48px.

---

### Post by EgoGratis on 2013-03-23
Yes it has been like this for a while. Maybe it's intentional but i don't know. 

P.S. I would prefer the old behaviour too.

---

### Post by rrnbtter on 2013-03-24
Greetings,
Its part of the boot process. In previous versions the minimum size icon for the launcher icons was 32px. Now there is a new icon package that goes down to 8px. The issue is that the 32px is available without the Unity Plugin but the smaller sizes require the setting in the Unity plugin. Hence they can't be changed from default until Unity Plugin loads. Personally I don't see a problem with whats happening. When I plug in my USB Modem there is a few second wait time for it to show in the Wifi panel. It is a process that occurs in real time. Time takes time. No big deal to me.

---

