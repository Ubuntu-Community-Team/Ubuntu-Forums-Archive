---
title: "Ultra 5: how to force command line login? gdm hangs on launch (user error)"
date: 2007-07-04
forum: Sun Sparc Users
---

### Post by joespr on 2007-07-04
Hi all

Installed Ubuntu 6.06 successfully on Ultra 5. :D

In trying to get X installed I installed xubuntu (plus, it seems, gdm), then in trying to configure and testing different settings in my xorg.conf, I ended up with bad settings for both my keyboard and video card.

Therefore, now when I boot, Ubuntu launches gdm which puts me in X but since the xorg.conf settings are bad, my keyboard is useless.   :(
I cannot do anything, I cannot do an Ctrl+Alt+F1 or Ctrl+Alt+Fn, nor does Ctrl+Backspace or Ctrl+Alt+Backspace work. Stop+A does not bring me back to the ok prompt. All I can do is cut the power.

But Stop+A works normally prior to gdm launching.

So... aside from a reinstall, how can I force launch into command line mode, so I can login in on command line and disable gdm at least temporarily until I get the xorg.conf setting right? Is there a setting I can enter at the 'ok' prompt to not launch gdm? 

Currently if I do a Stop+A prior to gdm launch I can enter OBP commands, and I can do a 'boot Linux'
is there something I can do to prevent gdm launch?

Also, once I do get to log in, what is the best way to prevent gdm launch until I get xorg.conf correct?

Thanks
joespr

---

### Post by toastkid on 2007-07-05
This is just a guess based on the Intel world, but will it work if you do

boot Linux 1

or

boot Linux s

These should (I hope) take you into single user mode.

---

### Post by ykanello on 2007-07-06
You can also press alt+cntrl+F1 to get a console and stop gdm.

---

