---
title: "Text Corruption on Wow (set UIFaster doesn't work)"
date: 2009-06-28
forum: Wine
---

### Post by Ollock on 2009-06-28
I'm running wow under Ubuntu 8.04.  I can only run it under opengl mode (d3d either hangs on entering the world or runs with an unplayably low framerate and bad controls), and when I do the 3D graphics are pretty smooth, but I can't get it to stop the text from getting corrupted.  I have tried setting UIFaster to 2 and then to 0 but it doesn't seem to do much.  I am running a refurbished Dell Inspiron 1501 with ATI Technologies Inc RS485 graphics card and 2GB RAM (The RAM was a DIY upgrade).  Is there some other setting somewhere that will get rid of the text corruption

---

### Post by Blood//Stain//Child on 2009-06-28
Do you use Anti-Aliasing? 
Did you install any fonts to the /home/yourusernamehere/.wine/dosdevices/c:/windows/Fonts?
Are you using triple buffering in the WoW graphics settings?

---

### Post by Ollock on 2009-06-29
1) Is there a way to check anti-aliasing?
2) No, not sure what it would do.  The text shows up fine for a while then goes bonkers and gets stretched into weird shapes all over the screen.
3) Tried setting Triple Buffering but I'm not sure if it stayed set -- do I have to add something to xorg.conf to make that work?

EDIT: Figured it out -- had the same problem as this guy: [http://iamyouruser.blogspot.com/2009/01/ubuntu-world-of-warcraft.html](http://iamyouruser.blogspot.com/2009/01/ubuntu-world-of-warcraft.html)

Unfortunately now I have to play without a minimap, but I guess that's not all that big a deal -- just makes farming a bit harder.  Better than not being able to play at all.

Anyone have a workaround that might let me see the minimap while playing?

---

### Post by Blood//Stain//Child on 2009-06-29
Yes there are several fixes for this, depending on what is causing the issue.

---

