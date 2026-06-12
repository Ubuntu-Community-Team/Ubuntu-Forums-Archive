---
title: "fstab and crontab questions"
date: 2008-06-25
forum: Server Platforms
---

### Post by magicplayr2000 on 2008-06-25
Hey, I'm trying to get my fstab set up correctly, and I'm having a problem with this particular line:
```

/dev/sdb1    /media/media    ext3    none    auto    0    1

```

Then, there's crontab.  I'm trying to set up a job that'll automatically email out formatted logs.  Here's my crontab:
```

# m h  dom mon dow   command
05 17 * * * /home/administrator/log.sh > /home/administrator/cronResults

```

log.sh does this:
```

#!/bin/bash
cd /home/administrator
logwatch --range yesterday --detail high > logOut
./mailSend.py

```

and mailSend just sends out the email with logOut.  When I run this by hand, it works fine.  When it runs on crontab, logOut is always empty.  What am I doing wrong?

---

### Post by earthmeLon on 2008-06-25
```
/dev/sdb1 /media/media ext3 rw,user,auto 0 0
```


Try that

---

### Post by unixbills on 2008-06-25
On the crontab issue redirect your errors to the file or go look in syslog to see what is going on.  Your environment is different. Like you have logwatch in your PATH but the system doesn't so it works for you but not when run from cron.  I would set it to run every minute "* * * * *" while working on it.

Are you sure the script ran?  Add an echo or date to a file so you are sure you ran.

---

### Post by magicplayr2000 on 2008-06-25
Thanks, I guess logwatch isn't in the path for crontab.  I gave it the absolute filepath and it works now.

EDIT: The fstab changes worked too, thanks.

---

