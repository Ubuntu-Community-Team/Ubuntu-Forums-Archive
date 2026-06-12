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
mail -s "Server Backup Job Status Report - Run : $todaysdatetime" email@example.com < /home/agarwaldvk/serverbackupjoboutput.txt

```



Best regards


Deepak

---

### Post by CharlesA on 2017-01-03
If you are running that in a root cronjob, you do not need sudo in the script.

If you want to run it manually, either use sudo or switch to the root user and run the script.

There are ways to disable the sudo password prompt, but if a user is not in the sudoers file, they will not be able to issue a sudo command at all.

---

### Post by alexandari on 2017-01-03
Hi,

You can use the following in your script:
echo yourpassword123 | sudo -S command

---

### Post by agarwaldvk on 2017-01-03
Hi


This is definitely a root cron job - I set it up that way!

I just tried it an hour ago by making the script run every 10 minutes after 7 pm (as a cron job) my time with no sudo privileged user logged on the server and the script ran and it didn't ask for the password - how come????????

I don't get it! Shouldn't it have?


Best regards


Deepak

---

### Post by Irihapeti on 2017-01-03
How did you setup the cron job? That is, what command did you use? Did you use crontab or something else? That might have some bearing on things.

---

### Post by agarwaldvk on 2017-01-03
Hi

I used the following command to set it up :-

sudo crontab -e

and then the parameters for the minute, hour, day of month, month etc etc


Best regards


Deepak

---

### Post by Irihapeti on 2017-01-03
Then you shouldn't need "sudo" in the script itself, since the process is being run as root.

Edit the line 

```
sudo backup2l -b > /home/agarwaldvk/serverbackupjoboutput.txt
```

and remove "sudo" at the beginning.

My guess - and it's only a guess - is that having the "sudo" present is confusing the system into thinking that the logged-in user needs to enter a password.

---

### Post by Habitual on 2017-01-03
> **agarwaldvk said:**
> Hi


This is definitely a root cron job - I set it up that way!

I just tried it an hour ago by making the script run every 10 minutes after 7 pm (as a cron job) my time with no sudo privileged user logged on the server and the script ran and it didn't ask for the password - how come????????
sudo has a 10 minute timeout feature.
Anything else run in less than 10 minutes from the top-level session needing sudo pass is granted without secondary prompting.

```
sudo -k
``` resets and forces password prompt.
That's been my experience with sudo.

---

### Post by agarwaldvk on 2017-01-03
Hi


Tried it this morning and it worked without the sudo in the script file and not logged in on the server as the sudo privileged user. But the job was run within the 10 minute window.

Testing it now with the time window exceeding the 10 min grace period afforded by sudo functionality.

Will keep you all posted.


Edit:-
The job ran just now after nearly a 20 minute time lag between when the cron job was set up and the time for running and it seems to work OK without asking for password - is that how its supposed to work?



Best regards


Deepak

---

### Post by ian-weisser on 2017-01-03
> **agarwaldvk said:**
> is that how its supposed to work?

Yes.
The system does not need to use passwords with itself.
Passwords confirm the identity of users, not programs.

---

### Post by agarwaldvk on 2017-01-04
Hi ian_weisser


Thanks for that. Now I know.

Then this works as intended.


Best regards


Deepak

---

