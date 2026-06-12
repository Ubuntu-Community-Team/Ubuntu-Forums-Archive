---
title: "[SOLVED] What's the best/most common backup medium these days?"
date: 2008-04-10
forum: Server Platforms
---

### Post by Cadmus on 2008-04-10
I'm looking at building some network solutions for people (small offices and the like), but I'm scratching my head over how to back things up away from the server.

Are tapes still king? What about automated cd burners? Are there any compatible with linux? Or do we all just rsync stuff to a hired server elsewhere these days?

Any pointers or rules of thumb I can use to carry on my research myself would be very much appreciated.

---

### Post by Deathrend on 2008-04-10
Tape is always the safest bet, it's very relyable (More so than hard drives), and faster than CD's.  Also compair sizes.  CD holds 700 MB, DVD Holds 4.7, DVD+DL holds 8+Gb, Blu-ray Holds 25 Gb, Blu-Ray-DL holds 50Gb, the tapes we currently use Hold 800 Gb.

Tapes are also reuseable, and with a good setup, you can have everything automated so that your client just walks in and swaps the tapes out of the drive as needed (If sending them offsite).

As for programs, if they're willing to spend a bit more, I would definitly go with Symantec Backup Exec, which has a very robust usage list, and very very cross platform friendly.  If you pay a bit more for the best support, they will practicly walk you through the backup/restore process word for word, step by step, until it's done correctly (This is very nice when you need something restored ASAP, and aren't sure exactly how to do it, like recently we had to restore two corrupt Exchange accounts, which took four or so hours (You have to stage the whole backup before hand, which is the only down side) to which the support was very very helpful with).

---

### Post by stefangr1 on 2008-04-10
I believe that online solutions are also used nowadays. They require little knowledge from users, and backups are physically separated from the user environment so which provides some additional safety in case of fire and theft.

---

### Post by Cadmus on 2008-04-10
Thanks for the quick response, this leads me onto another couple of questions:

Is there a Free back-up program you'd recommend? I'm not a fan of Symantec, is is totally possible to do backups through a command line?

Are tape drives all Linux compatible? Do tape drives all use common standards?

---

### Post by Deathrend on 2008-04-10
Yeah, it mounts just like a CD burner for the most part, the drivers should be built in.  As for command line, you can back up linux machines using the tar command.  This isn't something I've used, but I hear of people backing up complete networks using just the tar command from one PC.

I've never had much luck with free software, however I have heard many good things about rsync/Baccula/BackupPC just to name a few.

As for Symantec, I really dislike most of the products they put out, more so the virus scanners, but this one I like.

Hope this helps.

---

### Post by wieman01 on 2008-04-10
I also recommend 'rsync' or possibly 'unison'. I use both.

---

### Post by Cadmus on 2008-04-10
Ahhh, it's all starting to click, here's a couple of conclusions I've reached reading vendors sites, and I was hoping someone could confirm or correct them

[LIST=1]
[*]Tape drives come in many formats that have built up over the years, the most modern common one is 'LTO Ultrium' and goes up to 800GB with 2-4x that planned for the future.
[*]Tape drives exclusively use SCSI as the interface
[*]Tape drives are random access, you don't have to unpack the whole tape somewhere to find a file
[*]Tape drives can be internal or external
[/LIST]

More questions about this I'm afraid...

Are tape drives in a different form factor to HDs? It looks that way from photos, would I be right in assuming most servers can have one fitted?

---

### Post by Deathrend on 2008-04-10
They can be.  Some fit in the same slot as a CD-ROM, others fix in 4-6U rack slot.  We use a 4U rack  mounted rig, that auto-swaps tapes for large backups.  Some load a lot like VCR's, others load by just sticking the tape into the front.  Most tapes themselves are about the size of a hard drive, only square.

It also depends on internal or external.  Also a SCSI tape will require a SCSI terminator, just remember to have one handy, will save you much much grief if you forget it (more so internally)  I think they also work on SAS (Serial Attached SCSI) these days, and even iSCSI (Internet SCSI) depending on price.

---

### Post by Deathrend on 2008-04-10
I just remembered this: [http://www.smallnetbuilder.com/content/view/30360/234/](http://www.smallnetbuilder.com/content/view/30360/234/) They're asking for what people use for backup these days, which will give you a bit more information to work with (As for free products and such), just check the Comments near the bottom.

---

### Post by jonabyte on 2008-04-10
we will be moving from tape to hd backup (with ubuntu server) during this year sometime.

the cost to upgrade our existing backup/tape machine was way too much considering the cost of getting a simple server with a large hd.

plus hard drives are cheaper than tapes these days even if they are not as reliable you can go through a bunch on hds and save money than buying tapes.

---

### Post by Cadmus on 2008-04-10
Thanks all, I think I've got enough now to start looking at needs and such for the people I'm building this for.

I'm a child of the 90s in many ways, so I'd always considered tapes to be dead, I stand corrected. :)

---

### Post by kevdog on 2008-04-10
Tape backup is sooo slow!  And not fireproof.  I would think offsite, other the internet, encrypted transfer, encrypted data would be the way to back up (ok maybe not the encrypted data part, however it depends who is holding your data!).

---

### Post by wieman01 on 2008-04-11
> **kevdog said:**
> Tape backup is sooo slow!  And not fireproof.  I would think offsite, other the internet, encrypted transfer, encrypted data would be the way to back up (ok maybe not the encrypted data part, however it depends who is holding your data!).
That's not much faster either, is it?

---

### Post by songshu on 2008-04-11
i use local and remote hardisks with rsnapshot,

works really nice.

---

### Post by PointyWombat on 2008-04-11
Building a backup solution that works for you depends on what you need to do. You need to consider things like how much data needs to be backed up, how often do you want to do backups, how long do you need to retain this data, your budget, automation, etc. You may be able to get away with a network based backup service if you're not backing up too much data, or you can go with something more technical but cheaper such as a  tar over ssh to a remote tape drive controlled by homegrown scripts or backup software.

As for the argument that tape drives are slow, well that depends (mostly on budget). For example, I can sustain 200MB/s (that's bytes not bits) on my FC tape drives at work and get 1TB (compressed) on each tape, but then again, it cost $35K for each drive and around $180/tape :).  Note that 200MB/s is faster than most if not all single hard disks  today.

Jeeze, i just noticed this thread is marked as solved, but I'll post anyway..

---

### Post by songshu on 2008-04-11
> **PointyWombat said:**
> Building a backup solution that works for you depends on what you need to do. You need to consider things like how much data needs to be backed up, how often do you want to do backups, how long do you need to retain this data, your budget, automation, etc. You may be able to get away with a network based backup service if you're not backing up too much data, or you can go with something more technical but cheaper such as a  tar over ssh to a remote tape drive controlled by homegrown scripts or backup software.

As for the argument that tape drives are slow, well that depends (mostly on budget). For example, I can sustain 200MB/s (that's bytes not bits) on my FC tape drives at work and get 1TB (compressed) on each tape, but then again, it cost $35K for each drive and around $180/tape :).  Note that 200MB/s is faster than most if not all single hard disks  today.

Jeeze, i just noticed this thread is marked as solved, but I'll post anyway..

offtopic i know, but indeed solved already,

35K ????

---

### Post by PointyWombat on 2008-04-11
> **songshu said:**
> offtopic i know, but indeed solved already,

35K ????
[URL="http://www.sun.com/storagetek/tape_storage/tape_drives/t10000/"]
http://www.sun.com/storagetek/tape_storage/tape_drives/t10000/[/URL]

---

### Post by andguent on 2008-04-13
I realize it is marked as solved, but I wanted to throw one more option out there.

Boxbackup is a nice open source utility that encrypts the data, sends it up to a server, and the data stays encrypted. You have to host your own backup server, and the setup isn't quite as easy as some others, but it can be worth it. 

Boxbackup actually keeps old copies of files for as long as you can keep the disk space available. It can do a gig every two hours when both ends are using basic cable modem 6Mbps/1.5Mbps connections. It only sync changes in roughly the same way as rsync.

Honestly, the software is still maturing, but absolutely invaluable on Linux -> Linux setups. I personally wouldn't recommend the Windows agent.

---

