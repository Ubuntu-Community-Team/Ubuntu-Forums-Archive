---
title: "Top XFCE panel (taskbar) stops working"
date: 2013-08-26
forum: Ubuntu Studio
---

### Post by shaunthesheep on 2013-08-26
I'm having problems with the XFCE top panel in Ubuntu Studio 12.04. Several times a day when I click on the open tabs, nothing happens and the right hand side log out/shut down menu  also is gone. I have to do a hard reboot. Rebooting restores the panel.

I've just been investigating the Panel Preferences and see that there are two panels. I have just deleted one of them so I now have just the one. 

Any suggestion gratefully received

---

### Post by jejeman on 2013-08-26
I'm sure that there is not need for hardware reset.
Just go to tty1 and restart lightdm.
Or even better, kill the panel, then start it via Alt+F2.
```
killall xfce4-panel
xfce4-panel
```

---

### Post by shaunthesheep on 2013-08-27
Thanks. I have been doing some research on the Web about possible causes and one is CPU temperature being too high. Yesterday, I installed Psensor and the highest temperature I got was 67 degrees. Not only the panel but also other things stopped working like Alt F2 and Alt + Tab. I had to reboot several times. I have the PC on for long periods. Today I am cleaning the tower and fans to see if that helps. 

I have Dell Inspiron 560 MT desktop with a Core 2 Quad CPU. At what temperature is it over heating?

---

### Post by jejeman on 2013-08-27
67°C iz not much if you are working something, but for idle mode on desktop with that CPU it is.
But also, that is not temperature for overheating. I guess >80°C would be.

---

