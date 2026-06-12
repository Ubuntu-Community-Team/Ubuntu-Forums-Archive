---
title: "RAID6 Reshape Gone Awry"
date: 2012-08-09
forum: Server Platforms
---

### Post by kflynn on 2012-08-09
I have an issue with a RAID6 reshape that I'm hoping someone out there has some thoughts on.  Bear with me, it's a little complex to describe -- and although it won't sound like at the start, this **is** an Ubuntu question!

Something like four years ago I created a 4-drive RAID5 on CentOS 5.2 (I worked at an RHEL shop at the time).  I had 500GB drives, which I knew I'd want to upgrade, but mdadm explicitly said it couldn't do reshapes of RAID5 or RAID6 at the time, so I used a hack with LVM + md + multiple partitions instead.  I have ten partitions (5 - 14), so I had e.g.

md5: RAID5 (sda5, sdb5, sdc5, sdd5 )
md6: RAID5 (sda6, sdb6, sdc6, sdd6 )
etc.

and LVM concatenates 'em all.  Works fine for my use, which is basically backups of other stuff (few writes, many reads), and when the time came I could use LVM to move data off of e.g. md5, disassemble the md5 RAID, reassemble it with the new disk, etc.

This worked great for four years, including going from 4x500GB RAID5 -> 4x1500GB RAID5 -> 5x1500GB RAID6.  As such, please, let's skip the discussions about how crazy an idea it is, and move on.  It's a crazy idea with a purpose, and it actually filled that purpose pretty well. :)

Fast forward to last week.  Still running on CentOS 5.2 (I'm a big fan of sysadmin by not messing with running systems).  But I wanted to add a drive to the RAID.  Not only is CentOS 5.2 rather long in the tooth, at 5x1500GB that LVM trick is awfully slow (it would've taken several weeks).  So I upgraded to Ubuntu 12.04 LTS, to get a better mdadm.

All was well, briefly.

Adding the drive with the 10-partition setup means issuing 10 [FONT="Courier New"]mdadm --grow[/FONT] commands, and I screwed up a step in the script that did it.  Rather than do one grow, wait for it to finish, do the next, etc., it skipped the 'wait' steps and just issued all 10 grow commands.  I ended up with all ten partitions grown to 6 drives, and all but one of them marked "pending reshape".  The one remaining was rebuilding.

A little while later, the machine crashed.  :P  On reboot, the reshape that had been underway at the time (partition 7) picked up and carried on just fine.  But partition 8 didn't. Nor anything after.

So at this point I have partitions 5, 6, and 7 happy; 8 - 14 are marked inactive.  The initial [FONT="Courier New"]mdadm --grow[/FONT] reported that it passed the critical section long before the machine crashed, for all partitions.  [FONT="Courier New"]mdadm --examine[/FONT] on the individual drives shows that each of these partitions believes that they are part of a RAID6 with 6 drives, correct checksums everywhere, event counters the same, but:

1)  Trying e.g.

[FONT="Courier New"]    sudo mdadm --assemble --force /dev/md8 /dev/sd[bdefgh]8
[/FONT]
says

[FONT="Courier New"]mdadm: Failed to restore critical section for reshape, sorry.
      Possibly you needed to specify the --backup-file
[/FONT]
Given that I didn't specify [FONT="Courier New"]--backup-file[/FONT] to the initial [FONT="Courier New"]mdadm --grow[/FONT], this seems... perhaps not entirely helpful.

2)  In a working partition, I always see the *this* entry in [FONT="Courier New"]mdadm --examine[/FONT]'s output matching up with the drive being read (e.g. /dev/sde5 will say *this* is /dev/sde5).  In a **non**-working partition, that's not the case (e.g. /dev/sdb7 says *this* is /dev/sdg7).

3)  Finally, all the working partitions show that their superblocks are version 0.90.00, but all the non-working partitions show 0.91.00.

Suggestions welcome.  ;)  In theory there's no data that I can't replace on these arrays (it's a backup, after all) but it'd be nice to not have to make that particular experiment...

---

### Post by rubylaser on 2012-08-09
Sorry you are experiencing this.  I will be happy to try to help you, but I'd need more info to understand what's going on exactly.

```
cat /etc/mdadm/mdadm.conf
```

Since this is a backup, I'd really suggest you blow this whole config away, zero the superblocks and build this thing correctly.  This sounds like a maintenance nightmare.

---

### Post by kflynn on 2012-08-11
rubylaser, many thanks!  As it happens, I was able to get in touch with NeilBrown, who was kind enough to provide some advice.  Here's the upshot:

[LIST=1]
[*]Yes, metadata version 0.91 is OK, it just means a reshape is pending.

[*]Mismatches in 'this' are most likely due to probe ordering changes; no problem.

[*]The most likely cause for a failure like this if you know that the critical section was passed, and the checksums etc. are consistent, is simply that the backup of the critical section is too old.

[*]To confirm that the timestamp is the issue, use ```
mdadm -A -v
``` which will say 'too-old timestamp on backup-metadata on xxxx' if that's the issue -- and indeed it was, for me.

[*]```
export MDADM_GROW_ALLOW_OLD=1
``` will allow mdadm -A to use the old backup anyway.
[/LIST]
I'm happy to report that that worked just fine for me.  One note is that I was using mdadm 3.2.5 for this; I don't know if 3.2.3 (which Ubuntu 12.04 ships with) supports MDADM_GROW_ALLOW_OLD.

So many thanks to Neil, and thanks again for the offer to help!

---

### Post by rubylaser on 2012-08-12
That was my suspicion.  This [thread ]("http://comments.gmane.org/gmane.linux.raid/37040") is basically your same scenario. MDADM_GROW_ALLOW_OLD=1 has been around at least since 3.1.4 because that supported a RAID 5 -> 6 reshape, but I'm glad you got it figured out.

---

