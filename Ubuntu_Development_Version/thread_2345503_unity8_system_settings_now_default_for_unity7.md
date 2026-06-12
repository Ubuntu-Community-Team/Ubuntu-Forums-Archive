---
title: "unity8 system settings now default for unity7"
date: 2016-12-04
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-12-04
Hard installing ubuntu-desktop 17.04/current/ the unity8 system settings panel is now the default for unity7 also.  This may be yet another sign towards desktop convergence.

---

### Post by mc4man on 2016-12-04
Probably a bug, you'd get the normal one for Desktop from cog menu until logging into unity8 & likely opening system setting once.
The orig.  SS launcher icon for Desktop would still open correctly but the panel cog menu route would open the unity8 one now. 

Shouldn't hard to find the errant setting as it's possibly user configured

---

### Post by ventrical on 2016-12-04
It came first from  updating an existing install of unity8. When I seen it on fresh install of daily/current 17.04 I assumed it may be a convergence bump of some sort.

Regards..

---

### Post by mc4man on 2016-12-05
Here, (fresh 12/04 image) it occurs when one uses system settings in unity8. Then the cog menu > ss in unity7 will open wrong panel.
There seems to be some other things between the 2 sessions needing work, for ex. - 
switching background in 7 changes greeter & background in 8
switching background in 8 changes greeter but not the background in 7

Whether the 2 sessions should be 100% separate or 100% same or a bit here & there as far as settings, no clue..

---

### Post by ventrical on 2016-12-05
I would think it only logical that they would implement a separate desktop for mir (unity8-system-compositor) for the unity8 desktop. I assume, however, that they have probably left a unity7 backdoor share so a user can access folders and  copy music and video files (for testing the technical preview).

They have now included unity8-desktop-session package in the bug I filed concerning no read access to files on USB drives.  [https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1646655](https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1646655)

So my point for brining this up is that there appears to be big problems with mir and unity8-desktop-session. I would have hoped that Libertine and some deb app could do this for us  but there is a networking  share problem. I have no idea what package it could be.

Regards..

---

