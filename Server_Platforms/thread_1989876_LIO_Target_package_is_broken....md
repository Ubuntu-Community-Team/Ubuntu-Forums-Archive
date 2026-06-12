---
title: "LIO Target package is broken..."
date: 2012-05-28
forum: Server Platforms
---

### Post by kevin11951 on 2012-05-28
I submitted a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/targetcli/+bug/1000490](https://bugs.launchpad.net/ubuntu/+source/targetcli/+bug/1000490)

> 
== OS Details ==

Distributor ID: Ubuntu
Description: Ubuntu 12.04 LTS
Release: 12.04
Codename: precise

Linux san 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

== Problem ==

After installing the "targetcli" package on a fresh install of Ubuntu 12.04 LTS, it complains with the following error:

ImportError: No module named urwid

This is due to the "python-urwid" package not being included as a dependency.

== Reproduction ==

After installing the "targetcli" package, simply run the following command:

# targetcli

/> cd

[...]
ImportError: No module named urwid

/>

== Solution ==

Please include "python-urwid" as a dependency of the "targetcli" package.


This bug is not that serious considering that most admins would know how to install the "python-urwid" themselves, but I think that this "paper cut" would leave a bad taste in their mouths.  This doesn't seem terribly difficult to fix.  So why doesn't Canonical fix it?

> LIO Target is the new standard for Linux iSCSI target support, and Ubuntu 12.04 is the latest LTS release for enterprise use. This combination makes any flaw in the LIO Target application on Ubuntu a major issue.

**I just wanted to raise awareness of a bug that hasn't gotten any attention yet.  If this bug affects you in any way, please mark it as such so that we can get this REALLY simply bug fixed soon.**

---

