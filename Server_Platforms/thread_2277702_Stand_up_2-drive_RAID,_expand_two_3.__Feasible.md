---
title: "Stand up 2-drive RAID, expand two 3.  Feasible?"
date: 2015-05-11
forum: Server Platforms
---

### Post by tylersontag on 2015-05-11
Hey all

I'm moving data from an old RAID5 (2TBx3) to a new RAID5 (4TBx3) and I'm wondering how to approach it.

I have a 5 bay external RAID enclosure.  3 bays are for the existing RAID.  I'm wanting to toss 2 of the 4TB drives in, stand up the new RAID5 and move the files over.  

I'm wondering how best to do this.  theres only about 3TBs being used on the old RAID so all the data could fit on any one of these drives.  I was wanting to assemble 2 of the drives in a RAID5 (which should be basically a RAID1), move the files over, then add the 3rd drive.

Well, when i tried this, but RAID5 won't assemble with only two drives.

So, i'm wondering how to get everything moved around?  Do I try to move the files over to the degraded RAID5 (new one built, but is marked as degraded)?  Do i assemble the 2 drives as a RAID1, add the 3rd drive and upgrade from a RAID1 to 5?  Yet some other option?

---

### Post by tylersontag on 2015-05-11
OK, its not degraded, i think its just doing building the initial parity set.  However its taking forever to assemble.. running at 1 MB/s.  Should i review my setup options?  i picked a 512K chunk size.

---

### Post by darkod on 2015-05-11
How did you create the new array? As raid5 and using the 'missing' placeholder?

Don't create it as raid1. No point doing that and then doing a reshape right away.

You could also try replacing the disks one by one with the bigger ones but what you are trying is also good if you have space for the arrays to run in parallel until you copy the data and decomission the old one.

---

### Post by tylersontag on 2015-05-11
> **darkod said:**
> How did you create the new array? As raid5 and using the 'missing' placeholder?

Don't create it as raid1. No point doing that and then doing a reshape right away.

You could also try replacing the disks one by one with the bigger ones but what you are trying is also good** if you have space for the arrays to run in parallel until you copy the data and decomission the old one.**

I think so too... i did some tweeking and got the resync up to 35Mb/s so it should be up by tomorrow morning, i can get the move started and hopefully have the data moved by EOD (no idea how long thats going to take, right now)  Then i can decom the old drives, re-purpose one of the old bays and add/grow the array by later in the week.  Thanks all

---

### Post by darkod on 2015-05-12
Actually you can start using a mdadm array as soon as it is created. You don't need to wait the initial sync to finish. But you are in no hurry so you can wait if you want to. The most important part is whether it was created as raid5 with a member missing. What does cat /proc/mdstat say?

The sync of 35MB/s seems little low to me but I might be wrong. The initial sync doesn't even copy any data. It just prepares the partitions.

---

