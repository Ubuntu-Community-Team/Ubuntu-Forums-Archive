---
title: "Ubuntu 18.04 Gnome Tweak says no Shell Installed"
date: 2018-04-08
forum: Ubuntu Development Version
---

### Post by jonesyp on 2018-04-08
Hello,

I have installed Gnome Tweak and it is telling me that no Shell is installed.  Is this normal?

[IMG]https://s14.postimg.org/x33kj1wch/Tweaks.png[/IMG]

Thanks

---

### Post by exploder on 2018-04-08
Nice find! The tweak tool does still appear to work though because I used it to turn off the desktop icons.

---

### Post by PaulW2U on 2018-04-08
> **jonesyp said:**
> I have installed Gnome Tweak and it is telling me that no Shell is installed.  Is this normal?
Yes but it's actually telling you that no shell **theme** is installed. [Why is Shell theme disabled in Gnome Tweak Tool?]("https://askubuntu.com/questions/545741/why-is-shell-theme-disabled-in-gnome-tweak-tool") explains how this option works better than I can.

I tried it here and if I had additional themes available then I would be able to select and install them.

---

### Post by vanadium on 2018-04-10
In short, install the gnome extension "User themes". This will activate this option "Themes - Shell" you refer to, and enable to apply your own installed themes to the shell.

---

### Post by logix2 on 2018-04-11
By the way, the "User theme" Gnome Shell extension is part of the "[FONT=&quot]gnome-shell-extensions" package in Ubuntu. So install that package, then restart Gnome Shell (Alt + F2, type "r", then ENTER) and then you'll be able to change the Gnome Shell theme.[/FONT]

---

### Post by jbicha on 2018-04-11
If you click the application menu for Tweaks and then click About, it will tell you your GNOME Shell version.

---

