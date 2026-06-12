---
title: "Server has not been updated in a year - update help"
date: 2012-06-15
forum: Server Platforms
---

### Post by leegold on 2012-06-15
Hi,

I have Ubuntu Server 10.04 on a home network, with LAMP but I use lighttpd instead of Apache. It has not been updated in about a year. I'm worried if I do apt-get update, apt-get upgrade in one swoop it's going to break something, maybe be hard to fix.

Is there a better way, like upgrading certain things first, doing it in steps, so if something breaks I can narrow down the problem easier? Will config files especially server config files be overwritten?

Thanks

---

### Post by Lars Noodén on 2012-06-15
Like with every situation where there are potentially big changes, make a back up of your data and maybe also of your system.  

That said, the config files should not be overwritten during the upgrade.  And things should work nicely afterwards after the update.  The update should not introduce major changes.

---

### Post by LHammonds on 2012-06-15
If you make a small change, a large change or no change, always have a backup that you can restore if anything goes sideways.

If you were running in a virtual server, it would be as easy as making a snapshot and then do the upgrade...if anything goes sideways, restore the snapshot.

If you are running on bare-metal, you could use an external USB drive and "Redo Backup and Recovery" to boot your machine to the CDROM and make a quick backup.

LHammonds

---

