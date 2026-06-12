---
title: "initramfs update may help (BlackScreen) issues we discussed here"
date: 2011-10-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-23
> Version 0.99ubuntu8: 
Too optimistic in thinking that the DRM driver will always be loaded
in time for scripts/init-top/framebuffer to load; some users find that
vesafb gets loaded first anyway, scrambling their console state in the
initramfs.  Add a one-second sleep before checking if we should fall back
to vesafb, which seems to be long enough to work around this.
LP: #869119.

We had discussed it a little here, when talking about the "BlackScreen" issues, and how we were helping users by askiing them to add temporary boot parameters to force a text mode, as a way to be able to see what was actually going on with their system below a broken video mode. This update may help for a more smooth boot process in PP.

---

### Post by MAFoElffen on 2011-10-23
> **effenberg0x0 said:**
> We had discussed it a little here, when talking about the "BlackScreen" issues, and how we were helping users by askiing them to add temporary boot parameters to force a text mode, as a way to be able to see what was actually going on with their system below a broken video mode. This update may help for a more smooth boot process in PP.
Haven't looked at that bug yet, but will.

My experience with this so far, is taht it works once everytihing else is set up. Looking at logs and making that decision for me is usally a timing issue- Look 2 modules get started in loading. many processes are running , it's a race to load... and the 2d loaded modules finished first... Crashing the first. Look at Solution, Step 2, at the end of this post: 
[http://ubuntuforums.org/showpost.php?p=10909540&postcount=280](http://ubuntuforums.org/showpost.php?p=10909540&postcount=280)

It does work as a sledge hammer kind of "take this now!" Realistically, Out of about 500 users in the past 6 months that I've helped, I've only had 3 users that required this down to the initramfs  level.

Another problem is that these are edits to files that I don't usually trust new users to make.  Mis-edits in /etc/modprobe.d/ and /etc/udev/rules.d/ make a mess. And all the fixes there are still "Hardware" specific.  One fix does not cure all.

EDIT- Now read... Yes, that is what the fix in the mentioned section of the link I posted fixes.

---

