---
title: "warnings disabling systemd services on 16.04"
date: 2017-06-21
forum: Server Platforms
---

### Post by inflatablemouse on 2017-06-21
I've inherited a bunch of servers running Ubuntu server 16.04. The systems are all cloned from the same template and all are running unnecessary services that I want to stop and disable (yes, I've recreated all host ssh keys, in case you're wondering :P).

When I stopped and disabled some of them, I got the following output for which I can find more info, but it seems to vary depending on the service and what the OP wants to accomplish, and that makes it confusing for me to find relevant info for myself. Figured I'd ask to be sure, better safe than sorry since these servers are production servers and in use. The example below is a dedicated server providing a search engine backend for web servers (elastic search, to be precise).

```
root@server07:/# systemctl stop iscsi.serviceroot@server07:/# systemctl disable iscsi.service
Removed symlink /etc/systemd/system/iscsi.service.
Removed symlink /etc/systemd/system/sysinit.target.wants/open-iscsi.service.
root@server07:/# systemctl stop iscsid.service
root@server07:/# systemctl disable iscsid.service
Synchronizing state of iscsid.service with SysV init with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install disable iscsid
insserv: warning: current start runlevel(s) (empty) of script `iscsid' overrides LSB defaults (S).
insserv: warning: current stop runlevel(s) (0 1 6 S) of script `iscsid' overrides LSB defaults (0 1 6).
root@server07:/# systemctl stop lxcfs.service
root@server07:/# systemctl disable lxcfs.service
Synchronizing state of lxcfs.service with SysV init with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install disable lxcfs
insserv: warning: current start runlevel(s) (empty) of script `lxcfs' overrides LSB defaults (2 3 4 5).
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `lxcfs' overrides LSB defaults (0 1 6).
root@server07:/# systemctl stop lxd-containers.service
root@server07:/# systemctl disable lxd-containers.service
Removed symlink /etc/systemd/system/multi-user.target.wants/lxd-containers.service.
root@server07:/#
```

My question here is, what (if anything) should I do with the warnings 'insserv' spits out?

Second question, the list of services enabled and running that I think I can and want to disable is:

```
iscsi.service                              enabled
iscsid.service                             enabled
lxcfs.service                              enabled
lxd-containers.service                     enabled
mysql.service                              enabled
open-iscsi.service                         enabled
snapd.autoimport.service                   enabled
snapd.service                              enabled
snapd.system-shutdown.service              enabled
unattended-upgrades.service                enabled
lxd.socket                                 enabled
snapd.socket                               enabled
apt-daily.timer                            enabled
snapd.refresh.timer                        enabled
```

Is there anything specific about these services that I need to be aware of? I've checked each of them and more info is below.

Last but not least, unattended-upgrades.service and apt-daily.timer I want to disable because we control our updates manually during a service window agreed upon with the customer, so that updates are installed in a controlled fashion, followed by a reboot and checked afterwards. However, I'm not sure if apt-daily.timer does more than that and should be left enabled?

I would appreciate some feedback on these, thanks in advance!

I checked iscsi and it is not in use:

```
**# ls/dev/disk/by-path/**
pci-0000:00:07.1-ata-1              pci-0000:00:10.0-scsi-0:0:0:0-part2 pci-0000:00:10.0-scsi-0:0:1:0-part1
pci-0000:00:10.0-scsi-0:0:0:0        pci-0000:00:10.0-scsi-0:0:0:0-part5
pci-0000:00:10.0-scsi-0:0:0:0-part1  pci-0000:00:10.0-scsi-0:0:1:0
 
**#iscsiadm -m session -P 3**
iSCSI Transport Class version 2.0-870
version 2.0-873
iscsiadm: **No active sessions.**

```

I checked **lxc list **and it comes up empty:```
+------+-------+------+------+------+-----------+
| NAME | STATE | IPV4 | IPV6 | TYPE |SNAPSHOTS |
+------+-------+------+------+------+-----------+

```

MySQL does not have any databases:

**mysql> show databases;**
```
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+

```

Concerning snapd, 'snap list' returns nothing.

---

### Post by inflatablemouse on 2017-06-22
Can no one answer the inssrv warning question? :(

---

### Post by deadflowr on 2017-06-22
You can probably parse out something about the innserv warnings from here:
[https://wiki.debian.org/LSBInitScripts/DependencyBasedBoot]("https://wiki.debian.org/LSBInitScripts/DependencyBasedBoot")

Outside of that, I see nothing in your list that would be mourned if turned off.
No snaps and no plans on installing snaps means you can go ahead and turn that off.
No containers with no prospects of installing or running any containers would mean no need to have that up and running either.
And since you have obvious contractual needs to not have the updater mechanism running then disabling those is fine as well (the unattended-upgrades and apt-daily-timer services)

---

### Post by inflatablemouse on 2017-06-23
> **deadflowr said:**
> You can probably parse out something about the innserv warnings from here:
[https://wiki.debian.org/LSBInitScripts/DependencyBasedBoot](https://wiki.debian.org/LSBInitScripts/DependencyBasedBoot)

Outside of that, I see nothing in your list that would be mourned if turned off.
No snaps and no plans on installing snaps means you can go ahead and turn that off.
No containers with no prospects of installing or running any containers would mean no need to have that up and running either.
And since you have obvious contractual needs to not have the updater mechanism running then disabling those is fine as well (the unattended-upgrades and apt-daily-timer services)

Thanks, appreciate your help. The debian page gives some general info but not enough for me to actually solve the problem.

Almost all those services I want to disable spit out those warning messages and I've been digging for more info, but there is actually very little practical help to be found. They are mostly about other services that have a 'requiredby' tag in systemd and I found quite a few that actually end up on bugs.debian.org, without a solution or a fix.

/etc/rc*.d/ contain links to the services I am trying to disable. For instance, mysql which has no 'requiredby' also spits out those double insserv messages. rc*.d/ is full of mysql links still. Systemd says those services are disabled, but after a reboot earlier this week, they are still running and can be stopped with /etc/init.d/<service> stop.

I decided to leave the systems as they are, as my time here is limited (a few more days at most). Still, I'm interested to know what is going on but I doubt I'll have the time to fix it for this customer.

Thanks!

---

