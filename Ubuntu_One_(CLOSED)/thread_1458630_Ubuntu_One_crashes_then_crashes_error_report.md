---
title: "Ubuntu One crashes then crashes error report"
date: 2010-04-20
forum: Ubuntu One (CLOSED)
---

### Post by gvernold on 2010-04-20
Title says it all really but I'm trying to find out where I can get some error logs out of this.

I'm running Ubuntu 10.04 32bit, installed from desktop CD. Each time I boot up Ubuntu One issues a crash notice but then the error reporting back to Ubuntu crashes too. I've tried looking through as many log files as I can find to find errors relating to this boot it seems everything is normal.

I can start Ubuntu One by clicking on it normally on the task bar and it runs fine but the error message on startup is getting annoying and I wanted to send a bug report in, but have nothing to back it up with. Anybody tell me where I can find error logs for Ubuntu One?

---

### Post by joshuahoover on 2010-04-20
> **gvernold said:**
> Title says it all really but I'm trying to find out where I can get some error logs out of this.

I'm running Ubuntu 10.04 32bit, installed from desktop CD. Each time I boot up Ubuntu One issues a crash notice but then the error reporting back to Ubuntu crashes too. I've tried looking through as many log files as I can find to find errors relating to this boot it seems everything is normal.

I can start Ubuntu One by clicking on it normally on the task bar and it runs fine but the error message on startup is getting annoying and I wanted to send a bug report in, but have nothing to back it up with. Anybody tell me where I can find error logs for Ubuntu One?

Sorry to hear Ubuntu One is crashing on you. Do you catch what the crash message says? Are you all up-to-date on the latest software? If not, please be sure to install all the latest Lucid updates, as we've recently released some important fixes related to Ubuntu One.

You can log files at ~/.cache/ubuntuone/log and ~/.cache/desktop-couch/log My guess is the bug is related to desktop-couch-service and should be resolved with the latest update. But it's hard to say for sure without knowing what the crash message is saying (i.e. ubuntuone-login, desktop-couch-service, etc.)

Thank you,

Joshua

---

### Post by gvernold on 2010-04-21
Yep thanks for that. Latest update did seem to correct this issue.

---

### Post by joshuahoover on 2010-04-21
> **gvernold said:**
> Yep thanks for that. Latest update did seem to correct this issue.

Excellent! It's always good to hear that an update fixes a problem. :) Thank you for taking the time to post an update here.

---

