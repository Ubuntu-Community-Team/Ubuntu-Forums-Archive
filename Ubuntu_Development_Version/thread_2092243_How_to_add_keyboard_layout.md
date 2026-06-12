---
title: "How to add keyboard layout?"
date: 2012-12-07
forum: Ubuntu Development Version
---

### Post by zika on 2012-12-07
I've just noticed that I'm unable to add new keyboard layout through Systemsettings>KeyboardLayout. "+" is grayed and...
I can erase existing layout(s)... I can shuffle them around. I can change current layout OK...
Just no way to add new one...
Also, I can not find way to change pc105 to pc102 (or the other way around) keyboard in existing layouts...
Existing layouts were made during install as far as I can recall... Or while I was still on 12.10 before upgrade to 13.04 in recent re-install...
What is this old head of mine missing?
Reason because I discovered this is that I want to make (somehow) Super key to work on this old pre-pre-Win IBM keyboard of mine to test these Launcher hints ...

Update&#8321;: OK, I've changed Super to another combination and I can now test hints in Launcher... But the question given above still stands...
(I must admit that most of the time I spend in dwm, spectrwm, fvwm so I'm used to change keyboard layout through setxkbmap, but of course this GUI way worked for me earlier, I do not know if it worked in RR...)
Luckily I've set keyboards OK on the first attempt (probably in install time) and now I have to be careful not to erase any of these because I'll not be able to get it back...

---

### Post by pkadeel on 2012-12-07
all keyboard layouts are in ```
/usr/share/X11/xkb/symbols/
``` folder.

To add a new none existing (not already present in the above mentioned folder) keyboard layout, you need to put the layout file in that folder. Then you need to put an entry for this new layout in ```
/usr/share/X11/xkb/rules/evdev.xml
``` file. Putting entry in this file will enable you to see it in SystemSettings > Keyboard Layouts

Then you can use the + button to add it to the active layouts used on your system.

---

### Post by zika on 2012-12-07
> **pkadeel said:**
> all keyboard layouts are in ```
/usr/share/X11/xkb/symbols/
``` folder.

To add a new none existing (not already present in the above mentioned folder) keyboard layout, you need to put the layout file in that folder. Then you need to put an entry for this new layout in ```
/usr/share/X11/xkb/rules/evdev.xml
``` file. Putting entry in this file will enable you to see it in SystemSettings > Keyboard Layouts

Then you can use the + button to add it to the active layouts used on your system.I think I've accomplished the same via```
gksu gnome-control-center
```It looks a bit counter-intuitive to me, but, who am I to complain...
It was available to ordinary user before, or I might be wrong...
I'll investigate Your suggestion in the next break. Thank You...

Update&#8321;: Strolling through the file You've pointed me to, I've found the way to make CapsLock a new Super... The thing about adding new layout will have to wait to the next break. Thank You...
Update&#8322;: Still on break: Many (including ones that I want to add) keyboard layouts are in that file... But...  So, the only way I see at this moment is via```
gksu gnome-control-center
```Funny, when I do that I do not see English keyboard and a secondary local one that I already have in my user's ```
gnome-control-center
```... Something is going astray here... I can live with that, I'll refrain to setxkbmap if needed, but it still is astray...

Update&#8321;: Behavior of keyboard switcher depends on kernel being used... It is even more astray if I try to use 3.6(liquorix)... Not to mention that setting about Super key is in some instances bluntly overlooked... I'll look into this more...

---

