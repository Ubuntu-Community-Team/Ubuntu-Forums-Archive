---
title: "Wine fonts"
date: 2010-10-11
forum: Wine
---

### Post by bryncoles on 2010-10-11
Hi all. I'm trying to install wine, as I sudden;y need some windows-only software. Alas, wine needs some configuring. The fonts come out looking like this: (I hope the picture is attached). 

What can I do?

---

### Post by dino99 on 2010-10-11
if not already done, add this ppa to synaptic repo tab:

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

update and then into a terminal run: winetricks to add the missing fonts files

if you have the needed fonts from windows, you can also copy/paste them into .wine/drive_c/windows/Fonts

note: next time use the "wine" subforum for related issue

---

### Post by TheAnachron on 2010-10-11
Basically what dino99 said. Make sure to have the latest version of winehq.

---

### Post by bryncoles on 2010-10-11
Cheers for that! The fonts are now readable, but they're a little small. Any idea how I can fix the size issue?

Also, sorry for posting in the wrong forum. I'll report myself and get moved!

---

### Post by dino99 on 2010-10-11
about the font size you might tweak the properies of your app ( sometime you can do it with the keys: ctrl + and ctrl - )

---

### Post by s.fox on 2010-10-11
Thread moved to Wine as per request of original poster.

---

