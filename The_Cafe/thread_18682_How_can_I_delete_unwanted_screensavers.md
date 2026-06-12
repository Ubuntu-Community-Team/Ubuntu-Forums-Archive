---
title: "How can I delete unwanted screensavers?"
date: 2005-03-08
forum: The Cafe
---

### Post by JumpyLINUX on 2005-03-08
Hey,
Is this the right place to ask questions conserning Ubuntu? If so I have a question. **How can I delete unwanted screensavers that were preinstalled with Ubuntu? **Please note that I'm new to Linux, and don't know almost anything about it.

---

### Post by landotter on 2005-03-08
You most likely have two screensaver metapackages installed, xscreensavers and glxscreensavers. You can delete either of these with Synaptic.

If you just want to delete individual screensavers, you can go into /usr/lib/xscreensaver and delete the executables--or you can just run desktop preferences/screensavers, and enable/disable the ones you like.

---

### Post by JumpyLINUX on 2005-03-09
Thanks I'll try that!  :grin:

---

### Post by JumpyLINUX on 2005-03-10
I deleted a whole lot of screensavers from /usr/lib/xscreensaver/, but they appear still on the list of XSCREENSAVER.  :-(  Only now they're greyed and it states they are not installed. It's really frustrating to choose a screensaver when the list is endless.  :mad: 

Should I simply remove the whole program? Or is there a way to get completely rid of the extra screensavers?

---

### Post by Retrix on 2005-03-10
Perhaps try deleting the corresponding xml files from /usr/share/xscreensaver/config? Personally I wouldn't bother though, I just have a random ssaver set anyway.

---

