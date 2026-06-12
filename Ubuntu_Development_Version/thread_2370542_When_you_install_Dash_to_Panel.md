---
title: "When you install Dash to Panel"
date: 2017-09-04
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-09-04
This is what happens, when you install Dash to Panel. Gnome Tweak is not there, but most of us know that app is available in Gnome. I didn't install it, but installed extensions from Gnome shell extensions. Dash to Panel takes over the top panel and the dash to make one panel and goes to the bottom and autohides too.

---

### Post by amano on 2017-09-05
sudo apt remove ubuntu-dock 

That should remove the ubuntu Dock. 

At present you have both installed (one as a deb file and the other via chrome-gnome-shell) and neither one notices the other.

Maybe the "ubuntu-dock" description could be changed to tell the user that this dock has to be removed via "apt remove".

---

### Post by Chanath on 2017-09-05
> **amano said:**
> sudo apt remove ubuntu-dock 

That should remove the ubuntu Dock. 

At present you have both installed (one as a deb file and the other via chrome-gnome-shell) and neither one notices the other.

Maybe the "ubuntu-dock" description could be changed to tell the user that this dock has to be removed via "apt remove".

That's not the way extensions work. And, extensions are galore. You going to prohibit the user from using extensions?

---

