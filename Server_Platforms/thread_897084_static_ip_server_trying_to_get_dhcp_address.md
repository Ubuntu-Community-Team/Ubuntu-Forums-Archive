---
title: "static ip server trying to get dhcp address"
date: 2008-08-21
forum: Server Platforms
---

### Post by caitifty on 2008-08-21
Hi all

I have an 8.04 server set up with a static IP and dhcpd uninstalled.  Iptables is enabled, with a basic ruleset to drop all unwanted incoming & outgoing port traffic.  One thing I'm seeing in /var/log/messages is the following every 30 seconds..

Aug 21 16:55:25 php10 kernel: [2939156.750552] ** DROPPED ** IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:02:b9:f4:ef:80:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=255 ID=31226 PROTO=UDP SPT=68 DPT=67 LEN=308

Which sort of looks to me like my server is trying to get an ip address via dhcp every 30 seconds, but the attempt is being dropped by iptables..

Any ideas how to stop this log-filling behaviour?

Thanks in advance

Pete

---

### Post by MJN on 2008-08-22
Am I right in thinking you have only recently moved over to a static IP, and ditched DHCP? If so, it could well be that the DHCP client (dhclient) is still running despite the package on disk being removed hence it is likely trying to renew its last-assigned address.
 
Solution - find the running process and kill it.
 
Mathew

---

### Post by redroad55 on 2008-08-22
hi I've been also trying to resolve a similar issue...please be more specific as to your current config and changes made to get to where you are currently..I fond this thread that may pertain to your scenario worth reading was entertaing for sure.[http://ubuntuforums.org/showthread.php?t=686954&highlight=fixed+lease]("http://ubuntuforums.org/showthread.php?t=686954&highlight=fixed+lease")

---

### Post by caitifty on 2008-08-22
Thanks all for replying..

Mathew, I switched to static about 3 months ago (only just noticed all the garbage in logs.. oops).  I've rebooted at least once since then.  I also ran ps aux and looked for anything that looked like a dhcp client or daemon and couldn't see anything (can post the entire output if you'd like though).

Redroad55, Here's how I set up static IP (and yeah, that thread was pretty funny..):

Regards

Pete

--

Get rid of dhcp client:

$sudo apt-get remove dhcp3-client

Change interfaces to match your static IP setup:

$sudo vi /etc/network/interfaces

and (assuming your primary interface is eth0) change it to:

[INDENT]	# The primary network interface
	
	auto eth0
	iface eth0 inet static
	address <static ip>
	netmask <netmask>
	network <network address>
	broadcast <broadcast address>
	gateway <gateway address>[/INDENT]

replacing <static ip> with your actual ip address eg 172.16.1.33 and so on..

To set DNS without it being overwritten by resolvconf every time you reboot, create

$sudo vi /etc/resolvE.conf

[INDENT]	# DNS
	
	nameserver <nameserver 1 address>
	nameserver <nameserver 2 address>
[/INDENT]
then create an init script to copy this file to resolv.conf at boot:

$sudo vi /etc/init.d/fixresolv

[INDENT]	#!/bin/bash
	cp /etc/resolvE.conf /etc/resolv.conf
[/INDENT]	
and use update-rc.d to create the init script links:

$sudo update-rc.d fixresolv defaults

Run it once immediately so you don't have to reboot just to set DNS right now:

$sudo /etc/init.d/./fixresolv

Finally, restart network services:

sudo /etc/init.d/networking restart

If all went well, you'll now be up on a static IP with working DNS which will continue to come up properly next time you need to reboot.

---

