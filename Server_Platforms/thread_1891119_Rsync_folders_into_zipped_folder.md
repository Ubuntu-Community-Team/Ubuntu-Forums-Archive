---
title: "Rsync folders into zipped folder"
date: 2011-12-04
forum: Server Platforms
---

### Post by Fallacy on 2011-12-04
I'm trying to make a cron job that uses rsync to backup everything from /var/www except the backups folder, which is in /var/www. I've been trying to make it work with something like this:

```
30 2 * * * cd /var/www && rsync -avm *[!backups] | gzip > backups/webcontent/` `date +%m-%d-%Y'`.zip 
```

But so far, I've only gotten corrupted archives, unusable files, etc.

I've somewhat of a noob and I'm probably missing something obvious, so please don't laugh at me :KS

---

### Post by papibe on 2011-12-05
Hi Fallacy.

I would recommend calling a bash script file, instead of writing actual bash code on the crontab.

For example:
```
30 2 * * * /path/to/script.sh
```
And then sctipt.sh would be:
```
#!/bin/bash
cd /var/www && rsync -avm *[!backups] | gzip > backups/webcontent/` `date +%m-%d-%Y'`.zip
```
I'd start by testing the script manually, and then in the crontab.

Now, the code...

rsync takes a source and a destination, but it doesn't write to standard output so it can be piped the way you want. I think the command you are looking is 'tar'.

This is an idea using tar:
```
#!/bin/bash
TARNAME=$(date +%m-%d-%Y)
tar cvzf  /path/to/backups/webcontent/"$TARNAME".tar.gz   /var/www/
```
Hope it helps, and tell us how it goes.
Regards.

---

### Post by Fallacy on 2011-12-05
> **papibe said:**
> Hi Fallacy.

I would recommend calling a bash script file, instead of writing actual bash code on the crontab.

For example:
```
30 2 * * * /path/to/script.sh
```And then sctipt.sh would be:
```
#!/bin/bash
cd /var/www && rsync -avm *[!backups] | gzip > backups/webcontent/` `date +%m-%d-%Y'`.zip
```I'd start by testing the script manually, and then in the crontab.

Now, the code...

rsync takes a source and a destination, but it doesn't write to standard output so it can be piped the way you want. I think the command you are looking is 'tar'.

This is an idea using tar:
```
#!/bin/bash
TARNAME=$(date +%m-%d-%Y)
tar cvzf  /path/to/backups/webcontent/"$TARNAME".tar.gz   /var/www/
```Hope it helps, and tell us how it goes.
Regards.
Okay, I updated cron. I tested what I could manually and it seems to work.

crontab:
```
0 2 * * * /home/scripts/mysqlbackupcron.sh
10 2 * * * /home/scripts/webcontentbackupcron.sh
15 2 28 * * root find /home/backups -atime +30 -execdir 'rm -f' \;
```mysqlbackupcron.sh:
```
#!/bin/bash
mysqldump -u root -p(password) --all-databases | gzip > /home/backups/database/`date '+%m-%m-%Y'`.sql.gz
```webcontentbackupcron.sh:
```
#!/bin/bash
TARNAME=$(date +%m-%d-%Y)
tar cvzf /home/backups/webcontent/"$TARNAME".tar.gz /var/www
```

---

