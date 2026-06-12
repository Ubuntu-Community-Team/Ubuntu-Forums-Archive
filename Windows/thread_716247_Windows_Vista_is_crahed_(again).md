---
title: "Windows Vista is crahed (again)"
date: 2008-03-05
forum: Windows
---

### Post by mr.propre on 2008-03-05
I hope they planning to do something about it because its getting on my nerves.
After a simple reboot on my windows machine, I get the lucky error: "disk failure, bablabla"

I have vista less then a year and those is about the third time I had this error, last time I needed to patch my Ubuntu laptop was ... never.

Now I'm running the repair disk hoping that it get fixed without losing a partition (like last time).

---

### Post by K.Mandla on 2008-03-05
Moved to Windows Discussions. Perhaps another Vista user can help you troubleshoot it.

---

### Post by rickyjones on 2008-03-05
> **mr.propre said:**
> I hope they planning to do something about it because its getting on my nerves.
After a simple reboot on my windows machine, I get the lucky error: "disk failure, bablabla"

I have vista less then a year and those is about the third time I had this error, last time I needed to patch my Ubuntu laptop was ... never.

Now I'm running the repair disk hoping that it get fixed without losing a partition (like last time).

If you are getting disk error then I'm going to suggest looking at the hard drive as the culprit. I know how people love to bash Microsoft, but sometimes it really isn't the fault of Microsoft software. Pop in a new hard drive and see if it fixes the issues.

-Richard

---

### Post by mr.propre on 2008-03-06
I guess -_-
The strange thing is that the Ubuntu live cd and other live cd's can access the windows partition without a problem, 2 time ago. This time it seems I have an other situation because windows gives the error "invalid partition table". Strange because the start up disk can boot windows and chkdsk didn't discover any problems -_-

I even can acces the volumes trough windows diskpart using the repair cd >_<

EDIT: and its fixed by resigning the active partition. This is why I get it on my nerves when using windows, things like that needed to be detected and be repaired automatically.

---

### Post by isaacngym on 2008-03-10
ive been using vista for quite a while alrealy and i have never seen that error. i hope ubuntu is better though...


P.S. i heard vista is different from other windows syatems and is not easy to change drivers compared to otherwise. is it true?

---

### Post by futureproof on 2008-03-11
reinstall your HD controllers.

---

### Post by Calash on 2008-03-11
Honestly that sounds like a hardware error to me.  If you can get into Windows at all, check the event logs and see if you have a mess of "Disk Write" failures.  That is a good sign of a drive going down hill.

Browsing a damaged hard drive is not that hard as long as the directory table is intact so that is really not a good indication of an impending error.

---

### Post by Chelidon on 2008-03-11
My own Vista decided to kill itself. I don't know what happened, other than it tried to load some updates, rebooted into safe mode, rebooted into normal mode, gave me a blue screen with a cryptic message like "system dump crash" rebooted and then complained that the loader couldn't find my operating system!

I've had Linux for a few months. I just got this box back from repair (my screen was broken) and to my relief they hadn't wiped my drive, but it's starting to look like I have to do it myself anyway! I wouldn't mind but my Photoshop will be obliterated...

---

### Post by mr.propre on 2008-03-16
Well just in case you wonder, It wiped an other partition -_-
As from now on, my vista installation gets its own HD. All my other files are safe on other Disks and as soon  windows crashes I unplug my other drives.

---

