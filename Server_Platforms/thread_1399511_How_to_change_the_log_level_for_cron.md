---
title: "How to change the log level for cron"
date: 2010-02-05
forum: Server Platforms
---

### Post by narnie on 2010-02-05
Hello,

I'm wondering how to change the log level to level 2 for cron without manually have to restart it with every boot.

I didn't thing this would be hard to find, but searching has cause me to come up empty.

System is 9.10

With thanks,
Narnie

---

### Post by yogesh.girikumar on 2010-02-09
Hi,

This can be achieved by editing the /etc/rsyslog.d/50-default.conf
       ```
$ sudo nano /etc/rsyslog.d/50-default.conf
```       Uncommenting the '#' before the line that says cron in it will enable logging for cron.
   ```
[..snip..]

#cron.*                         /var/log/cron.log

[..snip..]
```      Remove the '#' symbol from this line. You can choose the logging level by specifying the log level in the line.
For example
       ```
cron.*                                                      /var/log/cron.log
```       will log all the messages to the cron.log file, whereas
   ```
cron.crit         /var/log/cron.log
``` will log messages tagged as crit, emerg and alert as well.. Then you can restart the logging daemon by giving the following command in the terminal
```
$ sudo /etc/init.d/rsyslog reload
```or 
```
$ sudo kill 1 `cat /var/run/rsyslogd.pid`
```       Hope this helps

---

### Post by narnie on 2010-02-10
> **yogesh.girikumar said:**
> Hi,

This can be achieved by editing the /etc/rsyslog.d/50-default.conf
       ```
$ sudo nano /etc/rsyslog.d/50-default.conf
```       Uncommenting the '#' before the line that says cron in it will enable logging for cron.
   ```
[..snip..]

#cron.*                         /var/log/cron.log

[..snip..]
```      Remove the '#' symbol from this line. You can choose the logging level by specifying the log level in the line.
For example
       ```
cron.*                                                      /var/log/cron.log
```       will log all the messages to the cron.log file, whereas
   ```
cron.crit         /var/log/cron.log
``` will log messages tagged as crit, emerg and alert as well.. Then you can restart the logging daemon by giving the following command in the terminal
```
$ sudo /etc/init.d/rsyslog reload
```or 
```
$ sudo kill 1 `cat /var/run/rsyslogd.pid`
```       Hope this helps

It does help a great deal. Thanks. Quite a thorough explanation.

I'm curious how the logging gets turned on in the first place. Cron is sending logs every time it is running to the syslog.log (not cron.log) which is fine with me, but mails had been going to root and to the running user. How does one turn off ALL logging that cron is doing by default. I know I can put MAILTO="" in /etc/crontab and into the user's crontab using crontab -e (but the user might not know that).

With thanks,
Nathan

---

### Post by yogesh.girikumar on 2010-02-12
Hi,


       MAILTO="" is the best way to do that. But in case you want to stop mailing for a specific select cronjobs, you can redirect the mailing output to /dev/null which is like a "digital blackhole inside Linux" ;-) Redirecting the output to the /dev/null file will simply destroy the output, meaning it won't be mailed to anyone.

       It can be done by editing the crontab file. Just place a ">& /dev/null" after the particular job for which you want to suppress mailing.

   For example:
```
20 6 * * 1-5 /home/bob/alarm >& /dev/null
```      will suppress all mailing for the cron job that starts the alarm.

       Hope this helps.

---

