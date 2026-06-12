---
title: "Best Process for Upgrading Servers"
date: 2008-10-07
forum: Server Platforms
---

### Post by steve_c on 2008-10-07
I have a few production servers which now have operating systems past their end-of-life. They're running SuSE 9.1 which is no longer supported. The hardware is still adequate for their job function, but since SuSE will no longer provide security updates now is an excellent time for me to upgrade these to Ubuntu 8.04 LTS.

Since these are production servers though I want to do this the absolute best way possible, and I'd like as much help as you all can give me.

Right now I'm planning to back up the following folders:
/etc
/home
/root
/srv
/opt
/usr/local

If this were a Debian-based OS I would also run:
```
dpkg --get-selections > installed-software.txt
```
so that I could have a list of packages that I know were installed and potentially need reinstalled. That said, I don't have that. Does anyone know how to generate a similar list of installed packages with yast?

So my plan as of now is to back all that up, format, and install Ubuntu 8.04 LTS.

Does anyone have any other advice or suggestions?

Thanks.

---

### Post by MusicMastaMike on 2008-10-07
Check this link out, it should tell you what you need:

[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

---

### Post by lykwydchykyn on 2008-10-07
If there is room on the drive, you might consider installing Ubuntu on a different partition, that way you can swap back if things fail.  How much downtime can you afford?

---

### Post by steve_c on 2008-10-07
I plan on doing each server over the course of a weekend, which should be acceptable. That also should give me more than enough time to get things installed and check that things are in good working order by Monday.

---

### Post by steve_c on 2008-11-30
Just to update anyone interested I'm two servers into the five servers I intend to upgrade. So far everything is going more smoothly than I would've imagined.

The only hiccups I've had were decision making on my part (deciding the ideal file system and partitioning schemes--I didn't realize you couldn't use software raid5 as a boot device so I had to scale back to an OS drive and a pair of raid1 disks, all running ext3 because it's probably the most tested and reliable journaled Linux FS at the moment), and a problem with NFS and automounted drives that seems to be fixed now.

Administering Ubuntu/Debian-based systems is just so much nicer. Lots of thanks to the developers.

---

