---
title: "LTO tape and tape drives"
date: 2009-06-24
forum: Server Platforms
---

### Post by Hospadar on 2009-06-24
Hi,
I'm just wondering if anyone uses LTO tapes to back stuff up, if so, how does it work?
Does it mount like a (really slow) file system?

I just want to be able to back up my disks and store some extra stuff I don't really have space for or the desire to have on hand readily.  I know lto tapes can probably do all that, I've just never had to do it myself and don't know how it works.

---

### Post by alastair on 2009-06-24
I've not used LTO, but imagine it is fairly similar (on Linux) to DAT tape however (but larger capacity). This is just an informed guess however and I have not researched. 

DAT is not seen as a filesystem at all - but a tape device (that you can seek in, rewind etc.). I used a SCSI DAT tape device for backup a while ago - seen as /dev/st0 (say) i.e. "scsi tape". Use the "mt" command to send commands to it (e.g. mt status). Use "tar" to back up to /dev/st0. All quite 1950's, or this that 1970's :-)

Now, I backup over the net (offsite), and/or to remote filesystems and USB.

---

### Post by windependence on 2009-06-24
I have done this and it's exactly like any other type of tape. If you want a nice GUI to configure it I would suggest Bacula.

-Tim

---

### Post by Vegan on 2009-06-24
Tape is so last year. I use commodity  RAID 6 machines on a rack that users can backup to. Cheap and reasonably safe. A second machine located elsewhere could be a rsync second layer of security.

---

### Post by Hospadar on 2009-07-13
Thanks for the replies, the reason I want to use tape is because (aside from the tape drive itself), tape seems like the absolute cheapest per GB storage you can get, and since I am a private citizen and not a business, buying several large $50+ hdds for a big raid array is not really an option.

If anyone can correct me on my assumption, or show me where all the super-cheap large hdd's are hiding, It'd be appreciated.

The whole idea is to offload some of the lesser-used media (movies, games, music) from my server's main hdd's.  I do have regular hard drives to back up all the documents and important configuration data, as that doesn't amount to much in comparison to all the media.

---

### Post by Vegan on 2009-07-14
Every time I check prices it seems a large disk is cheaper. I am in Canada and a Seagate 1.5TB disks can be had for $140 in Vancouver so it will be cheaper in the US.

You can use a single disk dedicated for backup.

Best is a separate machine so that if the main machine croaks then there is a copy. Most backups are now done this way.

Given that Linux is free, many now repurpose old desktops as file servers for backups.

If you have a spare machine with SATA disk controller, mind you boards are cheaper too now. Then a disk or 2 can be used for backups galore.

---

### Post by windependence on 2009-07-14
> **Vegan said:**
> Tape is so last year. I use commodity  RAID 6 machines on a rack that users can backup to. Cheap and reasonably safe. A second machine located elsewhere could be a rsync second layer of security.

It's also what most enterprises still use for off site backups. 

> Most backups are now done this way.

Dude, you need some serious real world experience. Hard drives are great for high availability backups on site, but what if there is a fire? That's right, we get out the ancient tapes we have for a restore. Funny how that works.

-Tim

---

