---
title: "Wine Intercepts ALT key?"
date: 2010-07-14
forum: Wine
---

### Post by McRat on 2010-07-14
Is there a way to stop WINE from intercepting the ALT key?

TIA!

---

### Post by hikaricore on 2010-07-14
I don't think that wine is intercepting anything.
Perhaps you should explain your issue.

---

### Post by McRat on 2010-07-14
When you hit ALT-V, it highlights the Wine menu in the top left corner.  

Usually hotkeys have a setup feature, but I can't find it.  I can work around it (and do) by not using that hotkey (it controls the 3D view in my CAD app) but I've been using it for 20 years so it's a hard habit to break.

---

### Post by cogadh on 2010-07-14
Are you referring to the Applications menu in Ubuntu? If so, this is not a Wine issue, it is something to do with your Gnome configuration, though I am not aware of ALT+V being a particular shortcut for the menu.

---

### Post by McRat on 2010-07-14
If you look in the upper left corner of the application window, you'll see a little wineglass.

The more I play with, the more I realize that it doesn't always do the same thing.  If the last keyboard stroke before the ALT-V was a successful ALT command, then it will ALT-V -once- correctly.  But most the time, ALT-V will give focus to the Wineglass, which does not even have a ALT-V menu pick.

Perhaps it is Gnome.  But it doesn't happen on non-Wine applications that I can tell.

---

### Post by cogadh on 2010-07-14
Well, I did find this in the [Wine FAQ]("http://wiki.winehq.org/FAQ#head-7eee1ae08420583a297b20761702283dbb4e9ec4"):
> **[SIZE="3"]6.16. Some key combinations in my application do not work.[/SIZE]**

Even in full screen mode, window managers typically capture some keys. For example, in KDE and GNOME, Alt+Left Click is used to move the whole application window by default. Thus, this key combination is not available to applications in Wine. You have to disable the colliding combinations in your window manager. For KDE, see Control Center/Window Behaviour or (better) Window-specific settings/Workarounds/Block global shortcuts. For GNOME, see System/Preferences/Windows and change the "Movement Key" setting. Also see System/Preferences/Keyboard Shortcuts for specific keyboard combinations.
(Keywords: Keyboard, Shortcut, Modifier, Alt, Ctrl, Control.)
Not sure if it applies here, like I said I'm not sure that ALT+V is a standard key combo in Gnome, but it couldn't hurt to check.

---

