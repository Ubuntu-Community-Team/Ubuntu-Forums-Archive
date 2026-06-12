---
title: "server showing 0 updates, but Cron job is reporting packages to be updated"
date: 2017-11-14
forum: Server Platforms
---

### Post by mastablasta on 2017-11-14
the setup is that security updates are applied automatically, but no the ones that need dis-upgrade. so i receive this kind of info on email and then trigger them manually:
```
apticron report [Tue, 14 Nov 2017 06:01:21 +0100]
========================================================================

apticron has detected that some packages need upgrading on:

        blekbox
        [ 192.168.1.9 ]

The following packages are currently pending an upgrade:

        perl 5.18.2-2ubuntu1.3
        perl-base 5.18.2-2ubuntu1.3
        perl-modules 5.18.2-2ubuntu1.3

========================================================================
Package Details: [I]"blah, blah, blah..."
[/I]========================================================================

You can perform the upgrade by issuing the command:

        apt-get dist-upgrade

as root on blekbox

```
however when i run apt-get dist-upgrade, the system reports there are no packages to update.

even if i run apt-get update first and then upgrade and/or dist-upgrade it still says 0 to update.

what could be causing this? HWE stack is enabled. 

Server OS: 14.04.5 LTS

---

### Post by ian-weisser on 2017-11-14
Here's an example using perl-modules

```
$ rmadison perl-modules
 perl-modules | 5.14.2-6ubuntu2   | precise          | all
 perl-modules | 5.14.2-6ubuntu2.5 | precise-security | all
 perl-modules | 5.14.2-6ubuntu2.5 | precise-updates  | all
 perl-modules | 5.18.2-2ubuntu1   | trusty           | all
 perl-modules | 5.18.2-2ubuntu1.3 | trusty-security  | all
 perl-modules | 5.18.2-2ubuntu1.3 | trusty-updates   | all
```

The new update was *also* a security update, so was already applied automatically

---

### Post by mastablasta on 2017-11-15
ok so just the message 

> You can perform the upgrade by issuing the command:

        apt-get dist-upgrade


as root on blekbox

is then standard for all emails regarding updates. never though of that...

---

