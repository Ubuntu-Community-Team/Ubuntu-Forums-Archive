---
title: "backuppc rsync failure"
date: 2006-02-11
forum: Server Platforms
---

### Post by dave84 on 2006-02-11
hi everybody!

i'm using backuppc to backup my notebook from the server 
and it's really a great program. i use rsync and ssh but the point is:

when i start the backup from the cgi-interface it fails:
the log file says s.th about ***fileListReceive failed***

i was able to start the backup by typing in a shell as backuppc-user:

```
/usr/share/backuppc/bin/BackupPC_dump -v -f "my-notebook-name"
```

now everythings set off and after some while the backup is finished.
(although this comand executes the command below; 
i see the filenames when they are transmitted and after it's finnished i can watch all the files with the cgi-interface)

if i enter the command which is executet by the cgi-script last

```
/usr/bin/ssh -A -q -x -l backuppc 192.168.2.101 nice -n 19 /usr/bin/rsync --server --sender --numeric-ids --perms --owner --group --devices --copy-links --times --block-size=2048 --recursive --ignore-times . /home/david/importantdirs/
```

in a shell, then i get an error message where it says:

```
protocol version mismatch -- is your shell clean?
(see the rsync man page for an explanation)
rsync error: protocol incompatibility (code 2) at compat.c(64)
```

has anybody the same problem or knows how to solve it???

lg david

---

