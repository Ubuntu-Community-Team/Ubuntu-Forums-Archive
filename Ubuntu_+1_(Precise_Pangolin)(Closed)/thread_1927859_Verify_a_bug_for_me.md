---
title: "Verify a bug for me?"
date: 2012-02-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by QwUo173Hy on 2012-02-18
I can't run 12.04, but need someone to confirm that this issue is no longer reproducable in Firefox. Anyone care to try?

> If you use F11 with Firefox, it goes fullscreen. Pressing it again restores the window. This is okay.

But if you go fullscreen and quit (ALT F4), the next time you start Firefox you will have a problem; it will be fullscreen, but when you try to restore with F11, the window title is under the gnome panel.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/551473](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/551473)

---

### Post by Gregory Lee on 2012-02-18
> **jarlath said:**
> I can't run 12.04, but need someone to confirm that this issue is no longer reproducable in Firefox. Anyone care to try?
I don't have a gnome panel (using unity).  I hit F11 then Alt F4, then started Firefox again.  I hit F11 again to get out of fullscreen mode.  I noticed that the Firefox window was to the left of where it had been before I hit F11 the first time.  I dragged it back to where it belonged.  I don't really understand what the bug is.

---

### Post by QwUo173Hy on 2012-02-18
Thanks Greg. In previous versions of Ubuntu (11.04 for certain), when you hit F11 to exit fullscreen after restarting firefox, the windows titlebar is behind the main panel, which means you can't grab or move it. But it seems to be fixed now, thank you.

This was a pretty annoying bug if you use fullscreen a lot and happen to repeat the sequence above regularly, as I did.

---

### Post by grahammechanical on 2012-02-18
I can confirm that on 12.04 the action of going fullscreen with Firefox and then closing using alt+F4, then open firefox = fullscreen and then F11 does in fact un-maximise Firefox. It is placed up against the left edge of the screen and up under the top panel but not underneath it.

Some on this section of the forum have shared in testing Unity improvements before they were put into 12.04. We have tested Unity 5, Unity 5.4 and Unity 5.4+HUD. The tests involved actions with firefox such as you describe.

Regards.

---

### Post by QwUo173Hy on 2012-02-19
Ah, thanks graham that's great. I've added that to the bugreport so it can be marked invalid / fix committed.

---

