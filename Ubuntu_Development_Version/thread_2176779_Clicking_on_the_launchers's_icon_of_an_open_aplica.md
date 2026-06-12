---
title: "Clicking on the launchers's icon of an open aplication in another workspace"
date: 2013-09-26
forum: Ubuntu Development Version
---

### Post by wgarcia on 2013-09-26
Clicking on the launchers's icon of an open application that is in a workspace which is not the active one, does not take you to the other workspace and therefore does not open the application's window. This is happening now in the updated Unity in 13.10, is this now a feature or is it a bug?

---

### Post by PJs Ronin on 2013-09-26
[http://ubuntuforums.org/showthread.php?t=2175823](http://ubuntuforums.org/showthread.php?t=2175823)

---

### Post by wgarcia on 2013-09-26
Thanks, good to know it's not a feature.

---

### Post by grahammechanical on 2013-09-26
I get the feeling that it is a feature. It used to be possible to move around the workspaces by using Ctrl+Alt+ an arrow key. We could move left - right and up - down. Now we can only move left - right. But if we press super+S and let go of S but hold Super we can move around the square of workspaces using the keys. This is listed in the keyboard shortcut overlay. That is why I am beginning to think it is a feature.

Regards.

---

### Post by grahammechanical on 2013-09-26
Sorry for the double post. In the middle of an "It's dead, Jim." message. Is it Chromium or my connection to the ISP that dropping?

---

### Post by mc4man on 2013-09-26
I doubt this is intended, thought I saw a report on though no time to find. 
Note that it only affects wall, rotate is fine, both from clicking on launcher icon & with the ctrl+alt+arrow keys

---

### Post by mc4man on 2013-09-26
I don't use wall but as far as the  Ctrl+Alt+an up/down arrow key take a look at this bug I filed quite some time ago
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1201405](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1201405)

(see if resetting in ccsm helps...

---

### Post by deadflowr on 2013-09-26
> **grahammechanical said:**
> I get the feeling that it is a feature. It used to be possible to move around the workspaces by using Ctrl+Alt+ an arrow key. We could move left - right and up - down. Now we can only move left - right. But if we press super+S and let go of S but hold Super we can move around the square of workspaces using the keys. This is listed in the keyboard shortcut overlay. That is why I am beginning to think it is a feature.

Regards.

It felt more like a bug, since the last time I checked to enable workspaces it gave you 2x2 instead of 1x4.
Of course it was sometime ago and I've since re-established the up/down keybinding and haven't had a problem again.
That said, don't know what the latest fresh install workspace layout is.(Whether 1x4 or 2x2)
I usually set it to 3x3 and then muck about with expo and viewport switcher for fun.

---

### Post by grahammechanical on 2013-09-26
An update a few minutes ago might have fixed it. I can now used Ctrl+Alt+arrows key to move around the default 2x2 box of workspaces. The Super + S feature still works. I Challenge anyone to press Shift+Ctrl+Alt+arrow key action.

---

### Post by mc4man on 2013-09-26
> **grahammechanical said:**
> to press Shift+Ctrl+Alt+arrow key action.
That is to move to another workspace with window currently in focus - works fine here

---

### Post by wgarcia on 2013-09-28
On the updates that I received today the issue that  I report in the title is solved.

---

