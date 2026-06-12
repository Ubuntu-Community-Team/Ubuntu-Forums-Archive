---
title: "Issue switching worksapce when virtualbox is active"
date: 2016-07-18
forum: Virtualisation
---

### Post by Dr._B on 2016-07-18
I recently replaced my work computer and installed the newest version of Ubuntu (16.04) and Virtualbox (5.2). I am running windows 10 in virtualbox. Everything works fine except for one issue I cannot solve. When virtualbox is in full-screen mode, I cannot switch ubuntu workspaces like I used to on my old system (Virtualbox 5/Ubuntu 14.0x); specifically, when I hit the "switch to host" key (right-Ctrl), then use the "switch workspace" key combination (ctrl+alt+arrow), the screen will briefly switch to the new workspace and then "bounce back" to the windows guest.

This behavior does not occur if virtualbox is not full-screen, and likewise, if I use the workspace switcher while in full screen, switching works properly.

My google searches showed this was an issue in much older version of ubuntu and virtualbox, but have found no useful information on how to fix the issue.

Any insight is appreciated.

Bryan

---

### Post by Dr._B on 2016-07-19
Just to add, any time I close a window or program in ubuntu, it also jumps back to the virtualbox Win10 virtual machine...weird!

---

### Post by jvinokuroff-r on 2016-10-24
I also had this behaviour in 14.04 LTS. For the time being, it appears to be corrected after I tweaked one unity variable. In Unity Tweak Tool, I selected Workspace Settings -> Additional, then I made sure Focus Behaviour -> Auto-raise was switched to off.

---

