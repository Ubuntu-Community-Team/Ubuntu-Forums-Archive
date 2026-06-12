---
title: "black screen after awhile"
date: 2024-03-12
forum: Ubuntu/Debian BASED
---

### Post by 14nd on 2024-03-12
hi folks 
i have mxlinux running ,if i leave pc for awhile the screen would turn black and i cant get anything to display after i move mouse or touch keyboard, it just stays a black screen with the mouse curser showing which i can move around.
any idea why this  is ?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293480&stc=1[/IMG]

---

### Post by deadflowr on 2024-03-12
*Thread moved to **Ubuntu/Debian BASED***

---

### Post by Rubi1200 on 2024-03-12
It has been some time since I played around with MX Linux but have you tried setting the screen to never blank?

What version are you using and what DE is installed?

---

### Post by 14nd on 2024-03-12
haven't tried to never blank...i'll try that
MX-23.2 Libretto
xfce DE

meantime found this [thread](https://forum.mxlinux.org/viewtopic.php?t=79596&start=20) which i'm busy working through.

we'll see :)

---

### Post by 14nd on 2024-03-12
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293482&stc=1[/IMG]

ok wait i found a solution
i just toggled the **display power management** to off.
it lets the power manager handle display power instead of X11

[https://forum.mxlinux.org/viewtopic.php?p=768856#p768856](https://forum.mxlinux.org/viewtopic.php?p=768856#p768856)

---

### Post by ajgreeny on 2024-03-12
Brilliant!
Please mark this thread as SOLVED from thr Thread Tools menu up top.
It is a great help to other users searching the forum.

---

### Post by 14nd on 2024-03-12
oh shoot now it dont work anymore ...
back to same problem

---

### Post by 14nd on 2024-03-13
ok tried going back to previous kernel , which didn't help
then i figured out if the screen stays black like that , and i press ctrl+alt+backspace (kill X server) screen comes on like normal.
i'll just go with that now , tired of trying to figure this out lol

---

### Post by 14nd on 2024-03-14
ok found a solution 

MX tweaks -- other -- check "use intel driver instead of default modesetting driver"
reboot 

and thats that :)

*courtesy of* : [https://forum.mxlinux.org/viewtopic.php?t=79702](https://forum.mxlinux.org/viewtopic.php?t=79702)

---

