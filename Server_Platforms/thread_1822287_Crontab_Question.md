---
title: "Crontab Question"
date: 2011-08-10
forum: Server Platforms
---

### Post by Jay89 on 2011-08-10
Is there a way to schedule a task to run on the _1st Saturday_ of every month? I'm a bit confused and not sure if what I have here will run. Any ideas? I am running Ubuntu 10.04 Server x64

What I have right now is:

[B]# m h  dom mon dow   command
   00 00 1 * Sat /storage/scripts/monthly-script.sh[/B]

This looks to me that it will only run at midnight if a Saturday *is* the first of the month. But if that's the case then that's not quite what I'm looking for...

---

### Post by Hack.The.Pow. on 2011-08-10
I believe the entry you are looking for is this

```
0 0 * * 6 /bin/sh /storage/scripts/monthly-script.sh

```

The first * indicates that it doesn't matter what day it is.  Your command would have only executed if it was the first day of the month on a saturday.

I believe you also need the /bin/sh line because cron needs absolute paths.

Hope that helps.

Please somebody correct me if I'm wrong, I am relatively new at this as well

**Edit:** just reread your post.  I don't think you can do it for the first saturday of the month only using cron(somebody correct me if wrong).

You can however include this in your script to check that it is within the first 7 days of the month.

```
#! /usr/bin/ksh
day=$(date +%d)
if ((day <= 7)) ; then
   exec somecommand
fi
exit 1
```

And then your cron entry would be

```
0 0 * * 6 /bin/sh /storage/scripts/monthly-script.sh

```

---

### Post by Jay89 on 2011-08-10
Thanks Hack.The.Pow,
       Your command does the job!

---

