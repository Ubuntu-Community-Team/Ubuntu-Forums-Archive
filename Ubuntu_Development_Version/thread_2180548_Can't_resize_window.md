---
title: "Can't resize window"
date: 2013-10-13
forum: Ubuntu Development Version
---

### Post by Sageth on 2013-10-13
Is anyone else having a situation where they can't resize any window?  I can make it fullscreen and minimize, but if I want to make it a window and then change how much of the desktop space it's using, I can't.  I searched Launchpad and the forums here, but didn't see anything about it.

If no one else is having the issue, could someone recommend which package I would need to reinstall?  Presumably Unity, but I don't know that for sure.

---

### Post by ping-wu on 2013-10-13
The easiest way is to move your cursor all the way up, then move down a little bit (i.e., place your cursor in the menu bar), double-click it (the menu bar).  This will reduce your "full screen" to a window (or partial screen).  Drag its corner to re-size it.

---

### Post by Sageth on 2013-10-13
I understand that, but the part where I'm supposed to drag it to resize doesn't work.  I get the changed icon (the arrow with the line), but it doesn't actually move.

---

### Post by Cavsfan on 2013-10-14
> **Sageth said:**
> I understand that, but the part where I'm supposed to drag it to resize doesn't work.  I get the changed icon (the arrow with the line), but it doesn't actually move.

Sounds like it's Compiz related. I have had that issue. Went into CCSM and changed some stuff under Windows Management.
Everything worked great then.
This is only for Gnome Flashback though, not Unity. I believe Unity does what it wants and doesn't have this problem.

[ATTACH=CONFIG]246942[/ATTACH]

---

### Post by Sageth on 2013-10-14
Ah, thanks!  That gave me enough to go on.  Rebooting on its own didn't help, and I went into CompizConfig and "Resize window" was checked.  I unchecked and rechecked it and it didn't work.  So then I did the following to determine what compiz items were installed and reinstall them:
```

dpkg --get-selections | grep -i compiz
sudo apt-get install compiz compiz-core compiz-gnome compiz-plugins-default compizconfig-settings-manager libcompizconfig0 python-compizconfig --reinstall

```

When I went back in, there were LOTS of Compiz settings unchecked, but this time checking the box allowed me to resize immediately.  Thanks for your help... just needed a small pointer.

---

