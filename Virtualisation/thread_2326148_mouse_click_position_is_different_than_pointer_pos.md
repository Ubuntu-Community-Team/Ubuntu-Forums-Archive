---
title: "mouse click position is different than pointer position in VmWare"
date: 2016-05-28
forum: Virtualisation
---

### Post by Joe_Willmann on 2016-05-28
I am running Ubuntu 16.04.  Intalled VmWare 12.1.1 build-3770994.  Installed widows 7 64 bit.

everything seems to be running OK but.....

Let VmWare come up and let windows come up.  Use windows, things work fine.  Now bring up firefox.  Firefox comes up.  Position the cursor over the "X" in the title bar, click, Firefox closes.  Everything is at it should be.

Now bring up Firefox.  Grab the VmWare titlebar and slide the window right one inch.  Now click the X, or try to.  Nothing happens.  Move the mouse cursor 1 inch to the right of the X and click.  Firefox closes.

So the point returned when clicking does not match the point the cursor is on.

It is like after the move VmWare isn't adjusting the mouse postion to relative to the client window.

---

### Post by Joe_Willmann on 2016-05-28
Something I noticed.
If the VmWare is not in Full Screen and you move the VmWare widow the mouse registration gets off.
But if you resize of move the VmWare widow, go to Full Screen mode, then exit Full Screen mode the widow returns to the previous position but the mouse registration is now correct.

This originally showed up because I moved the VmWare window and then tried to exit an app and clicking did just funny stuff.

At least now I know how to get the mouse registration back in sync but I would like to know if this is a problem with Ubuntu, VmWare, Windows, or a driver of something.

---

