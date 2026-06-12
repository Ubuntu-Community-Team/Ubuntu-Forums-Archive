---
title: "Screen resolution problem - VirtualBox with XP and dual-monitors"
date: 2009-03-18
forum: Virtualisation
---

### Post by JerryI on 2009-03-18
Hardy 64 - VirtualBox with XP - Nvidia TwinView on two 22-inch Acer monitors

Problem:  I start VirtualBox and adjust its window to a respectable portion of the left monitor, say 40-50 percent. Then when I start XP in the window, it blooms out to a black screen across the whole 2-monitor display with a small (maybe 800 x 500 pixels) XP window smack in the middle, bridging the two monitors.

Question 1:  How can I get XP to stay in the VirtualBox window that I set up? I want to see other stuff besides XP, which is why I have 40 inches of horizontal viewing area.  

After playing around with the settings for nvidia, I found that I can set it for a couple dual display options besides to twin view, allowing me to start Virtual Box on either screen, but the app grabs one whole monitor, although it really only uses about 30 percent of the screen.  Can I fix it to share the monitor with other apps?  How?

---

### Post by Ng Oon-Ee on 2009-03-19
Sounds like its automatically going full-screen.

Try your Host Key->F to see if that corrects it. Normally the right Ctrl button is the host key.

Also check to see if you have anything (devilspie or compiz) which automatically maximizes/full-screens some windows.

---

