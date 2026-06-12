---
title: "Software RAID1 - Second Drive as Backup"
date: 2009-02-26
forum: Server Platforms
---

### Post by Inigo Montoya on 2009-02-26
i have an ubuntu server which runs 7.04. i want to upgrade it to at least 8.04 because its an lts distribution. this server is productive so backing up things is of serious importance. dd'ing or partimage'ing the whole data on an external hdd before upgrading is not an option because it would take ages (2-4 hours) and the server needs to be back online fast. so i thought about the following scenario.
first i'd copy the essential data (mails, files, conig asf.) to an external drive just in case everything else fails using the existing backup script. second thing i plan to do is to unplug one of the harddrives as the server is runnnig a linux software raid1 to use the unplugged drive as fallback if upgrade fails. i don't have lots of experience with md so my question is:
[LIST=1]
[*]what state will the raid array be in on the "primary" drive and will i be able to do the upgrade on it after unplugging the second drive?
[*]if upgrading finished ok on the first drive and i reconnect the second drive what will happen? will the raid array sync automatically? will i have to re-add the second drive? in what direction will syncing happen?
[*]will i be able to run the system from the unplugged drive if upgrading fails on the first drive? (grub is not yet installed in the second drives mbr))
[/LIST]
thanks in advance!

---

