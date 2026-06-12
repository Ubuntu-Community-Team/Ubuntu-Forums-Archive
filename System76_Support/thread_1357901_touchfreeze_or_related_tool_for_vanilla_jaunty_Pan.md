---
title: "touchfreeze or related tool for vanilla jaunty PanP5?"
date: 2009-12-17
forum: System76 Support
---

### Post by tlroche on 2009-12-17
Apologies if this is a FAQ, but I found nothing searching about this topic:

Is there something like '[touchfreeze]("http://packages.ubuntu.com/jaunty/touchfreeze")', or a way to tune 'touchfreeze', that will work with my vanilla PanP5? Why I ask:

I have a PanP5 that I received in late September, but only started using much this week, to take notes @ a conference. (My fall-semester project required windows-only software (ArcGIS), so I've been using my old dual-booted ThinkPad.) It still has the installed Ubuntu (9.04) and window manager (but is up-to-date patch-wise), with nothing much installed.

I encountered a crippling problem: my cursor was jumping all over during notetaking, often to a window other than the one I had been typing in. I noted the cursor appeared to jump to the mouse's current location, so I googled about that. I saw touchfreeze recommended and tried to use that, but it apparently had no effect (although it did start its process and install its control in the tray), and certainly did not end the cursor jumping.

Per post from Tom Aaron, I went to System>Preferences>Mouse and turned off "Enable mouse clicks with touchpad", which seems to have solved the problem. (I also turned on "Show position of pointer when the Control key is pressed", which I assume had no effect on this matter.)  However that, as advertised, totally disables the touchpad.  I would much prefer to have the touchpad disabled only while I'm typing, with a configurable restore delay, as with touchfreeze. Is there a way I can get that?

---

### Post by japhyr on 2009-12-18
I think Fn-F1 does that on the panp5.

---

### Post by tlroche on 2009-12-23
> **tlroche said:**
> I would much prefer to have the touchpad disabled only while I'm typing, with a configurable restore delay, as with touchfreeze.

> **japhyr said:**
> I think Fn-F1 does that on the panp5.

No, Fn-F1 completely disables the touchpad. The tools available (on my PanP5 with vanilla jaunty) seem to be

[LIST=1]
[*][touchfreeze]("http://packages.ubuntu.com/jaunty/touchfreeze"): attempts to transparently toggle all touchpad functions ({touchpad cursor move, touchpad click, touchpad button click}) while typing, i.e. starting to type disables all touchpad functions, and ceasing to type enables them. Unfortunately this is not working on my PanP5.
[*]System>Preferences>Mouse>Touchpad>"Enable touchpad": toggles all touchpad functions, and is hard to do from the keyboard.
[*]System>Preferences>Mouse>Touchpad>"Enable mouse clicks with touchpad": equally hard to do from the keyboard, but only toggles {touchpad click}, which is most what I need to solve the cursor-jumping problem.
[*]Fn-F1: toggles all touchpad functions. Requires explicit gesture, but is relatively easy to get to from the keyboard.
[/LIST]

touchfreeze still seems like the most preferable option. Is it working for anyone out there? If so, which version are you running? (I've tried to use the stock version from Add/Remove.)

---

