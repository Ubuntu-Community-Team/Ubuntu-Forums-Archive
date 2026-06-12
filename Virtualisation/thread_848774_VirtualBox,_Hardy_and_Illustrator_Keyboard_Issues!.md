---
title: "VirtualBox, Hardy and Illustrator Keyboard Issues! PLEASE HELP"
date: 2008-07-03
forum: Virtualisation
---

### Post by niiiick on 2008-07-03
Hey guys...this one puzzles me...

so i was completely happy with running virtualbox/winxp sp3 in fullscreen mode with adobe illustrator cs3 inside that on one of the desktops (ubuntu hardy heron with compiz).  (i changed my host key to F1 because i use all ctrl and alt keys, fyi).

until i actually started USING illustrator and the pen tool.  the first thing i noticed that didn't work was Alt+Scroll Mouse Wheel didn't zoom in our out, and that's a feature that i absolutely cannot live without.  a substitute was to use Ctrl+Space to temporarily switch to zoom in tool and Ctrl+Alt+Space to temporarily switch to zoom out tool.  ctrl+space would work, but when i did ctrl+alt+space and clicked somewhere on the image, the desktop cube BEHIND fullscreen virtualbox would zoom out and i couldn't work.  how strange.  if i turn off compiz with "metacity --replace &" then that zoom out feature would work.  i would still definitely rather have the alt+mouse wheel control zoom in and out though.

next, holding Alt (to switch to a variation of the pen tool) would change the mouse icon (as it's supposed to) to the variation, but when i would click, it wouldn't do anything.  i cannot do without those two things.

any idea why this alt key doesn't work like it's supposed to?

---

### Post by tentotwo on 2008-07-29
Hey niiick,

have you tried using the right alt key (marked as "Alt Gr" on my German keyboard)? This key isn't intercepted by the Linux desktop and works fine with InDesign -- I assume that the whole Adobe family will behave similarly.
It's still only a rough workaround, though, I usually like to keep my left hand over the Ctrl, Shift and Alt key on the left side of the keyboard, but it's much better than switching into zoom mode...

---

### Post by The Beth on 2008-09-13
I'm having the same problem. The right alt key yields the same results as the left. I really miss Illustrator.... :-/

---

### Post by The Beth on 2008-09-13
OK, here's an excellent workaround I found for this unpleasant bug! 

In your Windows XP (or Vista?) guest,

1. Download SharpKeys from Randyrants.com. To get SharpKeys working, you may also need to install .Net 2.0. 
2. Use SharpKeys to map, say, your caps lock key to left alt. Be sure to capture the 'from' keystroke rather than pick it from the list, and to pick the 'to' keystroke from the list rather than via capture. I don't know why it has to be like this -- I hypothesize that the keystrokes that VirtualBox feeds to the guest aren't exactly the same as the ones that'd be typed in if XP was running native.
3. Reboot the guest.
4. Try using your caps lock as your left alt key. Have fun zooming in with Illustrator and everywhere else! ^_^

---

