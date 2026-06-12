---
title: "Running a sync task once a day"
date: 2011-11-10
forum: Server Platforms
---

### Post by Nessaja on 2011-11-10
Hi,

I have a fairly easy question, but for some reason can't get it working properly.

I have a bash script that uses rsync to sync folders from a server to a nas storage device once a day. The script works fine, but if I add it to crontab it only runs for an hour then stops the script. I know I hade a stupid mistake somewhere, is there a specific part in the crontab command that's supposed to make it run for more than an hour that I need to add?

Any help would be greatly appreciated.

---

### Post by CharlesA on 2011-11-10
Are you sure it runs for an hour and doesn't encounter an error that stops the script from working?

The cron environment is different from your user's environment, so I try to use full paths whenever possible.

Can you post the crontab entry and the script you are using?

---

