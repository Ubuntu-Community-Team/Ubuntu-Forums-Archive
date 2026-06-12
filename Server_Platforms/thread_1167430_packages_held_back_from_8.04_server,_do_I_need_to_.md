---
title: "packages held back from 8.04 server, do I need to upgrade?"
date: 2009-05-22
forum: Server Platforms
---

### Post by DrJohn999 on 2009-05-22
The packages held back by apt-get for this 8.04 server are now:
```
# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  bind9 bind9-host dnsutils libbind9-30 libisc32 libisccc30 libisccfg30
  linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

```
Can someone clarify the meaning of "Long-Term Support" in this context? If bind9 and dependencies are being held back, that seems to imply there are potential security upgrades (now or maybe in future updates) which this server will not receive. I have no other particular reason / need to upgrade and no particular problems with the server. 

Several applications (including Mediawiki and Wordpress) are purposely running versions later than 'officially' supported by 8.04, for both feature and security reasons, and are likely to need some reconfiguration post upgrade to 8.10 +. That's OK, I knew what I was getting into. But, these aren't 'held back', they're up to date.

So, when does it make sense to upgrade to a later distribution? At this time, I'd have to either 1) double-upgrade 8.04 --> 8.10 --> 9.04 and hope for the best or 2) install a new 9.04 setup and reinstall / rebuild / restore the rest. Or, 3) wait for ... which?

---

### Post by Thirtysixway on 2009-05-22
You can still update those packages

apt-get dist-upgrade

This does not upgrade you to the latest version of Ubuntu.  These are just bigger packages like kernel updates etc that could mess up some software.  Example is whenever I do a dist-upgrade, I have to reconfigure my vmware server for it to run because the kernel changed.

I'd only upgrade for new features.  even if 8.04 is running an older version of software, it doesn't mean security patches aren't released for it.

---

### Post by mellowd on 2009-05-23
sudo aptitude full-upgrade

---

### Post by DrJohn999 on 2009-05-24
Running apt-get -s dist-upgrade gives this:

```
# apt-get -s dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libdns35 libisc35 linux-image-2.6.24-24-server
  linux-ubuntu-modules-2.6.24-24-server
The following packages will be upgraded:
  bind9 bind9-host dnsutils libbind9-30 libisc32 libisccc30 libisccfg30
  linux-image-server linux-server
9 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Inst linux-image-2.6.24-24-server (2.6.24-24.53 Ubuntu:8.04/hardy-updates)
Inst linux-ubuntu-modules-2.6.24-24-server (2.6.24-24.39 Ubuntu:8.04/hardy-updates)
Inst libisc35 (1:9.4.2.dfsg.P2-2ubuntu0.1 Ubuntu:8.04/hardy-updates)
Inst libdns35 (1:9.4.2.dfsg.P2-2ubuntu0.1 Ubuntu:8.04/hardy-updates)
Inst bind9 [1:9.4.2-10] (1:9.4.2.dfsg.P2-2ubuntu0.1 Ubuntu:8.04/hardy-updates) []
Inst libisccc30 [1:9.4.2-10] (1:9.4.2.dfsg.P2-2ubuntu0.1 Ubuntu:8.04/hardy-updates) []
Inst libisccfg30 [1:9.4.2-10] (1:9.4.2.dfsg.P2-2ubuntu0.1 Ubuntu:8.04/hardy-updates) []
Inst libbind9-30 [1:9.4.2-10] (1:9.4.2.dfsg.P2-2ubuntu0.1 Ubuntu:8.04/hardy-updates)
Inst bind9-host [1:9.4.2-10] (1:9.4.2.dfsg.P2-2ubuntu0.1 Ubuntu:8.04/hardy-updates)
Inst dnsutils [1:9.4.2-10] (1:9.4.2.dfsg.P2-2ubuntu0.1 Ubuntu:8.04/hardy-updates)
Inst libisc32 [1:9.4.2-10] (1:9.4.2-10ubuntu0.1 Ubuntu:8.04/hardy-updates)
Inst linux-server [2.6.24.16.18] (2.6.24.24.26 Ubuntu:8.04/hardy-updates) []
Inst linux-image-server [2.6.24.16.18] (2.6.24.24.26 Ubuntu:8.04/hardy-updates)
Conf linux-image-2.6.24-24-server (2.6.24-24.53 Ubuntu:8.04/hardy-updates)
Conf linux-ubuntu-modules-2.6.24-24-server (2.6.24-24.39 Ubuntu:8.04/hardy-updates)
Conf libisc35 (1:9.4.2.dfsg.P2-2ubuntu0.1 Ubuntu:8.04/hardy-updates)
Conf libdns35 (1:9.4.2.dfsg.P2-2ubuntu0.1 Ubuntu:8.04/hardy-updates)
Conf libisccc30 (1:9.4.2.dfsg.P2-2ubuntu0.1 Ubuntu:8.04/hardy-updates)
Conf libisccfg30 (1:9.4.2.dfsg.P2-2ubuntu0.1 Ubuntu:8.04/hardy-updates)
Conf libbind9-30 (1:9.4.2.dfsg.P2-2ubuntu0.1 Ubuntu:8.04/hardy-updates)
Conf bind9 (1:9.4.2.dfsg.P2-2ubuntu0.1 Ubuntu:8.04/hardy-updates)
Conf bind9-host (1:9.4.2.dfsg.P2-2ubuntu0.1 Ubuntu:8.04/hardy-updates)
Conf dnsutils (1:9.4.2.dfsg.P2-2ubuntu0.1 Ubuntu:8.04/hardy-updates)
Conf libisc32 (1:9.4.2-10ubuntu0.1 Ubuntu:8.04/hardy-updates)
Conf linux-image-server (2.6.24.24.26 Ubuntu:8.04/hardy-updates)
Conf linux-server (2.6.24.24.26 Ubuntu:8.04/hardy-updates)

```
It's (re)installing bind9 and configuring it: does this mean that the named and zone configurations will be reset to defaults? I saw somewhere that it's possible to force keeping old configurations using -o to set apt-get configuration, but man apt.conf doesnt show anything that pertains, nor is there anything in the 'rc'-like /etc/apt/apt.conf.d to show how. IAEF I can restore from backup, but why have to do that?

---

### Post by mellowd on 2009-05-24
with full-upgrade it will generally ask you if you want to keep your old config file or install the new (default) one

---

### Post by DrJohn999 on 2009-05-26
Running [FONT="Courier New"]aptitude full-upgrade[/FONT] installed the new kernel etc. but bind did not start after reboot. The problem turns out to be apparmor: the full-upgrade installation re-enabled apparmor (I had disabled it) and added / updated a policy for named at /etc/apparmor.d/usr.sbin.named which fails when bind9 is chrooted (see [http://www.howtoforge.com/forums/showthread.php?t=21699](http://www.howtoforge.com/forums/showthread.php?t=21699), which includes a modified policy that may work with apparmor and chrooted bind9). Simply removing the policy did not work. I choose to stop apparmor and remove it from the startup scripts:
```
/etc/init.d/apparmor stop
update-rc.d -f apparmor remove
```
which is how this server was configured in the first place.
Always a fun time here!

---

