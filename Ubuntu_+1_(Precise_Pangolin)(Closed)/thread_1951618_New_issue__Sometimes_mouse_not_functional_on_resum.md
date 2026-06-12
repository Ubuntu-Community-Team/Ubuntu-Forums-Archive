---
title: "New issue?  Sometimes mouse not functional on resume from suspend"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by robwilkens on 2012-04-02
When i resumed from suspend twice _today_ (I've been running it the beta a few weeks now), my mouse (or touchpad rather) is nonresponsive.  It's not every time, and the computer is not frozen (the keyboard still works).  Before i report this, i have to ask: Has anyone else noticed this or is it limited to my hardware (an hp laptop).

Also, how do i report this?

-rob

---

### Post by nd456 on 2012-04-02
I don't have a fix but here is a article describing how to report bugs...
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by Muflon on 2012-04-06
> **robwilkens said:**
> When i resumed from suspend twice _today_ (I've been running it the beta a few weeks now), my mouse (or touchpad rather) is nonresponsive.  It's not every time, and the computer is not frozen (the keyboard still works).  Before i report this, i have to ask: Has anyone else noticed this or is it limited to my hardware (an hp laptop).

Also, how do i report this?

-rob

Have you raised a bug for this?  I am expiriencing the same issue and would like to add to your bug report.

Muflon

---

### Post by ~Hinterland on 2012-04-06
I had the same trouble with touchpad scrolling, unchecking "Disable touchpad while typing" in the mouse and touchpad settings solved it for me.

---

### Post by effenberg0x0 on 2012-04-06
Hi
No, Unfortunately, it's not a new bug. We reported it during Oneiric cycle, at alpha 1 stage. 

By then:
- I suggested the synclient TouchpadOff=0 workaround via console to immediately "unfreeze" the touchpad. Still works but it's just a workaround.
- mc4man studied it more and suggested some more advanced options to try to avoid it from happening and it did seem to fix it for most people. Search for his posts in this sub-forum plus syndaemon. 
- Later we verified there was more than one instance of syndaemon running in some cases and we saw new reports of it. 
- Devs seem to have attempted to fix it, but users still got the problem and more than one instance running frequently. 
- Someone recently verified that disabilng two-finger scroll in touchpads that support it seem to reduce the frequency of this bug, yet it already happens. 
- Somewhere between Beta 1 and Beta 2, it became worse: Instead of fixing it, changes made it more frequent.

That's the full story, as far as I know, from OO Alpha to PP Release.

Regards,
Effenberg

---

### Post by Muflon on 2012-04-08
> **effenberg0x0 said:**
> Hi

- Somewhere between Beta 1 and Beta 2, it became worse: Instead of fixing it, changes made it more frequent.

Regards,
Effenberg

This is certainly the case for me.  I have tried unchecking "Disable touchpad while typing" in the mouse and touchpad settings but I am still experiencing the issue.

Muflon

---

### Post by rldev on 2012-04-09
I have the very same problem.

---

### Post by PilotPaul on 2012-04-10
Just happened to me - can someone post a link to the existing bug report?

---

### Post by effenberg0x0 on 2012-04-10
Hi, 
Here's a thread from 2011 in which I pointed out some LP reports about it (last post in thread): [http://ubuntuforums.org/showthread.php?p=11326444#post11326444](http://ubuntuforums.org/showthread.php?p=11326444#post11326444)

I haven't been following this bug since it was fixed. So I'm not sure anymore if there's an active bug report for it, if all of those are closed dups, etc (for all effects this bug is fixed, so the main report is probably closed - not sure).

Regards,
Effenberg

---

