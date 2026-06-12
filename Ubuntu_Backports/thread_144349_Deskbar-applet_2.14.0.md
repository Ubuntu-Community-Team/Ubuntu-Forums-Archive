---
title: "Deskbar-applet 2.14.0"
date: 2006-03-14
forum: Ubuntu Backports
---

### Post by magnusbb on 2006-03-14
I have today backported the fresh 2.14 release of Deskbar-applet for use with Ubuntu Breezy. It works perfectly, and includes Evolution support.

 (not Beagle support at this time, as it is too unstable on my computer).

TIP: For those who want to use this fresh build, I would reccommend to delete the gconf keys and the config dir from the former deskbar-installation. This is easily done by opening the GNOME search tool, and searching for  "deskbar" in your HOME directory. Make sure you include "show hidden and backup files" - then delete the two directories you'll find (config-dir and gconf), and it should work.

---

### Post by engla on 2006-03-14
This is cool.
I tried it myself yesterday, and I was amazed that it just compiled on breezy, no dependency trouble!

However, I couldn't use my build due to some gconf error that was thrown on startup... Did you do anything special to make it work, or was it a plain compile? Other tips?

I can't use the attached .deb sadly; since I'm on ppc I have to make my own..

---

### Post by magnusbb on 2006-03-14
Yes, thanks for noticing - I should have mentioned that you will have to delete both the config dir and the gconf dir, in order to make a new installation of deskbar work correctly. I have added some instructions to my first post now.

---

### Post by ernando on 2006-04-17
Hi, thanks for the backported :)
No prob during installation, but when I try to add to panel I got this error :

The panel encountered a problem while loading "OAFIID:Deskbar_Applet".
Do you want to delete the applet from your configuration?

Please help me. Thanks you...

---

