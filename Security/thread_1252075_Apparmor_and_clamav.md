---
title: "Apparmor and clamav"
date: 2009-08-28
forum: Security
---

### Post by mohnkern on 2009-08-28
I've got a modified version of Ubuntu 8.04 installed with apparmor on it.

When I install clamav the install goes fine, but freshclam won't run, it generates an error about being unable to write to /var/clamav.

Apparmor is blocking it.

I've got clamav .95-1 installed from the backport, but my understanding is that .95-2 fixes this problem.

I'm trying to find a place I can pick up the .95-2 .deb files, or alternatively, does someone know how to configure apparmor to eliminate this problem?

---

### Post by XCan on 2009-08-28
Did you run freshclam with sudo btw?

---

### Post by mohnkern on 2009-08-28
> **XCan said:**
> Did you run freshclam with sudo btw?

Actually, run it while logged in as root.

---

### Post by rookcifer on 2009-08-28
```

sudo aa-logprof
```

This will allow you to configure AppArmor policy.  You will likely see a few warning messages about how AppArmor is blocking ClamAV, just go through there and click "allow" on any ClamAV warnings. Click "S" for save when done, and then type:
```

sudo /etc/init.d/apparmor restart 
```

---

### Post by nickweavers on 2009-10-06
I too am having trouble getting the daemon for clamav to run successfully. I can start it okay
```

root@myserver:/etc/clamav# /etc/init.d/clamav-daemon start
 * Starting ClamAV daemon clamd
   ...done.

```
But when I try to execute any commands I get an error:
```

root@myserver:/etc/clamav# clamd version
ERROR: LOCAL: Socket file /tmp/clamd.socket is in use by another process.
root@myserver:/etc/clamav# clamd ping
ERROR: LOCAL: Socket file /tmp/clamd.socket is in use by another process.

```

genprof does not seems to find a problem:
```

root@myserver:/etc/apparmor.d# genprof
Please enter the program to profile: /usr/sbin/clamd

Please start the application to be profiled in
another window and exercise its functionality now.

Once completed, select the "Scan" button below in
order to scan the system logs for AppArmor events.

For each AppArmor event, you will be given the
opportunity to choose whether the access should be
allowed or denied.

Profiling: /usr/sbin/clamd

[(S)can system log for SubDomain events] / (F)inish
Reading log entries from /var/log/messages.
Updating AppArmor profiles in /etc/apparmor.d.

```
Has anyone else had a similar problem and managed to solve it?

TIA,
Nick.

---

