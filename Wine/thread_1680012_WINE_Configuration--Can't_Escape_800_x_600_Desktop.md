---
title: "WINE Configuration--Can't Escape 800 x 600 Desktop Emulation..."
date: 2011-02-01
forum: Wine
---

### Post by casparov on 2011-02-01
Hi, Everyone...

In attempting to get an old game to run I reconfigured WINE to emulate a virtual desktop of 800 x 600 under the Graphics tab, "Windows Settings" (WINE configuration program)  

Now, I can't return to a normal desktop because the 800 x 600 desktop settings will not display the bottom portion of the Graphics tab; therefore, I can't check the box to save settings and return to a normal resolution.

Can anybody out there possibly solve this?

Many thanks for any help at all...

Regards,    Casp

---

### Post by _outlawed_ on 2011-02-01
Winetricks can help in terminal:

```
winetricks vd=off
```

Will disable virtual desktop, while:

```
winetricks vd=1000x1000
```

Will force a virtual desktop resolution that you set (used 1000x1000 as example).

---

### Post by casparov on 2011-02-01
Outlawed...

Thanks so much for your helping.

Unfortunately, both terminal commands generate "command not found" within Winetricks.

Does that make sense?

Regards,   C.

---

### Post by _outlawed_ on 2011-02-01
> **casparov said:**
> Outlawed...

Thanks so much for your helping.

Unfortunately, both terminal commands generate "command not found" within Winetricks.

Does that make sense?

Regards,   C.

Oops, sorry. I meant type in winetricks and it will open a window with a bunch of software. Scroll down and select one of the 2 options, vd=off or vd=widthxheight.

---

### Post by casparov on 2011-02-01
see below

---

### Post by casparov on 2011-02-01
Outlawed, you're a genius...

I installed Winetricks again, and your advice worked perfectly.

Thank-you so much for your time.

Regards,  C.

---

