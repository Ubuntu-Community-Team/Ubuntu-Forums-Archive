---
title: "md RAID data scrubbing"
date: 2008-07-30
forum: Server Platforms
---

### Post by BobMUK on 2008-07-30
Hi
I've got a home media server running a 4 member RAID 5 array.  I'd always assumed that MD did background data-scrubbing until this week I discovered that you have to activate a scan like so:

echo check > /sys/block/md0/md/sync_action

Well I'd already run for a year without a scrub so kicked it off as above.  Around an hour later the machine had hung and had to be rebooted.  Hardly ideal!  The logs showed nothing out of the ordinary when the box came back up.

After a bit of digging around it seems that "check" actually triggers a parity resync across the whole array.  Does anyone know if this is true?  It's certainly what's being reported in /proc/mdstat when the "check" is running.

I really don't want a full parity re-sync to be run once a week (as I was planning to schedule a weekly scrub) - regardless of whether the "check" somehow caused the crash.


So onto the real question:
when MD reads a bad block it obviously reconstructs the data from the remaining components - does it (by default) then rewrite the data to the bad LBA?

If this is the case then I can write a script that simply reads every LBA on the array in the background (at a low priority, perhaps in an infinite loop), which relies on MD to rewrite any bad LBAs it finds.

Any comments/thoughts welcome!
Bob

---

### Post by Paul Crawford on 2010-05-31
I had been wondering about this myself.

Generally I have stuck with proper hardware RAID cards such as the Areca ARC-1210 which allows me to dual-boot from the RAID-5 array (it is presented as a single logical SCSI device to Windows & LINUX, just like a normal disk) and it supports periodic background low-priority scrubbing. 

OK, it starts the scrub on every boot, and not just after 2 weeks or whatever the schedule suggests, but then it is probably not intended for a desktop machine.

I found this article that suggests the MD check being periodically initiated:

[http://en.gentoo-wiki.com/wiki/RAID/Software](http://en.gentoo-wiki.com/wiki/RAID/Software)

But as you suggest, it might be easier to have some low priority script dd'ing data to /dev/null to force a read of all sectors.

So far I have not returned to having a machine with software RAID after the pain of getting one up originally, and it dropping a disk for no obvious reason and not telling me! But with Ubuntu 10.04 having MD capability for the desktop installer, I might come back to this again.

---

### Post by indulis on 2011-06-26
Reading the whole drive with dd or some other utility does not help. 

The Linux software RAID subsystem (like most low and midrange adapters and dedicated controllers) does NOT check parity on read.  This is due to the performance hit for forcing each I/O to read from all disks (even if the data you wanted was just on the 2nd disk of the 6 disks in the RAID stripe), and the CPU overhead of calculating the parity (CPU or microprocessor on the adapter/controller).  For some adapters and controllers you can switch the "always check parity" on, but not for Linux s/w RAID = mdadm. 

So just reading the data will always give you "good" data even if the data is in error ("silent corruption"), because the parity was not checked. 

"md RAID does not do parity check on read" [http://www.spinics.net/lists/raid/msg32816.html](http://www.spinics.net/lists/raid/msg32816.html)

There are 2 solutions:
1) Regularly run data scrubbing on your disks, this will correct "silent corruption" errors, hopefully before you use the data.  It will also ensure you get some warning before you get more than 1 disk giving you an error, so you can replace the drive before losing a 2nd drive in the group.
[http://en.gentoo-wiki.com/wiki/RAID/Software](http://en.gentoo-wiki.com/wiki/RAID/Software) - see Data scrubbing section
2) enable "parity check on read" if your adapter/controller/subsystem has this facility
3) monitor your drives using SMART (smartctl) to check for impending problems with drives- there is a list of blocks used to automatically replace blocks on the drive that have problems.  The drive does not let teh operating system see the problems that it covers up by moving bad blocks.. until it runs out of "spare blocks"! (AFAIK- whether block redirects are passed on the the OS and what the OS does with this information is a subject for more investigation).

Data scrubbing via mdadm seems to be safe to do at any time, as the data scrubbing pauses if there is any other I/O activity. To start:
echo check >> /sys/block/mdX/md/sync_action

To stop the scrubbing:
echo idle >> /sys/block/mdX/md/sync_action


And despite the push for ZFS etc to fix "silent corruption" by doing checksums on the file at a higher level, this is just moving the work that should have been done at the lower RAID level to check the parity of each read.

---

### Post by rubylaser on 2011-06-26
mdadm should be doing checks for you every Sunday at 12:57 A.M via cron.  You can verify that this in in place by checking cron.d like this.

```
root@fileserver:~# cat /etc/cron.d/mdadm 
#
# cron.d/mdadm -- schedules periodic redundancy checks of MD devices
#
# Copyright © martin f. krafft <madduck@madduck.net>
# distributed under the terms of the Artistic Licence 2.0
#

# By default, run at 00:57 on every Sunday, but do nothing unless the day of
# the month is less than or equal to 7. Thus, only run on the first Sunday of
# each month. crontab(5) sucks, unfortunately, in this regard; therefore this
# hack (see #380425).
57 0 * * 0 root if [ -x /usr/share/mdadm/checkarray ] && [ $(date +\%d) -le 7 ]; then /usr/share/mdadm/checkarray --cron --all --idle --quiet; fi
```

That should be what the contents of your /etc/cron.d/mdadm file looks like.  You'll want to make sure that you're using smartmontools to monitor your disks, and that you have email alerts setup to warn in you in the event of problems.

---

### Post by indulis on 2011-06-28
Seeing as the check "backs off" to about 1 MByte/sec when there is any other disk traffic, why not run it every Sunday though the default crontab is once a month?

---

### Post by rubylaser on 2011-06-28
I don't do that, as I don't want to go through a whole sync action on 10 hard disks every week (or deal with powering all of them up from standby). But, you can certainly edit that cron entry to do that if you so choose.

---

