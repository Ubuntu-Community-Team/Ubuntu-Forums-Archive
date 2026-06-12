---
title: "Server problems"
date: 2010-11-03
forum: Server Platforms
---

### Post by djanie78 on 2010-11-03
This is a strange problem. I have Ubuntu server installed on a proper server hardware. My RAID card reports all four HDDs to ubuntu as single drives, which is how i set it up because Ubuntu does not recognize the raid card on the server.
Now you might say if thats the case, why dont i remove the raid card and have the BIOS report to ubuntu as four single drives then i can perhaps setup software raid. Well my board has only one sata port.
Ubuntu is all setup. on the first drive and i have set the other three up using software RAID. 

System works great only problem is it freezes sometimes. Not everytime, just on the odd occassion

I use the same Hardware without the raid card and of course just one HDD and it great. No freezes.

That leads me to believe its the RAID card.

My question is why will it run great for days and sometimes just freeze on me? 

Probably silly but if theres an issue with the RAID card, it should not work at all, should it?

---

### Post by SteveHillier on 2010-11-03
Not a solution, but how are your three disks set up.  What RAID are you trying to use?  RAID0, RAID1 etc?
The problem with the on board RAID and the add on RAID systems I have used is that they are not seen by the OS when being installed.
I recently built a ClearOS system and a Windows 2008 system and for both of them I used Software RAID to get it set up.
I will admit I am getting disenchanted with RAID as a concept.

---

### Post by djanie78 on 2010-11-03
Raid 5 on the other three. thanks

---

