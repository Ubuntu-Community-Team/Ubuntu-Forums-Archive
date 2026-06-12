---
title: "Freeze after login"
date: 2010-10-30
forum: Ubuntu Studio
---

### Post by Christie_k22 on 2010-10-30
Hi I am new to the forums and fairly new to Linux in general. I have been using Ubuntu for almost a year now on my laptop but just recently decided to install Ubuntu Studio (dual boot w/ Vista) on my desktop. I have had many years experience with installing many versions of windows and I have installed a few different distros of Linux in the past year mainly to see which one I liked. 

Today I installed Studio on my main desktop. Vista still works fine. Ubuntu Studio seemed to be working as well. I started customizing my desktop panels to be similar to the ones I am using on this computer (my laptop). There was an error msg saying that the panel wasn't working and it forced quit. At that point it seemed to freeze. The mouse pointer still moves but there are no panels and I can't do anything. I did a manual shutdown and rebooted to Studio. I still get the same thing. I can log in but as soon as it loads up the desktop I get the same thing. . . just a blank desktop with the background only. The mouse still moves but I can't do anything. Right clicking doesn't even do anything. 

640GB HDD - Windows Vista (64 bit) installed
320GB HDD - Ubuntu Studio 10.04 (32 bit) Installed
160GB HDD - Extra space (completely empty)
4GB DDR2 RAM
Intel(R) Core(TM)2 Duo CPU E7300 @ 2.66GHz/2.67GHz
ATI Radeon HD 2400 Pro

---

### Post by ajgreeny on 2010-10-30
Boot to recovery mode and then try renaming /home/<username>/.gconf/apps/panel folder as a backup with ```
mv /home/<username>/.gconf/apps/panel /home/<username>/.gconf/apps/panel~
``` and then try again.  It sounds as if some configuration change you made has upset something or other, and this should get you back to where you were before making the changes.

You may even be able to do this from the cli after logging in to your studio desktop and using Ctrl+Alt+F1.

---

### Post by Christie_k22 on 2010-10-30
Thank you so much that took it back to where it was. The unfortunate thing is when I went back and tried to add another panel (i like having one at the top and one at the bottom) it acts as if the panel is there but doesnt show it. The way I figured this is that when I move the one visible panel to the bottom then back to the top it has an open space (where you can see the desktop background) where a panel would go at the top with the other panel just below. I attached a pic with this post. Any other ideas?[IMG]file:///media/6234-6236/Screenshot.png[/IMG]

After a nice long nap (i got frustrated and laid down for a bit) and like 5 or 6 reboots later it seemed to fix itself. Everything seems to be working just fine now!

---

