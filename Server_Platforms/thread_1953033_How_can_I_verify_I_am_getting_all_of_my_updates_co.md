---
title: "How can I verify I am getting all of my updates correctly?"
date: 2012-04-05
forum: Server Platforms
---

### Post by tbharber on 2012-04-05
I have an Ubuntu Server running 11.04.  When setting it up I chose to automatically apply updates, but my question is how can I confirm this is working correctly?  I assume it is updating the security updates and such in the background but have not seen any prompts or anything to show me this is working.

Because there is no GUI I am not sure where to go to verify everything is updating as it should.

Thoughts?

---

### Post by CharlesA on 2012-04-05
You can always run an update and upgrade manually:

```
sudo apt-get update && sudo apt-get upgrade
```

You can also check /var/log/unattended-upgrades/unattended-upgrades.log

Mine says this:

```
2012-04-02 06:29:05,452 INFO Initial blacklisted packages:
2012-04-02 06:29:05,452 INFO Starting unattended upgrades script
2012-04-02 06:29:05,453 INFO Allowed origins are: ["['Ubuntu', 'lucid-security']"]
2012-04-02 06:29:06,337 INFO No packages found that can be upgraded unattended
2012-04-03 06:33:35,790 INFO Initial blacklisted packages:
2012-04-03 06:33:35,798 INFO Starting unattended upgrades script
2012-04-03 06:33:35,799 INFO Allowed origins are: ["['Ubuntu', 'lucid-security']"]
2012-04-03 06:33:36,739 INFO No packages found that can be upgraded unattended
2012-04-04 06:53:52,952 INFO Initial blacklisted packages:
2012-04-04 06:53:52,961 INFO Starting unattended upgrades script
2012-04-04 06:53:52,961 INFO Allowed origins are: ["['Ubuntu', 'lucid-security']"]
2012-04-04 06:53:53,855 INFO No packages found that can be upgraded unattended
2012-04-05 06:29:04,561 INFO Initial blacklisted packages:
2012-04-05 06:29:04,569 INFO Starting unattended upgrades script
2012-04-05 06:29:04,570 INFO Allowed origins are: ["['Ubuntu', 'lucid-security']"]
2012-04-05 06:29:08,437 INFO Packages that are upgraded: libtiff4
2012-04-05 06:29:08,437 INFO Writing dpkg log to '/var/log/unattended-upgrades/unattended-upgrades-dpkg_2012-04-05_06:29:08.437408.log'
2012-04-05 06:29:11,786 INFO All upgrades installed

```

Check here too:
[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

---

### Post by tbharber on 2012-04-07
Perfect!  That log file let me know the information I needed.  Now one followup question would be do you know ho to change the time of day it is running the update?  I find that it is running around 6:30am everyday.  I would prefer it to run earlier (say around 3am).  Is this possible?

---

### Post by CharlesA on 2012-04-07
> **tbharber said:**
> Perfect!  That log file let me know the information I needed.  Now one followup question would be do you know ho to change the time of day it is running the update?  I find that it is running around 6:30am everyday.  I would prefer it to run earlier (say around 3am).  Is this possible?
You'd have to edit /etc/crontab (and restart cron)

```
charles@Thor:~$ cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

```

```
sudo service cron restart
```

See here for more detail:
[http://serverfault.com/questions/135906/when-does-cron-daily-run](http://serverfault.com/questions/135906/when-does-cron-daily-run)

---

