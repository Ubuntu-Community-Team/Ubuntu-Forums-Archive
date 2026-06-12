---
title: "Easy MP3-player/USB-stick formating"
date: 2007-10-29
forum: Ubuntu Brainstorm
---

### Post by metallica1788 on 2007-10-29
I really love ubuntu but there is one thing i really miss...
i think it would be really cool to add a formatting function to nautilus, it would be much easier to click the right mouse button and then format the MP3-player/USB-stick.
For security reasons you need offcourse a sudo password.
If you add such a feature it would be another big step in terms of user friendliness:)

---

### Post by smartboyathome on 2007-10-29
> **metallica1788 said:**
> I really love ubuntu but there is one thing i really miss...
i think it would be really cool to add a formatting function to nautilus, it would be much easier to click the right mouse button and then format the MP3-player/USB-stick.
For security reasons you need offcourse a sudo password.
If you add such a feature it would be another big step in terms of user friendliness:)

One problem: What filesystem do you want? If it is a newbie, it will probably be EXT3, but if you are moving in between windows and Linux (and possibly Mac), you may want to set it as FAT32 or something similar.

---

### Post by metallica1788 on 2007-10-30
For MP3 players it is not such a big problem,most of them are formatted in FAT32 so ubuntu just need to detect what file system it uses and format it.
The best way is some kind of dialog where you can choose between different filesystems and if a filesystem is detected on the device it will select that one as default.

---

### Post by smartboyathome on 2007-10-30
> **metallica1788 said:**
> For MP3 players it is not such a big problem,most of them are formatted in FAT32 so ubuntu just need to detect what file system it uses and format it.
The best way is some kind of dialog where you can choose between different filesystems and if a filesystem is detected on the device it will select that one as default.

Wouldn't this be complicated for a new user without any previous Linux experience?

---

### Post by metallica1788 on 2007-10-31
It is much easier than using console commands...
So i dont see why this would make it more difficult

---

### Post by smartboyathome on 2007-10-31
They might not know which filesystem to choose. This in itself may be troublesome.

---

### Post by xanikseo on 2007-10-31
In Windows you have to select the file system and sector size.... What's wrong with that? There should be at least a clone of the Windows format thing in Ubuntu, it's better than not having it at all :P.

---

### Post by Brinstar on 2009-03-09
> **smartboyathome said:**
> Wouldn't this be complicated for a new user without any previous Linux experience?

then they can do what everyone else does when they're new to computers: LEARN.

I like the GUI-based format idea personally.

---

### Post by smartboyathome on 2009-03-09
> **Brinstar said:**
> then they can do what everyone else does when they're new to computers: LEARN.

I like the GUI-based format idea personally.

That is like throwing the kid who doesn't know how to swim in the pool and telling them "swim". They might get lucky and naturally know how to swim, but they might also drown and give up, never to swim again.

It would be better to have more English-oriented and less tech oriented wording (ie, don't use "FAT32" or "EXT2", as that would confuse people).

EDIT: By the way, what about GParted? Have many of you tried it? It is included on the Ubuntu CD.

---

