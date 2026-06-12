---
title: "Hot Swapping Removable SATA drives WITHOUT manual intervention"
date: 2009-03-01
forum: Server Platforms
---

### Post by vaf on 2009-03-01
Hi all

This must be possible! I have been reading up as much as I can handle (3 days now!) and I can't find any solution for this.

I have built headless Ubunto 8.10 Server Edition box that uses crone to run Rsync and backup the /Server directory to a removable drive mounted at /Backup. 

This drive is to be removed every night and taken off site, for data integrity, and as this server has no monitor or keyboard I want to be able to remove the drive and the system automatically unmounts the /Backup directory (so that the Rsync process fails) and then remounts the drive and directory when the drive is re-inserted the next day, allowing Rsync to catchup!

The system picks up the removal and insertion of the drive, so surely there is an application that accommodates this setup. Non-Gui is prefered, as no GUI is installed!

Thanks

---

### Post by netztier on 2009-03-02
> **vaf said:**
> crone to run Rsync and backup the /Server directory to a removable drive mounted at /Backup. 


Well, does the application or shell script that handles your rsync-job have some form of pre- and post-job routines that it can invoke? 

With some more shells cripting, you should be able to:

[LIST]
[*] check for the drive's presence 
[*] mount it if not already done so
[*] do some sanity checking such as verifying free space, bad sector count as reported by hdparm 
[*] start the rsync job
[*] report it's success or failure to some log or e-mail 
[*] then unmount the drive, so that the operator can take it away.
[/LIST]

What I didn't quite get: is rsync running continously or is it started on a particular time of day to run once then stop?


I wouldn't know about common backup apps (Amanda, anyone?) doing all of this, but I assume that these problems've been addressed before.

regards

Marc

---

### Post by HDave on 2009-06-17
I have the exact same issue.  netztier's post is 100% right on, and while I know shell scripting I don't know the commands to:

# check for the drive's presence
# mount it if not already done so

Any help is much appreciated...

---

### Post by Jonie on 2009-06-17
It depends whether your drive is in Legacy IDE mode, or AHCI. In first case you could use hdparm to stop the disk. If the disk is in the AHCI mode you might try the s3g-utils. Read on:

[http://blog.mymediasystem.net/uncategorized/simple-way-to-spindown-a-sata-hard-disk-drive-after-being-idle-linux/](http://blog.mymediasystem.net/uncategorized/simple-way-to-spindown-a-sata-hard-disk-drive-after-being-idle-linux/)

Note that sdparm (for real SCSI disks) will not work with SATA AHCI.

Hope this helps.

---

### Post by redmk2 on 2009-06-17
> **HDave said:**
> I have the exact same issue.  netztier's post is 100% right on, and while I know shell scripting I don't know the commands to:

# check for the drive's presence
# mount it if not already done so

Any help is much appreciated...

I have a similar situation.  I have an eSATA drive that I leave off most of the time. It is the backup device.  I wrote a script to mount the drive before I run my backup routine.

The host is running when I power up the drive.  I have seen the comments in dmesg. Nothing serious seems to happen.

After I power up the  connected drive I invoke a script that looks  for the presence of a file that I keep in the directory that is the mount point (in my case it is at /smb/backup).  If the script can find the file then the drive MUST NOT be mounted, so we: mount UUID/blah, blah.  I echo to the screen if we have success.

I umount the drive and turn off the power and all seems to be well.  No reason that the mount and/or the umount can be done via ssh if it is remote to you.  If you want my script let me know.

I have though about spinning down the drive but have not been happy with any of the documentation.  As I am within arms length of the host, I just power down the device.

---

### Post by HDave on 2009-06-18
> **redmk2 said:**
> I umount the drive and turn off the power and all seems to be well.

How do you turn off power to the device?

I have been having success using the blkid command to find out which hard drive has been inserted into the cage tray.

---

### Post by redmk2 on 2009-06-18
> **HDave said:**
> How do you turn off power to the device?

I have been having success using the blkid command to find out which hard drive has been inserted into the cage tray.

HDave,

I have the drive in an external case that has a on/off switch.  The power is supplied from a switched outlet.  I use the switch on the outlet as it is cheaper to replace if it fails.  I think you should be able to just remove the drive though.  If you wanted to spin down the drive with hdparm you could.  

My brother uses a caddy to hold his backup drives; he just removes them without turning the power off.  I believe the drive heads auto-park.

Look at the messages in the messages log when you remove the drive.  You will see that the system is not really bothered by removal or insertion.  

I used blkid to identify my drive and use that in my mount script.

Hope this helps.

-Red

---

### Post by HDave on 2009-06-18
Thanks a lot -- for some reason I though you had a software switch to control the power!

I have also since found out that a package called ivman can help a lot with this stuff, but it requires hal, and I didn't want all that stuff on my server.  But for a desktop, it would be great.

---

### Post by redmk2 on 2009-06-18
> **HDave said:**
> Thanks a lot -- for some reason I though you had a software switch to control the power!

I have also since found out that a package called ivman can help a lot with this stuff, but it requires hal, and I didn't want all that stuff on my server.  But for a desktop, it would be great.

It looks like ivman controls the auto-mount of removable media in a GUI environment.  As you say not for server situations.  

The OP stated that the drive was removed every night.  That means a human is present to power down and power up the drive.  The power up and down could be scripted, by why do that if someone is there on site with there hands on the device.  As my backup host is right beside me, I do it manually.  :D

The most difficult part in scripting this is ID'ing the drive if you have more than one.  In that type of situation you would have multiple UUID's to deal with.

---

