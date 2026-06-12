---
title: "Wine G15 x11drv/keyboard.c ... drops keys!"
date: 2009-06-05
forum: Wine
---

### Post by nautilus on 2009-06-05
Hi all.

I'm narrowing down why my G1-G6 keys of my G15 keyboard don't work with World of Warcraft running on Wine 1.1.21.

I followed the steps at [https://help.ubuntu.com/community/LogitechG15/](https://help.ubuntu.com/community/LogitechG15/) with the exception of using xev to build both my xmodmap and my XKeysymDB additions.  (By the way, my scancodes were very different than those on the page, but g15daemon seems to hum along nicely.)

The xev utility correctly identifies the G1-G6 keys, and labels them as such, so I know X11 is identifying them properly.  Wine doesn't seem to even notice them.

By running wine with WINEDEBUG=+key I have the following code to prove Wine is receiving the events:

```
...
trace:key:X11DRV_KeyEvent type 2, window 920000a, state 0x0000, keycode 0x00af
trace:key:X11DRV_KeyEvent nbyte = 0, status 0x0
trace:key:X11DRV_KeyEvent KeyPress : keysym=15000001 (G1), # of chars=0 / ""
trace:key:EVENT_event_to_vkey e->keycode = af
trace:key:X11DRV_KeyEvent keycode 0xaf converted to vkey 0x0
trace:key:X11DRV_KeyEvent type 3, window 920000a, state 0x0010, keycode 0x00af
trace:key:X11DRV_KeyEvent nbyte = 0, status 0x0
trace:key:X11DRV_KeyEvent KeyRelease : keysym=15000001 (G1), # of chars=0 / ""
trace:key:EVENT_event_to_vkey e->keycode = af
trace:key:X11DRV_KeyEvent keycode 0xaf converted to vkey 0x0
trace:key:X11DRV_KeyEvent type 2, window 920000a, state 0x0010, keycode 0x00af
trace:key:X11DRV_KeyEvent nbyte = 0, status 0x0
trace:key:X11DRV_KeyEvent KeyPress : keysym=15000001 (G1), # of chars=0 / ""
trace:key:EVENT_event_to_vkey e->keycode = af
trace:key:X11DRV_KeyEvent keycode 0xaf converted to vkey 0x0
trace:key:X11DRV_KeyEvent type 2, window 920000a, state 0x0010, keycode 0x00b0
trace:key:X11DRV_KeyEvent nbyte = 0, status 0x0
trace:key:X11DRV_KeyEvent KeyPress : keysym=15000002 (G2), # of chars=0 / ""
trace:key:EVENT_event_to_vkey e->keycode = b0
trace:key:X11DRV_KeyEvent keycode 0xb0 converted to vkey 0x0
trace:key:X11DRV_KeyEvent type 3, window 920000a, state 0x0010, keycode 0x00af
trace:key:X11DRV_KeyEvent nbyte = 0, status 0x0
trace:key:X11DRV_KeyEvent KeyRelease : keysym=15000001 (G1), # of chars=0 / ""
trace:key:EVENT_event_to_vkey e->keycode = af
trace:key:X11DRV_KeyEvent keycode 0xaf converted to vkey 0x0
trace:key:X11DRV_KeyEvent type 3, window 920000a, state 0x0010, keycode 0x00b0
trace:key:X11DRV_KeyEvent nbyte = 0, status 0x0
trace:key:X11DRV_KeyEvent KeyRelease : keysym=15000002 (G2), # of chars=0 / ""
trace:key:EVENT_event_to_vkey e->keycode = b0
trace:key:X11DRV_KeyEvent keycode 0xb0 converted to vkey 0x0
trace:key:X11DRV_KeyEvent type 2, window 920000a, state 0x0010, keycode 0x00b1
trace:key:X11DRV_KeyEvent nbyte = 0, status 0x0
trace:key:X11DRV_KeyEvent KeyPress : keysym=15000003 (G3), # of chars=0 / ""
trace:key:EVENT_event_to_vkey e->keycode = b1
trace:key:X11DRV_KeyEvent keycode 0xb1 converted to vkey 0x0
trace:key:X11DRV_KeyEvent type 2, window 920000a, state 0x0010, keycode 0x00b2
trace:key:X11DRV_KeyEvent nbyte = 0, status 0x0
trace:key:X11DRV_KeyEvent KeyPress : keysym=15000004 (G4), # of chars=0 / ""
trace:key:EVENT_event_to_vkey e->keycode = b2
trace:key:X11DRV_KeyEvent keycode 0xb2 converted to vkey 0x0
trace:key:X11DRV_KeyEvent type 3, window 920000a, state 0x0010, keycode 0x00b1
trace:key:X11DRV_KeyEvent nbyte = 0, status 0x0
trace:key:X11DRV_KeyEvent KeyRelease : keysym=15000003 (G3), # of chars=0 / ""
trace:key:EVENT_event_to_vkey e->keycode = b1
trace:key:X11DRV_KeyEvent keycode 0xb1 converted to vkey 0x0
trace:key:X11DRV_KeyEvent type 3, window 920000a, state 0x0010, keycode 0x00b2
trace:key:X11DRV_KeyEvent nbyte = 0, status 0x0
trace:key:X11DRV_KeyEvent KeyRelease : keysym=15000004 (G4), # of chars=0 / ""
trace:key:EVENT_event_to_vkey e->keycode = b2
trace:key:X11DRV_KeyEvent keycode 0xb2 converted to vkey 0x0
trace:key:X11DRV_KeyEvent type 2, window 920000a, state 0x0010, keycode 0x00b3
trace:key:X11DRV_KeyEvent nbyte = 0, status 0x0
trace:key:X11DRV_KeyEvent KeyPress : keysym=15000005 (G5), # of chars=0 / ""
trace:key:EVENT_event_to_vkey e->keycode = b3
trace:key:X11DRV_KeyEvent keycode 0xb3 converted to vkey 0x0
trace:key:X11DRV_KeyEvent type 2, window 920000a, state 0x0010, keycode 0x00b4
trace:key:X11DRV_KeyEvent nbyte = 0, status 0x0
trace:key:X11DRV_KeyEvent KeyPress : keysym=15000006 (G6), # of chars=0 / ""
trace:key:EVENT_event_to_vkey e->keycode = b4
trace:key:X11DRV_KeyEvent keycode 0xb4 converted to vkey 0x0
trace:key:X11DRV_KeyEvent type 3, window 920000a, state 0x0010, keycode 0x00b3
trace:key:X11DRV_KeyEvent nbyte = 0, status 0x0
trace:key:X11DRV_KeyEvent KeyRelease : keysym=15000005 (G5), # of chars=0 / ""
trace:key:EVENT_event_to_vkey e->keycode = b3
trace:key:X11DRV_KeyEvent keycode 0xb3 converted to vkey 0x0
trace:key:X11DRV_KeyEvent type 3, window 920000a, state 0x0010, keycode 0x00b4
trace:key:X11DRV_KeyEvent nbyte = 0, status 0x0
trace:key:X11DRV_KeyEvent KeyRelease : keysym=15000006 (G6), # of chars=0 / ""
trace:key:EVENT_event_to_vkey e->keycode = b4
trace:key:X11DRV_KeyEvent keycode 0xb4 converted to vkey 0x0
...
```

Of course, it's converting the keycodes to NULL vkeys!  So, when wading through the WINEDEBUG=+all log, I found this in the InitKeyboard function...

```
...
0009:trace:keyboard:X11DRV_InitKeyboard keycode 00ad => vkey 01b1
0009:trace:keyboard:X11DRV_InitKeyboard keycode 00ae => vkey 01b2
0009:trace:keyboard:X11DRV_InitKeyboard keycode 00af => vkey 0000
0009:trace:keyboard:X11DRV_InitKeyboard keycode 00b0 => vkey 0000
0009:trace:keyboard:X11DRV_InitKeyboard keycode 00b1 => vkey 0000
0009:trace:keyboard:X11DRV_InitKeyboard keycode 00b2 => vkey 0000
0009:trace:keyboard:X11DRV_InitKeyboard keycode 00b3 => vkey 0000
0009:trace:keyboard:X11DRV_InitKeyboard keycode 00b4 => vkey 0000
0009:trace:keyboard:X11DRV_InitKeyboard keycode 00b5 => vkey 01a8
0009:trace:keyboard:X11DRV_InitKeyboard keycode 00b6 => vkey 0100
...

```

The points of note are 'keycode 00af' through 'keycode 00b4', which as you see resolve to vkey 0000.  I'm not sure if this requires adding vkeys to the map for, but it seems to me they should resolve to vendor keys (01xx), but you'll notice keycode 00ad on the first line snaps up 01b1, so we can't simply vkey = keycode & 0x0100 it to get the new vkey... can we?

More to the point, why does this slip right through X11DRV_InitKeyboard?  Did I miss a step, or is this something that needs a patch?

---

### Post by waltons_pacman on 2009-06-12
I myself am very interested in this, but dont have the knowlege base or the experiance to really be of much help.

could someone smarter than myself take a look at this?

---

