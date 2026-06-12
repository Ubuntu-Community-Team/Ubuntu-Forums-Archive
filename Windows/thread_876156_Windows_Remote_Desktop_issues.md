---
title: "Windows Remote Desktop issues"
date: 2008-07-31
forum: Windows
---

### Post by DouglasAWh on 2008-07-31
Don't know what to do with this.  Any ideas?

> Sometimes logging back onto my computer after being remote desdktopped into my computer, my first monitor is not active. I see a black screen and i can't move my mouse over to it. Since the start buttons are on the first screen i can restart the computer without either hitting the power button or cutting the power to the computer. When the computer turns back on, my second monitor becomes the dominate monitor with the start menu and the first monitor acts as the second. I have to turn off the computer, switch the monitors from being 1 and 2. Turn the computer on, then turn the computer off and switch the cables to its original state to restore the correct placement of the dual monitors. Everything works fine and monitor 1 and 2 is mapped correctly during the setup. I'm not really sure what's going on. This only happens sometimes after remote desktop. Any suggestion on how to fix this will be great. Thanks.

Both sides are XP.

---

### Post by abgemacht on 2008-07-31
Have you tried using the options in the Settings Tab of Display Properties before the initial reboot?

---

### Post by dca on 2008-07-31
If you run dual screens, the user who remote's into your system can't see your second screen, only your primary.  This causes issues if they're trying to assist you with an issue on an app that's opened on your second screen.  I've seen this happen but I've always shrugged it off as a glitch.  Let's face it, RDP isn't exactly VNC or Dameware...
 
To prevent in the future if you're having someone remote into a dual-screen set-up, be sure to turn off your secondary under your display properties...
 
If you forget, depending on your graphics card you can go into display properties and drug your seconday monitor to be your primary....  Grab monitor marked '2' and move with mouse...

---

