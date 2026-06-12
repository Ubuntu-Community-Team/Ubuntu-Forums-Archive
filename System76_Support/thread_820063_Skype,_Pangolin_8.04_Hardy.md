---
title: "Skype, Pangolin 8.04 Hardy"
date: 2008-06-05
forum: System76 Support
---

### Post by roscoetuff on 2008-06-05
Have Skype, and Hardy on a Pangolin. Going fine. Everything works. Problem is in the "Software Sources" that keep telling me they are out of date. Not true. But the Skype is the problem. Software sources won't update... because of Skype. Says 8 days ago last updated. Seems an endless loop. Any ideas?

---

### Post by thomasaaron on 2008-06-06
1) Try: sudo apt-get install -f

2) Please post your exact errors (or screenshots of them)

3) Did you add something to your sources.list file?

---

### Post by roscoetuff on 2008-06-09
Have attached screen shots. Thanks!

---

### Post by thomasaaron on 2008-06-09
It looks like you have either typed in the Skype repository wrong, or it is no longer available -- or temporarily offline.

Go to System > Administration > Software Sources.
Click the Third-Party tab.
De-select the entry that has "Skype" in it.
Then run: sudo apt-get update

That should do the trick.

---

### Post by roscoetuff on 2008-06-12
That worked! Thanks!:guitar:

---

