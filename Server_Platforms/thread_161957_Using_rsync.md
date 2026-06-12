---
title: "Using rsync"
date: 2006-04-18
forum: Server Platforms
---

### Post by catfox on 2006-04-18
Hi all,
I've written a load of scripts which use rsync every day.
so i have a backup directory structure like this
/backups/day1
/backups/day2
/backups/day3

the day2 directory will only have new files since day1, but will include hard links to the old files. 
what i need to do is be able to get day2's files only, for example.
will i need to do that with a separate rsync command line, or is it doable via the command line.

---

