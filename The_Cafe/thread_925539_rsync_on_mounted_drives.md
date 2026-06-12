---
title: "rsync on mounted drives"
date: 2008-09-20
forum: The Cafe
---

### Post by DocForbin on 2008-09-20
Looking for tips on preventing rsync from running if the source or destination drives are not mounted.

I use rsync -avh --delete --progress /mnt/media /mnt/backup to sync a backup usb drive from another usb drive. If I run it and the destination drive isn't mounted, it will sync the files to the local filesystem. If the source drive isn't mounted, the destination drive is purged.

Would a shell script that checks if the drives are mounted before running rsync be straightforward?

---

### Post by DocForbin on 2008-09-20
well it's ugly (new to shell scripting), but I wrote a one liner that does the job

#!/bin/sh
df | grep /mnt/media && df | grep /mnt/backup && rsync -avh --delete --partial --progress /mnt/media /mnt/backup || echo "one or more disks not mounted, aborting"

---

