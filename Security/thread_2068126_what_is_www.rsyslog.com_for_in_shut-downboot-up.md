---
title: "what is www.rsyslog.com for in shut-down/boot-up?"
date: 2012-10-08
forum: Security
---

### Post by s1baker on 2012-10-08
hi,
What is [www.rsyslog.com](www.rsyslog.com) for in shut-down and boot-up?
( xubuntu 12.04.01  64 bit......kernel = 3.2.0-31-generic )

Here is the recent last two lines from the system log before my system shuts down:
```
->  kernel: Kernel logging (proc) stopped.
->  rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="823" x-info="http://www.rsyslog.com"] exiting on signal 15.
```

and the recent first 5 lines at boot-up:

```
->  kernel: imklog 5.8.6, log source = /proc/kmsg started.
->  rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="702" x-info="http://www.rsyslog.com"] start
->  rsyslogd: rsyslogd's groupid changed to 103
->  rsyslogd: rsyslogd's userid changed to 101
->  rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]

```


thanks

---

### Post by cipherboy_loc on 2012-10-08
The first quote is just showing that rsyslogd is shutting down, specifically more information about rsyslogd can be found at rsyslog.com (x-info attribute). The second quote shows that more information abou the error (cannot open the console for writing) can be found at that link. Rsyslogd is not accessing the remote server, it is just saying that you can go there to get more information.

Thanks,
Cipherboy

---

### Post by rookcifer on 2012-10-08
rsyslog is your system logger.  It is normal.  As the guy above said, the message is just giving info about where to find more info about rsyslog (website).

---

