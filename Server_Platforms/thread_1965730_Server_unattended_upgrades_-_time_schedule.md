---
title: "Server unattended upgrades - time schedule?"
date: 2012-04-26
forum: Server Platforms
---

### Post by mintybadger on 2012-04-26
Hi

I'm setting up a webserver with Ubuntu Server 10.04 and have installed/enabled "Unattended-Upgrade" package.

This *seems* to be running daily (like I setup in /etc/apt/apt.conf.d/10periodic ) around 06.40. However, I would like to change the time of this to a quieter time.

Any ideas how I do this? I'm guessing it's something to do with  the cron setup.

Thanks
Mintybadger

---

### Post by SeijiSensei on 2012-04-26
As a guess, the script is being run via /etc/cron.daily.  All the scripts in this directory are run by the "run-parts" command which is executed by crond.  If you look at /etc/crontab, you'll see that the daily scripts are run at, on my machine, 6:25 am.  If you change the six to, say, three, it will run at 3:25 am instead.

This will change the time all the scripts in cron.daily are run.  If, for some reason, you don't want this, you'll have to write a custom crontab entry to run the update script specifically at a certain time and move the script out of cron.daily.

---

### Post by mintybadger on 2012-04-27
Excellent, thanks. 

I tweaked the crontab script as suggested and it's working a treat.

Cheers

---

