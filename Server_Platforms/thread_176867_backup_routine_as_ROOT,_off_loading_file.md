---
title: "backup routine as ROOT, off loading file"
date: 2006-05-15
forum: Server Platforms
---

### Post by wgregori on 2006-05-15
I created a CRON job to TAR all my important backup directories.  I then programmed an FTP client on another computer to download the tar file on a nightly basis.  However, since I can not FTP into the Ubuntu server as ROOT I created another login that has the /backup directory as its home.  I can download the file but I can't erase it since my new login is not the owner of the file.  

I've thought of creating another cron job to to CHMOD the files but I thought that I would inquire here about a different strategy.


Thanks,
Wayne Gregori

---

### Post by MJN on 2006-05-15
Ever thought about using rsync instead? This will backup only the differences in your files - presumably the whole lot doesn't change every night? Even if it does, it'll manage the whole lot with ease and negate the need for a temporary backup locally.

Of course you might actually want daily snapshots in their entirety - this again is not a problem as you would just make rsync drop the backup in a different location each time.

Is the FTP computer/client remote from you? What's the bandwidth between them? Rsync will also compress the traffic to help matters... and wraps it securely in SSH.

Finally, did I mention rsync might be worth a look? ;)

Mathew

---

### Post by sjpwong on 2006-05-16
I would highly recommend looking at rdiff-backup.

It uses a library version of rsync so that only the changed portions of files are transferred, as mentioned by MJN, but also keeps all sorts of incremental data so you can roll-back to a given date.

It is also really easy to use.

---

### Post by wgregori on 2006-05-17
Thank you for the info.

Question: So far I have one linux system running and a couple Windows based systems.  Can I run Rsync on a windows based system so that I can use the disc resources on those systems?

Thanks,
Wayne

---

### Post by MJN on 2006-05-17
Sure - check out [http://itefix.no/cwrsync/]("http://itefix.no/cwrsync/") (There are many other guides and packages available but this one seems to get referenced a lot)

Mathew

---

