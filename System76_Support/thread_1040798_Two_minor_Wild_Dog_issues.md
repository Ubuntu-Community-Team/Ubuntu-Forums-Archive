---
title: "Two minor Wild Dog issues"
date: 2009-01-15
forum: System76 Support
---

### Post by ProfDecoy on 2009-01-15
I finally got my Wild Dog the other week and I've been quite happy with it so far.  However, right now I have two minor issues with it.

1) The onboard ethernet doesn't want to auto-negotiate to 100mbs to my 5-port (Linksys) 10/100 switch.  I've tried a couple of different cables and it only comes up at 10mbs and none of my other systems have issues.  I don't have a Gigabit switch right now to see if there's any other issues with it right now.

Is there an easy way to force it to 100mbs?  Though if it's not auto-negotiating to it, it may have a reason for it.  I'm just trying to sync a little over 100GB of data between my desktop and laptop, so the higher transfer rate would be appreciated (about 27 hours to copy when I started it last night and its still going, though the smarter thing would have been to connect the drive directly to my laptop).

2) I ordered my system with two burners in it.  However, I can only burn to the 2nd burner (slave on the IDE channel).  Not that I have any immediate need to be burning two discs at the same time, but it would be nice to have both working in the event that I do.

Is the dual burner a current limitation of the disc writing libraries?  Or am I forgetting/missing something?

Thank you.

---

### Post by thomasaaron on 2009-01-16
> Not that I have any immediate need to be burning two discs at the same time, but it would be nice to have both working in the event that I do.

That question is all over the web. I'm not aware of a Linux program that can burn multiple disks at the same time. I know that Nero in Windows is supposed to be able to do it.

From what I read, though, it would be a terrible drag on the system. But I don't really know.

Regarding your first question, I'll do some testing here in the shop and see what I can figure out.

---

### Post by ProfDecoy on 2009-01-16
Thank you.  I figured that was probably the case with the Disc burning.  More of a curiosity than anything, guess I should have done some searching first.

I've got a 2nd 5-port switch around somewhere that I'll try to dig out tonight to see if it makes a difference.  However, it's the same model as the one that it's connected to right now, but probably a newer revision.

---

### Post by ProfDecoy on 2009-01-16
Ok, I've done what I should have done from the beginning and tried a different switch (had to remember where it was hiding though).  The replacement switch (Linksys EZXS55W Rev 3) gets the desktop to negotiate at 100mbs, where as the other switch (same Model Rev 2) apparently causes errors when it tries to negotiate to 100mbs and it drops to 10mbs.

Now that I know that it's an issue, I'll use the older switch elsewhere.

---

