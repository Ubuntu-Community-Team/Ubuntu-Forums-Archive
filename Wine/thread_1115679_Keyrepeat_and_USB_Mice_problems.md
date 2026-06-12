---
title: "Keyrepeat and USB Mice problems"
date: 2009-04-04
forum: Wine
---

### Post by t.rei on 2009-04-04
Hi,

I am having some issues running World of Warcraft. (eve-online works fine)

The problems being:

key repeat settings make movement garbled, causing the character to "twich" as if the key is pressed superfast. This can result in wow-disconnects. Turning key repeat off in the ubuntu keyboad settings dialog fixes this, but is a pain for the chat (backspace). 
It also happens running xfce or kde. 

Is there a way to configure wine key repeat behavior seperately?

Any USB mouse connected to the laptop gets its mouse-buttons stuck, when pressing keyboard keys while using i.e. the right mouse button to turn. This is a real problem, since I know of no workaround, that makes me able to play the game.
The touchpad buttons do not have those problems, they work flawlessly. Unfortunately playing wow with a touchpad is ... no, just no.
Todays evdev update didnt do any good. 

Has anyone got any pointers that I could follow to make the usb mice work as intended?

I'd love to get WoW running. It's the only game I keep windows for, and honestly - rebooting for a quick look into the game just isn't it. :)

Thanks guys,

Timo

---

### Post by t.rei on 2009-04-04
A clean reinstall of Ubuntu Jaunty seems to have fixed the mouse problem. *cheer*

```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```
Is the only text in my xorg.conf now, altho I am pretty shure that the original probelm was somewhere deeper within the upgraded system.

Now all that remains is the "keyboard repeat problem" (other players can see me twitching about - my girlfriend laughed so sweetly at this *grr*) 

I will dig deeper into the wine / gnome settings later this evening. I figure it must be something along those settings.

---

