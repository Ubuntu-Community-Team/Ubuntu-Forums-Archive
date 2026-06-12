---
title: "Where has startup application been moved to or renamed?"
date: 2013-08-17
forum: Ubuntu Development Version
---

### Post by philinux on 2013-08-17
Typing startup in dash only brings up the usb disk creator.

---

### Post by grahammechanical on 2013-08-17
I cannot find it either. I tried looking in all the utilities in case it was now in a tab somewhere. On my system the terminal is also missing from the Dash. It is still installed. I locked its icon to the Launcher and it will launch but it is not in the Dash although xterm and uxterm are still there.

Regards.

---

### Post by philinux on 2013-08-17
> **grahammechanical said:**
> I cannot find it either. I tried looking in all the utilities in case it was now in a tab somewhere. On my system the terminal is also missing from the Dash. It is still installed. I locked its icon to the Launcher and it will launch but it is not in the Dash although xterm and uxterm are still there.

Regards.


Yep same here. Is it part of gnome-session or is there a terminal command for it.

---

### Post by howefield on 2013-08-17
> **philinux said:**
> Yep same here. Is it part of gnome-session or is there a terminal command for it.

philinux, try terminal command

```
gnome-session-properties
```

---

### Post by philinux on 2013-08-17
> **howefield said:**
> philinux, try terminal command

```
gnome-session-properties
```

Dang forgot that. Locked to launcher now cheers.

---

### Post by mc4man on 2013-08-17
It should be showing up in a Dash search in unity or the apps window in gnome-shell. There was a patch to the .desktop last year to allow this, - "13_display_session_properties.patch"
The patch removed this line from session-properties.desktop
NoDisplay=true

it shows up fine here in a Dash search, just need to type st & it appears

---

### Post by philinux on 2013-08-18
> **mc4man said:**
> It should be showing up in a Dash search in unity or the apps window in gnome-shell. There was a patch to the .desktop last year to allow this, - "13_display_session_properties.patch"
The patch removed this line from session-properties.desktop
NoDisplay=true

it shows up fine here in a Dash search, just need to type st & it appears

Something must have updated in the last 24 hours it's now back and terminal is too. :P

---

