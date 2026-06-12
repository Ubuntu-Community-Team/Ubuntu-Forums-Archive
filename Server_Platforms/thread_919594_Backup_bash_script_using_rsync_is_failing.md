---
title: "Backup bash script using rsync is failing"
date: 2008-09-14
forum: Server Platforms
---

### Post by Rounan on 2008-09-14
Hello, bash scripting wizards...

I am trying to write my first bash script, which is a dead-simple backup script: read the directories specified in a text file and rsync them to one backup directory. No compression or dated snapshots are required.

Here is the script (bash -x for verbosity):
```
#!/bin/bash -x

ORIGINAL_IFS=$IFS
IFS=$'\n'                       #separate on new lines, not spaces

for i in $(cat /home/user/backuplist); do
        echo "Backing up $i..."
        rsync -ar $i /backup/   #backup each directory specified
done

IFS=$ORIGINAL_IFS               #return IFS to original value
```

Here is the list:
```
/storage/Home\ Backup
/storage/ybtio\ data\ 2008
/storage/Projects
/storage/user's\ Puter
```


And here is how it fails:
```
+ ORIGINAL_IFS='
'
+ IFS='
'
++ cat /home/user/backuplist
+ for i in '$(cat /home/user/backuplist)'
+ echo 'Backing up /storage/Home\ Backup...'
Backing up /storage/Home\ Backup...
+ rsync -ar '/storage/Home\ Backup' /backup/
rsync: link_stat "/storage/Home\ Backup" failed: No such file or directory (2)
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]
+ for i in '$(cat /home/user/backuplist)'
+ echo 'Backing up /storage/ybtio\ data\ 2008...'
Backing up /storage/ybtio\ data\ 2008...
+ rsync -ar '/storage/ybtio\ data\ 2008' /backup/
rsync: link_stat "/storage/ybtio\ data\ 2008" failed: No such file or directory (2)
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]
+ for i in '$(cat /home/user/backuplist)'
+ echo 'Backing up /storage/Projects...'
Backing up /storage/Projects...
+ rsync -ar /storage/Projects /backup/
+ for i in '$(cat /home/user/backuplist)'
+ echo 'Backing up /storage/user'\''s\ Puter...'
Backing up /storage/user's\ Puter...
+ rsync -ar '/storage/user'\''s\ Puter' /backup/
rsync: link_stat "/storage/user's\ Puter" failed: No such file or directory (2)
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]
+ IFS='
'
```

The problem is clear: when bash substitutes for $i in the rsync command, it is adding single quotes. It doesn't do so, however, when it substitutes for $i in the echo command. And I have seen many, many sample scripts where they do things like
```
$cp -ar $DIRTOBACKUP $BACKUPDEST
```
with no special provisions.

I do not know how to change this behaviour. Colour me confused.

--Rounan

---

