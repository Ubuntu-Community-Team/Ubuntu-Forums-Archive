---
title: "Remote Desktop Viewer (Vinagre) issues and 14.04"
date: 2014-04-14
forum: Ubuntu Development Version
---

### Post by jon_williams on 2014-04-14
I used Vinagre happily (and frequently) with 12.04 LTS. Now, having moved some machines over to 14.04 LTS (not quite final release ...), it seems that if I try to use Vinagre to view 13.10 or 14.04 machines, it comes up with a black screen, but it still links OK to 12.04 and Win XP and Win7 machines. Anyone else noticed this? Is there a fix? 


**Reply from monkeybrain20122:**
Think it doesn't work with 3d desktops. In 12.04 it worked because you were using unity2d. So for 12.10 onwards you need to install an alternative 2d DE for remote session. In 13.04 gnome-fallback worked, it becomes (?) gnome-session-flashback in 13.10 and is broken, remote session shows blackscreen so one would need to install some other 2d desktop for remote sessions,lxde works nicely, don't know if gnome-session-flashback works in 14.04. You'd better post the thread in Ubuntu+1 as the testers may be able to give you more info about 14.04, which has not been released yet.

---

