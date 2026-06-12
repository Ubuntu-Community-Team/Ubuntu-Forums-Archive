---
title: "Wierd issue with Proftpd and Rsyslogd"
date: 2013-11-01
forum: Server Platforms
---

### Post by Groodles on 2013-11-01
Ubuntu 13.10 (upgraded from 13.04)

So this morning I noticed that my FTP transfers were stalled for some reason.  (connection refused)

I checked the server machine and found in the proftpd logs that the service had been KILLED (signal 15).  I restarted the service and normal operation resumed.

I then checked the syslog and found that exactly the same time stamp, rsyslogd had been huped.  However, I dont know why.

So, in general what i think happend is that proftpd was running, transferring files and writing to syslog.  When rsyslogd was huped, Proftpd couldn't write to syslog for a brief period of time and hence died.

Surely this isn't normal behaviour?
Am I on the right lines with my diagnosis?
Can you give me pointers as to where/what to look at next?

---

### Post by a.montali on 2013-11-04
Same problem here, no solution found yet.

---

### Post by Groodles on 2013-11-05
Since my first post, I've had the problem again, but the connection to rsyslogd was perhaps a red herring.

I updated /etc/proftpd/proftpd.conf to include the SystemLog variable which apparently disables all syslog activity and pushes the logs to a specific file instead.  Since doing this, there's no proftpd logs appearing in /var/log/syslog

However, proftpd is still randomly stopping.  :(

---

### Post by a-furmanov on 2014-01-08
I have the same problem. Any solutions?

---

### Post by T-u-N-i-X on 2014-01-24
Same here. Any solutions?

---

### Post by DaveWut on 2014-02-09
I had a similar problem with Freeradius a time ago and it was because of the logrotate script. 
To fix the problem, use your favorite text editor and edit the following file:

```
sudo nano /etc/logrotate.d/proftpd-basic
```

Its content should looks like this: 
```
/var/log/proftpd/proftpd.log
/var/log/proftpd/controls.log
{
        weekly
        missingok
        rotate 7
        compress
        delaycompress
        notifempty
        create 640 root adm
        sharedscripts
        postrotate
                # reload could be not sufficient for all logs, a restart is safer
                invoke-rc.d proftpd restart 2>/dev/null >/dev/null || true                 
        endscript
}


/var/log/proftpd/xferlog
/var/log/proftpd/xferreport
{
        monthly
        missingok
        rotate 7
        compress
        delaycompress
        notifempty
        create 640 root adm
        sharedscripts
        prerotate
        endscript
        postrotate
                # reload could be not sufficient for all logs, a restart is safer
                invoke-rc.d proftpd restart 2>/dev/null >/dev/null || true                 
                # run ftpstats on past transfer log
                ftpstats -a -r -l 2 -d -h -f /var/log/proftpd/xferlog.0 2>/dev/null >/var/log/proftpd/xferreport || true
        endscript
}

```

Locate two lines starting with: 
```
invoke-rc.d proftpd restart
```

And replace "restart" by "reload" without the double quotes. This should fix the "crashing" issue. Start proftpd and enjoy! 
Hope it helps! 

Dave

---

