---
title: "The FULL reason for different Firefox icons"
date: 2006-10-28
forum: The Cafe
---

### Post by SoloSalsa on 2006-10-28
I've read every thread I could find on the subject.  They all note that the Firefox packaged with Ubuntu has been modified.  *So*, what are the modifications?  What *exactly* is different from 'normal' Firefox, and the 'integrated' Firefox?
The only difference I see is edit>preferences (rather than tools>options) and home.

Thanks!

---

### Post by aysiu on 2006-10-28
Actually, that's not even a difference.

The Linux version always has Edit > Preferences, regardless of whether it's from Ubuntu or Mozilla.

Tools > Options is a Windows thing.

But for more on the subject you're asking about, read [this thread](http://ubuntuforums.org/showthread.php?t=285526&highlight=firefox+iceweasel).

---

### Post by mahy on 2006-10-28
> **aysiu said:**
> Tools > Options is a Windows thing.


Tools -> Options (or Preferences) is also a KDE thing ;)

Anyway, i don't get why there's a proper Firefox icon in the menu and also in the Firefox's About screen, but only the globe without a fox in the task list. Any ideas?

---

### Post by aysiu on 2006-10-28
> **mahy said:**
> Tools -> Options (or Preferences) is also a KDE thing ;) Not for Firefox.

What you're talking about is Settings > Configure *application name*.

---

### Post by GStubbs43 on 2006-10-28
> **mahy said:**
> 
Anyway, i don't get why there's a proper Firefox icon in the menu and also in the Firefox's About screen, but only the globe without a fox in the task list. Any ideas?

It's a known bug... until it gets fixed, you can do:
```

sudo cp /usr/share/pixmaps/firefox.png /usr/share/firefox/chrome/icons/default/default.xpm

```

---

### Post by mahy on 2006-10-28
> **aysiu said:**
> Not for Firefox.

What you're talking about is Settings > Configure *application name*.

Yes, that's exactly what i meant. Names are different, but the actual placement is the same. I didn't mean Firefox in KDE.

---

### Post by mahy on 2006-10-28
> **GStubbs43 said:**
> sudo cp /usr/share/pixmaps/firefox.png /usr/share/firefox/chrome/icons/default/default.xpm


Thanks a lot! Now i'm gonna do the same with Thunderbird.

EDIT: Managed! Now i'm using proper Mozilla products. (Previously i thought the icon is hard-coded into the program itself.)

---

