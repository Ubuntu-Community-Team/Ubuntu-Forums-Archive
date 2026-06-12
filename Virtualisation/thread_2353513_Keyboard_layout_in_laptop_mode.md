---
title: "Keyboard layout in laptop mode"
date: 2017-02-22
forum: Virtualisation
---

### Post by rdmcguire01 on 2017-02-22
While switching into and out of vbox / vmplayer VMs something happens to my keyboard layout wherein num lock is using both the number pad and letter keys. Typing ubuntu gives me 4b4nt4. This is not a laptop. Here is what xkbmap tells me about my configured layout:

```
$ setxkbmap -print -verbose 10
locale is C
Trying to load rules file ./rules/evdev...
Trying to load rules file /usr/share/X11/xkb/rules/evdev...
Success.
Applied rules from evdev:
rules:      evdev
model:      pc105
layout:     us,us
variant:    ,
Trying to build keymap using the following components:
keycodes:   evdev+aliases(qwerty)
types:      complete
compat:     complete
symbols:    pc+us+us:2+inet(evdev)
geometry:   pc(pc105)
xkb_keymap {
    xkb_keycodes  { include "evdev+aliases(qwerty)"    };
    xkb_types     { include "complete"    };
    xkb_compat    { include "complete"    };
    xkb_symbols   { include "pc+us+us:2+inet(evdev)"    };
    xkb_geometry  { include "pc(pc105)"    };
};

```

How do I restore normal operation where num lock toggles the number pad only? A reboot fixes it but I want to understand the underlying issue and find a quick solution. It's as if it is running in laptop mode when this happens.

---

### Post by howefield on 2017-02-22
Moved to the "*Virtualisation*" forum, probably a better fit.

---

