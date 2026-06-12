---
title: "global key binding for usp"
date: 2006-12-16
forum: Ubuntu System Panel
---

### Post by -fin on 2006-12-16
Hey guys

I just tried to find out how to create keybindings in GNOME

As I knew that the Deskbar-Applet has such a feature, i checked out the cvs tree and tracked the method used for the binding process.

You might be interested in this:

[http://raphael.slinckx.net/deskbar/index.php#download](http://raphael.slinckx.net/deskbar/index.php#download) - check out the CVS

The files responsible are:
/deskbar/keybinder/Keybinder.py -- Methods: bind
/deskbar/keybinder/tomboykeybinder.c -- Methods: tomboy_keybinder_bind & do_grab_key

Hope to have helped - however, i am not a GNOME/GTK programmer myself, so i guess i won't be able to help you any further

hoping for such a feature in usp2 of course ;)

greets

---

### Post by chanders on 2006-12-16
Hey! Thanks so much for your research. Myself or Malac will look at it and see if we can get it implemented ;-)

---

