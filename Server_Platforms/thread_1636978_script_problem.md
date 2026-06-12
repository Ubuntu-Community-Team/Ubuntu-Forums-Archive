---
title: "script problem"
date: 2010-12-03
forum: Server Platforms
---

### Post by Vegan on 2010-12-03
Seem my rotation part is not removing files older than 90 days. Anybody know what is wrong?

```
#!/bin/sh
#navigate to the desired backup location
cd /public/backup/linux
#dump the MySQL entirely, output file is dated
mysqldump -u root -pmt1jxz68f2 --all-databases > "`date +%Y%m%d`.sql"
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

### Post by Vegan on 2010-12-03
I see the problem, not enough time for today-90 to register

124 items means only 62 days worth are stored

---

