---
title: "Backup with rsync the entire server"
date: 2011-12-20
forum: Server Platforms
---

### Post by Azathoth_ on 2011-12-20
Hi,

I am trying to backup an entire server using rsync via ssh (remotely)
I managed to backup using the root user (root@IP) but when I check the backed up user folders (/home/user) and other folders like /proc, they are empties.
Is there any way to backup all the server including these and all the folders?

Thanks.
Best regards

---

### Post by Lars Noodén on 2011-12-20
You don't want or need to transfer the contents of [font=Courier New]/dev[/font] or [font=Courier New]/proc[/font]

[http://manpages.ubuntu.com/manpages/oneiric/en/man7/hier.7.html](http://manpages.ubuntu.com/manpages/oneiric/en/man7/hier.7.html)

---

### Post by SeijiSensei on 2011-12-20
Presumably the /home/user directories contain actual files on the source machine?  

I run rsync on the target machine and suck down the remote filesystem,  I put each backup into a separate directory with the name of the remote host.  

```

cd /path/to/backups/remotehost
sudo rsync -av root@remotehost:/ . --exclude-from=/path/to/backups/excludes --delete-excluded >> /var/log/backup

```

The file /path/to/backups/excludes contains this list of file "globs" 

```

proc/
dev/
sys/

```

that are excluded from the transfer.  As Lars observed, you don't want or need to back up directories like /proc.

---

### Post by aeiah on 2011-12-21
i suggest using similar flags as SeijiSensei uses (archive, verbose). perhaps also use the 'show progress' flag (P) and perhaps initially do a dry run (n) initially to see what's going on.

```

rsync -avPn source destination

```

and use an exclude list too 8-)

when you have the command right, remove the n so it actually does the transfer and not just a simulation, and then also remove the P and v flags when everything is correct, since these just report progress

---

### Post by Azathoth_ on 2011-12-21
I have a incremental backup script and, summing up, it would be:

```
rsync -e "ssh" --force --ignore-errors --delete --delete-excluded \
 --exclude-from=$EXCLUDES --backup --backup-dir=$HOME/server-backup/`date +%Y-%m-%d` -avz root@"IP":/ $HOME/server-backup/main --log-file=$HOME/server-backup/log
```

Just when I am writing this, I can see that the problem is that I am using -a rsync flag so it is backung up with owner and permissions so I have to write the script using root permissions, so I have to make a sudo...

So, solved... :D

---

