---
title: "What is taking up so much space? To Delete or not Delete a Snapshot?"
date: 2017-11-03
forum: Virtualisation
---

### Post by Rick St. George on 2017-11-03
Confused about this issue:

Looking at a second HDD with nothing but a WinXP VM thereon, via Properties it shows;

-----------------------------------
 24 items, totalling 116.6 GB 
(some contents unreadable)
17.7 GB of 141.5 GB free
-----------------------------------

When looking in the folder: /Data/VirtualBox VMs/XP32-1/Snapshots/, I see two Snapshots. Can I delete the old one?
One is dated today 42GB, and the other 11.21.2016 at 31GB.

My question is, what is taking up all the room? Besides WinXP, all I'm running therein is MetaStock (trading system). 
Don't remember it ever taking up that much room. Concerned about running out of space! I could delete the WinRE on this HDD, 
but that would only clear up approx. 14 more GB.

Sorry, this probably should be in Virtualization ... unsure!
Thanks!
Rick

---

### Post by ian-weisser on 2017-11-03
Delete VM snapshots from within Virtualbox's snapshot manager, else you may cause yourself much pain.

---

### Post by Rick St. George on 2017-11-03
Tried that ... this is what displayed ...

```

Unable to merge storage '/media/stephen/Data/VirtualBox VMs/XP32-1/Snapshots/{0a7d5839-e132-49ae-a39e-586dbbcfcb4e}.vdi'. Not enough free storage space.


```

---

### Post by ajgreeny on 2017-11-03
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

---

### Post by Rick St. George on 2017-11-03
This must be a BUG / DESIGN FLAW in VirtualBox. See this Link;
[https://www.virtualbox.org/ticket/7461](https://www.virtualbox.org/ticket/7461)

The above thread was opened 7 years ago ... and the problem still persists. Anyone have a suggestion to my delimma?
I thought it would be a good idea to take a snapshot after major changes. I now have 3 that are 40 GB each, taking up too much room.
In the current state, in Virtual Media Mgr, selecting the last vdi image - Copy & Remove is greyed out. 
What is Release? What if I Clone the VDI-current state, then can I delete the old VM?

---

### Post by Rick St. George on 2017-11-04
Here is what I did. Cloned the current state (after stopping vm). After cloning - Deleted the old VM with 3 snapshots of 40GB each. 
This freed up 80GB on the HDD. Case closed.

Thanks All!
Rick
:-\"

---

### Post by #&amp;thj^% on 2017-11-04
Good Job Rick! :)
Thanks for posting your fix.

---

