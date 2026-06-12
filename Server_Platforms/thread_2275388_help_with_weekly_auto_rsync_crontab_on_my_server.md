---
title: "help with weekly auto rsync crontab on my server"
date: 2015-04-25
forum: Server Platforms
---

### Post by hornbutu on 2015-04-25
Hello

I am running x32 ubuntu 14.04 headless server. My wish is to do two different auto backups every monday at midnight. I just want to make sure I am making the correct steps, and not screwing my machine up at the same time. My goal is to:
-duplicate the contents of dir A into dir B
-duplicate the contents of dir C into dir D
-do this every monday at midnight (as in 00:00:59 Monday)

I'm under the understanding I need to write a script, so: 
[COLOR=#232323][FONT=monospace]#!/bin/sh[/FONT][/COLOR]
[COLOR=#232323][FONT=monospace]# Monday Data Backup
[/FONT][/COLOR][FONT=verdana]sudo rsync -avucz --update --progress --human-readable /media/osstorage/ /media/osbunker/ && sudo [/FONT][FONT=verdana]rsync -avucz --update --progress --human-readable /media/storage/ /media/bunker/[/FONT][FONT=verdana]

I'd then save that script as "mon_sync_cron", and place it in /home/backup/script. This would be followed by "[/FONT][FONT=monospace][COLOR=#232323]sudo chmod +x [/COLOR][/FONT][FONT=verdana]/home/backup/script/[/FONT][FONT=verdana]mon_sync_cron.sh"[/FONT][FONT=verdana]

next, I'd have to add the following to "sudo crontab -e"
[/FONT][FONT=verdana]0 0 * * Mon [/FONT][FONT=verdana] [/FONT][FONT=verdana]/home/backup/script/[/FONT][FONT=verdana]mon_sync_cron.sh


Is this all correct?
Thanks![/FONT]

---

### Post by ian-weisser on 2015-04-26
It's unwise to use 'sudo' in an automated script. That's not what sudo is for. (And the system will ask for a password!)

'mon' as a day-of-week works if your locales are properly set up. Integers are often used instead for multilanguage or multilocale situations. 1 = Monday

When using crontabs, it's wise to redirect output to a tempfile or logfile. Otherwise helpful error messages are lost and you are left with a mystery.

If your script needs to run as root, then run it as root - add it to root's /etc/cron.weekly/ or /etc/cron.d/ directories instead of your user's crontab.
A root crontab in /etc has one additional field for username - in this case 'root'

'0 0 * * mon' may be confusing in the distant future when you need to maintain it. I always specify a minute before or after midnight...though I usually just lump weekly tasks into /etc/cron.weekly and not bother with a separate crontab at all.

```
## Example root crontab entry /etc/cron.d/my_weekly_backup with output redirection
1 0 * * mon root /home/my_username/backup/script/ > /tmp/my_weekly_backup_output 2>&1
```

---

