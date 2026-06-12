---
title: "Can't use install 2 disk games"
date: 2009-06-06
forum: Wine
---

### Post by walpoles93 on 2009-06-06
Hi,

I'm trying to install MOHAA using PlayonLinux.  As it isn't a supported game I have to search for it myself and set up the prefixes etc.  Everything goes fine until I have to install the new disk.  The dialog comes up saying please insert new disk etc but when I try to take it out it comes up with an error saying:

```
Cannot unmount volume
An application is preventing the volume 'MOHAA1' from being unmounted.
```

Does anyone know why this is happening?  I've also tried through the terminal but with no luck.

---

### Post by uberlube on 2009-06-06
Might be why its not a supported game.

---

### Post by walpoles93 on 2009-06-06
I used to be able to play it fine on 8.10, but trying to get everything to work on 9.04 is a nightmare.

Just using wine, I can install it fine.  It lets me eject the disk and everything goes fine, until I try to play the game and then it comes up with the splash screen and does nothing.  Thats why I'm trying PlayonLinux.

There is also a version native to Linux but when I downloaded it, I couldn't get it to work.

---

### Post by asdfoo on 2009-06-06
'wine eject' at a terminal to eject the cdrom drive

---

