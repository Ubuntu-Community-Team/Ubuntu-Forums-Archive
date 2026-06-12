---
title: "Changing Languages with Alt+Shift"
date: 2013-10-12
forum: Ubuntu Development Version
---

### Post by Chelidze on 2013-10-12
With old Ubuntu I easily could set keyboard shortcut that would allow me to change keyboard languages with Alt+Shift but on Ubuntu 13.10 There is a new menu that most probably does not even work.

[http://i.imgur.com/I0uuVRC.png](http://i.imgur.com/I0uuVRC.png)

As I understand Super+space should change the keyboard language.
Does not work and even when I want to set my custom shortcut It just does not work and reverts back to Super+Space  

[http://mkerala.com/u/image.php?di=4084](http://mkerala.com/u/image.php?di=4084)

---

### Post by varunendra on 2013-10-14
> **Chelidze said:**
> As I understand Super+space should change the keyboard language.
Does not work and even when I want to set my custom shortcut It just does not work and reverts back to Super+Space

What are the settings in **dconf Editor > org > gnome > libgnomekbd > keyboard > options** ?

I'm on 12.04 and it is **[...... 'grp\tgrp:alt_shift_toggle']** here with Alt+Shift to change the layout. Does that work for you?

---

### Post by grahammechanical on 2013-10-14
In 13.10 the Ibus key combination has changed to Super+Space but it is not working. Shift+Super+Space will change from a previously selected non-default language to the default language (English in my case) but neither Super+Space nor Shift+Super+Space will cycle through the options. At least on my Saucy install.

Regards.

---

### Post by GeorgeVita on 2013-10-14
In my desktop (105 keys HP keyboard) the "super" keys are indicated as:
**Mod4+Super+Hyper** or **Super** or **Super L** or **Super R**
depending the key combination, pressing sequence and setting menu used!
(pressing Ctrl before the super key has different output than pressing super key and then Ctrl).

From "System Settings, Keyboard, Shortcuts, Typing, Switch to ... source:", I managed to control various keyboard layouts using **Ctrl+Menu** and **Alt+Menu**

As the final release is almost here, I feel we cannot specify a bug now, so my work around is:

```
sudo gedit /etc/default/keyboard
```
(for Lubuntu replace "gedit" with "leafpad")

Change parameters to appropriate (below is the example for Us/Gr):
```
XKBLAYOUT="us,gr"
XKBOPTIONS="grp:ctrl_shift_toggle"
```

Save edited file, log-out, log-in and test it (possibly you have to reboot).
When you have just 2x layouts you can use "scroll LED" for the indicator:
```
XKBOPTIONS="grp:ctrl_shift_toggle, grp_led:scroll"
```

_edit_
Above worked on an installation. Using LiveCD/LiveUSB cannot reboot or logout, so use the terminal command:
```
setxkbmap -option grp:ctrl_shift_toggle,grp_led:scroll us,gr
```
(2x layouts toggle with Ctrl+Shift and scroll LED as the indicator)

---

### Post by terribly-important-person on 2013-10-14
I'd also like to figure out how to get ALT+SHIFT working under 13.10.  I even went through and removed all of the "accelerator keys" containing ALT+SHIFT (something like CTRL+ALT+SHIFT which switches tabs), hoping that it would get rid of the conflict, but still no luck.

---

### Post by varunendra on 2013-10-14
> **terribly-important-person said:**
> I'd also like to figure out how to get ALT+SHIFT working under 13.10.
Have you checked dconf Editor > org > gnome > libgnomekbd > keyboard > options like I mentioned above in post #2 ?
Is the setting not there or has no effects?

---

### Post by Norak on 2013-10-15
I have the same problem. Tried the solution with the dconf Editor.
I still have the previous setting of alt+shift stored in the dconf editor, but unity seems to ignore it.
In unity I have now switched to ctrl+space, which seems to work, but does also have no effect on the dconf value.
I have also noticed that there are error messages when selecting a shortcut that is already in use, but none of those appear when trying to set alt+shift. It is simply ignored and reset to the previous setting.

---

