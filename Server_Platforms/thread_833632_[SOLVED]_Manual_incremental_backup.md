---
title: "[SOLVED] Manual incremental backup"
date: 2008-06-18
forum: Server Platforms
---

### Post by Richard_ on 2008-06-18
Hi all,

I've had a look at some backup systems, including Amanda and Bacula, but what frustrates me to no end is the (apparent) inability to initialise a manual backup with any of these systems. Having to backup to virtual tapes is also very frustrating to say the least as I'm running a RAID array with no need for tape backups.

My scenario is as follows; I have a Windows laptop which connects to the network at completely **random times**, and as such it is futile setting up a cronjob on the backup server, since there is no way of telling when the laptop will connect to the network again, nor the duration of it's connection.

I need some method whereby I can implement an incremental backup on this laptop, but the user must be able to manually initialise these backups.

A gentle nudge in the right direction would be much appreciated. :)


*[edit] I guess the only reason I stuck this under the Ubuntu Server section is because the backup server is running this distro.*

---

### Post by firecat53 on 2008-06-19
Well, without actually having done it ...... I see at least 2 options.

1. Assign your laptop a static IP on the network. Write a small script that peridically looks to see if that IP is pingable, then initiate the backup when it sees that IP avaialble.

2. Install Cygwin on the laptop, and write a small shell script that initiates the backup. You could just use rsync, or rdiff-backup (for actual incremental backups). Put a desktop link to start the script.

Probably several other ways to skin that cat!

Good luck!
Scott

---

### Post by hyper_ch on 2008-06-19
I would do:

(1) install cygwin with ssh and rsync

(2) write a small script that will backup your notebook to the server using rsync and then "duplicate" with hardlinks to create an incremental snapshot-style backup

---

### Post by Richard_ on 2008-06-19
Thanks guys :) I didn't know about cygwin. I've just checked it out, and this will make life a lot easier. Thanks!

---

### Post by hyper_ch on 2008-06-19
if you want to use rsync, ssh and hardlinks, have a look here:

[http://www.howtoforge.com/rsync_incremental_snapshot_backups](http://www.howtoforge.com/rsync_incremental_snapshot_backups)

---

