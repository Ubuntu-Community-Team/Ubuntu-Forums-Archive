---
title: "Looking for backup software"
date: 2007-09-09
forum: Server Platforms
---

### Post by arrow_runner on 2007-09-09
I used to have all of my personal data on a Windows server and used Ghost to back it up to DVDs.  Now I'm moving it all to my Ubuntu server. This is what I'm looking for:

Must be able to backup and span across DVDs.  The initial image will be about 300GBs. I have 1TB total space that could be filled.

I'd prefer to do it remotely from an SSH shell, but I can do it from the console and even Gnome if need be.

I would like to be able to backup the contents of selected directories instead of an entire filesystem like Ghost did.  This way I can restore to a different type or size of filesystem if necessary.

I would also like to be able to EASILY search or browse the DVDs for files.  I never got Norton to work like that.

Something with incremental backups would be nice as well.

My biggest concern would be if something catastrophic happened like my raid card died or I lost too many hard drives and the operating system + data were destroyed, I would be able to rebuild and easily put the OS + data back on the drive.

Thanks, and why does this guy have Goku hair? :lolflag:

---

### Post by HermanAB on 2007-09-09
Bacula, rsync, tar...

Cheers,

H

---

### Post by arrow_runner on 2007-09-09
Bacula looks like overkill for what I'm wanting, and I want to do the backup locally.(The server will have a DVD burner). Bacula looks like it's for backing up systems on a network.

I'm not sure how rsync would work with DVDs, and I don't think plain tar would work for what I want.  I would think that I would have to tar all of my data back to the hard drive then burn the tarballs to DVDs.  Restoring data would be an equal pain, would it not?

---

### Post by HermanAB on 2007-09-09
Tar will do spanning, but you need to create a couple of scripts: One to do the main tarring and the other to tell it what to do when it needs to create a new volume.  Getting it to work is rather time consuming, but it can be all integrated with cdrecord to write the DVDs and if you have a little robot then you can change them too.  

In general, I find making backups to DVDs too cumbersome to be practical.  I therefore rather put a big hard disk in anothe PC and use rsync from the one to the other.  This can be done over the internet using ssh.  The backup machine need not even run Linux - Cygwin on Windows works fine too.

Cheers,

H.

---

