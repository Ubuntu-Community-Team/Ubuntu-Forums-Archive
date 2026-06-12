---
title: "[SOLVED] SSH Problem"
date: 2008-11-14
forum: Server Platforms
---

### Post by scottuss on 2008-11-14
Hi everyone,

I have a problem with 8.10 server, the problem is that everything works great on the server (ssh is awesome!) but when I leave the machine on overnight the next day I have to reboot it as I cannot ssh in. The server seems to be running and going over the logs there seems to be no issues. The only thing I can see is that could be a problem are these entries:

```
Nov 14 06:40:01 my-server console-kit-daemon[16105]: CRITICAL: cannot initialize libpolkit 

Nov 14 06:40:01 my-server /USR/SBIN/CRON[16168]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

Nov 14 06:40:02 my-server CRON[16102]: Sigfile not found

Nov 14 13:47:07 my-server syslogd 1.5.0#2ubuntu6: restart.
```

Clearly the last entry is when I restarted the server manually.

Could this be the problem?

---

### Post by Iowan on 2008-11-14
When my (almost antique) server boots, I get nastygrams about ACPI and APIC.  I remember a few versions ago when someone had a problem with an ethernet card and one of these settings. Otherwise, I'd wonder about a power saving setting in BIOS.

---

### Post by oneloveamaru on 2008-11-14
[https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/275432](https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/275432)

apt-get install policy-kit will fix that up for you

the sigfile not found is another problem I haven't seen.

---

### Post by scottuss on 2008-11-14
I've installed PolicyKit, and from looking around on Launchpad it looks as if it should have been installed by default but for some reason they didn't put it in :confused:

---

### Post by scottuss on 2008-11-15
Just in case anyone else has this issue, installing PolicyKit fixes it. I don't know how widespread this bug is but it's a show stopper as far as I'm concerned, it locked my entire server regularly!:(

---

### Post by dimitar_g_g on 2008-11-26
I have the same issue.
Just to be sure. Did it fix the locks?

---

### Post by scottuss on 2008-11-27
> **dimitar_g_g said:**
> I have the same issue.
Just to be sure. Did it fix the locks?

Yep, not had the problem since :)

---

