---
title: "How to set up cron job without having to enter sudo password"
date: 2017-01-03
forum: Server Platforms
---

### Post by agarwaldvk on 2017-01-03
Hi Everyone


I have created a root cron job to schedule by backup - it works all good except that it requires me to enter the sudo password when it is run manually.

Is there a way to run this job without having to enter the sudo password.

The normal modus operandi for running the server is to have it running without the sudo privileged user being logged on - the idea is that mostly, so far, only the media files (photos, videos, and audio) are being used and everybody can access read only. I, as the sudo privileged user, more often than not, only log on remotely when I need to run tasks that need root access.

Hence, when this server is running in the normal mode, with the sudo privileged user not logged on either directly or remotely, will the root cron job run?

The cron job definition is something like so (it might change slightly for the final version):-
```

*/2 15 03 01 * /home/agarwaldvk/serverbackupjob.sh

```



The script file (/home/agarwaldvk/serverbackupjob.sh)looks like so :-
```

#!/bin/bash
todaysdatetime=$(date)
sudo backup2l -b > /home/agarwaldvk/serverbackupjoboutput.txt
mail -s "Server Backup Job Status Report - Run : $todaysdatetime" deepakagarwalathome@gmail.com < /home/agarwaldvk/serverbackupjoboutput.txt

```



Best regards


Deepak

---

### Post by cariboo on 2017-01-03
Closed duplicate thread.

---

