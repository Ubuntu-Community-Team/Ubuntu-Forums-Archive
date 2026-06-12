---
title: "syslogd stops every day"
date: 2007-02-28
forum: Server Platforms
---

### Post by cshepherd on 2007-02-28
Hey guys,

I've done a lot of Ubuntu installs and haven't had this problem before.

At 0628 every morning all logging stops.  It turns out that syslogd is stopping at this time every morning.

If I start syslogd it will work fine until 0628 the next morning.

cron.daily is run at 0625 daily and sysklogd is the last script run; the last line of this script is /etc/init.d/sysklogd reload-or-restart > /dev/null

So I tried this line and it works fine, sysklogd successfully restarts.  So can anyone help me out as to why this would be happening?

uname -a
Linux arnon 2.6.15-27-amd64-generic #1 SMP PREEMPT Thu Jul 20 15:34:34 CEST 2006 x86_64 GNU/Linux

---

### Post by MJN on 2007-02-28
Get rid of the **> /dev/null** suffix and you (or rather root) will get sent (e-mail) details of any output that occurs when trying to restart syslogd.

Mathew

---

### Post by cshepherd on 2007-03-26
I still have this problem and I haven't seen any syslogd messages after removing /dev/null

---

### Post by Mr. C. on 2007-03-27
Did you look to see if there are mailbox items in root's mail box ?

Do you have a mailer (sendmail) installed ?

If not, replace:

```
  > /dev/null
```
with
```
  2>&1 > /tmp/syslog.out 
```

and check /tmp/syslog.out the next morning.

MrC

---

### Post by booyabazooka on 2007-03-28
Same problem:

Mar 27 07:34:34 antell -- MARK --
Mar 27 07:38:18 antell exiting on signal 15
Mar 27 07:38:19 antell syslogd 1.4.1#18ubuntu6: restart.
Mar 27 07:58:19 antell -- MARK --

This seems to be coming up so [frequently]("http://ubuntuforums.org/showthread.php?t=36504")... surely someone has a solution?

---

### Post by Mr. C. on 2007-03-28
What do you see as the problem ?

syslog restarted - this is expected, as logs need to be rotated, and they cannot be rotated while syslog is running.

MrC

---

### Post by LNick on 2007-03-30
I believe the OP knows that the restart entry is syslog restarting.  The OP is trying to figure out why logging stops after some time.  I'm having the same problem.

Below is a an unedited snippet of my logs.  Notice on Mar 29 that nothing is logged after 6:58 until 16:43 when I manually restarted sysklogd.  Logging works fine for 15 minutes and then nothing is logged until sysklogd automatically restarts at Mar 30 06:26.  I came in today an checked the logging and manually restarted sysklogd multiple times.

```
Mar 29 06:40:34 10.1.1.38 -- MARK --
Mar 29 06:55:30 192.168.111.201 -- MARK --
Mar 29 06:58:47 10.1.1.9 -- MARK --
Mar 29 16:43:11 ubuntu-dev syslogd 1.4.1#18ubuntu6: restart (remote reception
Mar 29 16:44:12 10.1.1.9 untrusted: test log
Mar 29 16:45:04 10.1.1.9 untrusted: 2nd test of logging
Mar 29 16:45:16 10.1.1.9 untrusted: 3rd logging test
Mar 29 16:45:44 10.1.1.9 untrusted: logging appears to work fine. stop fillin        he logs with test!
Mar 29 16:56:20 192.168.111.201 -- MARK --
Mar 29 16:57:49 10.1.1.37 -- MARK --
Mar 30 06:26:39 ubuntu-dev syslogd 1.4.1#18ubuntu6: restart (remote reception
Mar 30 06:37:29 192.168.111.201 -- MARK --
Mar 30 06:40:05 10.1.1.9 -- MARK --
Mar 30 06:40:33 10.1.1.37 -- MARK --
Mar 30 06:40:34 10.1.1.36 -- MARK --
Mar 30 06:40:34 10.1.1.38 -- MARK --
Mar 30 06:57:29 192.168.111.201 -- MARK --
Mar 30 08:32:49 ubuntu-dev syslogd 1.4.1#18ubuntu6: restart (remote reception
Mar 30 08:35:36 ubuntu-dev exiting on signal 15
Mar 30 08:35:39 ubuntu-dev syslogd 1.4.1#18ubuntu6: restart (remote reception
Mar 30 08:37:09 ubuntu-dev exiting on signal 15
Mar 30 08:37:10 ubuntu-dev syslogd 1.4.1#18ubuntu6: restart (remote reception
Mar 30 08:37:22 10.1.1.9 -- MARK --
Mar 30 08:37:39 192.168.111.201 -- MARK --
Mar 30 08:40:33 10.1.1.37 -- MARK --
Mar 30 08:40:34 10.1.1.36 -- MARK --
Mar 30 08:40:34 10.1.1.38 -- MARK --
```

Anyone have any ideas?

---

### Post by Mr. C. on 2007-03-30
I've looked through the various code, and the bug reports.

It is clear that the people who created the scripts to start, stop, and reload daemons do not understand race condtions, and are quite inexperienced.

The code blindly assumes that a signal delivered to syslog will be processed instantaneously and reliably, and during heavy system load and thrashing, this appears to be non-reliable.  Additionally, the rotate code is exacerbating the problem by moving and compressing the logfile immediately prior to sending syslog its signal to restart.  This is not wise.  The syslog file should be simply renamed, and then syslog sent its signal, and only after syslog has reloaded, should the log files be compressed.  All file compressions should occur after all log rotations are completed to reduce the load on the system during log rotation time.

To affect a quick workaround for those of you having this trouble, edit the file: /etc/cron.daily/sysklogd, and replace

```
/etc/init.d/sysklogd reload-or-restart > /dev/null
```

with:

```
/etc/init.d/sysklogd stop > /dev/null
/etc/init.d/sysklogd start > /dev/null
```

The stop will ensure that syslog is stopped before continuing with the start, whereas the reload-or-restart code assumes the signal is delivered.

MrC

---

### Post by Mr. C. on 2007-03-30
For those intrested, I've posted some comments regarding this bug:

[https://launchpad.net/ubuntu/+source/sysklogd/+bug/49165](https://launchpad.net/ubuntu/+source/sysklogd/+bug/49165)

MrC

---

### Post by cshepherd on 2007-03-30
Thanks MrC,

This looks promising.  I'll try the change and see how it goes.  As mentioned in the bug by the poster, this doesn't happen every day, but more often than not.  So I guess it'll take a few days to make sure it works :)

---

### Post by LNick on 2007-04-03
Thanks MrC!

I implemented the fix here and did a stop/start on sysklogd and I haven't had a problem since!

---

### Post by cshepherd on 2007-04-11
It's done it again.  I've implemented the above suggestion but it only lasted a few days.  The server isn't under much load, especially at 0628 when it's doing the cron job.

/var/log/syslog.0
Apr 11 06:28:10 arnon exiting on signal 15

/var/log/syslog is zero bytes until I manually start the service again.

---

