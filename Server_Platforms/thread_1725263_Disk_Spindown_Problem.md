---
title: "Disk Spindown Problem"
date: 2011-04-09
forum: Server Platforms
---

### Post by ThePol1 on 2011-04-09
I am running Ubuntu 10.10 (amd64). I have two SATA drives connected to the system that I use for weekly backups. I'd like to spin these two disks down when not in use. I have tried:

**1) Editing hdparm.conf like so:**

/dev/sdf {
spindown_time = 241
}

*Result*: The drives never spin down (checked them using hdparm -C /dev/sdf1)

**2) I have also tried adding a line to rc.local like so:**
sudo hdparm -S 241 /dev/sdf1

*Result*: The drives never spin down.

The drives are formatted as ext4. Here is how they are mounted in fstab:
UUID=(UUID) /media/(UUID) ext4 rw,suid,dev,exec,auto,user,async,relatime 0 2

I can't seem to find a way to spin these disks down. Any help would be appreciated.

---

### Post by ian dobson on 2011-04-09
Hi,

I imagine the problem is that the drives are mounted. All file systems write to the drivs every so often even if no application has written anything. So only mount the drives when your doing a backup.

I have 3 2tb wd drives in a RAID array that I use for backup, and I only mount the array when I'm doing a backup. I've kust checked and the drives are powered down at the moment. Also you should use the device name (/dev/sdf) not the partition number for hdparm.

Regards
Ian Dobson

---

### Post by ThePol1 on 2011-04-09
That's it! I modified my backup script to mount (when it starts) and then umount (when it completes) and both drives now spin down. Thanks!

---

### Post by ThePol1 on 2011-04-12
I spoke too soon. One of the drives spins down and stays in standby mode. The other drive spins down and then, after some time, spins back up... very strange since both drives are unmounted. Any thoughts?

---

### Post by ian dobson on 2011-04-12
Hi,

Could something be touching the drive/Smartdata or something like that. 

When the drive powers up do you see anything interesting in the syslog (/var/log/syslog) or dmesg?
How often does the drive power up? 
Are both drives setup exactly the same?
Maybe a different firmware on the drives?

Regards
Ian Dobson

---

### Post by rubylaser on 2011-04-12
I would bet it's the SMART daemon waking them up.  If it is, here's how I set mine up to prevent SMART from waking up idle disks.
```
nano /etc/default/smartmontools
```
And add this...
```
smartd_opts=”-q never -i 7200"
```
I have changed it to check every 2 hours, and to not spin the drive up if it is in standby.

Finally,
```
nano /etc/smartd.conf
```
and add this to the edit of your DEVICESCAN line
```
-n standby,q
```

---

### Post by ThePol1 on 2011-04-12
I added "-n standby,q" to smartd.conf and both drives have gone to Standby mode and haven't spun up again. I'll monitor them over the next 24 hours or so... but I think this has solved the problem!

---

### Post by rubylaser on 2011-04-12
Great, glad to hear that worked :)

---

