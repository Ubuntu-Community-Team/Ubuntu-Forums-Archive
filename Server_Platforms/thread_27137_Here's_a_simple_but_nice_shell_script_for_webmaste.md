---
title: "Here's a simple but nice shell script for webmasters..."
date: 2005-04-15
forum: Server Platforms
---

### Post by Trickyphillips on 2005-04-15
I created a small script that will create a directory named "[day]-[month]-[year]", download a database on a remote server (through cpanel), and save it to that directory.

I love the script, so I thought I'd share it with anyone that might want it. I suggest executing it via CRON, so you never have to manually download your backup again (as long as you leave your computer on 24/7).

Text in [COLOR=DarkRed]red[/COLOR] should be modified.
```
mkdir "[COLOR=DarkRed]/path/to/backup/directory/[/COLOR]`date +%d-%m-%Y`"

wget http://[COLOR=DarkRed]cpanel-username[/COLOR]:[COLOR=DarkRed]cpanel-password[/COLOR]@[COLOR=DarkRed]your-url.com[/COLOR]:2082/getsqlbackup/[COLOR=DarkRed]database-name[/COLOR].gz --output-document="[COLOR=DarkRed]/path/to/backup/directory/[/COLOR]`date +%d-%m-%Y`"
```

I know it's a pretty lame & simple script, but I love it. I made two; backup-am.sh and backup-pm.sh. They have "8AM" and "8PM" in the directory names, so I can run them in CRON every 12 hours. Executing this script through CRON really saves a lot of time. (I always forgot to make daily backups, before I started using this)

Just thought I'd share my idea with other webmasters. Have fun with it! :)

---

### Post by accuser on 2005-04-15
If you change the date formatting, thus:
```

`date +%Y-%m-%d`

```
your backups will be in chronological order whether listed by created date or filename.

---

### Post by Trickyphillips on 2005-04-15
[QUOTE=accuser]If you change the date formatting, thus:
```

`date +%Y-%m-%d`

```
your backups will be in chronological order whether listed by created date or filename.[/QUOTE]
Thanks. :) I usually just delete my backups after they've been around for a week or so, anyway (Just to save HD space). I don't have too much to sort through if I want to restore a backup. 8-)

---

