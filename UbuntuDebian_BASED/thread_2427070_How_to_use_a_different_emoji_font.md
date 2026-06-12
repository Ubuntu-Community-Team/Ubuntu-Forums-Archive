---
title: "How to use a different emoji font?"
date: 2019-09-17
forum: Ubuntu/Debian BASED
---

### Post by lirannl on 2019-09-17
I got chrome to render a different emoji font ([this is the font I want to be using everywhere]("https://github.com/C1710/blobmoji"), if you're curious), however, I can't get the emoji picker (I assume that's gtk?), gtk, or qt apps to use it. QT just uses b/w emojis for some reason, and gtk apps use Google's notocoloremoji (granted, I'm using a fork of it, but it has a different name in the system - when browsing fonts I see what I installed called Blobmoji, which is distinct from Noto Color Emoji). I tried loading a custom ~/.config/fonts.conf file which points at Blobmoji, but that only seems to work inside chrome, not gtk or qt apps.

I'm using gnome and my system is based on Ubuntu Disco (I have the official disco repos and all, it's the latest pop_os). Some help would be greatly appreciated, thank you!

---

### Post by cruzer001 on 2019-09-17
The wiki says you must remove all references to Noto Color Emoji.

And although similar, Pop is not Ubuntu.

---

### Post by jeremy31 on 2019-09-17
Moved to Ubuntu/Debian based

---

### Post by lirannl on 2019-09-17
I removed all references to Noto Color Emoji that I could find. That's how I got Chrome to render them. Unfortunately, that didn't do it for gtk/qt apps. I must be missing something, but I have absolutely no clue what.

Edit: I copied 2 files from /etc/fonts/conf.avail which had "Noto Color Emoji" in them and replaced them with Blobmoji, but that only fixed gtk apps. Qt apps still show noto (non color) emojis.

---

### Post by cruzer001 on 2019-09-17
Well it sounds like you did your homework :)
The readme file states it will **only** work on chrome.  Something the wiki is not clear about from what I have read.

I think you should post at GitHub
[https://github.com/C1710/blobmoji/issues](https://github.com/C1710/blobmoji/issues)

I have nothing else useful to offer, good luck.

Just seen your edit, I do not run Qt and surprise gtk works.  That should be added to the wiki.

---

### Post by milletramos28 on 2019-09-18
Download some applications on emoji.

---

### Post by uRock on 2019-09-18
> **milletramos28 said:**
> Download some applications on emoji.

huh?

---

