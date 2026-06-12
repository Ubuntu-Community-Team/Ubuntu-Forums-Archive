---
title: "Crontab Problem"
date: 2010-06-27
forum: Server Platforms
---

### Post by cian1500ww on 2010-06-27
Hopefully someone can help me as I think there's a simple solution to this problem but I can't seem to find it. I'm trying to run the below script daily using crontab:

```


#!/bin/bash
### MySQL Server Login Info ###
MUSER="BLANK"
MPASS="BLANK""
MHOST="BLANK""
MYSQL="$(which mysql)"
MYSQLDUMP="$(which mysqldump)"
BAK="/backup/mysql"
GZIP="$(which gzip)"
### FTP SERVER Login info ###
FTPU="BLANK""
FTPP="BLANK""
FTPS="BLANK""
NOW=$(date +"%d-%m-%Y")

[ ! -d $BAK ] && mkdir -p $BAK || /bin/rm -f $BAK/*

DBS="$($MYSQL -u $MUSER -h $MHOST -p$MPASS -Bse 'show databases')"
for db in $DBS
do
 FILE=$BAK/$db.$NOW-$(date +"%T").gz
 $MYSQLDUMP -u $MUSER -h $MHOST -p$MPASS $db | $GZIP -9 > $FILE
done

lftp -u $FTPU,$FTPP -e "mkdir /mysql/$NOW;cd /mysql/$NOW; mput /backup/mysql/*; quit" $FTPS

```

The crontab is setup as follows:
```


22 22 * * *  /etc/backupmysql.sh


```

The script runs perfectly when I run it as a command but not under crontab. I think it may have to something do with the environment its running in but I'm not all that sure how I'd go about changing that.

Thanks !!

---

### Post by tr333 on 2010-06-27
Crontab normally runs in a limited shell environment, so it won't have any extra directories in PATH that you might have added manually in .profile or .bashrc.  You can modify the PATH from inside the crontab file.

eg. PATH=/bin:/sbin:/usr/bin:/usr/sbin

If that doesn't fix it then I'm out of ideas.

---

### Post by pravindra.kumar on 2010-06-28
Dear cian1500ww,

You can try by doing the following:-

22 22 * * *  sh /etc/backupmysql.sh

I hope it will work.

Thanks & Regards
Pravindra

---

