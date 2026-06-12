---
title: "Remap Suspend Key (F4)"
date: 2016-08-15
forum: System76 Support
---

### Post by wannabegeek2 on 2016-08-15
I want to remap the suspend special function key (Fn F4) since it is adjacent to the lower volume key and causes frustration.

**Machine spec**

Galago Pro  
    Intel® Core™ i7-4770HQ CPU @ 2.20GHz × 8 
Ubuntu 16.04 LTS
    64-bit


I tried Xmodmap with no success.

[B]xev before doing anything
[/B]
```

    KeyRelease event, serial 37, synthetic NO, window 0x4400001,    root 0xd6, subw 0x0, time 3806795, (-639,1027), root:(321,1079),
    state 0x0, keycode 70 (keysym 0xffc1, F4), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False



```

**xmodmap command**

```

xmodmap -e "keycode 70 = F1"  

```

**xev output after**

```

KeyRelease event, serial 37, synthetic NO, window 0x4400001,
    root 0xd6, subw 0x0, time 4097183, (1163,259), root:(1163,311),
    state 0x0, keycode 70 (keysym 0xffbe, F1), same_screen YES,
    XKeysymToKeycode returns keycode: 67
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

Now I test, by pressing the function key and physical F1 hoping to send the machine into suspend. 

No love.

I'm not very expert with Xmodmap and I realize there are come caveats using it. Perhaps someone can offer help with Xmodmap or some other method.
TIA

---

### Post by wannabegeek2 on 2016-08-18
I realize this may not be the best forum for this question. However, the placement of the Galago's suspend key is really poor.
If no one can help here, will a mod please migrate this question to the right place ?

TIA

---

### Post by pauljw on 2016-08-20
> **wannabegeek2 said:**
> I realize this may not be the best forum for this question. However, the placement of the Galago's suspend key is really poor.
If no one can help here, will a mod please migrate this question to the right place ?

TIA

Since we're all just end users like yourself and Sys76 engineers don't hang out here, you'll do better to go to the Sys76 website and open a ticket.

---

