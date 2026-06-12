---
title: "Landscape On-premisis under LXD"
date: 2018-03-25
forum: Ubuntu Cloud and Juju
---

### Post by seanmahrt on 2018-03-25
In the past I was able to install Landscape On-Premisis in an LXD container.  It stopped working so I want to reinstall it again, but I'm getting an issue with rabbitMQ (or a password issue, not sure).  I've destroyed the container a number of times and have other operational containers.  Is it not supported?  I didn't want to stand up a full virtual node, as it's much more taxing on the system.

Steps: ([https://landscape.canonical.com/set-up-on-prem](https://landscape.canonical.com/set-up-on-prem))

lxc create ubuntu:xenial landscape
lxc exec landscape bash
sudo add-apt-repository ppa:landscape/17.03
apt update
apt install landscape-server-quickstart

----
Job for rabbitmq-server.service failed because the control process exited with error code. See "systemctl status rabbitmq-server.service" and "journalctl -xe" for details.
invoke-rc.d: initscript rabbitmq-server, action "start" failed.
&#9679; rabbitmq-server.service - RabbitMQ Messaging Server
   Loaded: loaded (/lib/systemd/system/rabbitmq-server.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Mon 2018-03-26 03:12:31 UTC; 11ms ago
  Process: 1106 ExecStartPost=/usr/lib/rabbitmq/bin/rabbitmq-server-wait (code=exited, status=2)
  Process: 1101 ExecStart=/usr/sbin/rabbitmq-server (code=exited, status=1/FAILURE)
 Main PID: 1101 (code=exited, status=1/FAILURE)

Mar 26 03:12:27 landscape systemd[1]: Starting RabbitMQ Messaging Server...
Mar 26 03:12:28 landscape rabbitmq[1106]: Waiting for rabbit@landscape ...
Mar 26 03:12:28 landscape rabbitmq[1106]: pid is 1111 ...
Mar 26 03:12:30 landscape systemd[1]: rabbitmq-server.service: Main process exited, code=exited, status=1/FAILURE
Mar 26 03:12:31 landscape rabbitmq[1106]: Error: process_not_running
Mar 26 03:12:31 landscape systemd[1]: rabbitmq-server.service: Control process exited, code=exited status=2
Mar 26 03:12:31 landscape systemd[1]: Failed to start RabbitMQ Messaging Server.
Mar 26 03:12:31 landscape systemd[1]: rabbitmq-server.service: Unit entered failed state.
Mar 26 03:12:31 landscape systemd[1]: rabbitmq-server.service: Failed with result 'exit-code'.
dpkg: error processing package rabbitmq-server (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of landscape-server-quickstart:
 landscape-server-quickstart depends on rabbitmq-server (>= 2.2.0); however:
  Package rabbitmq-server is not configured yet.

dpkg: error processing package landscape-server-quickstart (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 rabbitmq-server
 landscape-server-quickstart

---

### Post by sam_vde on 2018-07-20
Host resolution might be the cause.

I have added "192.168.0.99 landscape" to /etc/hosts. I assume it tries to resolve the hostname without the domain at some point (the router would resolve the FQDN query).

---

### Post by trans-ix on 2018-07-25
We are having the same problem on a new Ubuntu 16.04.5 installation:

```

add-apt-repository ppa:landscape/18.03
apt-get update
apt-get install landscape-server-quickstart -y

.....

Job for rabbitmq-server.service failed because the control process exited with error code. See "systemctl status rabbitmq-server.service" and "journalctl -xe" for details.
invoke-rc.d: initscript rabbitmq-server, action "start" failed.
&#9679; rabbitmq-server.service - RabbitMQ Messaging Server
   Loaded: loaded (/lib/systemd/system/rabbitmq-server.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Wed 2018-07-25 14:41:03 CEST; 6ms ago
  Process: 23879 ExecStartPost=/usr/lib/rabbitmq/bin/rabbitmq-server-wait (code=exited, status=2)
  Process: 23878 ExecStart=/usr/sbin/rabbitmq-server (code=exited, status=1/FAILURE)
 Main PID: 23878 (code=exited, status=1/FAILURE)

Jul 25 14:41:01 landscape.trans-ix.net systemd[1]: Starting RabbitMQ Messaging Server...
Jul 25 14:41:01 landscape.trans-ix.net rabbitmq[23879]: Waiting for rabbit@landscape ...
Jul 25 14:41:01 landscape.trans-ix.net rabbitmq[23879]: pid is 23889 ...
Jul 25 14:41:02 landscape.trans-ix.net systemd[1]: rabbitmq-server.service: Main process exited, code=exited, status=1/FAILURE
Jul 25 14:41:03 landscape.trans-ix.net rabbitmq[23879]: Error: process_not_running
Jul 25 14:41:03 landscape.trans-ix.net systemd[1]: rabbitmq-server.service: Control process exited, code=exited status=2
Jul 25 14:41:03 landscape.trans-ix.net systemd[1]: Failed to start RabbitMQ Messaging Server.
Jul 25 14:41:03 landscape.trans-ix.net systemd[1]: rabbitmq-server.service: Unit entered failed state.
Jul 25 14:41:03 landscape.trans-ix.net systemd[1]: rabbitmq-server.service: Failed with result 'exit-code'.
dpkg: error processing package rabbitmq-server (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of landscape-server-quickstart:
 landscape-server-quickstart depends on rabbitmq-server (>= 2.2.0); however:
  Package rabbitmq-server is not configured yet.

dpkg: error processing package landscape-server-quickstart (--configure):
 dependency problems - leaving unconfigured
Setting up python-zope.browsermenu (4.0.0-0ubuntu2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up libnss3-nssdb (2:3.28.4-0ubuntu0.16.04.3) ...
Setting up libnss3:amd64 (2:3.28.4-0ubuntu0.16.04.3) ...
Setting up librados2 (10.2.9-0ubuntu0.16.04.1) ...
Setting up librbd1 (10.2.9-0ubuntu0.16.04.1) ...
Setting up libcephfs1 (10.2.9-0ubuntu0.16.04.1) ...
Setting up python-cephfs (10.2.9-0ubuntu0.16.04.1) ...
Setting up python-rados (10.2.9-0ubuntu0.16.04.1) ...
Setting up python-rbd (10.2.9-0ubuntu0.16.04.1) ...
Setting up libradosstriper1 (10.2.9-0ubuntu0.16.04.1) ...
Setting up librgw2 (10.2.9-0ubuntu0.16.04.1) ...
Setting up ceph-common (10.2.9-0ubuntu0.16.04.1) ...
[/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Setting up landscape-server (18.03-0ubuntu2) ...
Installing new version of config file /etc/landscape/service.conf ...
========================================================================
WARNING: schema upgrade disabled, services might not
restart after an upgrade.
If you are using the landscape-server-quickstart package,
setup will be handled for you automatically.
Otherwise, please run setup-landscape-server manually after
an upgrade, and read the documentation.
========================================================================
Job for landscape-package-search.service failed because the control process exited with error code. See "systemctl status landscape-package-search.service" and "journalctl -xe" for details.
landscape-package-search.service couldn't start.
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Errors were encountered while processing:
 rabbitmq-server
 landscape-server-quickstart
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

