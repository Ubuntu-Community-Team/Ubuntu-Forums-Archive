---
title: "Dark Theme Issue GTK4"
date: 2023-08-31
forum: Ubuntu Development Version
---

### Post by TenPlus1 on 2023-08-31
When selecting a dark theme like Greybird-dark or Adwaita-dark in Xubuntu's Appearance setting, GTK4 applications do not use the dark-theme and appear in light mode.

The only way to fix this was to enter this line into terminal:

echo "export GTK_THEME=Greybird-dark:dark" >> ~/.profile

Would it be possible to add an option in the Appearance tab that allows the user to toggle a switch for dark mode to make this easier ?

---

### Post by Wise Ferret on 2023-09-07
GTK4 themes are broken for me on standard ubuntu. Even though my selected theme is yaru-bark-dark (for apps and for gnome-shell), I get only the default orange theme for all GTK4 apps, and some of them (like settings and nautilus) appear in the light version, even though the dark option is selected.
OP's workaround works for my GTK4 apps, but not for gnome-shell.

---

### Post by jbicha on 2023-09-07
There was a new dark theme regression this week that is fixed in the gnome-session updates that is rolling out now. You will need to log out and log back after installing the update to get the fix.

This is unrelated to the Xubuntu issue.

---

