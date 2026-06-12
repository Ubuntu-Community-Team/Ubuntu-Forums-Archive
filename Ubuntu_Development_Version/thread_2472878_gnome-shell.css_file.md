---
title: "gnome-shell.css file"
date: 2022-03-15
forum: Ubuntu Development Version
---

### Post by speartip on 2022-03-15
Does anyone know where the .css file is for the Yaru-dark theme in 22.04? Yaru-light seems to have one, but not dark.
What I'm trying to do is increase the font size in gnome-shell.

---

### Post by Claus7 on 2022-03-15
Hello,

this is how you will be able to see the content of the file:
askubuntu.com/questions/1261156/editing-yaru-gtk-theme-where-is-resource-com-ubuntu-themes-yaru-3-20-gtk-css

so in the Yaru-dark case you should type:
gresource extract /usr/share/themes/Yaru-dark/gtk-4.0/gtk.gresource /com/ubuntu/themes/Yaru-dark/4.0/gtk.css > /home/*user_name*/gtk.css

by substituting the *user_name* with yours and you could change the contents of gtk.css. 

There are a lot of fonts under:
/**********************
 * General Typography *
 **********************/

Next I would backup the original gtk.css file and substitute it with the one created above. Haven't tested it though.

Regards!

---

### Post by speartip on 2022-03-16
Thanks Claus7.
It used to be so easy. :P

---

### Post by speartip on 2022-03-19
Actually this issue has now resolved itself. After the latest update, the relevant css file is now in the Yaru folders and can be edited.

---

