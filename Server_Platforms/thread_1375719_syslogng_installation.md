---
title: "syslogng installation"
date: 2010-01-08
forum: Server Platforms
---

### Post by mansonthomas on 2010-01-08
Hi,

  I'd like to centralize the logs of all my servers on one server.
  I've heard of syslog-ng.

  When I simulate the install, it says it brokes "ubuntu-minimal" package :

[PHP]aptitude -s install syslog-ng
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
The following packages are BROKEN:
  ubuntu-minimal
The following NEW packages will be installed:
  libevtlog0{a} syslog-ng
The following packages will be REMOVED:
  rsyslog{a}
0 packages upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
Need to get 138kB of archives. After unpacking 221kB will be freed.
The following packages have unmet dependencies:
  ubuntu-minimal: Depends: rsyslog but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-minimal

Score is 115

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.[/PHP]

How do you feel about it ? 
I would say it would be safe to do that but I'm not sure.

Thomas.

---

### Post by eldar40k on 2010-01-08
That's probably because ubuntu uses the rsyslog logging daemon by default, and installing syslog-ng removes rsyslog (since they both do the same thing). ubuntu-minimal depends on rsyslog, so it will be broken when you remove rsyslog, but that doesn't really matter because it is only a meta package. 

Please correct me if I'm wrong.

---

