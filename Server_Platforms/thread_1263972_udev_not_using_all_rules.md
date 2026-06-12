---
title: "udev not using all rules?"
date: 2009-09-11
forum: Server Platforms
---

### Post by austin987 on 2009-09-11
I'm working on a backup scheme involving rsync, two external hard drives, and (eventually), truecrypt encryption of the drives.

The first two is mostly done. udev will wait for the drive, mount it, rsync the files, unmount it and provide notification. Wonderful.

The problem is there are two drives, and soon each will be encrypted with its own key. As a result, I need to tell the backup script which drive it's dealing with:
ID_SERIAL_SHORT=="serial1", KERNEL=="sd[a-z]1", ID_MODEL_ID=="3000", ID_FS_USAGE=="filesystem", DEVTYPE=="partition", ACTION=="add", OPTIONS+="last_rule", RUN="/usr/local/bin/backup %k drive1"

ID_SERIAL_SHORT=="serial2", KERNEL=="sd[a-z]1", ID_MODEL_ID=="3000", ID_FS_USAGE=="filesystem", DEVTYPE=="partition", ACTION=="add", OPTIONS+="last_rule", RUN="/usr/local/bin/backup %k drive2"

Everything is the same in the rules, aside from the serial numbers and either drive1/2 being passed as $2 to the backup script. The problem is, no matter which drive I plug in, udev is seeing it as drive1! How can I get it to recognize the ID_SERIAL_SHORT parameter properly?

---

### Post by austin987 on 2009-09-30
Ping

---

