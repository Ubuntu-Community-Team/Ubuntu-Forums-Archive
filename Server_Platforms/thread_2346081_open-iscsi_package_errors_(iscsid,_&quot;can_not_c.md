---
title: "open-iscsi package errors (iscsid, &quot;can not create NETLINK_ISCSI socket&quot;)"
date: 2016-12-11
forum: Server Platforms
---

### Post by michaeltyson on 2016-12-11
Hi guys,

I've been seeing some minor-but-annoying errors lately from iscsi (which I'm not using at all) whenever I interact with apt:

```
Setting up open-iscsi (2.0.873+git0.3b4b4500-14ubuntu3.2) ...
Job for iscsid.service failed because a configured resource limit was exceeded. See "systemctl status iscsid.service" and "journalctl -xe" for details.
invoke-rc.d: initscript iscsid, action "restart" failed.
dpkg: error processing package open-iscsi (--configure):
 subprocess installed post-installation script returned error exit status 1

```

The underlying error is:

```
Dec 05 16:13:07 nettle iscsid[13987]: iSCSI logger with pid=13990 started!
Dec 05 16:13:07 nettle systemd[1]: iscsid.service: Failed to read PID from file 
Dec 05 16:13:07 nettle iscsid[13990]: iSCSI daemon with pid=13991 started!
Dec 05 16:13:07 nettle systemd[1]: iscsid.service: Daemon never wrote its PID fi
Dec 05 16:13:07 nettle iscsid[13990]: can not create NETLINK_ISCSI socket
Dec 05 16:13:07 nettle systemd[1]: Failed to start iSCSI initiator daemon (iscsi)

```

Can't put my finger right on when it started - it was a recent set of updates. 

Seems open-iscsi is a dependency of ubuntu-server, so I can't remove it without getting rid of ubuntu-server (which has a package description saying "It is also used to help ensure proper upgrades, so it is recommended that it not be removed.").

Anyone know a quick fix?

---

### Post by Graham_Willis on 2016-12-11
What's the output of **uname -a; cat /etc/lsb-release**?

---

### Post by michaeltyson on 2016-12-12
```
Linux nettle 4.8.6-x86_64-linode78 #1 SMP Tue Nov 1 14:51:21 EDT 2016 x86_64 x86_64 x86_64 GNU/Linux
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"

```

(I've actually since removed open-iscsi and ubuntu-server, despite the warnings -- I think it's more trouble than its worth)

---

### Post by johan-ehnberg on 2016-12-22
See the bug report here:
[https://bugs.launchpad.net/ubuntu/+source/open-iscsi/+bug/1651497](https://bugs.launchpad.net/ubuntu/+source/open-iscsi/+bug/1651497)

---

### Post by michaeltyson on 2016-12-22
Thanks for the heads up! Looks close - the bug notes that the issue is transient, whereas it seems to be permanent in my setup.

---

### Post by collinmachine on 2017-05-17
I am still getting this same error. Has anyone found a fix yet?

---

