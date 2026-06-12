---
title: "Backing up data"
date: 2012-08-29
forum: Server Platforms
---

### Post by lordhedgehog on 2012-08-29
I posted a previous question that did not get any satisfactory answers, so I'll generalize the question. At this point I'm willing to take any reasonable solution.

What I need: I have a remote server. It's not mission critical -- if a hard drive fails, I can accept a day or two of downtime. However, I want to ensure minimal data loss, preferably no data loss, in the event of a hard drive failure.

What I have: An EFI motherboard that doesn't appear to be able to disable EFI mode. I can access SATA through IDE, Legacy IDE, ACHI, and RAID (emulated), along with two identical 1.5TB hard drives, one of which has a currently working Ubuntu installation.

I spent a lot of time trying to get a proper RAID1 set up, before coming to the realization the at the moment, EFI cannot be used with RAID1. At one point I managed to get the / mount on a RAID1, and although it couldn't boot from the second drive, it did back up the data. I don't know how I achieved it, and I haven't been able to re-create that condition since.

I'm open to any and all suggestions. Is there a good way to take an existing / partition and convert it to a RAID1 using another drive? If so, is there a good way to convert a drive with a degraded RAID / partition into a working bootable drive after failure of the primary drive? Barring that, is there a good way to backup a working system onto a separate hard drive with little or no downtime to the system for backups?

---

### Post by SeijiSensei on 2012-08-29
How about using a USB device with RAID1 like [this one](http://www.newegg.com/Product/Product.aspx?Item=N82E16822165286)?  I back up my office server to a similar device from Maxtor using rsync.

---

### Post by lordhedgehog on 2012-08-29
Considering the box already has an unneeded extra hard drive installed, I'd really like someone to help me figure out how to easily back up data to it.

I can easily write a cron job that copies /var/vmail, /etc, /home, and backs up the SQL database... But that still requires a really significant effort to rebuild the machine after a fail. Is there a way to get all the packages, binaries, libraries, etc., all backed up and restored without buying additional hardware?

---

### Post by koenn on 2012-08-29
> **lordhedgehog said:**
>  Barring that, is there a good way to backup a working system onto a separate hard drive with little or no downtime to the system for backups?

I remember trying something along those lines, quite a while ago, but iirc, it's possible.

notes:
[http://users.telenet.be/mydotcom/howto/linux/diskfakeraid.htm](http://users.telenet.be/mydotcom/howto/linux/diskfakeraid.htm)

---

### Post by LHammonds on 2012-08-29
I use a combination of fsarchiver, LVM and rsync.  Check my signature for how I setup an Ubuntu Server which covers backup / restore of the system.  Other links have examples of how I backup specific data and archive it over time (e.g. MySQL server)

With my server setup to use LVM, I then have fsarchiver configured to make a backup of my boot (non-LVM) and all my LVM partitions (including root) while the server is online because I use snapshots to get a consistent state for the file system while online.  This provides the full-server recovery and I really only need that particular backup in the event of a full system failure.

I use rsync to keep data files backed up and easily retrieved if I delete a file (non-system recovery).  I typically have a location set aside to have an online backup of my data files (e.g. duplicated) and also have compressed archives of this duplicate data in order to go back in time to retrieve a file that may have been deleted weeks ago and not noticed until later.  This provides for file-level recovery over extended periods of time.

LHammonds

---

### Post by SeijiSensei on 2012-08-30
> **lordhedgehog said:**
> Considering the box already has an unneeded extra hard drive installed, I'd really like someone to help me figure out how to easily back up data to it.

I can easily write a cron job that copies /var/vmail, /etc, /home, and backs up the SQL database... But that still requires a really significant effort to rebuild the machine after a fail. Is there a way to get all the packages, binaries, libraries, etc., all backed up and restored without buying additional hardware?

I'd use something like [Remastersys](http://www.remastersys.com/) to make a backup snapshot of the installation to DVD or a USB pendrive.  Then use rsync to make daily updates of the files that change to the spare drive.  In the event you need to recover you can use the backup disc to recreate the basic system, then copy over the backup images on the spare drive.

Another option is to [use LVM and take snapshots]("http://www.howtoforge.com/linux_lvm_snapshots").

---

