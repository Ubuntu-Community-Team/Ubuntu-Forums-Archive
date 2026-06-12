---
title: "Gnome themes and icons in root browser"
date: 2005-08-04
forum: The Cafe
---

### Post by Curlydave on 2005-08-04
Why do the vast majority of Gnome themes remove the individual icons from the root browser? Instead of appropriate icons, all files and folders are represented by page icons. The default theme doesn't do this, and a few themes don't, but the vast majority of custom themes do. What's up with this?

---

### Post by varunus on 2005-08-04
This is generally because if you open a root nautilus, it tries to use the theme you have set for the user.  However, if you have the theme kept in ~/.themes/themename or ~/.icons/iconthemename, it won't work.  You need to either copy the theme to /root/.themes/ or /root/.icons, or do what I do, and keep all of your themes in /usr/share/themes or /usr/share/icons.

You can also type gksudo gnome-control-center to adjust the theme for root applications.

---

