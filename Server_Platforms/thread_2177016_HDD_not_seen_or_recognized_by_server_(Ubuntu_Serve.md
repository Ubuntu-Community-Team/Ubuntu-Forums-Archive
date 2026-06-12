---
title: "HDD not seen or recognized by server (Ubuntu Server 12.04.3, 64, mdadm RAID5)"
date: 2013-09-26
forum: Server Platforms
---

### Post by greyday on 2013-09-26
Hi all--it's been a fun month of moving our servers; after lots of troubleshooting, upgrading to 12.04.3, spending an entire week rebuilding our backup RAID (ironic) and converting from a 5 to a 6, and now spending the last night solving fstab and mdadm.conf problems, I was proud to say I got everything exactly where I wanted it as of this morning without having to ask for help (googling about a hundred times, sure, but help? nah.).  But...

So of course, everything was perfect for about 12 hours.  Then I had one of our drives fail out of one of our raids (we currently have 1 4 disc RAID5, 1 5 disc RAID6, and 1 3 disc RAID5, the latter of which is the one that failed).  Through various attempts to unmount (kept getting the "in use" error, even though I stopped all applicable programs), I finally just decided "meh" and rebooted so that I could diagnose the problem.

Here's where the fun begins.

On reboot, the server didn't pop back up on the network.  I went to the basement to find it was in Bash.  Weird.  Rebooted to find the "blah blah blah RAID is degraded, attempt to mount degraded RAID?" message, so I hit Y.  The screen went blank and stayed that way.

Reboot.  This time hit N, ended up in Bash.  Could see the degraded RAID, but the failed disc wasn't showing up.  Huh.  Tried removing the disc entirely from the rack, rebooted.  Same problem as above.  So I pulled all three drives and rebooted.  Success!  Quickly went into mdadm.conf and fstab and #ed out the lines connected to that RAID.  Then slotted the drives back in and rebooted with the non-failed drives returned to make sure everything worked properly.  It all does.

So now here's the weirdness: the two healthy drives are showing up as spares in the array, and the third drive won't show up.  At all.  Hot swapping it in results in the system identifying that the drive is there, but ls /dev/sd* shows no new drive.  Nothing, not even showing up.  I thought maybe it was a mechanical issue, so I brought it upstairs and plugged it into my USB diagnostic drive caddy, and OSX recognized it immediately, and putting my ear to the drive nothing sounded amiss. So...

Was the failure partition related or mechanical?  If mechanical, why can my mac identify the existence of the drive but Ubuntu not?  I should also mention that this is, of course, the replacement drive we just bought to replace another dead drive (wasn't part of the array, we built this 5 from the new drive and a previous RAID 0 that we destroyed), so does it sound like the drive may be just hosed?  I spent the last hour searching around but couldn't find any topics that matched or explained/resolved this...

---

### Post by SaturnusDJ on 2013-09-27
Begin with acquiring S.M.A.R.T. reports for all drives.
```
smartctl -a /dev/sda
```

If it's a long time since a test has been run, do a test first:
```
smartctl -t short /dev/sda
```
A long test is better but will take several hours.

For the drive not showing up in the system, maybe you can get the S.M.A.R.T. data via another computer?
And is it detected in the BIOS/POST in a way?

---

### Post by rubylaser on 2013-09-27
Also, did you swap the disk order to verify that the failed disk doesn't work in all bays, and it's not a bad backplane/SATA cable/SATA head/etc in that machine?

---

### Post by greyday on 2013-09-27
@SaturnusDJ--thank you for the note to run the test; after running it (using an AZIO hot swap USB dock through a netbook running 13.04): overall-health assessment test result: PASSED.  Which is good.  I can't really make sense of a lot of the rest of the data in the table to be honest, it's all a bit convoluted.  I pasted it to a document but unfortunately my netbook's wireless doesn't work, so I can post it later if needs be (but I think the point is made, it is seen by the netbook and it passed SMART)...

@rubylaser--a good thought.  Now that I know it can at least be recognized by my netbook, that is my next step.  It's unlikely to be the cable or the card, though it could be the bay (it's bay 4 of a 4 bay multiplier, and the other three drives are fine [they're on a different array]).

...and to top it off I just had a drive fall out of my RAID6.  DURING a backup, which means rebuilding time no matter what (yay).  It's going to be a looong weekend.

---

### Post by greyday on 2013-09-28
Ok, sorted. Turns out Occam's Razor can suck it, it was actually three separate problems; one software, two hardware. The eSATA cable WAS bad, but so was one of the two PCIe cards, which is why one drive from each multiplier was malfunctioning and why the drive dropped out of my other array as well. I'm still not sure why that prevented the system from booting, but with the parts swapped out (thanks to downsizing I have no end of spares) everything seems to be running smoothly. The RAID6 is rebuilt and in perfect health, the RAID5 is currently rebuilding with the two healthy drives still showing all content. Phew! Thanks, guys for the help (and the SMART testing suggestion, it helped me catch a dying drive during this whole process). :)

---

### Post by rubylaser on 2013-09-28
Great, I'm glad you got it figured out :)

---

