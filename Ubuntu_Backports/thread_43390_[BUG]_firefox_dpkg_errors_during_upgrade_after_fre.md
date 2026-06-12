---
title: "[BUG] firefox dpkg errors during upgrade after fresh install"
date: 2005-06-21
forum: Ubuntu Backports
---

### Post by sjmorgan on 2005-06-21
I just installed a fresh Hoary system and one of the first things I did was put the backports repository in my sources.list (as well as uncommenting out all the updates/security stuff). When I attempted to update, apt/dpkg spat out a load of errors related to firefox and firefox-gnome-support and the process died.

I seem to have got it all installed and working now by manually removing and reinstalling some stuff but I think somebody should try to address this issue if possible. Obviously if you need any more info just ask.

---

### Post by jdong on 2005-06-21
Exact errors would help. Did you do a dist-upgrade? It's ALWAYS preferred over just an upgrade. The package names DID change, thanks to Breezy...

---

### Post by sjmorgan on 2005-06-22
[QUOTE=jdong]Exact errors would help. Did you do a dist-upgrade? It's ALWAYS preferred over just an upgrade. The package names DID change, thanks to Breezy...[/QUOTE]Sorry, I don't have exact errors. I was kinda hoping somebody would have a testing machine they can reinstall with so that they can confirm it. I didn't do a dist-upgrade.

---

### Post by jdong on 2005-06-22
Please try to form the habit of using a dist-upgrade for all your updates.

---

