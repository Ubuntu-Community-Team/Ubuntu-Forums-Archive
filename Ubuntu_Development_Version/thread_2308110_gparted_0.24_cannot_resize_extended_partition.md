---
title: "gparted 0.24 cannot resize extended partition"
date: 2015-12-31
forum: Ubuntu Development Version
---

### Post by monkeybrain20122 on 2015-12-31
Hi, not sure if I should post this here. But since gparted 0.24 is default for xenial so I think someone may want to check this out to see if this maybe a problem. 

I have a hard drive partitioned with 1 primary partition for Ubuntu 15.10's /  (sdb1) , an extended partition which is sdb2 and contains the /home of Ubuntu 15.10 (sdb7), swap (sdb6) and a storage part (sdb5) 

I was on vivid. I tried to shrink sdb7 on the left end, then resize sdb2 to the right to eliminate the gap between and then resize sdb1 to the right (see screenshot for what I have achieved finally) 

The first step was completed with no problem (shrinking sdb7) but the second step (resizing sdb2) failed with a popup with an error similar to this one [https://lists.gnu.org/archive/html/bug-parted/2015-09/msg00018.html](https://lists.gnu.org/archive/html/bug-parted/2015-09/msg00018.html) but the scenario may be different since he has a gap between two logical partition apparently. I clicked "No" on the popup and gparted just closed. So there was an unallocated space between sdb2 and sdb7 (right to sdb2, left to sdb7) Restart gparted several time and same problem. It just refused to resize sdb2


At that point I realised my garted has been upgraded to 0.24 because of a ppa I activated, so I downgraded it to Vivid's default 0.19 and everything worked with no issue. Sorry for not being able to get a bit more detailed because my problem is fixed now the condition no longer exists . But the Xenial testers may be interested.

---

### Post by gedakc on 2015-12-31
Unfortunately I am unable to determine what the problem is with the information provided.

If the problem occurs again, please save the gparted_details.htm log file and post it with the report.  That way we can see the exact error message and the steps that GParted was executing.

---

