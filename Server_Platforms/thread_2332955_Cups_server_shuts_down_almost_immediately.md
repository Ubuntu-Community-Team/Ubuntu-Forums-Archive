---
title: "Cups server shuts down almost immediately"
date: 2016-08-05
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2016-08-05
Server 16.04. My print server service keeps shutting down with this. If I restart it lasts for a few minutes then this comes through the log again and the service shows as 
```

systemctl status cups
&#9679; cups.service - CUPS Scheduler
   Loaded: loaded (/lib/systemd/system/cups.service; enabled; vendor preset: ena
   Active: inactive (dead) since Fri 2016-08-05 13:34:22 MST; 46s ago
     Docs: man:cupsd(8)
  Process: 9462 ExecStart=/usr/sbin/cupsd -l (code=exited, status=0/SUCCESS)
 Main PID: 9462 (code=exited, status=0/SUCCESS)


Aug 05 13:32:51 myserver systemd[1]: Started CUPS Scheduler.

```

Cups error log from /var/log/cups/error_log

```
I [05/Aug/2016:13:33:22 -0700] Saving subscriptions.conf...
D [05/Aug/2016:13:33:22 -0700] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
I [05/Aug/2016:13:33:22 -0700] Expiring subscriptions...
I [05/Aug/2016:13:34:22 -0700] Printer sharing is off and there are no jobs pending, will restart on demand.
I [05/Aug/2016:13:34:22 -0700] Scheduler shutting down normally.
D [05/Aug/2016:13:34:22 -0700] cupsdMarkDirty(----S)
D [05/Aug/2016:13:34:22 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Not busy"
I [05/Aug/2016:13:34:22 -0700] Saving subscriptions.conf...
D [05/Aug/2016:13:34:22 -0700] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
D [05/Aug/2016:13:34:22 -0700] Creating keep-alive file "/var/cache/cups/org.cups.cupsd".
I [05/Aug/2016:13:34:22 -0700] Saving job.cache...
D [05/Aug/2016:13:34:22 -0700] cupsdStopSelect()

```

---

### Post by blitzahei on 2016-12-06
Bump...

I am also suffering with this issue. Does anyone have any ideas?

Similar log entries:

```

I [06/Dec/2016:08:28:21 +0000] Printer sharing is off and there are no jobs pending, will restart on demand.
I [06/Dec/2016:08:28:21 +0000] Scheduler shutting down normally.
d [06/Dec/2016:08:28:21 +0000] cupsdAddEvent(event=server-stopped, dest=(nil)(), job=(nil)(0), text="Scheduler shutting down normally.", ...)
D [06/Dec/2016:08:28:21 +0000] Discarding unused server-stopped event...
d [06/Dec/2016:08:28:21 +0000] cupsdCloseAllClients() Clients=0
d [06/Dec/2016:08:28:21 +0000] cupsdStopListening: closing all listen sockets.
d [06/Dec/2016:08:28:21 +0000] cupsdPauseListening: Clearing input bits...
d [06/Dec/2016:08:28:21 +0000] cupsdRemoveSelect(fd=10)
d [06/Dec/2016:08:28:21 +0000] cupsdRemoveSelect(fd=11)
d [06/Dec/2016:08:28:21 +0000] cupsdRemoveSelect(fd=3)
d [06/Dec/2016:08:28:21 +0000] cupsdRemoveSelect(fd=12)
d [06/Dec/2016:08:28:21 +0000] cupsdDeleteProfile(profile="(null)")
D [06/Dec/2016:08:28:21 +0000] Creating keep-alive file "/var/cache/cups/org.cups.cupsd".
I [06/Dec/2016:08:28:21 +0000] Saving job.cache...
D [06/Dec/2016:08:28:21 +0000] cupsdStopSelect()

```


EDIT!

Found this: [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1598300](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1598300)

---

