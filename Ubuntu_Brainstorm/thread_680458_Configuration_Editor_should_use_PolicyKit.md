---
title: "Configuration Editor should use PolicyKit"
date: 2008-01-27
forum: Ubuntu Brainstorm
---

### Post by Mr. Picklesworth on 2008-01-27
A neat feature in gconf is the ability to set default and mandatory keys. Particularly handy when I want to set a specific list of random screensavers, but gnome-screensaver keeps putting it back to its own list of every screensaver. I can change the list manually, set it as a mandatory key and never worry again!

Sadly, that is not so, because setting a key as mandatory or default requires root privileges. (Which definitely necessitates an option to "lock" a key for the local user, but I'll leave that be). The problem with running "sudo gconf-edit" is that now all those keys I had set for my local user are gone; instead, all I can see is the keys set by the root user.
Thus, that function is almost useless.

At the moment, gconf-edit demands that I be running as root in order to set a key as mandatory or default. It would be very good if we were instead greeted with an authorization dialog, ultimately leading to that key being set as mandatory very quickly and easily.

---

### Post by 23meg on 2008-01-28
That sounds like a good enhancement request that's fit for the GNOME bug tracker. Please file it there if it hasn't already been filed.

---

