---
title: "how to install recent items extension for gnome 46"
date: 2024-04-23
forum: Ubuntu Development Version
---

### Post by Claus7 on 2024-04-23
Hello,

recent items extension has seen an update for gnome 46, yet it is not offered by default. It needs installation. As a result download the code from here: [https://github.com/bananenfisch/RecentItems](https://github.com/bananenfisch/RecentItems)
extract the compressed folder and place it under ./local/share/gnome-shell/extensions.

Rename the folder to: [email]RecentItems@bananenfisch.net[/email]

and in order to avoid the error:
"~/.local/share/gnome-shell/extensions/RecentItems@bananenfisch.net/schemas/gschemas.compiled": open() failed: No such file or directory

issue the commands:
export GSETTINGS_SCHEMA_DIR=~/.local/share/gnome-shell/extensions/RecentItems\@bananenfisch.net/schemas 
glib-compile-schemas ~/.local/share/gnome-shell/extensions/RecentItems\@bananenfisch.net/schemas

It has some drawbacks at the time being, yet it is working more or less.

Regards!

---

