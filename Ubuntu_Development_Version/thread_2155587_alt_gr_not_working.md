---
title: "alt gr not working"
date: 2013-06-18
forum: Ubuntu Development Version
---

### Post by wildgeier on 2013-06-18
( Sorry, the title should be ' "alt gr"-key is not working properly' )

Hi

I just installed ubuntu 13.10 and now my 'alt gr' ke[SIZE=2]y is not working how it should.

When i run xev, pressing 'alt gr' gives:

[/SIZE]```

KeyPress event, serial 41, synthetic NO, window 0x3800001,
     root 0x256, subw 0x0, time 597707, (-545,157), root:(245,209),
     state 0x10, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
     XKeysymToKeycode returns keycode: 92     XLookupString gives 0 bytes:
     XmbLookupString gives 0 bytes:
     XFilterEvent returns: False

  KeyRelease event, serial 41, synthetic NO, window 0x3800001,
     root 0x256, subw 0x0, time 597787, (-545,157), root:(245,209),
     state 0x98, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
     XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes:
     XFilterEvent returns: False

```

and ISO_Level3_Shift should be right ... but the key seems to function more like an 'alt'-key ( 'alt-gr'+E does not produce an euro-sign (like it should on a french keyboard),  but instead opens the menu 'Edit' ... but 'alt-gr'+Tab does not change windows)

Setting "Key to choose 3rd level" in Keyboard > Layout Settings to "Right Alt" does not make it better.

Any ideas ?

---

### Post by matt_symes on 2013-06-18
Thread moved to **Ubuntu +1**.

---

### Post by wildgeier on 2013-06-22
This work-around worked for me:

-map keycode 108 to "Mode_switch"  instead of "ISO_Level3_Shift"

-edit the .Xmodmap file (copy the  "ISO_Level3_Shift" column to the "Mode_switch" column)

---

