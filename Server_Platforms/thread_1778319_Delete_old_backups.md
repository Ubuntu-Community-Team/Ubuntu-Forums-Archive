---
title: "Delete old backups"
date: 2011-06-08
forum: Server Platforms
---

### Post by pcarlos853 on 2011-06-08
Hi!,

I have set up my ubuntu 10.10 server to back up to a dir using tar. What can I add in my script that allows me to delete backup tar files over 30 days old?

Backup Script:

cd /var/BackupPlan
tar zcf "`date +"%Y-%m-%d-%H-%M"`.tar.gz" /var/www /var/www2 /var/log /etc/ssh /home/carlos
sudo -u carlos rsync -avz /var/BackupPlan 10.0.0.66:/home/carlos/ServerBackup

Thanks!

---

### Post by ruffEdgz on 2011-06-08
You could add the following:
```

sudo find . -name *.tar.gz -mtime +29 -exec rm -Rf {} \;

```
Before placing this in your code, you can run the command below to make sure it will grab the oldeest backups.
```

cd /var/BackupPlan
sudo find . -name *.tar.gz -mtime +29

```

Cheers!

---

### Post by pcarlos853 on 2011-06-08
Thanks for the quick reply!
When I ran it I got this output. Does it look ok? I dont have backups older then a day yet.
```
carlos@UbuntuSvr:/var/BackupPlan$ find . -name *.tar.gz -mtime +1
find: paths must precede expression: 2011-06-08-17-30.tar.gz
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

```Thanks!

---

### Post by ruffEdgz on 2011-06-08
Sorry, I forgot the quotes after -name:
```

cd /var/BackupPlan
sudo find . -name "*.tar.gz" -mtime +29

```
This also goes for the part about executing rm with each result:
```
sudo find . -name "*.tar.gz" -mtime +29 -exec rm -Rf {} \;
```

---

### Post by pcarlos853 on 2011-06-09
Thanks I added it to my script!

---

