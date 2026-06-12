---
title: "'Media Play/Pause' key stopped working on gazp9"
date: 2014-10-30
forum: System76 Support
---

### Post by KoRnKloWn on 2014-10-30
My 'Media Play' key  stopped working, I upgraded to Ubuntu 14.10, but it worked for a while  after the upgrade, I think it may have been after the latest Linux Kernel  update. Anyways, I've tried everything, I tried resetting it in Keyboard  Shortcut settings, however this incorrectly sets it to AudioPlay when  it should be XF86AudioPlay, I also used dconf to switch it back to  default (XF86AudioPlay), and it still does nothing.

Here is the output from xev:
```
FocusOut event, serial 37, synthetic NO, window 0x6600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 37, synthetic NO, window 0x6600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 37, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
```

Which is strange, because when I use xev for volume down it produces this:
```
FocusOut event, serial 37, synthetic NO, window 0x6600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 37, synthetic NO, window 0x6600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 37, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   4   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 37, synthetic NO, window 0x6600001,
    root 0x9c, subw 0x0, time 25627004, (183,422), root:(968,474),
    state 0x0, keycode 122 (keysym 0x1008ff11, XF86AudioLowerVolume), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

---

