---
title: "Conky Changing Dock Color"
date: 2017-09-22
forum: Ubuntu Development Version
---

### Post by Frogs Hair on 2017-09-22
I noticed conky changes the color of ubu-dock after autostart in the Ubuntu session. I have no idea what the cause my be.

> 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company 2nd Generation Core Processor Family Integrated Graphics Controller




Edit: Defaults affected as well.

---

### Post by again? on 2017-09-23
The conky window behaves like other windows.
You need to give sufficient gap or use 
```
own_window_type desktop
```

Turn off transparency to see the actual window.

---

### Post by Frogs Hair on 2017-09-23
That worked !

I had been experimenting with window types, but hadn't tried that yet because it caused conky to disappear when the desktop was selected on previous releases. I don't remember witch DE though.

Edit:

Thunderbird ,with or without conky causes the dock to change color when opened. ?

---

