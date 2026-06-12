---
title: "partclone/s bloated logs?"
date: 2012-07-15
forum: Server Platforms
---

### Post by DocHoliday52090 on 2012-07-15
Hey there, 

I use a scheduled cron command through webmin to basically clone the server's system partition to an .img file on another hard drive. 

sudo partclone.dd -c -d -s /dev/sda -O /media/"Ubuntu Server Backup"/UbuntuServerBackup.img   

/media is the second drive

sda is the DRIVE that the system partition lives on, which includes the system partition

The idea was if the system drive were to fail, I could pop in another drive and image the .img file onto the new drive and keep chugging. I didn't know if I could image a partition and flash that onto a new drive, so I simply decided to image the whole drive.

However, the log file for partclone is massive and routinely uses up all available space. I originally planned to run the .img file on a 2 gig flash drive I had lying around so I limited total space for the system partition to about 1.7 gb, which was workable because the system partition with everything install was about 1.45 gb or so. 

After cloning itself, the log file, in var/log, swells to 250 gb or so, filling up root. I delete it manually.

How can I avoid this? I looked into the log file itself, which after choking Word for about 10 min showed pages and pages of blockid, block size information. 

Is this a result of self-imaging? How can I 'mute' partclone?

---

### Post by DocHoliday52090 on 2012-07-15
I did some more research and realized I was using partclone's inefficient dd copy method for unspported filesystems. 

I switched FROM partclone.dd TO partclone.ext4

Because it will stop copying block by block I am hoping it will fill up logs slower.

Thoughts?

---

