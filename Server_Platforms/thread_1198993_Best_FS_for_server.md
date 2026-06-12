---
title: "Best FS for server"
date: 2009-06-28
forum: Server Platforms
---

### Post by comandrei on 2009-06-28
I'm about to install Jaunty to a new machine, and i tought i should give ext4 a try. The machine will be used as web, mysql, mail server + router.
Is ext4 too new to be used in this kind of environment? Did you have issues with it? Other file-system recomendations?

---

### Post by v3xtra on 2009-06-28
Please search, as there has been topics on this.  :)

I posted in one of them, giving links to benchmarks for all of the top Filesystems.  I don't think EXT4 was in there, because as you said it is too new, and shouldn't really be used in an environment which needs to be reliable.  The fastest I believe was XFS, while the most "reliable" was EXT3 for its ability to recover files after power surges and other things.  You're welcome to try it though.  Please try and do a bit of research on it, there are many benchmark sites out there to help you come to a good conclusion!

You're in luck, it was right on the front page.  

[http://ubuntuforums.org/showthread.php?t=1184931](http://ubuntuforums.org/showthread.php?t=1184931)

---

### Post by &#1082;&#1086;&#1084;&#1084;&#1091;&#1085;&#1080;&#1089;&#1090;&#1080;&#1095;&#1077;&#1089;&#1082; on 2009-06-28
If time is an issue, XFS is possibly the best. If you want a truly reliable filesystem, you may want to just use EXT3. The only bug with EXT3 that may cause concern (I am not aware that it has been fixed or not) is a problem when barrier=1 isn't added to the fstab file. Since ext3 does not checksum while writing to the Journal, if data is being written out-of-order onto the disk and the system crashes, it runs the risk of severe data corruption. The best thing I can suggest is to buy a UPS, but I think EXT3 is a very reliable file system to use. I don't use EXT4 yet on my servers because I'm afraid of undocumented features hurting me later :)

---

### Post by tubezninja on 2009-06-28
I'd say as long as you have backups, and the server is on a UPS, ext4 is worth having a look at.  Be aware that there could still be risks, and some have experienced data loss that they blame on ext4. 

That said, I have ext4 successfully running on several servers since the release of jaunty, and have not had problems.  It's been very fast.  Then again, the facility they're housed in has stable, conditioned power, and I haven't had any crashes that necessitated a non-graceful restart.

If you have a filesystem or a sepearate bx you can test ext4 on, you should do that first.

---

### Post by Vegan on 2009-06-28
I use ext3 as the new one is not necessary. My IBM has a 80GB boot disk so its not critical.

The 80GB disk is fine for all the stuff I want to do for now, but I am looking at a new machine.

ext3 can work with 2TB disks so its not a problem.

---

### Post by comandrei on 2009-06-29
Thanks everyone. I do have a UPS, but just to be on the safe side, I will be using ext3.

---

