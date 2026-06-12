---
title: "Software raid breaks HD's?"
date: 2010-01-28
forum: Server Platforms
---

### Post by Ellhound on 2010-01-28
I recently bought two 2TB hard drives (seagate LP). I used mdadm to create a RAID5 array with these and an identical one I already had, then started copying files to it. after a while it stopped copying and stopped the raid array. I rebooted, and was presented with a popup saying two out of the three disks had 'many bad sectors' according to SMART. One of the new ones, and the old one that had never caused any trouble. These sectors are 'waiting to be remapped'.
I assumed this was just some bad luck, and got replacement drives. Yesterday I tried again, with the new disks, and the same problem repeated itself. 


I'm wondering if its possible that RAID is breaking the disks (seems unlikely to me, but I dont know what else it could be).

Any help or suggestions would be appreciated.

---

### Post by Grenage on 2010-01-28
Software RAID won't be breaking any disks, so it's possible that the SMART is mistaken.  For example, 9.10 used to bring up SMART alarms for disks that were fine (not sure if that's still the case).  If real damage is occurring, I would check the PSU.

Either way, take SMART with a pinch of salt.

---

### Post by Ellhound on 2010-01-28
Well copying files did stop working, and the small RAID0 array that I use for root (same disks) doesnt work. So I'm pretty sure theres something wrong.

---

### Post by Grenage on 2010-01-29
Then it's probably time to check hardware; I'd look at the PSU first.

---

### Post by Ellhound on 2010-01-29
I changed the PSU, same problem. Guess its the motherboard next (onboard SATA controller).
I cant keep replacing these disks, so I had better find the problem fast :\

---

### Post by Grenage on 2010-01-29
Hi again,

The board really shouldn't be able to damage the drives, but it is possible it's simply having sporadic issues communicating with them.  Can you verify the drives in another machine?

---

### Post by Ellhound on 2010-01-29
Doing that right now. Unfortunately formatting a 4TB volume takes a while.
Edit: no luck there either. Also replaced the cables, still no better.

---

### Post by Ellhound on 2010-02-03
I tested the voltages on the original PSU, and the 12v was at 11.7v. Not sure what kind of impact that would have, but I'm going to go with the assumption that it somehow damaged the drive causing it to malfunction in the other system as well(getting some clicking sounds from the drives now so theres definately something off). I'm probably going to get new drives(again)and test them in the second system.

---

### Post by Grenage on 2010-02-04
I'm not an engineer and my electrical knowledge is limited, but I don't think 11.7v would do any harm, that's probably normal.  If the PSU does have issues or spikes power, then that's a very possible cause.

---

