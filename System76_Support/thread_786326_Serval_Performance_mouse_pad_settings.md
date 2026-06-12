---
title: "Serval Performance mouse pad settings?"
date: 2008-05-08
forum: System76 Support
---

### Post by Sean-Michael on 2008-05-08
This mouse pad is driving me crazy, often times the workspace changes and I dont know what mouse(pad) gesture is doing it.  I also have problems when moving threw menus items are selected when I'm trying to navigate threw to another...

So I'm hoping someone can point me in the direction to learn where these settings are and be able to take advantage of them... not accidentally move to differnt workspaces and select the wrong menu items' :popcorn:

Thanks in advance as always,
Sean-Michael.

---

### Post by erfahren on 2008-05-08
Is this a laptop and are you talking about the touchpad? If so then post the output of:
```

cat /etc/X11/xorg.conf

```
(I'm really only interested in the section that identifies the touchpad.)

---

### Post by jdb on 2008-05-08
> **Sean-Michael said:**
> This mouse pad is driving me crazy, often times the workspace changes and I dont know what mouse(pad) gesture is doing it.  I also have problems when moving threw menus items are selected when I'm trying to navigate threw to another...

So I'm hoping someone can point me in the direction to learn where these settings are and be able to take advantage of them... not accidentally move to differnt workspaces and select the wrong menu items' :popcorn:

Thanks in advance as always,
Sean-Michael.

I know what you mean, I have big hands & when I type I'm alwas accidently touching the pad & doing stuff I don't want to do.

I use a real mouse whenever possible & turn the touchpad off, FN F3 on the Daru2, I don't know about the Serval.

I installed a program called gsynaptics, it allows me to turn off tapping & scrolling, that limits the damage when I do need to use the touchpad :)

jdb

---

### Post by thomasaaron on 2008-05-08
Synaptics will not work on the new Servals. They have an elantech touchpad.

The only available adjustments are via System > Preferences > Mouse.

You can turn it completely off by running this from the command line:
sudo modprope -r psmouse

And you can turn it back on with:
sudo modprobe psmouse

---

### Post by Sean-Michael on 2008-05-08
I'm not interested in completely turning off the touch/mouse pad.  I just want to know what the gestures are that I make on accident.  I like the idea of being able to switch workspaces and even the scrooling behavior but I cannot do it when I want to lol

I'll keep looking and post back if I find the settings.

jdb,
I also have a hard time bumping the pad from time to time and do as you suggested, I use an external mouse for my blender work but it's when I'm just writing or checking email that I want to use the built in pad...

Oh, here's the information erfahren asked for...

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
```

---

### Post by XStylus on 2008-07-16
> **Sean-Michael said:**
> I'm not interested in completely turning off the touch/mouse pad.  I just want to know what the gestures are that I make on accident.  I like the idea of being able to switch workspaces and even the scrooling behavior but I cannot do it when I want to lol


Ditto on trying to figure out the touchpad gesture. I've figured out how to switch it with keyboard hotkeys (CTRL+ALT+Left/Right) but not with the touchpad. Any info would be appreciated.

I'd also like to reduce (what I would call) the activation time on the page scroll feature on the right side of the touchpad activates. If I barely brush the right side of the touchpad, the page scrolls. I'd like to drop the sensitivity of that a bit so that it'd have to be more of a deliberate thing for the page scroll to activate, kinda like with (hate to say it) Windows.

---

### Post by thomasaaron on 2008-07-16
If you place your fingertip on the top right corner of the mousepad, and then, holding it there, lay the rest of your finger down on the pad from the the top right corner to the bottom right corner. That should switch your desktops.

---

### Post by XStylus on 2008-07-16
> **thomasaaron said:**
> If you place your fingertip on the top right corner of the mousepad, and then, holding it there, lay the rest of your finger down on the pad from the the top right corner to the bottom right corner. That should switch your desktops.

I just now discovered that the vertical scrolling feature was the culprit. Now I just need to reduce the sensitivity of it. :)

---

### Post by stefansjs on 2008-08-06
I am experiencing the same behaviour where the vertical scrolling (on the right side of the touchpad) is triggering switching of workspaces.  I would like to keep the vertical scrolling behavior, but disable the switching of workspaces when I scroll.  I still want the workspaces, but if anybody knows how to disable the workspace switch when you scroll, I would really appreciate it.
thanks

---

### Post by thomasaaron on 2008-08-07
Try disabling Desktop Effects.

---

### Post by stefansjs on 2008-08-16
What do you mean by desktop effects?  I can't find any settings that indicate they would affect this behavior.

---

### Post by thomasaaron on 2008-08-18
With compiz activated, the touchpad can be used to switch workspaces. To deactivate Deaktop Effects, go to System > Preferences > Appearance > Visual Effects and select "None."

If this fixes the problem you know it is compiz causing it.

If this turns out to be the problem, we can probably find a setting in compiz's advanced configuration manager to deactivate it.

---

### Post by stefansjs on 2008-08-20
That solved it.  Once I figured out that it was compiz, I found in the help file that I needed to install compizconfig-settings-manager to change the specific settings.

---

