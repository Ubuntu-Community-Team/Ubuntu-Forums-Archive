---
title: "Trying to automate chmod via cron"
date: 2009-02-15
forum: Server Platforms
---

### Post by chmac on 2009-02-15
On my web server, when a user upoads a file the permissions on the file are 600 so my backup script (not running as root) cannot read the files to back them up. In order to get round this, I schedule a cron job to chmod the permissions in that directory.

```
sudo crontab -u root -l
55 * * * * /bin/chmod -R +r /path/to/dir/
```

Can anyone suggest what's wrong with this? If I copy the command and run it via sudo it works as I'd expect. I previously had a wildcard, but I removed that as I thought cron may expand wildcards differently.

Could it be that I'm just using +r instead of ugo+r ? I'd rather not use an octet set of permissions as my aim is specifically to make all files in that directory readable by all users.

Any suggestions would be greatly appreciated.

---

### Post by Vegan on 2009-02-15
You might want to stuff the command into a shell script, make it executable and use that. This way you will get what you want easier.

:guitar:

---

### Post by chmac on 2009-02-16
Hey Vegan, thanks for that. I thought about making it a shell script. I'm kinda curious to know why it doesn't work right now though. Partly to solve the problem but moreso because I'm curious! :)

---

### Post by chmac on 2009-03-03
Update, I tried putting the command into a cron script, no dice. It doesn't work. I call the command via sudo and it works fine, but not via cron.

Anyone else have any suggestions?

---

