---
title: "Bug? No network w/ VirtualBox windows host, ubuntu guest after today's upgrade"
date: 2010-09-03
forum: Virtualisation
---

### Post by zman97211 on 2010-09-03
I have VirtualBox version 3.2.8.r64453 running on Windows XP SP3.

Installed as a guest is Ubuntu 10.04, which was installed a few days ago  and I let the update manager fully update after the install.

I then installed guest additions, and haven't had any problems. Although  the last couple of days Update Manager has done "partial updates" due  to an external package changing some files. I have installed Eclipse,  and sun-java5-jdk.

Everything worked great up until an update was installed today. After the update, Ubuntu has no network connectivity.

Here is a bit from Package Manager's history:

```
Commit Log for Wed Sep  1 16:32:16 2010


Installed the following packages:
gitk (1:1.7.0.4-1)
tcl (8.4.16-2)
tk (8.4.16-2)

```and

```
Commit Log for Wed Sep  1 16:35:45 2010


Upgraded the following packages:
aptdaemon (0.11+bzr345-0ubuntu4) to 0.11+bzr345-0ubuntu4.1
bogofilter (1.2.1-0ubuntu1) to 1.2.1-0ubuntu1.1
bogofilter-bdb (1.2.1-0ubuntu1) to 1.2.1-0ubuntu1.1
bogofilter-common (1.2.1-0ubuntu1) to 1.2.1-0ubuntu1.1
libgudev-1.0-0 (1:151-12) to 1:151-12.1
libudev0 (151-12) to 151-12.1
libwww-perl (5.834-1) to 5.834-1ubuntu0.1
linux-headers-2.6.32-24 (2.6.32-24.41) to 2.6.32-24.42
linux-headers-2.6.32-24-generic (2.6.32-24.41) to 2.6.32-24.42
linux-image-2.6.32-24-generic (2.6.32-24.41) to 2.6.32-24.42
linux-libc-dev (2.6.32-24.41) to 2.6.32-24.42
mountall (2.15) to 2.15.1
python-aptdaemon (0.11+bzr345-0ubuntu4) to 0.11+bzr345-0ubuntu4.1
python-aptdaemon-gtk (0.11+bzr345-0ubuntu4) to 0.11+bzr345-0ubuntu4.1
udev (151-12) to 151-12.1
usb-creator-common (0.2.22) to 0.2.22.1
usb-creator-gtk (0.2.22) to 0.2.22.1

```I reinstalled the guest additions after that thinking that would  probably solve the networking problem, since it appears the kernel was  upgraded. The difference in time was due to a trip to some great Mexican  food for dinner :)

```
Commit Log for Fri Sep  3 22:00:16 2010


Downgraded the following packages:
linux-image-2.6.32-24-generic
linux-headers-2.6.32-24
linux-libc-dev
linux-headers-2.6.32-24-generic

```After that I rebuilt the guest additions again.

'ifconfig' tells me eth0 interface isn't up. 'ifconfig eth0 up' does  bring the interface up, but no DHCP action is afoot. To me, none of the  other packages look like they would have an effect on my network  interface, although of course I could be wrong.

Anyway, still no network... Any ideas from the community? A search of  pages on Google for the last 24 hours has resulted in no leads.

Thanks!

Steve

edit: some new info - grepping dmesg for eth0:

```
[    5.836449] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[  616.322242] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  616.331419] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[  616.347467] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  627.104400] eth0: no IPv6 routers present
[ 1345.591838] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1345.599462] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[ 1345.600991] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1355.792182] eth0: no IPv6 routers present

```Maybe ipv4 isn't setup for that interface? I don't know enough about where to look to make sure...

---

### Post by zman97211 on 2010-09-04
Just installed 10.10 beta, network is working... But now I have to reinstall everything to set up my build environment. Ugh...

---

