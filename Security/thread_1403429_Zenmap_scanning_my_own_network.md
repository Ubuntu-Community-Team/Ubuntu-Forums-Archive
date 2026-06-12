---
title: "Zenmap scanning my own network"
date: 2010-02-10
forum: Security
---

### Post by dogdo on 2010-02-10
Hi

I want to do a 'slow comprehensive scan' of my network but zenmap keeps saying i need root privileges. I know that ubuntu forums has a strict anti root how to policy but where else am i going to find reliable advice?

---

### Post by mkvnmtr on 2010-02-10
Open a terminal type sudo senmap. Then type your passwork and press enter.  On my Gnome Ubuntu it shows up in the menu as zenmap and zenmap with root. On other desktops sometimes it does not.

---

### Post by Sarmacid on 2010-02-10
You can edit the menu entry. Go to System -> Preferences -> Main menu. There you just need to look for zenmap, hit properties and on the command, add 'gksu' at the start. Then you'll be prompted for password when you want to use it, but you'll be able to do all kinds of scans.

---

