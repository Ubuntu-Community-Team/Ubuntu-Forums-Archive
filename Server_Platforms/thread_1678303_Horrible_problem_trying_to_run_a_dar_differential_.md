---
title: "Horrible problem trying to run a dar differential script"
date: 2011-01-30
forum: Server Platforms
---

### Post by gyzer on 2011-01-30
Ok so I have been able to setup a full using dar with it doing everything that I want it to do, but the diff now I cannot get to work AT ALL.

I was using this tutorial to base by script off of:
[http://gradha.sdf-eu.org/textos/dar-differential-backup-mini-howto.en.html](http://gradha.sdf-eu.org/textos/dar-differential-backup-mini-howto.en.html)

My script is as follows(All other sections of the script have # so they should have nothing to do with the errors I am getting):

```

#Path to "Todays" Backup File"
  FILE=/mount/server_backup/Backups/$(date +"%b-%d-%y")_diff
  PREV=ls /mount/server_backup/Backups/*.dar|/usr/bin/tail -n 1| cut -c1-43
# Commands
dar -m 256 -y -Z "*.gz" -Z "*.bz2" -Z "*.zip" -Z "*.png" -R / -c $FILE -A $PREV -P backups -P dev -P lib32 -P lost+found -P media -P mnt -P mount/server_backup -P multimedia -P nas -P private -P proc -P rsync -P vms -D

```When I go to run it I get the following error:

```
/mount/server_backup/Backups/Jan-29-11_full.1.dar: 2: Syntax error: ")" unexpected
Parse error on command line (or included files): Unknown argument : backups
/mount/server_backup/Backups/Jan-30-11_diff.1.dar is required for further operation, please provide the file. [return = OK | Esc = cancel]
```I do have a full backup already for Jan-29-11_full.1.dar at /mount/server_backup/Backups.

Its almost seeming like the command is too long and dar is not recognizing some of its commands. I don't understand the Syntax error of : ")" because there are now ) characters in that part of the script. I'm also not getting why its picking up "backups" as an Unknown argument while it's right after the first -P.

I've really been tearing my hair out over this for the past 2 hours. 

Thanks

---

