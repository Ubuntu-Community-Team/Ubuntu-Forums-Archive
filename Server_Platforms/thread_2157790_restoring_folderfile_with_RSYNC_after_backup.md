---
title: "restoring folder/file with RSYNC after backup"
date: 2013-06-26
forum: Server Platforms
---

### Post by giobaxx on 2013-06-26
i'm tryng to learn how to backup and restore file folder using rsync demon

i have configured rsyncd.conf on a server 

```
log file = /var/log/rsyncd.log
pid file = /var/run/rsyncd.pid
use chroot = yes
[backup]
 path = /mnt/backup
 comment = serverbic backup
 uid = root
 gid = root
 read only = no
 list = no
# auth users = root
# secrets file = /etc/rsyncd.scrt
 strict modes = yes
# hosts allow = 
 transfer logging = no


```



I want to backup the folder Documents on the server and i use this script to do that:

```
start > rsync-root.log
date >> rsync-root.log
rsync --verbose --archive --numeric-ids --delete --stats /home/Joe/Documents root@192.168.1.4::backup
echo stop >> rsync-root.log
date >> rsync-root.log
```

It works and i save the folder Document on remote server under /mnt/backup.

My problem is how to restore the folder document from the remote server to the client which is the exact command? 
 
the command is that one?....i need only to exhange source and destination?....i have to run this command from the server or i can run also from the client?

```
start > rsync-root.log
date >> rsync-root.log
rsync --verbose --archive --numeric-ids --delete --stats root@192.168.1.4::backup /home/Joe/
echo stop >> rsync-root.log
date >> rsync-root.log
```


i have some big "kaos" in my mind.....you can help me?

---

### Post by CharlesA on 2013-06-26
I don't use rsync as a daemon, but the basically all you should need to do is switch the source and destination locations. Try running it with --dry-run first to make sure it does what you expect it does.

---

