---
title: "Backup"
date: 2011-02-25
forum: Server Platforms
---

### Post by brand1068 on 2011-02-25
Ok i'm running this server from the command prompt.
 
can someone recomend a Disaster Recovery backup ?
 
Cheers,
 
Chris

---

### Post by rubylaser on 2011-02-25
That's vague, as there's hundreds of solutions / scripts for backup.  Some questions: How much data do you have, do you have extra hardware & hard drives, do you want to backup to the cloud, or locally, do you need versioned backups, etc?

---

### Post by seawolf167 on 2011-02-25
Aye, more information would be helpful

[LIST]
[*]what happened (drive failure, erased partition tables, etc.)
[*]what drives/formats/partitions need to be recovered
[*]what do you want to do with the data
[*]do you have existing backups you can/want to restore
[/LIST]

---

### Post by HermanAB on 2011-02-25
Howdy,

Rsync is your friend.

Pretty much all fancy backup programs use rsync down beneath.  The funny thing is that a good rsync backup script is usually a one liner.  If it is more than a one liner, then you are doing it wrong.

The rsync man page is very good and has many examples.  Read it.

---

