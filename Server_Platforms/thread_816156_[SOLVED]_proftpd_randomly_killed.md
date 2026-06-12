---
title: "[SOLVED] proftpd randomly killed"
date: 2008-06-02
forum: Server Platforms
---

### Post by cdenley on 2008-06-02
I have a problem with proftpd randomly getting killed and not starting back up once in a while. I'm guessing it has something to do with log rotating. I have SSL configured and the key file is password-protected. The log for when it is randomly killed is
```

Jun 01 01:52:02 ftp.mydomain.com proftpd[25444] ftp.mydomain.com: ProFTPD killed (signal 15)
Jun 01 01:52:02 ftp.mydomain.com proftpd[25444] ftp.mydomain.com: ProFTPD 1.3.1 standalone mode SHUTDOWN

```

/etc/init.d/proftpd reload seems to work, except it breaks SSL. I can no longer connect with encryption until I do /etc/init.d/proftpd restart. Plain old ftp still works fine.
```

Jun 02 08:44:16 ftp.mydomain.com proftpd[14844] ftp.mydomain.com: received SIGHUP -- master server reparsing configuration file
Jun 02 08:44:16 ftp.mydomain.com proftpd[14844] ftp.mydomain.com: 192.168.0.9:21 masquerading as 192.168.0.9
Jun 02 08:44:16 ftp.mydomain.com proftpd[14844] ftp.mydomain.com: mod_tls/2.1.2: unable to use RSA certificate key in '/etc/ssl/private/www.key', exiting
Jun 02 08:46:23 ftp.mydomain.com proftpd[14938] ftp.mydomain.com: ProFTPD 1.3.1 (stable) (built Thu Feb 21 04:50:29 UTC 2008) standalone mode STARTUP

```

I'm guessing a work-around would be to use a key file that isn't password-protected. However, I would prefer to keep the key for my signed certificate password-protected. I would also prefer to use my signed certificate for proftpd as well as apache. Is this possible?

---

### Post by beniwtv on 2008-06-03
If you have enabled logrotate for this log file, this could indeed be a problem if each restart you have to enter the password by hand (logrotate will not be able to provide the password).

So I'd suspect logrotate restarting it and not able to restart it.

Of course, I may not be correct at all if you don't need to provide a password. :lolflag:

Cheers,

---

### Post by cdenley on 2008-06-03
Actually, I don't see any proftpd configuration in "/etc/logrotate.d". I assumed the logs would get rotated like apache since I had a similar problem with apache in gutsy. Could something else be trying to rotate the logs or kill/restart proftpd?

---

### Post by beniwtv on 2008-06-03
AFAIK, only the kernel would kill the process if there were not sufficient resources left to run it.

Or it could be called by the init script, which kills it...

Do you have any cron entries that could call the init script? How much memory does your server have? How much traffic?

You can verify the cron entries by doing:

```
crontab -l
```

Cheers,

---

### Post by cdenley on 2008-06-03
There should not have been a problem with resources. The server has 1GB of memory, and this happened at 2AM on a sunday night (it's usually only used during business hours).

The only crontabs for root are scripts I made, none of which would kill proftpd or run the last time proftpd was killed. Any other ideas?

---

### Post by cdenley on 2008-07-01
I can't believe I missed this last month!

/etc/cron.monthly/proftpd
```

#!/bin/sh
#
# cron script to rotate the proftpd server logfile, based on the
# wu-ftpd script by Peter Tobias <tobias@et-inf.fho-emden.de>.

[ -x /usr/sbin/ftpstats ] || exit 0

cd /var/log/proftpd
savelog -q -u root -g adm -m 640 -c 12 /var/log/proftpd/xferreport
ftpstats -a -r -l 2 -d 2>/dev/null >/var/log/proftpd/xferreport
savelog -q -u root -g adm -m 640 -c 7 /var/log/proftpd/xferlog
savelog -q -u root -g adm -m 640 -c 7 /var/log/proftpd/proftpd.log
savelog -q -u root -g adm -m 640 -c 7 /var/log/proftpd/controls.log
# reload could be not sufficient for all logs, a restart is safer
/usr/sbin/invoke-rc.d proftpd restart 2>/dev/null >/dev/null || true

```

After noticing it happened again at the same time on the first of the month, I knew it had to be a cron job. What exactly do they mean by "reload could be not sufficient for all logs"? Which logs, and does "could be" mean they are not sure, or that it definitely can in certain situations. Either way, encrypted SSL keys are basically unusable with proftpd in ubuntu since neither a reload or restart work correctly without user interaction. I gave up and created a self-signed certificate without a password to use specifically for proftpd. I don't think anyone uses encrypted ftp, anyway.

---

### Post by blagh on 2011-02-02
Thanks, I was having the same problem. I wasn't quite sure how to go about making the self-signed certificate, but this page came in handy (ignoring the MySQL bits): [http://2stech.ca/index.php/linuxtutorials/65-installingproftpdwithmysqlandtls](http://2stech.ca/index.php/linuxtutorials/65-installingproftpdwithmysqlandtls)

---

