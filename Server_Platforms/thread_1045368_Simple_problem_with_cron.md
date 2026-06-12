---
title: "Simple problem with cron"
date: 2009-01-20
forum: Server Platforms
---

### Post by jjggag on 2009-01-20
I have a little Script:

tar cvf /media/160/COPIASEGURIDAD/www.`date --iso-8601`.tar /var/www
find /media/160/COPIASEGURIDAD/www.* -type f -mtime +7 | xargs rm -f

So I use tar to compress www directory and copy it to another place.
I use cron to repeat this action:

00 20 * * * /home/tiry/backup_www.sh

If I run backup_www.sh in console it works perfectly and it creates a tar file (34mb) but when cron runs this action weirdly it creates the tar file but only 11mb! it doesnt take all the files. I have tried many ways but I haven't get to solve it.

Sorry for my bad english and thank you

---

### Post by HermanAB on 2009-01-20
Cron has a very limited environment in order to prevent exploits.  Try running the script using the 'at' daemon and the 'at' or 'batch' command instead.

See 'man at' or 'man batch' for details.

Cheers,

Herman

---

