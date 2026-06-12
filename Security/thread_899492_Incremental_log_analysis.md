---
title: "Incremental log analysis"
date: 2008-08-24
forum: Security
---

### Post by ngmachado on 2008-08-24
Hi,

I'm setting up my first server, using Ubuntu 8.04 LTS. It'll be just for personal unimportant files but my main concern is security (I also want to learn).

I'm just a noob but from what I read the most important way to detect an intrusion or other forms of hacking is through log analysis. Am I right?

So I've already come to the conclusion that the most important logs are: syslog, auth.log, messages and the logs from the software you run (apache logs, mail logs,...).

Following this I'm thinking about implementing a cronjob that would send me a daily mail with the lines from the past 24h of every log. 

It would be more or less like (for syslog): 

```

sudo diff /var/log/syslog ~/logs/syslog > syslogDATE
sudo cp /var/log/syslog ~/logs
mail syslogDATE me@mymail

```

What do you think about this incremental (daily) log analysis? Is it possible to implement? (I'll have to execute sudo commands in a cronjob, which implies disclose my password). 

Your help and advise are greatly appreciated.

---

### Post by rogeriopvl on 2008-08-24
Well, your log analysis is fine, but you could save some time if you used grep to filter the suspicious content.

In example:

cat /var/log/auth.log|grep ssh

If you have a openssh server opened to the outside, this line will filter authentication failures against such service.

About the cron jobs, you have to put those line in root's crontab, not yours. Like this:

sudo crontab -e

Now you can add the desired commands without the sudo. They will run with root privileges.

---

