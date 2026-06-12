---
title: "Rsync backup to Synology"
date: 2018-12-31
forum: Server Platforms
---

### Post by OiPenguin on 2018-12-31
I'm trying to backup from my Ubuntu server to an (external) Synology, however I'm unable to exclude files and folders using an exclude-list. I'm using this rsync-command:

```
USER@IP:~# sudo rsync -av --progress --exclude-from 'rsync-excludelist-synology.txt' --log-file=/root/rsync-synology.log -e ssh /media/b0849d4b-e820-45d8-9736-d140bbd2e225/ USER@IP:/volume1/backup-2019-nyere
```

and I've tried several variations of this command, such as
... --exclude-from '/rsync-excludelist-synology.txt'
... --exclude-from '/root/rsync-excludelist-synology.txt'
... --exclude-from='/root/rsync-excludelist-synology.txt'

My 'rsync-excludelist-synology.txt' is stored in the same folder as where I run the command from and looks like this
#rsync-excludelist.txt
/media/b0849d4b-e820-45d8-9736-d140bbd2e225/backup/
/media/b0849d4b-e820-45d8-9736-d140bbd2e225/lost+found/
/media/b0849d4b-e820-45d8-9736-d140bbd2e225/plexmediaserver/
/media/b0849d4b-e820-45d8-9736-d140bbd2e225/m/.Trash-1000/
/media/b0849d4b-e820-45d8-9736-d140bbd2e225/m/.recycle/

I've also tried different variations such as
/media/b0849d4b-e820-45d8-9736-d140bbd2e225/backup
/media/b0849d4b-e820-45d8-9736-d140bbd2e225/backup/*

What am I doing wrong!?

---

### Post by howefield on 2018-12-31
Thread moved to the "*Server Platforms*" forum for a better fit.

---

