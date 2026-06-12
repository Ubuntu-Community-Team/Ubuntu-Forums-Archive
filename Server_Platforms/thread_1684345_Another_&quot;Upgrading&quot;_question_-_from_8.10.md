---
title: "Another &quot;Upgrading&quot; question - from 8.10 Server to 10.10 Server"
date: 2011-02-09
forum: Server Platforms
---

### Post by adlabens on 2011-02-09
Rather than hijacking [THIS]("http://ubuntuforums.org/showthread.php?t=1684318") thread, I'll ask a question on the same subject (Upgrading - from 8.10 to 10.10 Server Edition), tho this one is slightly different.

I've got an Asus motherboard with 5 SATA 3 drives installed, one is an 80 gb OS drive & the other 4 are 250 gb data drives in RAID5 configuration (approx 750 gb storage).  Overall, the system works fine (it's our home file server).  I've got an external drive port on my XP Pro desktop that is hot-pluggable for an internal drive (just plug & go), which I use with 1 tb drives to backup the files (drag & drop) on the server (not terribly inefficient as everything on the network side is gigabit - not 100 mb.  I'm not afraid of losing all the data as we have several generations of backups and would make a brand new one before starting any such "maintenance" work.  

The system runs without mouse, monitor, or even keyboard, and has no GUI installed - I like it like that, and I use PuTTy as my remote access.  

When I did the original install, I did it with 2 separate OS HDDs and disconnected the first one before doing the 2nd one.  But, that was 2 yrs ago and, reliable as it's been, I've forgotten the process (tho I do have it documented).

I'm thinking it'd be best to simply install a blank 80 gb HDD and do a completely clean install from dead scratch.  If I knew this would work without a hitch, I'd jump on it immediately.  But, I'm thinking it'd be best to disconnect the RAID5 array and do the install without any data drive at all, then connect the 4 physical data drives and issue whatever commands are necessary to remount the entire RAID5 array and have my data back without having to redo the array & restore the data.

**What suggestions would anyone have regarding the easiest and most reliable way to do this upgrade?**

I'm not in a hurry, but we are reconfiguring the house & I'm going to move the server, router, switch, DSL modem, printers, UPS from our current office (going back to being a bedroom) to another location in the house (cabinet in the den or tucked away elsewhere), and I was thinking that'd be a good time to open her back up & do the not-so-annual hardware cleanup (vacuuming) as well as swapping the OS HDD while I had her open.

Thanks for the help.
David
San Antonio, TX

---

### Post by adlabens on 2011-02-11
No replies.  Really?  Wow.

---

### Post by Dark_Stang on 2011-02-11
I always keep my root and home locations seperate, so I never really "upgrade". I just do clean installs. When the partitioner comes up I reformat root, mount swap, and mount home. Then I use the same username as before and I'm all set. I do to reinstall and reconfigure services of course, as those configurations are not stored in the home directory.

Now for your RAID. Is it a real hardware RAID or is it one of those fake "software RAID" setups (if people still do those)? If it's a hardware RAID you shouldn't have anything to worry about. But as always, backup just in case.

---

