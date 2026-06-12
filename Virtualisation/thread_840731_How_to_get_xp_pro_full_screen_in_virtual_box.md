---
title: "How to get xp pro full screen in virtual box"
date: 2008-06-25
forum: Virtualisation
---

### Post by Afkpuz on 2008-06-25
Like the title says, I'm running xp pro in virtual box.  Works great, except when I try to do fullscreen, it only fills a little bit of the screen in the middle and the rest with black around the edges.  In windows, I check the resolution and it's declared as 800x600 with only 1 other choice:1024x768.  I chose that higher setting, but there are still black borders.  Is it possible to make it fill the whole screen without the black borders?  If not, it's not the end of the world.  I should also note that I'm using compiz if that makes a difference.  

thanks

---

### Post by squaregoldfish on 2008-06-25
Sorry I can't be more informative than this, but I don't have VirtualBox to hand. However:

Assuming you've installed the VirtualBox extensions into Windows (there's a menu entry for it), you should be able to find another menu entry along the lines of "Adjust screen resolution" or similar, which resets the Windows resolution to the current size of the window. This has an associated keystroke, which you can remember and use once you've gone into full screen mode.

I believe there's also a preference for making VirtualBox resize the Windows desktop whenever the window is resized, which will automate the above process for you.

Have a sniff around and see what you can find. If you can't figure it out, and no-one else has helped before tomorrow, I'll have a look at exactly what's required.

Steve.

---

### Post by stevemot on 2008-06-26
Hi,

I had this problem, a while ago, then discovered the solution. I needed to allocate more memory to the vbox virtual graphics card in the VBox control panel (sorry, don't have it in front of me, so I can't give you the exact setting). Once I had increased the graphics card memory, WinXP offered more options for the screen resolution, and it was able to dynamically resize as I resized the VBox window.

Hope this helps.

Steve

---

### Post by Afkpuz on 2008-06-26
Ok, I'll check that out tonight when I go home from work.

---

### Post by Afkpuz on 2008-06-26
Yeah, changing the video memory size (which was really low.  Like 8 mb) to 64 gave me tons more resolutions and now I have one side of my cube as windows.  Thanks!

---

