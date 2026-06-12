---
title: "World of Warcraft graphical problem when using teleport"
date: 2009-04-24
forum: Wine
---

### Post by blaise69 on 2009-04-24
Hi guys,

I know there are many WoW threads out there, but I've not found anything that seems to address my problem, or, strangely anyone else that has this issue.

I have an Ati Radeon X1950 with Catalyst 9.3, which runs WoW with the recommended opengl settings from the Wine App db, really quite well.

However when I use a teleportation stone, or character, my screen completely messed up once my destination has loaded, it's like when you point a camcorder at a tv it's connected to, the character and background just repeats over itself and it becomes completely unplayable, I've tried resizing screen, alt-tabbing out, but nothing get's it working again.

Can anyone recommend a course of action here apart from buying an Nvidia card?

Cheers,

Blaise.

---

### Post by RebateFX on 2009-04-26
> **blaise69 said:**
> Can anyone recommend a course of action here apart from buying an Nvidia card?

You could try lowering your graphics settings a bit and try again.

I personally think it's the awful state of the ATI Linux drivers that is at fault. An Nvidia card would help a lot. Their drivers are far better.

---

### Post by blaise69 on 2009-04-26
I read through the Ubuntu Howto for WoW and there were a few tweaks that helped, one in particular was the following.
```
SET ffxSpecial "0"
```
It seems that it was a fix for something else, but it has helped with a few bugs I was having.

Cheers,

Blaise.

---

