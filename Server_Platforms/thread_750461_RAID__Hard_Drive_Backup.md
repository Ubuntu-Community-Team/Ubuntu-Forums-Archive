---
title: "RAID / Hard Drive Backup"
date: 2008-04-09
forum: Server Platforms
---

### Post by efriese on 2008-04-09
I want to provide an easy way of backing up a hard drive on an existing Ubuntu Dapper server. I bought a fake RAID card and separate hard drive to do RAID 1, but the software to control the card only works in Windows. I started reading the fake RAID community tutorial, but it sounds like I would have to start from scratch with the server, which really isn't possible. Is there a way I can configure RAID to mirror the main hard drive on to the backup? Is there a better way to do this? The end result I'm looking for is if the main HD fails, I can quickly boot off the second drive and have the server up and running again.

Thanks!

---

### Post by efriese on 2008-04-09
Would rsync work?

---

### Post by efriese on 2008-04-10
Any advice?

---

### Post by songshu on 2008-04-10
for what its worth,

forget about the unreliable flimsy raid card and use the linux raid that you can find in the installer or after you installed it with mdadm, its pretty easy to create a raid array and add a drive to it on a running system.


having a dedicated device to manage your raid definetely used to be a must in the days that processors were not like today, nowadays its only worth it in cases where you might consider raid5 under certain circumstances where they have positive and negative aspects and you are willing to spend a lot of cash.

the cheap on-board raid you can find on any mobo nowadays is something you should stay away from...period...

not really sure what kind of card you got, but for raid1 i personally would not consider anything else then using mdadm.

*edit
just saw this link is for raid0, but its basically the same principle, just google some cause there is plenty of guidance on this subject.
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by rickyjones on 2008-04-10
> **efriese said:**
> Any advice?

If you already have a hard drive in the system and you want to mirror it without reloading the OS then the only option I see is to use software, like rsync, to sync the disks on a regular basis.

If you want RAID1 then you'll have to reload the OS and configure the RAID1 at that time.

-Richard

---

### Post by songshu on 2008-04-11
> **rickyjones said:**
> If you already have a hard drive in the system and you want to mirror it without reloading the OS then the only option I see is to use software, like rsync, to sync the disks on a regular basis.

If you want RAID1 then you'll have to reload the OS and configure the RAID1 at that time.

-Richard

rsync does a very nice job if you want to make backups indeed.
however it is NOT needed to re-install if you would want to do raid1

[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)
i guess this one applies to ubuntu as well.

i did it myself several times, and even made notes once when i did a raid10 + raid1 with 4 disksand 2 disks on a running system.
[http://songshu.org/doku/doku.php?id=host.cipar.net#setup_raid_10](http://songshu.org/doku/doku.php?id=host.cipar.net#setup_raid_10)

---

### Post by rickyjones on 2008-04-11
> **songshu said:**
> rsync does a very nice job if you want to make backups indeed.
however it is NOT needed to re-install if you would want to do raid1

[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)
i guess this one applies to ubuntu as well.

i did it myself several times, and even made notes once when i did a raid10 + raid1 with 4 disksand 2 disks on a running system.
[http://songshu.org/doku/doku.php?id=host.cipar.net#setup_raid_10](http://songshu.org/doku/doku.php?id=host.cipar.net#setup_raid_10)

I stand corrected! Thank you for the links, I guess you learn something new every day!

I will recommend that you prepare a full backup before attempting this, however. Just in case!

Sincerely,
Richard

---

### Post by songshu on 2008-04-11
always backup before doing something new or before a few beers ;)

depending on how critical your server is you could ofcourse always try to do it on a spare machine to get yourself confident with the procedure but its pretty straightforward once you understand the procedure.

IF something goes wrong, please remember the word "tesdisk" it saved my life once when formatting the wrong drive ;)

---

### Post by rickyjones on 2008-04-11
> **songshu said:**
> depending on how critical your server is you could ofcourse always try to do it on a spare machine to get yourself confident with the procedure but its pretty straightforward once you understand the procedure.


VMWare is great for this if anyone would like my suggestion. Replicate a similar system in VMWare and give it a dry run.

-Richard

---

### Post by songshu on 2008-04-11
> **rickyjones said:**
> VMWare is great for this if anyone would like my suggestion. Replicate a similar system in VMWare and give it a dry run.

-Richard

never actually tried that but it should be possible, how do you get it to notice the second disc?

---

### Post by rickyjones on 2008-04-11
> **songshu said:**
> never actually tried that but it should be possible, how do you get it to notice the second disc?

When you create a new VMWare virtual machine it by default sets you up with a single disk. From within the virtual machine settings window you can add new hardware, one of which is hard disks. Just add one and it'll show up when you boot the virtual machine.

-Richard

---

### Post by songshu on 2008-04-11
nice....

---

### Post by andguent on 2008-04-13
All of songshu's links look good. I would like to second any opinions on migrating a live server into a mirrored raid. I've done it twice in the last month. I personally end up doing it by pulling pieces from the following links:

[http://www.linuxjournal.com/article/9942](http://www.linuxjournal.com/article/9942) -- Written for migrating a live server into a VM, but not using RAID at all. I personally pick out the 'rsync while live, then knoppix and rsync to finish' concept.

[http://really.slacking.net/~modat7/howto/RAID-mdadm-Setup.txt](http://really.slacking.net/~modat7/howto/RAID-mdadm-Setup.txt) -- Semi short semi sweet howto. I pull out the 'sync into the raid using knoppix' section to use in conjuction with above.

[https://alioth.debian.org/frs/?group_id=30283&release_id=288](https://alioth.debian.org/frs/?group_id=30283&release_id=288) -- I personally ignore anything LILO or initrd related, and really only use this guide when the other two are missing something.

It is very possible that the howto's already posted have all of the same info or even more.

---

