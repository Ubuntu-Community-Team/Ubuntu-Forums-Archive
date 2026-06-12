---
title: "Backup Shell Script"
date: 2009-10-18
forum: Security
---

### Post by cky on 2009-10-18
Hello!

I wan't to know if there is any writen script to backup my files from Ubuntu server to my external disc at specified time. Example that backup is made from folder /home/username/files at 8 pm...

Thanks in advance.

My regards

---

### Post by Lars Noodén on 2009-10-19
Look at using [cron]("http://linux.die.net/man/1/crontab") to run a script at a specified time.
Look at [rsync]("http://linux.die.net/man/1/rsync") for how to back up a directory.

Then make a script you can run to do the backup manually.  When it works, put it in /usr/local/sbin/ and then call it from cron.  

It can be something simple like this:

```

#!/bin/sh

# UUID for the external disk
UUID=76824-1222-4aaf-90cb-76341167d5b0c

# quit if that external disk is not plugged in
# and mounted
findfs UUID=$UUID || exit 1;

# backup will succeed only if the external drive 
# is mounted in the same place each time
rsync -a /home/myhomedir /media/removabledisk42

# backup, but delete old files.  riskier
# rsync -a --delete-after /home/myhomedir /media/removabledisk42
```

Remember, during the time that the external drive is plugged in, it is not a back up and anything can happen to it.  So if you have only one back up drive, for the duration it is plugged in you actually have no backup.   :O  

For the duration the back up is within a few hundred meters of your location, it's not an offsite backup, either.  ;)

---

### Post by HermanAB on 2009-10-20
Howdy, in the simplest case, you can use rsync and drop the script into /etc/cron.daily and it will execute every morning at 1 minute past 4.

---

