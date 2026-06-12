---
title: "ISSUE - FakeAlert-MY.gen (Trojan)"
date: 2010-05-07
forum: Security
---

### Post by rebz7 on 2010-05-07
ePolicy Orchestrator 4.5.0 (Build:8.5.1)
AntiVirus 8.5
 
I have currently received a outbreak of around 5 machines being affected by the above Trojan. The issue has been dealt with but would welcome any ideas on to how i can protect myself from this in future?
 
The machines that were infected were updated to the latest DAT.

---

### Post by OpSecShellshock on 2010-05-07
These trojans won't run on Linux, even if the files are there. Also, you can tell they're fake even on a compromised website because they mimic the file structure and look/feel of Windows. You can avoid the whole thing in the first place by using NoScript and AdBlock Plus while browsing. If these are Windows machines with users who don't know how to browse with caution, then there's nothing you can do but clean up afterwards. In ePO, if the event level is 3 that means it's been removed or blocked. If the level is 4, that usually means it has to be manually removed.

---

### Post by The Tronyx on 2010-05-08
The question isn't Linux specific, at least not as I read it.  The information given by the OP and the mention of EPO indicates that it's a Windows specific issue and that he is asking how to protect his Windows machines from this more effectively.

> 
I have currently received a outbreak of around 5 machines being affected by the above Trojan. The issue has been dealt with but would welcome any ideas on to how i can protect myself from this in future?


User education.

And for what it's worth, FakeAlert-MY.gen is very common to see in the wild with different strings/versions, etc.

---

### Post by cariboo on 2010-05-08
Seeing as this isn't a Ubuntu problem. Thread Closed.

---

