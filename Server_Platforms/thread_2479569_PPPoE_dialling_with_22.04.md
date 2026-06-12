---
title: "PPPoE dialling with 22.04"
date: 2022-09-29
forum: Server Platforms
---

### Post by nathancrjackson on 2022-09-29
Hi,

I am using an rPi CM4 on a carrier board with multiple Ethernet ports as a router. After doing a fresh install of Ubuntu Server 22.04 I have found that I cannot configure PPPoE for my WAN connection.

When running pppd I get the following error:
```
Failed to create PPPoE socket: Address family not supported by protocol
```

 I do not have this issue with Ubuntu Server 20.04 and believe that the ppp networking drivers have been dropped from 22.04.

Checking how the kernel is compiled I can see that ppp is not compiled into the kernel and that there is nothing ppp in my modules.

```
root@rpi-22_04:/home/admin# modprobe configs

root@rpi-22_04:/home/admin# zgrep PPP /proc/config.gz
CONFIG_PPP=y
CONFIG_PPP_BSDCOMP=m
CONFIG_PPP_DEFLATE=m
CONFIG_PPP_FILTER=y
CONFIG_PPP_MPPE=m
CONFIG_PPP_MULTILINK=y
CONFIG_PPPOATM=m
CONFIG_PPPOE=m
CONFIG_PPPOL2TP=m
CONFIG_PPP_ASYNC=m
CONFIG_PPP_SYNC_TTY=m
CONFIG_HDLC_PPP=m

root@rpi-22_04:/home/admin# modprobe pppoe
modprobe: FATAL: Module pppoe not found in directory /lib/modules/5.15.0-1015-raspi

root@rpi-22_04:/home/admin# cd /lib/modules/5.15.0-1015-raspi

root@rpi-22_04:/lib/modules/5.15.0-1015-raspi# find | grep ppp
```

Whereas if I do the above for 20.04 I get the following:

```
root@rpi-20_04:/home/admin# modprobe configs
root@rpi-20_04:/home/admin# zgrep PPP /proc/config.gz
CONFIG_PPP=y
CONFIG_PPP_BSDCOMP=m
CONFIG_PPP_DEFLATE=m
CONFIG_PPP_FILTER=y
CONFIG_PPP_MPPE=m
CONFIG_PPP_MULTILINK=y
CONFIG_PPPOATM=m
CONFIG_PPPOE=m
CONFIG_PPPOL2TP=m
CONFIG_PPP_ASYNC=m
CONFIG_PPP_SYNC_TTY=m
CONFIG_HDLC_PPP=m

root@rpi-20_04:/home/admin# modprobe pppoe

root@rpi-20_04:/home/admin# cd /lib/modules/5.4.0-1045-raspi/

root@rpi-20_04:/lib/modules/5.4.0-1045-raspi# find | grep ppp
./kernel/drivers/net/wan/hdlc_ppp.ko
./kernel/drivers/net/ppp
./kernel/drivers/net/ppp/ppp_synctty.ko
./kernel/drivers/net/ppp/ppp_async.ko
./kernel/drivers/net/ppp/ppp_mppe.ko
./kernel/drivers/net/ppp/pppoe.ko
./kernel/drivers/net/ppp/pppox.ko
./kernel/drivers/net/ppp/pptp.ko
./kernel/drivers/net/ppp/bsd_comp.ko
./kernel/drivers/net/ppp/ppp_deflate.ko
./kernel/net/l2tp/l2tp_ppp.ko
./kernel/net/atm/pppoatm.ko
```

Ideally I would like to run 22.04 but PPPoE support is required for my use-case. Is anyone aware of a way to obtain or complile just the ppp network drivers?

Thank you in advance for any advice or assistance.

---

### Post by MAFoElffen on 2022-10-01
I think the driver for pppoe is external, not a kernel module... Your error says something is missing to provide that protocol right?.

Is the 'pppoe" package installed? For Debian Branch, that is the package that provides the 'pppd' daemon and the 'pppoe' driver. I think I remember the config files being /etc/ppp/peers/provider (man pppd to config), the connection handling scripts in /etc/ppp/ip-up.d/, and for systemd started by /etc/systemd/system/pppoe.service

---

### Post by nathancrjackson on 2022-10-05
The pppoe package is installed. Looking the manpage for pppoe it does say it's a "user-space PPPoE  client" but it looks like there was also a pppoe kernel module in 20.04 too. So maybe there are multiple ways to skin a cat and the way I could do it in 20.04 is no longer valid for 22.04?

Here are some new comparisons of package contents for 22.04 and 20.04:

In 22.04

```
root@rpi-22_04:/home/admin# apt-file list linux-modules-5.15.0-1011-raspi | grep pppoe

root@rpi-22_04:/home/admin# apt-file list pppoe
pppoe: /etc/ppp/peers/dsl-provider
pppoe: /usr/sbin/pppoe
pppoe: /usr/sbin/pppoe-connect
pppoe: /usr/sbin/pppoe-relay
pppoe: /usr/sbin/pppoe-server
pppoe: /usr/sbin/pppoe-sniff
pppoe: /usr/sbin/pppoe-start
pppoe: /usr/sbin/pppoe-status
pppoe: /usr/sbin/pppoe-stop
pppoe: /usr/share/doc/pppoe/README.Debian.gz
pppoe: /usr/share/doc/pppoe/changelog.Debian.gz
pppoe: /usr/share/doc/pppoe/copyright
pppoe: /usr/share/lintian/overrides/pppoe
pppoe: /usr/share/man/man5/pppoe.conf.5.gz
pppoe: /usr/share/man/man8/pppoe-connect.8.gz
pppoe: /usr/share/man/man8/pppoe-relay.8.gz
pppoe: /usr/share/man/man8/pppoe-server.8.gz
pppoe: /usr/share/man/man8/pppoe-setup.8.gz
pppoe: /usr/share/man/man8/pppoe-sniff.8.gz
pppoe: /usr/share/man/man8/pppoe-start.8.gz
pppoe: /usr/share/man/man8/pppoe-status.8.gz
pppoe: /usr/share/man/man8/pppoe-stop.8.gz
pppoe: /usr/share/man/man8/pppoe.8.gz
```

In 20.04

```
root@rpi-22_04:/home/admin# sudo apt-file list linux-modules-5.4.0-1045-raspi | grep pppoe
linux-modules-5.4.0-1045-raspi: /lib/modules/5.4.0-1045-raspi/kernel/drivers/net/ppp/pppoe.ko

root@rpi-22_04:/home/admin#apt-file list pppoe
pppoe: /etc/ppp/peers/dsl-provider
pppoe: /usr/sbin/pppoe
pppoe: /usr/sbin/pppoe-connect
pppoe: /usr/sbin/pppoe-relay
pppoe: /usr/sbin/pppoe-server
pppoe: /usr/sbin/pppoe-sniff
pppoe: /usr/sbin/pppoe-start
pppoe: /usr/sbin/pppoe-status
pppoe: /usr/sbin/pppoe-stop
pppoe: /usr/share/doc/pppoe/README.Debian.gz
pppoe: /usr/share/doc/pppoe/changelog.Debian.gz
pppoe: /usr/share/doc/pppoe/copyright
pppoe: /usr/share/lintian/overrides/pppoe
pppoe: /usr/share/man/man5/pppoe.conf.5.gz
pppoe: /usr/share/man/man8/pppoe-connect.8.gz
pppoe: /usr/share/man/man8/pppoe-relay.8.gz
pppoe: /usr/share/man/man8/pppoe-server.8.gz
pppoe: /usr/share/man/man8/pppoe-setup.8.gz
pppoe: /usr/share/man/man8/pppoe-sniff.8.gz
pppoe: /usr/share/man/man8/pppoe-start.8.gz
pppoe: /usr/share/man/man8/pppoe-status.8.gz
pppoe: /usr/share/man/man8/pppoe-stop.8.gz
pppoe: /usr/share/man/man8/pppoe.8.gz
```

Without comparing hashes both pppoe packages look the same and the Linux modules package for 20.04 definitely has something pppoe related that 22.04 doesn't.

I'll see if I can work it out and report back.

---

### Post by nathancrjackson on 2022-10-06
Not a good start, I've found how to do PPPoE in user-space but am getting the following error.

```
Couldn't set tty to PPP discipline: Invalid argument
```

So far the consensus online appears to be that this is due to a missing kernel module (probs ppp_async.ko).

---

### Post by nathancrjackson on 2022-10-06
Okay I have cracked the case, it turns out that there is an extra kernel modules package you can install with exactly what I need.

For the Raspberry Pi install the following package
```
linux-modules-extra-raspi
```

From there PPPoE started working without issue and for reference that includes fixing my problems with the user-space client.

---

### Post by MAFoElffen on 2022-10-06
> **nathancrjackson said:**
> Okay I have cracked the case, it turns out that there is an extra kernel modules package you can install with exactly what I need.

For the Raspberry Pi install the following package
```
[COLOR=#ff0000]linux-modules-extra-raspi[/COLOR]
```

From there PPPoE started working without issue and for reference that includes fixing my problems with the user-space client.
Dang. Seemed to be an adventure finding what was missing from 22.04...

Happy that you found out where to find it and that it is now working. Please use the "Thread Tools" link in the upper right of the page to mark this thread as "Solved" so that others can find your solution to solve there similar issues.

---

