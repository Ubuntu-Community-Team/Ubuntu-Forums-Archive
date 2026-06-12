---
title: "Gnome Terminal has lost this menus"
date: 2015-12-18
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2015-12-18
It does not matter if the menus are set to appear in the Global menu or the application top panel it is now no longer possible to access File, Edit, etc. menus in Gnome Terminal. I can find no way to copy and paste into and out of gnome terminal.

Also, once maximised it does not restore to the original size that it was when first opened. To get that back we have to close and load again.

---

### Post by ventrical on 2015-12-18
I just updated with proposed open and got working gnome-terminal.

---

### Post by sammiev on 2015-12-18
Hi grahammechanical,

I can access File, Edit. etc in the menus as well as copy and paste into and out of gnome terminal.

Once maximized, I can restore to the original size that it was when first opened.

However, I have been taking all the proposed updates since the start of Xenia if it makes any difference.

Thanks

---

### Post by ventrical on 2015-12-18
Ok .. gottchya! :)

[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/1527704](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/1527704)

---

### Post by ventrical on 2015-12-18
> **sammiev said:**
> Hi grahammechanical,

I can access File, Edit. etc in the menus as well as copy and paste into and out of gnome terminal.

Once maximized, I can restore to the original size that it was when first opened.

However, I have been taking all the proposed updates since the start of Xenia if it makes any difference.

Thanks

There is bug ... even on newer machine. There is a fickerty mouse and the pull down menus won't work with the Copy nor Paste option but I can use mouse to copy n paste but it is blind mouse in terninal.

Regards..

please check out bug I posted.

---

### Post by grahammechanical on 2015-12-18
I do have proposed enabled. Terminal does not allow Ctrl+C or Ctrl+V. It has to be done through the Edit menu. And I was able to copy a screen print from a command just the other day to use in a thread that I was replying to.

It is version 3.18.2.1ubuntu2. But it is lacking the Gnome redesign that recent utilities have been getting. Where the menus are now accessed through 2 buttons.

EDIT: I have another install of Xenial on this machine & that has Terminal 3.18.2.1ubuntu2 which still has menus in the global menu. Strange goings on. Differences? Radiance & Ambiance? No it is not that. Nouveau & Nvidia? Let us see.

EDIT 2: As of 21 Dec this has been fixed. Menus are back either in the global menu or the terminal window's top panel according to the setting. And it is nothing to do with anything I have done except a daily update.

Regards.

---

