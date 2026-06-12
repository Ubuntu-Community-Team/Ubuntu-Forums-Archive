---
title: "Sweet integration of window buttons in nautilus 3.10"
date: 2014-01-03
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2014-01-03
Not sure if this will make it into Trusty or not but I asked:

[https://lists.launchpad.net/ubuntugnome-qa/msg00202.html](https://lists.launchpad.net/ubuntugnome-qa/msg00202.html)

Before:

[ATTACH=CONFIG]249149[/ATTACH]

After:

[ATTACH=CONFIG]249150[/ATTACH]

---

### Post by kansasnoob on 2014-01-03
Arrrgh .............. that's a terrible link!

Please give me time to figure out what's up :redface:

Fixed it, thanks for your patience.

---

### Post by mc4man on 2014-01-03
I would guess that if they went to .10 in trusty (unity) they'd remove the x button, return deco, ect. Doesn't fit in as seen..
(see ubuntu-desktop mailing list regarding  "Epiphany 3.10 landed sans title bar"

---

### Post by kansasnoob on 2014-01-03
> **mc4man said:**
> I would guess that if they went to .10 in trusty (unity) they'd remove the x button, return deco, ect. Doesn't fit in as seen..
(see ubuntu-desktop mailing list regarding  "Epiphany 3.10 landed sans title bar"

I just like the idea of creating more usable vertical space :)

---

### Post by tista on 2014-01-03
@kansasnoob,

Today Client-Side-Decorations is still under heavy developments, Actually, The 'Close-Button' on nautilus's new Titlebar(or Header-Bar) was hard-coded into the parent widget. So we could not change the layout of window-title-button yet, you know. :P
Gtk3 3.12 series might have such features in GtkHeaderbar, though it now has only a choice as boolean 'Show/Hide close button'.
Anyway the big problems would be revealed that Metacity window-title compositing makes visual glitches in the future.

Regards,
Tista

---

