---
title: "server partitions with solid state hard drive"
date: 2008-11-24
forum: Server Platforms
---

### Post by txtiger on 2008-11-24
I am configuring a new server for use as a secondary firewall, ssh, asterisk, etc. and would appreciate some suggestions.

This little box is to provide me access to my LAN at home while I am abroad, so reliability is paramount.  I notice that the cost of true Solid State hard drives (not just ordinary flash) has droppped to a reasonable price for a 32 Gb drive.  I will then use a pair of regular server drives in a RAID 1 configuration for the remainder of the system.

What I am needing is guidance on how to partition.  The major objectives would be to A) fit all Ubuntu Server files that are needed for basic operation onto the 32 GB, B) make sure that any partitions that do lots of writes is on the regular drives, and C) have the "mission critical" apps like openVPN, ssh, x, watchdog, anacron, nis, portmap, etc. fit on the SSD as well -- if possible.

Is this too much to ask for a 32 GB space?

What partitions should go where and how big would you recommend?

---

### Post by CrucifiedEgo on 2008-11-24
that should be fine for 32GB.  I'm planning on doing the same thing with a 8GB CF card in a mini itx machine (with a 500GB WD Green drive).  

I'd recommend first, setting noatime in your kernel parameters.  This will greatly reduce the number of writes to the flash.  Also, i would put at least /var/log on your standard disk as that gets a lot of writes as well.  Depending on what you're doing in your home directory, you may consider that as a candidate as well.

---

### Post by HermanAB on 2008-11-24
If it is a server with no GUI or only a simple X install for a local terminal, then the / partition can be very small - as little as 1GB.  However, I would make / = 3 to 5GB, /swap = RAM size, /var = 1 to 2 GB and /home the rest.

The reason for making /var a separate partition is to limit damage in case of a DOS attack or an error filling up the logs.  Make sure that your applications and databases store all their data in /home.  That way you only need to back up /home.

To avoid filling up /, only install the applications you really need, which is always a good idea on a server.  If you really need a GUI, install something smaller like IceWM or XFCE.

Hope that helps!

Herman

---

### Post by CrucifiedEgo on 2008-11-24
Thanks for reminding me to bring this up: don't put your swap partition on the flash drive. That's asking for trouble.

---

### Post by txtiger on 2008-11-25
Thanks, that is pretty much the direction I was heading.  But, the recent disto upgrade for Ibex "burned" me because it needed 3 GB of free space on /boot to run and I had typically been sizing /boot in the 1 GB range.

Then, after reading your posts I had a forehead slap moment and did a disk use check on my main AMD64 machine with Ubuntu 8.10 and a big 32bit workstation with Ubuntu 8.04  It is what I would call fully optioned with lots of applications.  

The biggest partition (excluding /home) was /usr which was less than 7 GB on all the machines I checked.  Next was /lib which was 1.2 GB on one (and under 0.2 GB on the other). Also, on a Mandriva distro I ran out of space in /var at 2 GB which makes me cautious about that partition as well. 

Everything would fit comfortably in 16 GB on any of my machines.  

Based on that and your comments here is the scheme I am currently planning:

/ (root) partition = 16 GB (or 32 GB) on SS drive
/swap    partition = RAM size (2 GB) on Hard drive (/sda1)
/var     partition = 10 GB on Hard drive (/sda2)
/tmp     partition = 10 GB on Hard drive (/sda3)
/home    partition = Everything else on Hard drive (/sda4)

I will use the $/GB price to determine whether I get a 16 GB or bigger.  Also, I am considering only flash rated as SS Drive not just ordinary flash.

---

### Post by txtiger on 2009-03-17
Just adding a follow-up.  I have done the partitioning as described in this thread and have not had any downtime since doing so (now 4 months 24/7).  Since this I have also created a software RAID 1 using mdadm and then put the /var, /tmp, and /swap on the RAID set.  I then used the remaining portion of the set to create an LVM block for /home.  That allows me to grow the /home by adding another RAID set later.

Two suggestions I have heard, but not tried (and they sound sensible):
    1.  Set the /etc/fstab parameters for the SSD to include noatime.  That will reduce the writes for system file accesses.
    2.  Create your /home on the SSD and then create and mount a /home2 on the regular drive.  Then ensure that all of your files and work are in the /home2.  That will cause the hidden configurations to be written to the SSD which will improve speed of startups.  I personally would not do this on a server, but it might be okay for a workstation.

---

