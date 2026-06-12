---
title: "Keyboard layout issues: no effect when changing settings in lxkeymap"
date: 2015-02-11
forum: Ubuntu Development Version
---

### Post by syntaxerror74 on 2015-02-11
One of the recent updates (~ 1.5 weeks) has totally screwed up my previous keyboard layout.
Still worse, I can't seem to REMOVE what's pre-set in there.

I've always loved the variant to have the ever-useless CAPS LOCK as "Compose" key.
However, by some magic the "shift_caps_toggle" option was added (it was  not there before), and now is obviously blocking Caps Lock from working  the way I want it!

I've tried everything imaginable to get the *"grp:shift_caps_toggle"* option removed from the layout, but it just does not work.

Plus, I've tried to *grep* for this option to be configured anywhere, to no avail.

Though not recommended, I even removed the "shift_caps_toggle" option from **~/.config/lxpanel/Lubuntu/panels/panel**, but now look:

```
andy@andy-lubuntubox:~$ lxkeymap -a
/usr/lib/python2.7/dist-packages/lxkeymap/helpers.py:46: GtkWarning: Unknown property: GtkMenu.ubuntu-local
  builder.add_from_file(ui_filename)
Sections: ['Global']
Layouts: ['us']
Variants: ['', '']
Options: ['grp:shift_caps_toggle']
['Global']
['compose:caps']
Lxkeymap autostart running...
```

Ehh?? 
Where else does lxkeymap (which is a Python script, by the way) pull that Options line from?
For a moment, I've even thought of a random variable which was not  cleared (like in C, when you don't initialize a string variable, it  might display some random garbage)

Sometimes lxkeymap recently complains that it is unable to save current settings. Hmmm...

---

