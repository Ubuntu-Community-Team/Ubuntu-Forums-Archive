---
title: "lightdm/dbus error with 16.04"
date: 2016-02-06
forum: Ubuntu Development Version
---

### Post by dave0109 on 2016-02-06
Background: I installed 16.04 alpha 2 last weekend, which included installing 4.4 of the kernel in order to get the wifi card working (Dell XPS13 with Broadcom 4350).  At some point, one set of updates resulted in a few errors, which I've mostly resolved bar this one: lightdm is in a "half-configured" state...
```

$ dpkg -l | grep -v "^ii"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                  Version                                    Architecture Description
+++-=====================================-==========================================-============-================================================================================
iF  lightdm                               1.17.5-0ubuntu2                            amd64        Display Manager

```

If I try to finish off the package installation, I get...
```

$ sudo dpkg --configure lightdm
Setting up lightdm (1.17.5-0ubuntu2) ...
insserv: Service dbus has to be enabled to start service lightdm
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package lightdm (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 lightdm

```

As far as I can tell, dbus is running (at least, the part that dbus-monitor can monitor).  There don't appear to be any noticeable side-effects (system boots OK, I get a login screen, etc), the only issue that I've seen is the result of doing any updates is an "error", at which point checking for any packages with issues simply shows lightdm.

That said, I'd like to get this fixed, but I don't know where to go from here.

---

### Post by zika on 2016-02-06
The answer (I suppose) lies in those few other errors You mention. It would be helpfull if You would post tail of /var/log/apt/history*.log and /var/log/apt/term.*log that are pertinent to period just before insserv protest You mention above.

---

### Post by dave0109 on 2016-02-06
Thanks for that zika, I didn't know about those log files.

The history.log contains this entry when it started to go wrong...
```

Start-Date: 2016-02-03  19:16:03
Commandline: aptdaemon role='role-commit-packages' sender=':1.77'
Upgrade: passwd:amd64 (4.1.5.1-1.1ubuntu7, 4.2-3.1ubuntu1), udev:amd64 (228-4ubuntu1, 228-4ubuntu2), login:amd64 (4.1.5.1-1.1ubuntu7, 4.2-3.1ubuntu1), systemd:amd64 (228-4ubuntu1, 228-4ubuntu2), systemd-sysv:amd64 (228-4ubuntu1, 228-4ubuntu2), initramfs-tools:amd64 (0.120ubuntu7, 0.120ubuntu8), rsyslog:amd64 (8.14.0-2ubuntu2, 8.16.0-1ubuntu1), libsystemd0:amd64 (228-4ubuntu1, 228-4ubuntu2), libpam-systemd:amd64 (228-4ubuntu1, 228-4ubuntu2), libudev1:amd64 (228-4ubuntu1, 228-4ubuntu2), initramfs-tools-bin:amd64 (0.120ubuntu7, 0.120ubuntu8)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2016-02-03  19:16:18

```

In term.log, I have the following (with snipped "Reading database x%" messages)...
```

Log started: 2016-02-03  19:16:03
(Reading database ... 
(Reading database ... 235575 files and directories currently installed.)
Preparing to unpack .../login_1%3a4.2-3.1ubuntu1_amd64.deb ...
Unpacking login (1:4.2-3.1ubuntu1) over (1:4.1.5.1-1.1ubuntu7) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up login (1:4.2-3.1ubuntu1) ...
Installing new version of config file /etc/pam.d/login ...
Installing new version of config file /etc/pam.d/su ...
(Reading database ... 
(Reading database ... 235575 files and directories currently installed.)
Preparing to unpack .../udev_228-4ubuntu2_amd64.deb ...
Unpacking udev (228-4ubuntu2) over (228-4ubuntu1) ...
Preparing to unpack .../libudev1_228-4ubuntu2_amd64.deb ...
Unpacking libudev1:amd64 (228-4ubuntu2) over (228-4ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (228-4ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.21-0ubuntu5) ...
Setting up libudev1:amd64 (228-4ubuntu2) ...
Processing triggers for libc-bin (2.21-0ubuntu5) ...
(Reading database ... 
(Reading database ... 235575 files and directories currently installed.)
Preparing to unpack .../initramfs-tools_0.120ubuntu8_all.deb ...
Unpacking initramfs-tools (0.120ubuntu8) over (0.120ubuntu7) ...
Preparing to unpack .../initramfs-tools-bin_0.120ubuntu8_amd64.deb ...
Unpacking initramfs-tools-bin (0.120ubuntu8) over (0.120ubuntu7) ...
Preparing to unpack .../systemd-sysv_228-4ubuntu2_amd64.deb ...
Unpacking systemd-sysv (228-4ubuntu2) over (228-4ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up systemd-sysv (228-4ubuntu2) ...
(Reading database ... 
(Reading database ... 235575 files and directories currently installed.)
Preparing to unpack .../libpam-systemd_228-4ubuntu2_amd64.deb ...
Unpacking libpam-systemd:amd64 (228-4ubuntu2) over (228-4ubuntu1) ...
Preparing to unpack .../libsystemd0_228-4ubuntu2_amd64.deb ...
Unpacking libsystemd0:amd64 (228-4ubuntu2) over (228-4ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.21-0ubuntu5) ...
Setting up libsystemd0:amd64 (228-4ubuntu2) ...
Processing triggers for libc-bin (2.21-0ubuntu5) ...
(Reading database ... 
(Reading database ... 235575 files and directories currently installed.)
Preparing to unpack .../systemd_228-4ubuntu2_amd64.deb ...
Unpacking systemd (228-4ubuntu2) over (228-4ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for dbus (1.10.6-1ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up systemd (228-4ubuntu2) ...
addgroup: The group `systemd-journal' already exists as a system group. Exiting.
(Reading database ... 
(Reading database ... 235575 files and directories currently installed.)
Preparing to unpack .../passwd_1%3a4.2-3.1ubuntu1_amd64.deb ...
Unpacking passwd (1:4.2-3.1ubuntu1) over (1:4.1.5.1-1.1ubuntu7) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up passwd (1:4.2-3.1ubuntu1) ...
Installing new version of config file /etc/init/passwd.conf ...
Processing triggers for ureadahead (0.100.0-19) ...
(Reading database ... 
(Reading database ... 235577 files and directories currently installed.)
Preparing to unpack .../rsyslog_8.16.0-1ubuntu1_amd64.deb ...
Unpacking rsyslog (8.16.0-1ubuntu1) over (8.14.0-2ubuntu2) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (228-4ubuntu2) ...
Setting up udev (228-4ubuntu2) ...
addgroup: The group `input' already exists as a system group. Exiting.
update-initramfs: deferring update (trigger activated)
insserv: Service mountkernfs has to be enabled to start service udev
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package udev (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up initramfs-tools-bin (0.120ubuntu8) ...
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package initramfs-tools (--configure):
 dependency problems - leaving unconfigured
Setting up libpam-systemd:amd64 (228-4ubuntu2) ...
Setting up rsyslog (8.16.0-1ubuntu1) ...
Installing new version of config file /etc/logrotate.d/rsyslog ...
The user `syslog' is already a member of `adm'.
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Errors were encountered while processing:
 udev
 initramfs-tools
Log ended: 2016-02-03  19:16:18

```

In the process of trying to fix that, I ended up running several updates including the one that included the lightdm update.  Only after that point did I get to the bottom of the initramfs/udev issue.  In order to fix that, I came across reports on launchpad, and used the instructions provided at the [top of this bug entry]("https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1540568"), which sorted the error out and I was left with only the lightdm one.

---

### Post by zika on 2016-02-06
Saturday night it is so do not hold me responsible for what I would do in Your case (judging from log files)... ;)
```
sudo systemctl restart procps.service
sudo apt-get --configure -a
sudo apt-get install --reinstall insserv sysv-rc (add udev and initramfs-tools if any of those does not get fully configured above)
sudo apt-get install -f
```Be carefull and analyze each and every command as much as its (if You decide to use it) output.

---

### Post by dave0109 on 2016-02-06
OK, that gave me some ideas. Obviously replacing 'apt-get' with 'dpkg' for the configure-all command :)

So then I did...
```

$ sudo apt-get install --reinstall dbus lightdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 2 reinstalled, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 141 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu xenial/main amd64 dbus amd64 1.10.6-1ubuntu1 [141 kB]
Fetched 141 kB in 0s (630 kB/s)
E: Internal Error, No file name for lightdm:amd64

```

That led me to look at [the xenial repo]("http://packages.ubuntu.com/xenial/amd64/lightdm/download") and noted that the gb mirror isn't listed. However, changing mirrors in the software sources to one that is listed didn't help...

```

$ sudo apt-get install --reinstall lightdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 1 reinstalled, 0 to remove and 3 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for lightdm:amd64

```

As you point out, it's Sat night, so I'm done for the night. :)  It's geting to the point where it'll be quicker for me to re-install from scratch.  I won't be losing anything.

Thanks for your help.

---

### Post by zika on 2016-02-06
Speed of install is becoming a greatest curse of Ubuntu... ;) Have fun.

---

### Post by dave0109 on 2016-02-07
You know what... I hate giving up on stuff like this :)

So I purged lightdm, configured all, then re-installed lightdm.  That got me back to:-
```

Setting up lightdm (1.17.5-0ubuntu2) ...
insserv: Service dbus has to be enabled to start service lightdm

```

A bit of searching on issues where dbus was a runtime dependency and "I" manage to fix it by ensuring that dbus gets started in the init scripts...
```

$ sudo update-rc.d dbus defaults

```

At that point, configuring had no errors...
```

$ sudo dpkg --configure lightdm
Setting up lightdm (1.17.5-0ubuntu2) ...
$ 

```

Thanks for taking the time to help.

---

### Post by euthydemus on 2016-02-07
Thanks dave0109,

$ sudo update-rc.d dbus defaults

fixed it all up for me. I ran that and then sudo apt-get upgrade and the configuration finally completed. Everything held up previously by lightdm finished up as well. 

Cheers,

-Morgan

---

### Post by kenvac on 2016-02-08
> **dave0109 said:**
> 

```

$ sudo update-rc.d dbus defaults

```
.

Thanks a lot. It worked like a charm. I was cursed by this error.

---

### Post by syntaxerror74 on 2016-02-10
Amazing. I would never have gotten the idea of using update-rc.d for that.
Instead, I would probably have looked for a way to start/restart /usr/bin/dbus-daemon, even though it wouldn't have been for the faint of heart: do a ps -ef | grep dbus\-daemon and see that the daemon is not only started in *several* instances (4 here to be exact), but also with a boatload of (non-trivial) options. Hence, it will probably be much simpler to go your /sbin/update-rc.d  way.
Thanks for sharing your solution.

---

### Post by zeelink79 on 2016-12-17
> **kenvac said:**
> Thanks a lot. It worked like a charm. I was cursed by this error.
**update-rc.d dbus** defaults  generated **missing LSB tags and overrides... after searching on forums it only made obvious that it's ignorable in most cases .... **what fixed the problem for me was to downgrade dbus package by one version and that worked flawlessly...

---

### Post by marceloatm on 2017-05-02
Hello everyone,
I found one solution that really works for me with dropbox and a few others app that i had the same poblem.
I just add before the information dbus-launch before the aplication with the problem in the menu.
For example:
On the menu> internet> dropbox > properties > destop entry tab > command: dbus-launch dropbox start -i
Enjoy this solution when necessary.

---

### Post by QIII on 2017-05-04
Hello!

Thank you for your comment.

This sub-forum is for testing Ubuntu Development versions -- either new major releases or point releases of supported versions.  Neither of those apply to this thread.


Thread closed.

---

