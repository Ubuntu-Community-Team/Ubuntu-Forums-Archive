---
title: "Adding printer"
date: 2013-04-10
forum: Ubuntu Development Version
---

### Post by jallain on 2013-04-10
I just insalled 13.04 this morning. I tried to add my printer using the printer applet in settings. It finds my printer and when I click add, the applet just closes. No printer added. I tried to use the web interface and I can't log in for adming purposes. No user or password combination will work. Any ideas on where to start?

---

### Post by jallain on 2013-04-11
My bad. I left out the most important part of the equation. I installed the Gnome version of Ringtail. I tried the Unity version and printer applet works just fine. It's just the gnome version where I cannot add a printer. The printer applet just disappears when I select my printer. If it matters, the printer is wireless. The applet does find it but does not install it.

---

### Post by kurt18947 on 2013-04-11
I find the printer app in both Unity & Gnome Shell lacking.  As good fortune would have it, the old style app still works.  I use Synaptic but software center should work as well.  Look for this app:  system-config-printer.  Install if necessary then run from either a 'run box' (alt-f2) or terminal.  The older app tells me more and lets me configure more.

---

### Post by jallain on 2013-04-12
Thank you! A most excellent solution. That's the only show stopper I found for installing it. Thanks again...

---

### Post by gillmt on 2013-04-13
Had the same problem in Gnome but added HPLIP as I have an HP printer - printer appeared in "Add printer" immediately

---

