---
title: "[SOLVED] Another Backup Thread"
date: 2007-05-30
forum: Server Platforms
---

### Post by victorbrca on 2007-05-30
Hi guys,

  I did a search for backup and found lots of info, but could not find one specific explanation to my question. This is what I need:

1- Incremental backup of /dev/hdc1 to /dev/hdb on a monthly basis
  . /dev/hdc1 is mounted on /media/jinzora (mainly music files), and /dev/hdb will be a 500Gb drive used to backup files from all over my LAN

2- How can I make a incremental backup of files on my LAN ? 
  . Explanation: This server should grab files from another server through a share (smb or CIFS) and automatically do an incremental backup


  For the first option I read that I could use "rsync", but I could not totally understand the man page. Do I use -a for backup or -b? The -u option skips files that are newer on the receiver... Should i understand that as an increment?

  I'm sorry for my noob questions, but the truth is that I am a noob...  :)


Thanks a lot,


Vic.

---

### Post by obimeister on 2007-05-30
rsync compares source and dest dirs and updates only modified or new files so it works in incremental "mode" all the time. -a option is the one to use when backing up stuff. If you mount your smb or cifs shares you can use rsync with them too. Or you can use rsync over lan if those are linux machines also.

---

### Post by craigp84 on 2007-05-30
Hi victorbrca,

Checkout rsnapshot which has some excellent documentation and should take no more than 45mins to an hour to master.

It's just a set of helper scripts around rsync to make it trivial to do what you want to do.

-c

---

