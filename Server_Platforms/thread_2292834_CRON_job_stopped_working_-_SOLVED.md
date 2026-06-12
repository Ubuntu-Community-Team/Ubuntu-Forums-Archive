---
title: "CRON job stopped working - SOLVED"
date: 2015-08-31
forum: Server Platforms
---

### Post by Jon_Fear on 2015-08-31
Hi everyone

We have a server that runs U14.04.3 LTS.

We had a cron script working until a recent batch of updates. The contents are:

csv.csv {
  su vrs vrs
  daily
  dateext
  compress
  postrotate
    pkill -HUP python3.4
  endscript
  rotate 30
}

This worked well but now returns:

/etc/cron.daily/mlat-server:
run-parts: failed to exec /etc/cron.daily/mlat-server: Exec format error
run-parts: /etc/cron.daily/mlat-server exited with return code 1

We have not been able to work out why this has stopped working.

Can anyone throw some light on this?

Thanks

Jon

MLAT Radar Admin Support
[www.mlat-radar.net]("http://www.mlat-radar.net")

---

### Post by howefield on 2015-08-31
Thread moved to the "*Server Platforms*" forum.

---

### Post by SeijiSensei on 2015-08-31
That looks like a definition file for the logrotate program.  It certainly isn't executable by itself. We need to see the contents of the mlat-server file.

---

### Post by ian-weisser on 2015-08-31
> **Jon_Fear said:**
> run-parts: failed to exec /etc/cron.daily/mlat-server: **Exec format error**

An 'exec format error' usually means that the system cannot figure which interpreter to use on a file (shell, python, perl, whatever)
Add a shebang line (#!/bin/sh) to the top of /etc/cron.daily/mlat-server.

---

### Post by Jon_Fear on 2015-08-31
Hi

Well there's the thing. That is the complete contents of the mlat-server file which is currently residing in /etc/cron.daily. In addition we have tried adding the shebang to the top of the file and that screws the file completely. The output starts complaining of all sorts. This file listed above is the same as the file in /etc/logrotate.d.

Hence the reason for asking here, google is meant to be our friend, in this case not...!

Thanks for the quick replies.

Jon

---

### Post by SeijiSensei on 2015-08-31
By default, logrotate runs out of /etc/cron.daily so you shouldn't need any special task.  It should just read the file in /etc/logrotate.d/ when logrotate runs each day.  Try deleting mlat-server from cron.daily and see what happens tomorrow.

---

### Post by Jon_Fear on 2015-09-01
Thanks for the tip, I have removed the offending file, let's see what happens tonight!

Jon

---

### Post by Jon_Fear on 2015-09-02
> **SeijiSensei said:**
> By default, logrotate runs out of /etc/cron.daily so you shouldn't need any special task.  It should just read the file in /etc/logrotate.d/ when logrotate runs each day.  Try deleting mlat-server from cron.daily and see what happens tomorrow.


Thank you for the advice. That worked a treat, now working correctly.

Jon

---

