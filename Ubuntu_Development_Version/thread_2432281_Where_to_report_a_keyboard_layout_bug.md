---
title: "Where to report a keyboard layout bug?"
date: 2019-11-29
forum: Ubuntu Development Version
---

### Post by Irihapeti on 2019-11-29
I've discovered a bug in a keyboard layout in 20.04. However, I've got no idea which package I should report against.

Is there anyone who can tell me where the report should go?

---

### Post by corradoventu on 2019-11-30
I found some bugs about keyboard layout:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1812266](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1812266)
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1813304](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1813304)
see if they can help you

---

### Post by Irihapeti on 2019-11-30
Thanks. I've reported the bug against Gnome-shell.

I might try spinning up a VM with a different DE and see if that makes any difference.

---

### Post by Irihapeti on 2020-03-21
I reported a bug against Gnome-shell, but I'm not sure that Gnome-shell is the problem.

I get the keyboard layout misbehaviour in Gnome-shell and Openbox (where the layout is set using "setxkbmap"), but NOT in xubuntu or kubuntu.

Other than these discoveries, no progress.

Any further ideas?

---

### Post by dino99 on 2020-03-21
> **Irihapeti said:**
> I reported a bug against Gnome-shell, but I'm not sure that Gnome-shell is the problem.

I get the keyboard layout misbehaviour in Gnome-shell and Openbox (where the layout is set using "setxkbmap"), but NOT in xubuntu or kubuntu.

Other than these discoveries, no progress.

Any further ideas?

Also assign keyboard-configuration package, with details about language used and kind of keyboard (qwerty, ...)

---

