---
title: "Canonical internal error"
date: 2019-06-06
forum: Security
---

### Post by christon74 on 2019-06-06
Good morning fellow Ubunters ;) _ Just this morning I got this message:Canonical Livepatch has experienced an internal error. Please refer to [https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues](https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues) for further information.
I went there but got no further information. I mean nothing there gave me any hint about what I should do. Not even a brief description of this "internal error". Then I typed this into a terminal window: sudo canonical-livepatch status --verbose
Which gave this:
```
client-version: 9.3.0
machine-id: 7bc33508dca84dd39b7488f6b52d2666
machine-token: b2209fc545fd402ababae33682177590
architecture: x86_64
cpu-model: Intel(R) Core(TM)2 Duo CPU     E7500  @ 2.93GHz
last-check: 2019-06-05T20:33:53+02:00
boot-time: 2019-06-06T07:26:39+02:00
uptime: 18m14s
status:
- kernel: 4.15.0-51.55-generic
  running: true
  livepatch:
    checkState: check-failed
    patchState: nothing-to-apply
    version: ""
    fixes: ""
```
Is it really a very serious issue? Thanks in advance. Have a nice Thursday.

---

### Post by deadflowr on 2019-06-06
See what shows, if anything, in the logs
```
grep livepatch /var/log/syslog
```

---

### Post by matteo495 on 2019-06-06
Hi!
I have resolved this problem with a manual update of livepatch.
You have to run this command in a terminal:
```

sudo canonical-livepatch refresh

```
Maybe livepatch can't check for an update automatically (maybe for a temporary problem...)

EDIT:
After a reboot the error occurred again... so i've to run the manual update command on a terminal every time I reboot my PC:(.
I think that this error could be resolved by an update from canonical. Until you won't receive this update you have to do the same thing every time you power on your PC.

---

### Post by nulltosignin on 2019-06-06
Have the same issue with [**[COLOR=#000000]christon74[/COLOR]**]("https://ubuntuforums.org/member.php?u=1234372")
```
Canonical Livepatch has experienced an internal error. Please refer to https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues for further information.
```

sudo canonical-livepatch status --verbose
```
client-version: 9.2.1
machine-id: fe635606c50c489a8b93849b537a0af3
machine-token: 2209d2cec511433491cd868915b928bd
architecture: x86_64
cpu-model: Intel(R) Core(TM) i7-3930K CPU @ 3.20GHz
last-check: 2019-06-07T00:59:48+08:00
boot-time: 2019-06-07T01:02:19+08:00
uptime: 5m16s
status:
- kernel: 4.15.0-51.55-generic
  running: true
  livepatch:
    checkState: check-failed
    patchState: nothing-to-apply
    version: ""
    fixes: ""


```sudo canonical-livepatch refresh does not solve the issue. The error returns after a reboot.

grep livepatch /var/log/syslog
```
Jun  7 00:07:14 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed
Jun  7 00:07:14 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed
Jun  7 00:50:49 ubuntu-proton canonical-livepatch[1222]: stopping client daemon
Jun  7 00:50:49 ubuntu-proton canonical-livepatch[1222]: stopping service "mitigation loop"
Jun  7 00:50:49 ubuntu-proton systemd[1]: Stopping Service for snap application canonical-livepatch.canonical-livepatchd...
Jun  7 00:50:49 ubuntu-proton canonical-livepatch[1222]: service "mitigation loop" stopped
Jun  7 00:50:49 ubuntu-proton canonical-livepatch[1222]: stopping service "socket servers"
Jun  7 00:50:49 ubuntu-proton canonical-livepatch[1222]: while starting HTTP server: accept unix /var/snap/canonical-livepatch/74/livepatchd.sock: use of closed network connection
Jun  7 00:50:49 ubuntu-proton canonical-livepatch[1222]: while starting HTTP server: accept unix /var/snap/canonical-livepatch/74/livepatchd-priv.sock: use of closed network connection
Jun  7 00:50:49 ubuntu-proton canonical-livepatch[1222]: service "socket servers" stopped
Jun  7 00:50:49 ubuntu-proton canonical-livepatch[1222]: stopping service "refresh loop"
Jun  7 00:50:49 ubuntu-proton canonical-livepatch[1222]: service "refresh loop" stopped
Jun  7 00:50:49 ubuntu-proton canonical-livepatch[1222]: client daemon stopped
Jun  7 00:51:23 ubuntu-proton systemd[1]: Mounting Mount unit for canonical-livepatch, revision 54...
Jun  7 00:51:23 ubuntu-proton systemd[1]: Mounting Mount unit for canonical-livepatch, revision 58...
Jun  7 00:51:23 ubuntu-proton systemd[1]: Mounting Mount unit for canonical-livepatch, revision 74...
Jun  7 00:51:23 ubuntu-proton systemd[1]: Mounted Mount unit for canonical-livepatch, revision 54.
Jun  7 00:51:23 ubuntu-proton systemd[1]: Mounted Mount unit for canonical-livepatch, revision 58.
Jun  7 00:51:23 ubuntu-proton systemd[1]: Mounted Mount unit for canonical-livepatch, revision 74.
Jun  7 00:51:26 ubuntu-proton systemd[1]: Started Service for snap application canonical-livepatch.canonical-livepatchd.
Jun  7 00:51:36 ubuntu-proton canonical-livepatch[1222]: starting client daemon version 9.2.1
Jun  7 00:51:36 ubuntu-proton canonical-livepatch[1222]: starting svc "mitigation loop"
Jun  7 00:51:36 ubuntu-proton canonical-livepatch[1222]: service "mitigation loop" started
Jun  7 00:51:36 ubuntu-proton canonical-livepatch[1222]: starting svc "socket servers"
Jun  7 00:51:36 ubuntu-proton canonical-livepatch[1222]: service "socket servers" started
Jun  7 00:51:36 ubuntu-proton canonical-livepatch[1222]: starting svc "refresh loop"
Jun  7 00:51:36 ubuntu-proton canonical-livepatch[1222]: service "refresh loop" started
Jun  7 00:51:36 ubuntu-proton canonical-livepatch[1222]: client daemon started
Jun  7 00:51:36 ubuntu-proton canonical-livepatch[1222]: Client.Check
Jun  7 00:51:36 ubuntu-proton canonical-livepatch[1222]: Checking with livepatch service.
Jun  7 00:51:36 ubuntu-proton canonical-livepatch[1222]: No payload available.
Jun  7 00:51:36 ubuntu-proton canonical-livepatch[1222]: during refresh: cannot check: cannot send status to server: cannot send request: Put https://livepatch.canonical.com/api/machine/fe635606c50c489a8b93849b537a0af3: dial tcp: lookup livepatch.canonical.com: no such host
Jun  7 00:52:45 ubuntu-proton gnome-shell[1576]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.67/org/ayatana/NotificationItem/livepatch
Jun  7 00:52:48 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed
Jun  7 00:52:48 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed
Jun  7 00:52:48 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed
Jun  7 00:52:59 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed
Jun  7 00:53:08 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed
Jun  7 00:55:05 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed
Jun  7 00:59:47 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed
Jun  7 00:59:47 ubuntu-proton canonical-livepatch[1222]: Client.Check
Jun  7 00:59:47 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed
Jun  7 00:59:47 ubuntu-proton canonical-livepatch[1222]: Checking with livepatch service.
Jun  7 00:59:48 ubuntu-proton canonical-livepatch[1222]: updating last-check
Jun  7 00:59:48 ubuntu-proton canonical-livepatch[1222]: touched last check
Jun  7 00:59:48 ubuntu-proton canonical-livepatch[1222]: No updates available at this time.
Jun  7 00:59:48 ubuntu-proton canonical-livepatch[1222]: No payload available.
Jun  7 01:02:33 ubuntu-proton systemd[1]: Mounting Mount unit for canonical-livepatch, revision 74...
Jun  7 01:02:33 ubuntu-proton systemd[1]: Mounting Mount unit for canonical-livepatch, revision 58...
Jun  7 01:02:33 ubuntu-proton systemd[1]: Mounting Mount unit for canonical-livepatch, revision 54...
Jun  7 01:02:33 ubuntu-proton systemd[1]: Mounted Mount unit for canonical-livepatch, revision 74.
Jun  7 01:02:33 ubuntu-proton systemd[1]: Mounted Mount unit for canonical-livepatch, revision 58.
Jun  7 01:02:33 ubuntu-proton systemd[1]: Mounted Mount unit for canonical-livepatch, revision 54.
Jun  7 01:02:35 ubuntu-proton systemd[1]: Started Service for snap application canonical-livepatch.canonical-livepatchd.
Jun  7 01:02:44 ubuntu-proton canonical-livepatch[1222]: starting client daemon version 9.2.1
Jun  7 01:02:44 ubuntu-proton canonical-livepatch[1222]: starting svc "mitigation loop"
Jun  7 01:02:44 ubuntu-proton canonical-livepatch[1222]: service "mitigation loop" started
Jun  7 01:02:44 ubuntu-proton canonical-livepatch[1222]: starting svc "socket servers"
Jun  7 01:02:44 ubuntu-proton canonical-livepatch[1222]: service "socket servers" started
Jun  7 01:02:44 ubuntu-proton canonical-livepatch[1222]: starting svc "refresh loop"
Jun  7 01:02:44 ubuntu-proton canonical-livepatch[1222]: service "refresh loop" started
Jun  7 01:02:44 ubuntu-proton canonical-livepatch[1222]: client daemon started
Jun  7 01:02:44 ubuntu-proton canonical-livepatch[1222]: Client.Check
Jun  7 01:02:44 ubuntu-proton canonical-livepatch[1222]: Checking with livepatch service.
Jun  7 01:02:44 ubuntu-proton canonical-livepatch[1222]: No payload available.
Jun  7 01:02:44 ubuntu-proton canonical-livepatch[1222]: during refresh: cannot check: cannot send status to server: cannot send request: Put https://livepatch.canonical.com/api/machine/fe635606c50c489a8b93849b537a0af3: dial tcp: lookup livepatch.canonical.com: no such host
Jun  7 01:03:33 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed
Jun  7 01:03:46 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed
Jun  7 01:03:54 ubuntu-proton gnome-shell[1572]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.70/org/ayatana/NotificationItem/livepatch
Jun  7 01:03:56 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed
Jun  7 01:03:56 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed
Jun  7 01:03:56 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed
Jun  7 01:03:56 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed
Jun  7 01:05:25 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed
Jun  7 01:07:35 ubuntu-proton canonical-livepatch[1222]: error in livepatch check state: check-failed

```

---

### Post by QIII on 2019-06-06
@matteo495 and nulltosignin:

Please start your own threads rather than hijacking christon74's.  You may be experiencing similar symptoms but have entirely different underlying causes.

Please allow christon74 to get uninterrupted personal support.

---

### Post by benboruff on 2019-06-07
Same problem. I fixed this by disabling Livepatch, then re-enabling with a new token. I have since rebooted and all is well.

---

### Post by pyjnet2 on 2019-06-10
Hello,

I get a similar issue since some days : "Canonical Livepatch has experienced an internal error. Please refer to [https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues](https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues) for further information."

root@orion:/home/orion# sudo canonical-livepatch status --verbose
client-version: 9.3.0
machine-id: ff6d35bec5a34e41a127a8d8a9b8881f
machine-token: fc3fe0b767e8489bb7214397acb7a27a
architecture: x86_64
cpu-model: Intel(R) Core(TM) i5-7300HQ CPU @ 2.50GHz
last-check: 2019-06-09T20:12:45+02:00
boot-time: 2019-06-10T10:43:00+02:00
uptime: 25m24s
status:
- kernel: 4.18.0-21.22~18.04.1-generic
  running: true
  livepatch:
    checkState: check-failed
    patchState: nothing-to-apply
    version: ""
    fixes: ""


root@orion:/home/orion# grep livepatch /var/log/syslog
Jun 10 10:48:25 orion canonical-livepatch[1210]: error in livepatch check state: check-failed
Jun 10 10:48:25 orion canonical-livepatch[1210]: error in livepatch check state: check-failed
root@orion:/home/orion# 

disable enable seems to solve but the issue appear again after a reboot.

---

### Post by ijonfryderyk on 2019-06-13
Hi,
I have the same problem. I have to do ```
sudo canonical-livepatch refresh
``` after every reboot. 

```
client-version: 9.3.0
machine-id: 403ad3c8849a4f5792dae60b0689104b
machine-token: 5c438d420e8c44f6a2594e96fd4c92c7
architecture: x86_64
cpu-model: Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
last-check: 2019-06-13T00:10:56+02:00
boot-time: 2019-06-13T10:53:20+02:00
uptime: 25m27s
status:
- kernel: 4.18.0-21.22~18.04.1-generic
  running: true
  livepatch:
    checkState: check-failed
    patchState: nothing-to-apply
    version: ""
    fixes: ""
```

---

### Post by jcpfuntner on 2019-06-15
> **matteo495 said:**
> Hi!
I have resolved this problem with a manual update of livepatch.
You have to run this command in a terminal:
```

sudo canonical-livepatch refresh

```
...


This command worked for me too.  I just did a couple of minutes ago but the livepatch icon on the top of the desktop has a green checkbox now so I'm happy.

---

### Post by PaulW2U on 2019-06-17
> **christon74 said:**
> Just this morning I got this message:Canonical Livepatch has experienced an internal error.
If the matter hasn't resolved itself by now then you should probably report a bug against Livepatch: [https://bugs.launchpad.net/canonical-livepatch-client/+filebug](https://bugs.launchpad.net/canonical-livepatch-client/+filebug).

I can't do this on your behalf as although I see a checkstate of "check-failed" each time I boot I'm not currently seeing any error messages about an internal error.

---

