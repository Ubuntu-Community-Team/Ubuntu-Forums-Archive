---
title: "Auto Power Cycles"
date: 2013-02-24
forum: Server Platforms
---

### Post by chrisguk on 2013-02-24
My Ubuntu Server checks for updates each hour and installs them automatically.  Sometimes the updates require that the server is rebooted in order to implement the update respectively.

Is there a feasible way by the use of CRON to power cycle the server at lets say 4am to take care of this issue.  Also was is the industry norm in this situation?

---

### Post by howefield on 2013-02-24
Thread moved to the "*Server Platforms*" forum.

---

### Post by matt_symes on 2013-02-24
Hi

I see no reason why you can't reboot using cron. As long as you set the server to start all the services you need.

I don't think it's standard though. It's mostly kernel updates that need a reboot and you can use kslice to keep the server going with no reboot.

There's a paid version by oracle

[http://www.ksplice.com/uptrack/download-ubuntu](http://www.ksplice.com/uptrack/download-ubuntu)

but there is also an free version but you will have to set it up yourself.

[https://wiki.ubuntu.com/Ksplice](https://wiki.ubuntu.com/Ksplice)
[http://packages.ubuntu.com/precise/ksplice](http://packages.ubuntu.com/precise/ksplice)

Kind regards

---

### Post by chrisguk on 2013-02-24
I notice that ksplice only mentions Ubuntu desktop, is this package ok for server versions too?

---

### Post by matt_symes on 2013-02-24
Hi

> **chrisguk said:**
> I notice that ksplice only mentions Ubuntu desktop, is this package ok for server versions too?

It's actually for servers really so there is no problem there.

Kind regards

---

### Post by LHammonds on 2013-02-25
I use a script to automate my security updates (and log them).  I do not automate my reboots except for one server that runs a java app that handles memory poorly forcing me to reboot daily.

I also have an operator menu that allows any of my staff to log into a Linux server and select various tasks such as stopping and restarting primary services or to reboot the server.

Either way, I call a special reboot script that ensures the services for that particular server are shutdown cleanly and file/memory cache is written to disk (sync command) and then it issues the reboot.

I have those scripts documented in the Ubuntu Server thread in my signature.

**EDIT:** Oh, forgot to mention, I try not to automate reboots because I have seen issues with grub updates messing up configs where the server will not boot up properly...so I'm hesitant to have all my servers reboot and me getting blind-sided by all my servers not running in the morning.  So I typically pick a non-critical server to reboot 1st after an update.  If it works, I reboot the others one at a time.  My Nagios monitoring server lets me know when I need to reboot my servers.

LHammonds

---

### Post by matt_symes on 2013-02-25
Hi

I agree that scripts are a good way to control a reboot.

@OP you never said what your server was for.

Kind regards

---

