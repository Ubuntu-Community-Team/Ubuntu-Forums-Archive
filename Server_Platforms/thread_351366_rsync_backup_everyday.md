---
title: "rsync backup everyday"
date: 2007-02-01
forum: Server Platforms
---

### Post by detectiveinspekta on 2007-02-01
I'm making a backup script that backsup to files on the same computer

```
#!/bin/bash
#This script will backup $dpath everyday to the location
#defined in /etc/rsyncd.conf
#Rsync backup tool will check for changes based on the previous
#week. 

##
#specify backup path 
dpath="/home/jonathan/public"

#specify username
user="jonathan"

#specify server address
server="localhost"

#specify rsync parameters
parm="rtlv"

case `date +%a` in
Mon ) rsync -$parm $dpath rsync://$user@$server/monday;;
Tue ) rsync -$parm $dpath rsync://$user@$server/tuesday;;
Wed ) rsync -$parm $dpath rsync://$user@$server/wednesday;;
Thu ) rsync -$parm $dpath rsync://$user@$server/thursday;;
Fri ) rsync -$parm $dpath rsync://$user@$server/friday;;
Sat ) rsync -$parm $dpath rsync://$user@$server/weekend;;
Sun ) rsync -$parm $dpath rsync://$user@$server/weekend;;
esac

```

I have set 6 modules in rsyncd.conf so files for Mon Tue etc are seperated. So at the moment rsync will check for changes based on the previous week. Eg. rsync will compare last Friday to today (Friday) and make the changes. However it will be more efficient if it compared from the previous day.

Is it logical and efficient to do this:
rm currentdate
cp previousdate currentdate
preform the rsync.

File size could be a few GB not sure wheather forgetting rsync altogether and opting for cp's, but eventually it will be more remote insead of local.

---

### Post by detectiveinspekta on 2007-02-01
How do I add in support so it backsup from previous day?
So far but very messy
```

backuppath = /home/backup/
rm -R $backuppath/monday && mv $backupath/weekend $backuppath/monday && 
cp $backuppath/monday $backuppath/weekend

```

---

### Post by detectiveinspekta on 2007-02-02
Obviously no one uses rsync because I didn't even have to run a rsync server.

---

### Post by deuce868 on 2007-02-02
Check out rsnapshot. It's basically a super rsync for backup purposes. It works on creating multiple days worth of backup data, optimize space, etc.

---

