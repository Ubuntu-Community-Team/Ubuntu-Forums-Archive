---
title: "rdiff-backup command not executed by cron"
date: 2008-08-25
forum: Server Platforms
---

### Post by be4truth on 2008-08-25
I have a problem with a backup script on a Hardy 32 thin-client-server with rdiff-backup 1.1.5 as well as 1.1.15.

A simple script like this
```
#!/bin/bash
rdiff-backup /home/user/directory /media/storage/backup

```

script is on chmod 775 or even 777
in crontab my entry is 
```
01 12 * * * /home/backupscript
```

now: if I execute the script manually either as a user or as root it works perfectly. cron executes the script but doesn't execute the rdiff-backup command

if i run the same set-up on a single desktop or server things work.
on the thin-client-server it fails.

does anybody have an idea what could cause this problem? Any help is appreciated

---

### Post by Aurels on 2008-08-25
Hi, I exactly have the same problem at the moment.
None of my cron jobs are executed.

Here is my crontab for root:

```
aurels@malisart:~$ sudo crontab -l
# m h  dom mon dow   command
57 13 * * * root echo "42" > /home/aurels/test.txt
0 3  * * *   root    /srv/data/backup-script
```

Cron is running:

```
aurels@malisart:~$ ps aux | grep cron
root      2687  0.0  0.3   2244   892 ?        Ss   13:55   0:00 /usr/sbin/cron
aurels    2707  0.0  0.1   1680   516 pts/0    R+   13:58   0:00 grep cron
```

Thanks.

---

### Post by ghantoos on 2008-11-12
> **be4truth said:**
> 
A simple script like this
```
#!/bin/bash
rdiff-backup /home/user/directory /media/storage/backup

```script is on chmod 775 or even 777


Hi,

It may be a $PATH related issue.

You should change #!/bin/bash to #!/bin/sh, for portability purposes.

Then, try changing rdiff-backup to /usr/bin/rdiff-backup

Hope this still helps,
cheers,

---

