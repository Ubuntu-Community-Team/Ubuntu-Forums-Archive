---
title: "What part of the desktop is..."
date: 2008-07-23
forum: The Cafe
---

### Post by Silpheed2K on 2008-07-23
the part where you mouse over a music file and it plays as a preview without you opening it?
cause i found a bug in it... and I want to report it.

if you mouseover and let it play... then hit the delete key on it... it will keep playing.
by the way it has to be moved to the trash can to my knowledge.

---

### Post by paul101 on 2008-07-23
> **Silpheed2K said:**
> if you mouseover and let it play... then hit the delete key on it... it will keep playing.
by the way it has to be moved to the trash can to my knowledge.

afaik. . . thats a feature



youre supposed to click on it then delete :razz:

---

### Post by zmjjmz on 2008-07-23
It's a nautilus plugin that uses mpg123 to play a song if you hover your mouse over it.

---

### Post by bruce89 on 2008-07-23
> **zmjjmz said:**
> It's a nautilus plugin that uses mpg123 to play a song if you hover your mouse over it.

It isn't any more. They replaced it with a nice GStreamer based player, *totem-audio-preview*. One of the Totem developers implemented it.

---

### Post by Joeb454 on 2008-07-23
Funnily enough, I found out this bug earlier. I moved the file back (I had it backed up somewhere) and clicked again and it stopped :p

---

### Post by bruce89 on 2008-07-23
You've happened upon [Bug #240027](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/240027), which should be forwarded upstream.

---

