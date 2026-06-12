---
title: "Rsync Backup"
date: 2005-05-06
forum: Server Platforms
---

### Post by bazh on 2005-05-06
Ok,

Following on from my spare hard drive for backup, I need to accomplish the following

Mount a windows share, backup(compress it), report how it went(mail)

So far ive got a this.

A command
```
smbmount //server/windows_share /mnt/windows_share -o username=guest%,fmask=644,dmask=755,uid=1000,gid=1 00, debug=0,workgroup=mshome
``` 

That mounts my smbshare, and this script backs it up

```
 #!/bin/sh

    export PATH=/usr/local/bin:/usr/bin:/bin

    DAY=`date "+%A"`

    rsync -av --compress /mnt/windows_share /backup/windows share/$DAY

``` 

The raw amount on that windows_share is 4-5gb, ideally this could be compressed to half it, its got around 20,000 word documents :) and other flat files

Am i going in the right direction or what, also in my script where i use $DAY id like to have that in date format day-month-year

Thanks, oh and dont be afraid to tell me im doing it arseways and suggest a better method

---

### Post by enquiry on 2005-05-06
You might find backuppc a usefull tool for such tasks: [http://backuppc.sourceforge.net/](http://backuppc.sourceforge.net/)

---

### Post by bazh on 2005-05-09
Ok, been messing with backuppc, where does it default backup to. Cant find anything in the config.pl or hosts file

---

### Post by bazh on 2005-05-09
It backs upto /var/lib/backuppc/pc/ 

so ive monuted the large hard drive at this point :)

---

