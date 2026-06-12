---
title: "CRON problem with flexget"
date: 2012-09-01
forum: Server Platforms
---

### Post by kpuz on 2012-09-01
I am trying to get flexget plugin for deluge to run every 5 hours via root's crontab:
```
0 */5 * * * /usr/local/bin/flexget --cron
```
When I run this command as root in a shell, it works perfectly. But when I add it to root's cron (by sudo crontab -e), it fails. There is a log file in ~/.flexget/flexget.log that doesn't show anything which makes me think that the command is not running (correct me if I'm wrong). 
The following errors are found in the /var/log/syslog file:
```
Sep  1 10:00:01 toshibaserver CRON[31019]: (root) CMD (/usr/local/bin/flexget --cron)
Sep  1 10:00:02 toshibaserver CRON[31018]: (CRON) error (grandchild #31019 failed with exit status 1)
Sep  1 10:00:02 toshibaserver CRON[31018]: (CRON) info (No MTA installed, discarding output)
Sep  1 10:09:01 toshibaserver CRON[31025]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Sep  1 10:17:01 toshibaserver CRON[31032]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  1 10:39:01 toshibaserver CRON[31184]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)

```

I don't know how to fix this problem, anybody have ideas?

---

### Post by arrrghhh on 2012-09-02
I'm running flexget/cron as my user... so are you doing a 'sudo fleget' when you're testing, or just 'flexget'?

I basically have the same command, but again in my user's crontab, not root's.

---

### Post by kpuz on 2012-09-02
I was able to figure out my problem.

The CRON errors in /var/log/syslog were not being saved because I did not have a mail-transfer agent installed. I installed postfix which allowed the error output to be sent to /var/mail/root. 

The problem was that I had set up flexget to use the config file in my user folder. Root's crontab was running flexget, and flexget was looking for the config file in /root/.flexget/ which didn't exist. I got the following error output in /var/mail/root
```
2012-09-02 15:00 INFO     manager                       Tried to read from: /usr/local, /root/.flexget, /root/.config/flexget
2012-09-02 15:00 CRITICAL main                          Failed to find configuration file config.yml

```
So I changed root's crontab to specify the config file like so:
```
0 */5 * * * /usr/local/bin/flexget -c /home/myusername/.flexget/config.yml --cron
```
That fixed my issue. Hopefully this solution can help someone else in the future.

---

