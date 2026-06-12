---
title: "LibreOffice tabs in Calc (and Draw) in ver. 4.4"
date: 2014-11-25
forum: The Cafe
---

### Post by vasa1 on 2014-11-25
> Sheet tabs (Calc) and layer tabs (Draw) were moved to an independent row and are no longer displayed next to the horizontal scrollbar. As many visual styles under Linux (in addition to the default OS X configuration) use very thin scrollbars, these rendered the tabs too small to be clickable and, most importantly, readable. [fdo#36772]("https://bugs.freedesktop.org/show_bug.cgi?id=36772") (Tomaž Vajngerl and Samuel Mehrbrodt)
Source: [LibreOffice 4.4 Release Notes]("https://wiki.documentfoundation.org/ReleaseNotes/4.4#Tab_changes")

---

### Post by Dragonbite on 2014-11-25
Looks like a justified improvement.

---

### Post by WinEunuchs2Unix on 2014-11-27
I just encountered this monstrosity last night after downloading 4.3.x for Windows.  I'm glad they changed it.

---

### Post by vasa1 on 2014-11-27
> **WinEunuchs2Unix said:**
> I just encountered this monstrosity last night after downloading 4.3.x for Windows.  I'm glad they changed it.
There's a workaround for the current version so that you can keep your favorite theme. I'll post details later and PM you when I do so :)

---

### Post by vasa1 on 2014-11-29
The following will deal only with Calc and not Draw.

In the current releases of LibreOffice Calc, the sheet tabs and horizontal scrollbar are in the same row. With some gtk themes, Calc's sheet tabs appear very thin and the text in each tab may be to small to be legible.

To use this same theme because you like everything else about it, a small workaround is available.

Create **~/.gtkrc-LibO** with the following content:
```
include '/path/to/your/theme/gtk-2.0/gtkrc'

style "libreoffice-scrollbar" {
GtkScrollbar::slider-width = 18
}

widget_class "*" style "libreoffice-scrollbar"

```
The first line will point to *your* theme.
You may want a value lower or higher than 18 for slider-width.

Then modify the .desktop file for LibreOffice Calc to comment out the existing line with **Exec=** at the beginning. Below that line, have
```
Exec=bash -c 'GTK2_RC_FILES=$HOME/.gtkrc-LibO libreoffice --calc %u'
```
Note that you can still use Libreoffice Calc without this hack by running **libreoffice --calc** from the terminal.

---

### Post by vasa1 on 2015-01-29
From the [4.4 release notes]("https://wiki.documentfoundation.org/ReleaseNotes/4.4"):
[https://wiki.documentfoundation.org/images/e/eb/Tabs_new_row.png](https://wiki.documentfoundation.org/images/e/eb/Tabs_new_row.png)

---

### Post by The Cog on 2015-02-02
I understand moving the tabs out to a separate row, but I don't like the fact that they also removed the diagonal edges to the tabs.

---

