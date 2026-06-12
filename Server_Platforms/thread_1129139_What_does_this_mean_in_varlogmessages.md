---
title: "What does this mean in /var/log/messages"
date: 2009-04-18
forum: Server Platforms
---

### Post by gobstopper on 2009-04-18
Have just been checking my Ubuntu 8.04 server which I installed last week to run VMWare and took at look at the last 100 or so lines of /var/log/messages and they all look like this:-

Apr 18 13:57:45 dell-ubuntu -- MARK --
Apr 18 14:17:45 dell-ubuntu -- MARK --
Apr 18 14:37:45 dell-ubuntu -- MARK --
Apr 18 14:57:45 dell-ubuntu -- MARK --
Apr 18 15:17:45 dell-ubuntu -- MARK --
Apr 18 15:37:45 dell-ubuntu -- MARK --
Apr 18 15:57:45 dell-ubuntu -- MARK --

I've never seen this before and have no idea what it means.

Can anyone shed any light?

Thanks.

---

### Post by shel-hall on 2009-04-18
> **gobstopper said:**
> Have just been checking my Ubuntu 8.04 server which I installed last week to run VMWare and took at look at the last 100 or so lines of /var/log/messages and they all look like this:-

Apr 18 13:57:45 dell-ubuntu -- MARK --
Apr 18 14:17:45 dell-ubuntu -- MARK --
Apr 18 14:37:45 dell-ubuntu -- MARK --
Apr 18 14:57:45 dell-ubuntu -- MARK --
Apr 18 15:17:45 dell-ubuntu -- MARK --
Apr 18 15:37:45 dell-ubuntu -- MARK --
Apr 18 15:57:45 dell-ubuntu -- MARK --

I've never seen this before and have no idea what it means.

Can anyone shed any light?

Thanks.
It's tempting to say "Looks like you've been pwned by some guy named Mark," but I won't.

It's just the logging system marking time, so you can tell (a) that it's still running and (b) about when any non-timestamped items were logged.

Normal, nothing to worry about, and handy.

-Shel

---

### Post by Yashiro on 2009-04-18
It's normal but you can disable it if it really annoys you.

Editting the file */etc/default/syslogd *so the config line reads 
> SYSLOGD="-m0"
Disables the timestamps every 20mins.

---

### Post by gobstopper on 2009-04-19
Thanks, Yashiro.

As long as it's not a problem, I'm not too worried. Having just built the server with a new disk I didn't want to go head first into working with the virtual machines, only to have the whole thing crash down in a heap a week later.

Thanks again. :)

---

