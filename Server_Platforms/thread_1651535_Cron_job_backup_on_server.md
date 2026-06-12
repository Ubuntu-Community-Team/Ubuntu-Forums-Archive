---
title: "Cron job backup on server"
date: 2010-12-23
forum: Server Platforms
---

### Post by IllegalCharacter on 2010-12-23
I'm running a cron job every night to dump a MySQL database to an external hard drive. It works, however when I check on it the following morning the external is no longer mounted and the XFS log file is corrupted. If I run 
```
xfs_repair -L /dev/sdf1
```It works, but then I get these issues:```
XFS: Filesystem sdf1 has duplicate UUID - can't mount
```I can reset the UUID, but it's a pain to have to do this every day. Is there any way to fix this problem?

---

### Post by Vegan on 2010-12-23
Scrutinize my backup script, I backup MySQL daily with it.

```

#!/bin/sh
#navigate to the desired backup location
cd /public/backup/linux
#dump the MySQL entirely, output file is dated
mysqldump -u root -p********** --all-databases > "`date +%Y%m%d`.sql"
#backup the web folder
tar -cf `date +%Y%m%d`.tar /www
# the -9 option for gzip uses the maximum compression possible, slow
gzip -9 -q  *.sql
gzip -9 -q *.tar
#make easy to copy to an alternate location
chmod 777 *.*
#add error correcting codes, makes 5% recovery by default
#par2 c backup.par2 *.gz
#remove older backups so as not to consume infinite space
ROTATE=90
STALE=`date --date="$ROTATE days ago"`
rm -f "$STALE.sql.gz"
rm -f "$STALE.tar.gz"

```

---

### Post by IllegalCharacter on 2010-12-24
Hi Vegan, thanks for your response!

The issue I'm having isn't with the backup script (which works great when the drive is mounted), but with the external hard drive being used to store the backups. It seems to just disconnect after I copy over the file.

---

