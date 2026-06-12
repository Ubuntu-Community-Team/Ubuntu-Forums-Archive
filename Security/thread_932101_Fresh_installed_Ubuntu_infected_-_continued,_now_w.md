---
title: "Fresh installed Ubuntu infected - continued, now with logs"
date: 2008-09-28
forum: Security
---

### Post by ekh on 2008-09-28
Hi again.

I have beaten my personal record by being able to use an Ubuntu desktop 8.04.1 fully updated for a week, but nothing lasts forever :-(

```
** Alert 1222554996.8360: mail  - ossec,rootcheck,
2008 Sep 28 00:36:36 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
Port '953'(tcp) hidden. Kernel-level rootkit or trojaned version of netstat.

```

This is around 15 reinstalls in 5 weeks, I have lost track of the exact number.
This time the attack destroyed my LUKS password like many times before, but first I managed to get logs.

I have /bin, /etc, /proc, /tmp and /var, when I tried to copy /usr/bin the attack locked the computer.

As I previously have mentioned, I am no security expert, but I would be better off if I was one, as these attackers are very persistent.

I will be very thankful if someone will direct me through the forensics. I will deliver all evidence I have on request, so this very annoying vulnerability can be solved. It has now cost me 5 weeks of ordinary work.

I have collected a total of 1.9 GByte of data for this single attack, and I will post whatever logged data you find important.

The only thing I can trust for the moment is the CD from [www.polippix.org](www.polippix.org).

Here is the first place I suspect the attack succeeded. Clipped from /var/log/syslog.

```

Sep 27 10:16:13 ht41 NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Sep 27 10:16:13 ht41 dhclient: bound to 192.168.10.81 -- renewal in 50 seconds.
Sep 27 10:17:01 ht41 /USR/SBIN/CRON[12217]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 27 10:17:03 ht41 dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.10.7 port 67
Sep 27 10:17:03 ht41 dhclient: DHCPACK of 192.168.10.81 from 192.168.10.7
Sep 27 10:17:03 ht41 NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Sep 27 10:17:03 ht41 dhclient: bound to 192.168.10.81 -- renewal in 52 seconds.
Sep 27 10:17:55 ht41 dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.10.7 port 67
Sep 27 10:17:55 ht41 dhclient: DHCPACK of 192.168.10.81 from 192.168.10.7
Sep 27 10:17:55 ht41 NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Sep 27 10:17:55 ht41 dhclient: bound to 192.168.10.81 -- renewal in 45 seconds.
Sep 27 10:18:40 ht41 dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.10.7 port 67
Sep 27 10:18:40 ht41 dhclient: DHCPACK of 192.168.10.81 from 192.168.10.7
Sep 27 10:18:40 ht41 NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Sep 27 10:18:40 ht41 dhclient: bound to 192.168.10.81 -- renewal in 44 seconds.
Sep 27 10:18:56 ht41 anacron[12490]: Anacron 2.3 started on 2008-09-27
Sep 27 10:18:56 ht41 anacron[12490]: Normal exit (0 jobs run)
Sep 27 10:19:24 ht41 dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.10.7 port 67
Sep 27 10:19:24 ht41 dhclient: DHCPACK of 192.168.10.81 from 192.168.10.7
Sep 27 10:19:24 ht41 NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Sep 27 10:19:24 ht41 dhclient: bound to 192.168.10.81 -- renewal in 55 seconds.
Sep 27 10:19:31 ht41 kernel: [68179.062580] e1000: eth0: e1000_watchdog: NIC Link is Down
Sep 27 10:19:31 ht41 NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Sep 27 10:19:31 ht41 NetworkManager: <info>  Deactivating device eth0. 
Sep 27 10:19:31 ht41 dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 16126
Sep 27 10:19:31 ht41 dhclient: killed old client process, removed PID file
Sep 27 10:19:31 ht41 dhclient: DHCPRELEASE on eth0 to 192.168.10.7 port 67
Sep 27 10:19:31 ht41 avahi-daemon[5057]: Withdrawing address record for 192.168.10.81 on eth0.
Sep 27 10:19:31 ht41 avahi-daemon[5057]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.10.81.
Sep 27 10:19:31 ht41 avahi-daemon[5057]: Interface eth0.IPv4 no longer relevant for mDNS.
Sep 27 10:19:31 ht41 dhcdbd:  dhclient 16126 down (9) but si_code == 0 and releasing==0 !
Sep 27 10:19:32 ht41 avahi-daemon[5057]: Withdrawing address record for fe80::211:25ff:fe2d:29d2 on eth0.
Sep 27 10:19:32 ht41 NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Sep 27 10:19:32 ht41 NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Sep 27 10:19:41 ht41 kernel: [181955.128740] e1000: eth0: e1000_watchdog: NIC Link is Up 10 Mbps Half Duplex, Flow Control: None
Sep 27 10:19:41 ht41 NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Sep 27 10:19:41 ht41 kernel: [181955.130044] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Sep 27 10:19:41 ht41 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Sep 27 10:19:41 ht41 NetworkManager: <info>  Will activate connection 'eth0'. 
Sep 27 10:19:41 ht41 NetworkManager: <info>  Device eth0 activation scheduled... 
Sep 27 10:19:41 ht41 NetworkManager: <info>  Activation (eth0) started... 
Sep 27 10:19:41 ht41 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep 27 10:19:41 ht41 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Sep 27 10:19:41 ht41 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Sep 27 10:19:41 ht41 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Sep 27 10:19:41 ht41 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Sep 27 10:19:41 ht41 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Sep 27 10:19:41 ht41 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Sep 27 10:19:41 ht41 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Sep 27 10:19:41 ht41 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Sep 27 10:19:42 ht41 NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Sep 27 10:19:42 ht41 dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Sep 27 10:19:42 ht41 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Sep 27 10:19:42 ht41 NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Sep 27 10:19:43 ht41 avahi-daemon[5057]: Registering new address record for fe80::211:25ff:fe2d:29d2 on eth0.*.
Sep 27 10:19:43 ht41 NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Sep 27 10:19:47 ht41 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Sep 27 10:19:52 ht41 kernel: [181958.102779] eth0: no IPv6 routers present
Sep 27 10:19:54 ht41 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Sep 27 10:20:03 ht41 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Sep 27 10:20:15 ht41 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Sep 27 10:20:33 ht41 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Sep 27 10:20:42 ht41 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Sep 27 10:20:48 ht41 dhclient: No DHCPOFFERS received.

Sep 27 10:20:48 ht41 avahi-autoipd(eth0)[12696]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).


Sep 27 10:20:48 ht41 avahi-autoipd(eth0)[12696]: Successfully called chroot().

Sep 27 10:20:48 ht41 avahi-autoipd(eth0)[12696]: Successfully dropped root privileges.
Sep 27 10:20:48 ht41 avahi-autoipd(eth0)[12696]: Starting with address 169.254.5.161
Sep 27 10:20:53 ht41 avahi-autoipd(eth0)[12696]: Callout BIND, address 169.254.5.161 on interface eth0
Sep 27 10:20:53 ht41 avahi-daemon[5057]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.5.161.
Sep 27 10:20:53 ht41 avahi-daemon[5057]: New relevant interface eth0.IPv4 for mDNS.
Sep 27 10:20:53 ht41 avahi-daemon[5057]: Registering new address record for 169.254.5.161 on eth0.IPv4.

```

Like my OpenBSD attacked, also Ubuntu has lots of DHCPREQUEST preceeding the attack succeeding, But whether this is significant, I can't tell.

Please help.

---

### Post by ekh on 2008-09-28
Although I have 1.9 GByte collected from the disk, it vould be nice to get LUKS on the infected disk working again.

When I first installed the Ubuntu, after getting the system updated and operational, I used dd to make a verbatim copy of the harddisk to another identical type harddisk.

I then stored the original disk and inserted the copy for further use, and it is the copy that is infected and unable to be opened with LUKS.

I wonder if is is possible to copy a limited number of blocks from the original disk to make LUKS work again on the infected disk. Do anyone know how many blocks I must copy from the beginning of the disk using dd ?

It appears an extra hidden file system has been added, see last code list.

The computer was installed:

```

Log started: 2008-09-16  13:56:41
Selecting previously deselected package dmsetup.
(Reading database ... 8617 files and directories currently installed.)
Unpacking dmsetup (from .../dmsetup_1.02.20-2ubuntu2_i386.deb) ...
Selecting previously deselected package cryptsetup.
Unpacking cryptsetup (from .../cryptsetup_1.0.5-2ubuntu12_i386.deb) ...
Setting up dmsetup (2:1.02.20-2ubuntu2) ...
update-initramfs: deferring update (trigger activated)

```

From /var/log/daemon.log I have copied a sequence showing the last normal DHCP assignment and then the first assignment to 169.254.5.161

Sep 26 01:09:12 ht41 avahi-daemon[5057]: Withdrawing address record for 192.168.10.81 on eth0.
and
Sep 26 01:35:27 ht41 avahi-autoipd(eth0)[31049]: Callout BIND, address 169.254.5.161 on interface eth0

What is going on here ?

In a previous post someone thought I was doing this for fun, because I was not able to show logs.

It is not funny, and I now have lots of logs and data, please help, please.

Before I discovered this new attack, I had just finished an install of an Ubuntu server, just with NFS and subversion. It is my first server without desktop, attempting to have a more secure server. 

My T41 portable was setup as a subversion client, and succeeded a checkout of my backed up subversion database. With this last attack I can start all over again.

```

Sep 26 01:07:36 ht41 NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Sep 26 01:07:40 ht41 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Sep 26 01:07:40 ht41 dhclient: DHCPOFFER of 192.168.10.81 from 192.168.10.7
Sep 26 01:07:40 ht41 dhclient: DHCPREQUEST of 192.168.10.81 on eth0 to 255.255.255.255 port 67
Sep 26 01:07:40 ht41 dhclient: DHCPACK of 192.168.10.81 from 192.168.10.7
Sep 26 01:07:40 ht41 avahi-daemon[5057]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.10.81.
Sep 26 01:07:40 ht41 avahi-daemon[5057]: New relevant interface eth0.IPv4 for mDNS.
Sep 26 01:07:40 ht41 avahi-daemon[5057]: Registering new address record for 192.168.10.81 on eth0.IPv4.
Sep 26 01:07:40 ht41 NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Sep 26 01:07:40 ht41 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Sep 26 01:07:40 ht41 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Sep 26 01:07:40 ht41 NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Sep 26 01:07:40 ht41 NetworkManager: <info>    address 192.168.10.81 
Sep 26 01:07:40 ht41 NetworkManager: <info>    netmask 255.255.255.0 
Sep 26 01:07:40 ht41 NetworkManager: <info>    broadcast 192.168.10.255 
Sep 26 01:07:40 ht41 NetworkManager: <info>    gateway 192.168.10.7 
Sep 26 01:07:40 ht41 NetworkManager: <info>    nameserver 192.168.10.7 
Sep 26 01:07:40 ht41 NetworkManager: <info>    domain name 'xxnone' 
Sep 26 01:07:40 ht41 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Sep 26 01:07:40 ht41 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Sep 26 01:07:40 ht41 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Sep 26 01:07:40 ht41 dhclient: bound to 192.168.10.81 -- renewal in 58 seconds.
Sep 26 01:07:40 ht41 avahi-daemon[5057]: Withdrawing address record for 192.168.10.81 on eth0.
Sep 26 01:07:40 ht41 avahi-daemon[5057]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.10.81.
Sep 26 01:07:40 ht41 avahi-daemon[5057]: Interface eth0.IPv4 no longer relevant for mDNS.
Sep 26 01:07:40 ht41 avahi-daemon[5057]: Withdrawing address record for fe80::211:25ff:fe2d:29d2 on eth0.
Sep 26 01:07:40 ht41 avahi-daemon[5057]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.10.81.
Sep 26 01:07:40 ht41 avahi-daemon[5057]: New relevant interface eth0.IPv4 for mDNS.
Sep 26 01:07:40 ht41 avahi-daemon[5057]: Registering new address record for 192.168.10.81 on eth0.IPv4.
Sep 26 01:07:41 ht41 NetworkManager: <info>  Clearing nscd hosts cache. 
Sep 26 01:07:41 ht41 NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Sep 26 01:07:41 ht41 NetworkManager: <info>  Activation (eth0) successful, device activated. 
Sep 26 01:07:41 ht41 NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Sep 26 01:07:41 ht41 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Sep 26 01:07:42 ht41 avahi-daemon[5057]: Registering new address record for fe80::211:25ff:fe2d:29d2 on eth0.*.
Sep 26 01:07:45 ht41 ntpdate[28601]: adjust time server 91.189.94.4 offset -0.298091 sec
Sep 26 01:08:38 ht41 dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.10.7 port 67
Sep 26 01:08:38 ht41 dhclient: DHCPACK of 192.168.10.81 from 192.168.10.7
Sep 26 01:08:38 ht41 NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Sep 26 01:08:38 ht41 dhclient: bound to 192.168.10.81 -- renewal in 50 seconds.
Sep 26 01:09:05 ht41 rpc.statd[28979]: Version 1.1.2 Starting
Sep 26 01:09:09 ht41 NetworkManager: <debug> [1222384149.214441] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_1205_noserial'). 
Sep 26 01:09:09 ht41 NetworkManager: <debug> [1222384149.817265] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_1205_noserial_if0'). 
Sep 26 01:09:09 ht41 NetworkManager: <debug> [1222384149.921943] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_1205_noserial_if0_logicaldev_input'). 
Sep 26 01:09:12 ht41 NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Sep 26 01:09:12 ht41 NetworkManager: <info>  Deactivating device eth0. 
Sep 26 01:09:12 ht41 dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 28533
Sep 26 01:09:12 ht41 dhclient: killed old client process, removed PID file
Sep 26 01:09:12 ht41 dhclient: DHCPRELEASE on eth0 to 192.168.10.7 port 67
Sep 26 01:09:12 ht41 avahi-daemon[5057]: Withdrawing address record for 192.168.10.81 on eth0.
Sep 26 01:09:12 ht41 avahi-daemon[5057]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.10.81.
Sep 26 01:09:12 ht41 avahi-daemon[5057]: Interface eth0.IPv4 no longer relevant for mDNS.
Sep 26 01:09:13 ht41 avahi-daemon[5057]: Withdrawing address record for fe80::211:25ff:fe2d:29d2 on eth0.
Sep 26 01:09:13 ht41 NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Sep 26 01:09:13 ht41 NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Sep 26 01:30:24 ht41 rpc.statd[28979]: Caught signal 15, un-registering and exiting.
Sep 26 01:30:29 ht41 rpc.statd[30614]: Version 1.1.2 Starting
Sep 26 01:30:29 ht41 rpc.statd[30614]: unable to register (statd, 1, udp).
Sep 26 01:31:05 ht41 NetworkManager: <debug> [1222385465.805798] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_1205_noserial_if0_logicaldev_input'). 
Sep 26 01:31:05 ht41 NetworkManager: <debug> [1222385465.820040] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_1205_noserial_if0'). 
Sep 26 01:31:05 ht41 NetworkManager: <debug> [1222385465.826053] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_1205_noserial'). 
Sep 26 01:34:17 ht41 NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Sep 26 01:34:17 ht41 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Sep 26 01:34:17 ht41 NetworkManager: <info>  Will activate connection 'eth0'. 
Sep 26 01:34:17 ht41 NetworkManager: <info>  Device eth0 activation scheduled... 
Sep 26 01:34:17 ht41 NetworkManager: <info>  Activation (eth0) started... 
Sep 26 01:34:17 ht41 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep 26 01:34:17 ht41 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Sep 26 01:34:17 ht41 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Sep 26 01:34:17 ht41 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Sep 26 01:34:17 ht41 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Sep 26 01:34:17 ht41 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Sep 26 01:34:17 ht41 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Sep 26 01:34:17 ht41 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Sep 26 01:34:17 ht41 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Sep 26 01:34:18 ht41 NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Sep 26 01:34:18 ht41 dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Sep 26 01:34:18 ht41 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Sep 26 01:34:18 ht41 NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Sep 26 01:34:18 ht41 avahi-daemon[5057]: Registering new address record for fe80::211:25ff:fe2d:29d2 on eth0.*.
Sep 26 01:34:19 ht41 NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Sep 26 01:34:21 ht41 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Sep 26 01:34:27 ht41 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Sep 26 01:34:34 ht41 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Sep 26 01:34:42 ht41 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Sep 26 01:35:03 ht41 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Sep 26 01:35:22 ht41 dhclient: No DHCPOFFERS received.
Sep 26 01:35:22 ht41 avahi-autoipd(eth0)[31049]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Sep 26 01:35:22 ht41 avahi-autoipd(eth0)[31049]: Successfully called chroot().
Sep 26 01:35:22 ht41 avahi-autoipd(eth0)[31049]: Successfully dropped root privileges.
Sep 26 01:35:22 ht41 avahi-autoipd(eth0)[31049]: Starting with address 169.254.5.161
Sep 26 01:35:27 ht41 avahi-autoipd(eth0)[31049]: Callout BIND, address 169.254.5.161 on interface eth0
Sep 26 01:35:27 ht41 avahi-daemon[5057]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.5.161.
Sep 26 01:35:27 ht41 avahi-daemon[5057]: New relevant interface eth0.IPv4 for mDNS.
Sep 26 01:35:27 ht41 avahi-daemon[5057]: Registering new address record for 169.254.5.161 on eth0.IPv4.
Sep 26 01:35:31 ht41 avahi-autoipd(eth0)[31049]: Successfully claimed IP address 169.254.5.161
Sep 26 01:35:32 ht41 NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface eth0 
Sep 26 01:35:32 ht41 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Sep 26 01:35:32 ht41 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Sep 26 01:35:32 ht41 NetworkManager: <info>  No DHCP reply received.  Automatically obtaining IP via Zeroconf. 
Sep 26 01:35:32 ht41 NetworkManager: <info>  avahi-autoipd running on eth0, assuming IPv4LL address 
Sep 26 01:35:32 ht41 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Sep 26 01:35:32 ht41 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
Sep 26 01:35:32 ht41 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Sep 26 01:35:32 ht41 NetworkManager: <info>  not touching eth0 configuration, was configured externally 
Sep 26 01:35:32 ht41 NetworkManager: <info>  Activation (eth0) successful, device activated. 
Sep 26 01:35:32 ht41 NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth0 
Sep 26 01:35:32 ht41 NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Sep 26 01:35:32 ht41 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Sep 26 01:35:37 ht41 avahi-autoipd(eth0)[31049]: A routable address has been configured.
Sep 26 01:35:37 ht41 avahi-autoipd(eth0)[31049]: Callout UNBIND, address 169.254.5.161 on interface eth0
Sep 26 01:35:37 ht41 avahi-daemon[5057]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.5.161.
Sep 26 01:35:37 ht41 avahi-daemon[5057]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.10.33.
Sep 26 01:35:37 ht41 avahi-daemon[5057]: Registering new address record for 192.168.10.33 on eth0.IPv4.
Sep 26 01:35:37 ht41 avahi-daemon[5057]: Withdrawing address record for 169.254.5.161 on eth0.
Sep 26 01:35:52 ht41 ntpdate[31094]: can't find host ntp.ubuntu.com 
Sep 26 01:35:52 ht41 ntpdate[31094]: no servers can be used, exiting

```

Ossec log:

```

** Alert 1222554500.0: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/dhclient.eth0.pid' present on /dev. Possible hidden file.

** Alert 1222554500.268: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/rpc.statd.pid' present on /dev. Possible hidden file.

** Alert 1222554500.534: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/sm-notify.pid' present on /dev. Possible hidden file.

** Alert 1222554500.800: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/portmap_mapping' present on /dev. Possible hidden file.

** Alert 1222554500.1068: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/sudo/fefekh/1' present on /dev. Possible hidden file.

** Alert 1222554500.1335: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/sudo/fefekh/0' present on /dev. Possible hidden file.

** Alert 1222554500.1602: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/sudo/fefekh/unknown' present on /dev. Possible hidden file.

** Alert 1222554500.1875: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/console/fefekh' present on /dev. Possible hidden file.

** Alert 1222554500.2143: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/crond.reboot' present on /dev. Possible hidden file.

** Alert 1222554500.2409: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/crond.pid' present on /dev. Possible hidden file.

** Alert 1222554500.2672: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/gdm.pid' present on /dev. Possible hidden file.

** Alert 1222554500.2933: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/console-kit-daemon.pid' present on /dev. Possible hidden file.

** Alert 1222554500.3209: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/hald/acl-list' present on /dev. Possible hidden file.

** Alert 1222554500.3476: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/hald/hald.pid' present on /dev. Possible hidden file.

** Alert 1222554500.3743: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/dhcdbd.pid' present on /dev. Possible hidden file.

** Alert 1222554500.4007: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/hotkey-setup' present on /dev. Possible hidden file.

** Alert 1222554500.4273: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/cups/printcap' present on /dev. Possible hidden file.

** Alert 1222554500.4540: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/avahi-daemon/checked_nameservers' present on /dev. Possible hidden file.

** Alert 1222554500.4826: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/avahi-daemon/pid' present on /dev. Possible hidden file.

** Alert 1222554500.5096: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/system-tools-backends.pid' present on /dev. Possible hidden file.

** Alert 1222554500.5375: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/NetworkManager/NetworkManagerDispatcher.pid' present on /dev. Possible hidden file.

** Alert 1222554500.5672: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/NetworkManager/NetworkManager.pid' present on /dev. Possible hidden file.

** Alert 1222554500.5959: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/dbus/pid' present on /dev. Possible hidden file.

** Alert 1222554500.6221: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/klogd/klogd.pid' present on /dev. Possible hidden file.

** Alert 1222554500.6490: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/klogd/kmsgpipe.pid' present on /dev. Possible hidden file.

** Alert 1222554500.6762: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/syslogd.pid' present on /dev. Possible hidden file.

** Alert 1222554500.7027: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/PolicyKit/user-fefekh.auths' present on /dev. Possible hidden file.

** Alert 1222554500.7308: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/motd' present on /dev. Possible hidden file.

** Alert 1222554500.7566: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/utmp' present on /dev. Possible hidden file.

** Alert 1222554500.7824: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/network/ifstate' present on /dev. Possible hidden file.

** Alert 1222554500.8093: mail  - ossec,rootcheck,
2008 Sep 28 00:28:20 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
File '/dev/shm/var.run/sendsigs.omit' present on /dev. Possible hidden file.

** Alert 1222554996.8360: mail  - ossec,rootcheck,
2008 Sep 28 00:36:36 ht41->rootcheck
Rule: 510 (level 7) -> 'Host-based anomaly detection event (rootcheck).'
Src IP: (none)
User: (none)
Port '953'(tcp) hidden. Kernel-level rootkit or trojaned version of netstat.

** Alert 1222556559.8627: mail  - syslog,errors,
2008 Sep 28 01:02:39 ht41->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Sep 28 01:02:38 ht41 NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed

** Alert 1222556559.8912: mail  - syslog,errors,
2008 Sep 28 01:02:39 ht41->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Sep 28 01:02:38 ht41 NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed

** Alert 1222557761.9198: - syslog,sudo
2008 Sep 28 01:22:41 ht41->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: fefekh
Sep 28 01:22:41 ht41 sudo:   fefekh : TTY=pts/0 ; PWD=/home/fefekh ; USER=root ; COMMAND=/bin/su

** Alert 1222557761.9468: - pam,syslog,authentication_success,
2008 Sep 28 01:22:41 ht41->/var/log/auth.log
Rule: 5501 (level 3) -> 'Login session opened.'
Src IP: (none)
User: (none)
Sep 28 01:22:41 ht41 sudo: pam_unix(sudo:session): session opened for user root by fefekh(uid=0)

** Alert 1222557761.9750: - pam,syslog,
2008 Sep 28 01:22:41 ht41->/var/log/auth.log
Rule: 5502 (level 3) -> 'Login session closed.'
Src IP: (none)
User: (none)
Sep 28 01:22:41 ht41 sudo: pam_unix(sudo:session): session closed for user root

** Alert 1222557761.9992: - syslog, su,authentication_success,
2008 Sep 28 01:22:41 ht41->/var/log/auth.log
Rule: 5303 (level 3) -> 'User successfully changed UID to root.'
Src IP: (none)
User: (none)
Sep 28 01:22:41 ht41 su[27516]: + pts/0 root:root

** Alert 1222557761.10244: - syslog, su,authentication_success,
2008 Sep 28 01:22:41 ht41->/var/log/auth.log
Rule: 5303 (level 3) -> 'User successfully changed UID to root.'
Src IP: (none)
User: (none)
Sep 28 01:22:41 ht41 su[27516]: pam_unix(su:session): session opened for user root by fefekh(uid=0)

```

---

### Post by wirelessmonkey on 2008-09-28
There is absolutely nothing in any of the 3 posted logs that indicates a hack.  It does look like there may be a problem with your interface (eth0) or dhcp server, such that your connection fails and attempts to reconnect. Do 2 machines on your network have the same IP address?  Is your etheret cable in good condition? 
_
Your ossec logs may seem scary at a few points, but a quick google showed that they are normal false positives on Debian distros.
_

Please post more logs that contain information that concerns you, I'll address them as I'm able.
_

I suggest that you disable your wireless interface until you feel that your concerns have been addressed sufficiently.

---

### Post by ekh on 2008-09-28
> **wirelessmonkey said:**
> There is absolutely nothing in any of the 3 posted logs that indicates a hack.  It does look like there may be a problem with your interface (eth0) or dhcp server, such that your connection fails and attempts to reconnect. Do 2 machines on your network have the same IP address?  Is your etheret cable in good condition?

I have 2 undeniable indications, that I have been attacked:

1. I loose the ability as root to copy data from the harddisk to an usb device.
2. Luks stops to work, In previous attacks vith the same behavior it is possible to use the computer if I don't try to access the logs. If I do, the permissions gets changed, so I cant mount usb devices, or copy to them, if already mounted. At next boot LUKS is broken.

I have found that by only being connected to the internet while I need to communicate, prolongs the time to next attack. So when I constantly connect and disconnect the ethernet cable, then it is visible in the log. Sorry I did not mention this. 

> **wirelessmonkey said:**
> _
Your ossec logs may seem scary at a few points, but a quick google showed that they are normal false positives on Debian distros.

If they are false positives, I don't have much clue where to look. Perhaps I should make a new install without LUKS.


> **wirelessmonkey said:**
> 
Please post more logs that contain information that concerns you, I'll address them as I'm able.

Thank you very much, unfortunately I have no experience in where to look. I will study more logs and post what I find suspecious.
_
> **wirelessmonkey said:**
> 
I suggest that you disable your wireless interface until you feel that your concerns have been addressed sufficiently.

I never use wireless internet because of the health hazard, an I'm lucky to not to live in a large city with high levels of "electrosmog". A German professor has stated that there is hard evidence that WiFi, 3G, DECT and GSM is harmful to human health. So security with wireless is no issue for me. The German car manufacturer BMW has addressed these issues.

I saw that a 3G phone is able to cut DNA strings at 2,5% of max. allowed transmission power. 

[http://www.der-mast-muss-weg.de/016dectWLAN01.htm](http://www.der-mast-muss-weg.de/016dectWLAN01.htm)

The problem is lots of money for the telecommunication companies, that severely affects what truth is.

---

### Post by Amarsingh0793 on 2008-09-28
How did you install Ubuntu? Using Ubuntu's free-shipit discs are the best way to install a fresj clean ubuntu without problems. If you burned a disc, it might be corrupt or not burned correctly. By the way, you can file bugs at launchpad.

---

### Post by ekh on 2008-09-28
> **Amarsingh0793 said:**
> How did you install Ubuntu? Using Ubuntu's free-shipit discs are the best way to install a fresj clean ubuntu without problems. If you burned a disc, it might be corrupt or not burned correctly. By the way, you can file bugs at launchpad.

Thank you for the advice, unfortunately I can not point out a bug.

Install procedure:

I download the alternate 8.04.1 .iso and the checksums. The checksums is additionally downloaded with Tor ([www.polippix.org](www.polippix.org)) just to be sure they are correct.

I burn the iso and do a md5sum and verify.

Before I install, I check the CD for defects, so I'm sure it reads correctly on the actual computer.

The install is done without internet connected.

I do some hardening stuff (kernel and TCP stack), and remove some user accounts from /etc/passwd

I modify /etc/apt/sources.list, so it is like it was installed with internet connected.

internet connected:

apt-get update
apt-get upgrade
apt-get dist-upgrade

apt-get install libc6  (needed by ossec)

internet disconnected:

Install a checksum verified Ossec 1.6 as stand alone.

Internet connected:

Installed Thunderbird, noscript, adblock plus.
Restore the Thunderbird database.

Installed NFS
Installed RapidSVN
used netstat to verify I have no open ports.
Installed fwbuilder and installed the compiled script to run at boot time.

Internet disconnected:


Turn off power.

Remove original harddisk 

Boot from 8.04.1 live CD

usb mount harddisk seen as /dev/sda   (original)
usb mount extra HW identical harddisk seen as /dev/sdb  (copy)

dd if=/dev/sda of=/dev/sdb bs=16384   (verbatim disk copy)

store the original harddisk for later use

insert the copy for use in the computer
Boot from the copy harddisk

Wait for the attack to happen, If connected to the internet all the time, this happens in less than a day.

I have seen this specific attack type behavior on:

A Medion MD40100
A Lenovo T30
A Lenovo T41

And also one OpenBSD 4.3 install did not stand the pressure. I have to say it was an extended install, to be useful.

I also suffered from a ssh attack to my server 6 weeks ago. This server had an Ubuntu desktop, not so smart, and also I did trust the original install without using netstat. I had been running for about 6 months before attacked.

---

### Post by stmurray on 2008-09-29
The avahi and dhcpclient logs are exactly how they would expect to be if an interface loses connectivity.  The interface goes down and when it is seen to be back up again it tries to get its old IP reservation back.  In the logs, no DHCP server responds, so dhcpclient gives an address in the 169.xxx.xxx.xxx range (which is reserved for hosts that can't get an IP address any other way).

Your issues may both be harddrive issues that don't present themselves until the system has been running for a while (maybe because there is some bug using dd and using IDE drives in a USB interface???)

1)  When you say you can't copy to USB devices, what error are you getting?  

2)  Why aren't you using the original disk and storing the copy?

---

### Post by Yannick Le Saint kyncani on 2008-09-29
Hi Ekh, I don't think you're being attacked, relax.

You could check the integrity of your files (google is your friend) by creating md5sums for all your files before and after the general failure, then check which have changed.

Also, forget about luks until you have a working setup.

---

### Post by ekh on 2008-09-29
> **stmurray said:**
> The avahi and dhcpclient logs are exactly how they would expect to be if an interface loses connectivity.  The interface goes down and when it is seen to be back up again it tries to get its old IP reservation back.  In the logs, no DHCP server responds, so dhcpclient gives an address in the 169.xxx.xxx.xxx range (which is reserved for hosts that can't get an IP address any other way).

Your issues may both be harddrive issues that don't present themselves until the system has been running for a while (maybe because there is some bug using dd and using IDE drives in a USB interface???)

1)  When you say you can't copy to USB devices, what error are you getting?  

2)  Why aren't you using the original disk and storing the copy?

Thank you for interpreting the DHCP logs.

The harddisks are 2 weeks old, but now I will use the original as it is.
I bought 4 identical disks 2.5 inch Hitachi 160GB, I have many disk like these and have used then for more than a year without problems, and they behave the same "failure".

The same eror on more identical disks is possible but in my opinion unlikely.

Your questions:

1) I cant remember the exact error message, but it was something about the device not configured, but it worked OK on another Ubuntu.

There have been some cases where root did not have permission to copy. 

And there was this latest try with the cp program from an Identical Ubuntu:

```

root@ht41:/media/disk-1# ./cp -r --copy-contents -L /bin /media/disk-2/bin
root@ht41:/media/disk-1# ./cp -r --copy-contents -L /usr/bin /media/disk-2/usr/bin
./cp: cannot create directory `/media/disk-2/usr/bin': No such file or directory
root@ht41:/media/disk-1# ./cp -r --copy-contents -L /usr/sbin /media/disk-2/usr/sbin
./cp: cannot create directory `/media/disk-2/usr/sbin': No such file or directory
root@ht41:/media/disk-1# 


```

2) If I do that, I don't know if the copy was successful, I feel more confident making copies from the original.

I will do a fresh install without LUKS on the disk I see as infected"copy", or maybe I should buy more disks so I maybe later can open the disk again. 

I did look up the document on LUKS and copied the 2 first blocks from the original harddisk to the copy harddisk, but it say that the password may be wrong.

I have not tried to boot from the infected disk.

I think it may be a problem with the selected keyboard. Remember I have Danish keyboard layout, and I'm not sure if the selected layout at boot time is identical to the layout when running with Danish language from the 8.04.1 desktop live CD. 

This is the layout used to input my password involving keys that are not identical on us and dk layouts.

---

### Post by ekh on 2008-09-29
> **Yannick Le Saint kyncani said:**
> Hi Ekh, I don't think you're being attacked, relax.

Thank you for your suggestions.

I wish you were right on this one.

Apart from the Ubuntu related stuff, I also see other problems.

I have traded a lot on ebay for 3 years, no sweat. When my trouble started, I could not log into ebay, yahoo or my netbank.

Using the polippix CD I can log into ebay, without Tor, no way, having entered my username and password, I just get a new login page.

Also other surfing involving https does not work without Tor.

> **Yannick Le Saint kyncani said:**
> 
You could check the integrity of your files (google is your friend) by creating md5sums for all your files before and after the general failure, then check which have changed.

Sure, google is a very effective search machine, but also a very effective data miner with personal information. My friend...maybe...

I checked synaptic, and there are several choices for integrity test, I installed debsums on the original harddisk. Do your system generate similar output ?

The system is up to date.

> **Yannick Le Saint kyncani said:**
> 
Also, forget about luks until you have a working setup.

Except from ossec added, I have been running OK with LUKS since the 8.04 release, except from the last 5 weeks.

```

fefekh@ht41:~$ sudo debsums | grep FAILED
debsums: no md5sums for at
debsums: no md5sums for base-files
debsums: no md5sums for binutils
debsums: no md5sums for binutils-static
debsums: no md5sums for bogofilter
debsums: no md5sums for bzip2
debsums: no md5sums for dosfstools
debsums: no md5sums for ed
debsums: no md5sums for gnupg
debsums: no md5sums for gpgv
debsums: no md5sums for initscripts
debsums: no md5sums for installation-report
debsums: no md5sums for klogd
debsums: no md5sums for libbz2-1.0
debsums: no md5sums for libgdbm3
debsums: no md5sums for libncurses5
debsums: no md5sums for libncursesw5
/lib/modules/2.6.24-19-generic/modules.pcimap                             FAILED
/lib/modules/2.6.24-19-generic/modules.dep                                FAILED
/lib/modules/2.6.24-19-generic/modules.ieee1394map                        FAILED
/lib/modules/2.6.24-19-generic/modules.usbmap                             FAILED
/lib/modules/2.6.24-19-generic/modules.isapnpmap                          FAILED
/lib/modules/2.6.24-19-generic/modules.inputmap                           FAILED
/lib/modules/2.6.24-19-generic/modules.seriomap                           FAILED
/lib/modules/2.6.24-19-generic/modules.alias                              FAILED
/lib/modules/2.6.24-19-generic/modules.symbols                            FAILED
debsums: no md5sums for mawk
debsums: no md5sums for mime-support
debsums: no md5sums for module-init-tools
debsums: no md5sums for ncurses-base
debsums: no md5sums for ncurses-bin
debsums: no md5sums for netbase
debsums: no md5sums for rsync
debsums: no md5sums for startup-tasks
debsums: no md5sums for strace
debsums: no md5sums for sysklogd
debsums: no md5sums for sysv-rc
debsums: no md5sums for sysvutils
debsums: no md5sums for ubuntu-keyring
debsums: no md5sums for update-inetd
debsums: no md5sums for whois
debsums: no md5sums for xbase-clients
debsums: no md5sums for xorg
debsums: no md5sums for xserver-xorg
debsums: no md5sums for xserver-xorg-input-all
debsums: no md5sums for xserver-xorg-video-all
debsums: no md5sums for xutils
fefekh@ht41:~$


```

---

### Post by ekh on 2008-09-29
Edit: Deleted double post

---

### Post by Yannick Le Saint kyncani on 2008-09-29
Ekh :

- You cannot use debsums from a supposingly infected host, it holds no value. Md5sums are simply stored in /var/lib/dpkg/info/*.md5sums and these can/should be changed if a binary has been added/replaced.

- The output debsums reported looks normal as far as debsums goes I think. Debsums's output has little meaning I have found (from memory).

- So you have to md5sum by hand your entire installation before an attack, store these md5sum set A on a safe media, and after the attack, run md5sum again from a safe system (a livecd ?) to get md5sum set B, then compare sets A and B to find out which files have changed.

Edit: You seemed to imply that luks caused you problems to analyze the situation. Luks is not needed for protection against a distant attacker. It protects data from someone who has physical access to a hard drive when the filesystem is not mounted. So if you have trouble with luks, dump it as it won't help you in your case. When you know you are not being attacked, then you can encrypt everything again.

---

### Post by Excalibre on 2008-09-30
It's frankly obvious that this person has some kind of mental health issue -- the obsession with computer security and constant belief that their computer is compromised, the bizarre beliefs about imagined health effects from wireless internet, etc. There's really no point in trying to work out what's actually happening or explain that it's not an attack, because they didn't come up with the idea through rational thought.

I don't mean to offend and I don't imagine that ekh is going to seek psychiatric help on my advice, but what is the point of this thread continuing?

---

### Post by Yannick Le Saint kyncani on 2008-09-30
Excalibre, you're runing it !

---

### Post by ekh on 2008-09-30
> **Excalibre said:**
> It's frankly obvious that this person has some kind of mental health issue -- the obsession with computer security and constant belief that their computer is compromised, the bizarre beliefs about imagined health effects from wireless internet, etc. There's really no point in trying to work out what's actually happening or explain that it's not an attack, because they didn't come up with the idea through rational thought.

I don't mean to offend and I don't imagine that ekh is going to seek psychiatric help on my advice, but what is the point of this thread continuing?

When my computer stops working so I can't work as a developer, now for 5 weeks, computer security becomes an "obsession". How can I as a developer earn a living without a functional computer ?

Regarding the health issues I gave a link which enables the reader to access extensive research, research which has been considered valid by the EU authority.

Please explain for yourself how this referring relates to my personal mental health, and what about the mental health of the researchers and the EU authority ? 

I don't know how old you are and how much you know.

Let me give 2 examples where some people was insulted by strong economic interests.

How did tobacco start and how has it ended ? 

20 years ago a Danish doctor with last name "Foss" being on the tobacco companys paylist ridiculed people stating that smoking is harmful to your health. One year ago the Danish government made a law forbidding smoking in public indoor places. Was the people giving early warnings suffering mental health problems ? The official estimated yearly deaths related to tobacco in Denmark is 12.000.

Longer back in time a Danish company produced roofs containing asbestos. Early warnings was suppressed, but after many years of research documenting the health hazard and persistent pressure from a worker union, asbestos got classified as dangerous.

Today only environmental specialist companies are allowed to remove the roofs.

Frankly your post is OT and ought to be reported, but I choose to believe you and let lack of knowledge explain your bad behavior.

By the way I think I feel lucky that despite my "because they didn't come up with the idea through rational thought" characterization has been able to work as an embedded developer for 22 years in 5 companies and now creating jobs in my own company.

I wish you the best for your future !

---

### Post by ekh on 2008-09-30
> **Yannick Le Saint kyncani said:**
> Ekh :

- You cannot use debsums from a supposingly infected host, it holds no value. Md5sums are simply stored in /var/lib/dpkg/info/*.md5sums and these can/should be changed if a binary has been added/replaced.

- The output debsums reported looks normal as far as debsums goes I think. Debsums's output has little meaning I have found (from memory).

- So you have to md5sum by hand your entire installation before an attack, store these md5sum set A on a safe media, and after the attack, run md5sum again from a safe system (a livecd ?) to get md5sum set B, then compare sets A and B to find out which files have changed.

Thinking about the detection process you describe it is not so easy to do.

1. The system must be installed and updated before making set A.
2. What if a security update appears before an attack ? It does not make sense to monitor a system not up-to date.
3. If the system has to be updated, then it is necessary to shut down all other internet access to exclude the possibility of an attack during the update.
4. The same holds for the first update

The original disk has only been connected during update and the few program installs mentioned previously. If already infected at this stage it is not so easy.

> **Yannick Le Saint kyncani said:**
> Edit: You seemed to imply that luks caused you problems to analyze the situation. Luks is not needed for protection against a distant attacker. It protects data from someone who has physical access to a hard drive when the filesystem is not mounted. So if you have trouble with luks, dump it as it won't help you in your case. When you know you are not being attacked, then you can encrypt everything again.

I agree, and I did also mention that previously.

From now on my installs will be only experimental, so I skip luks.

Additionally trying to do forensics on an attacked system in my opinion requires much experience with examining infected disks, because the attackers may be very skilled hiding their traces. I don't have that experience. I have a saying that no one can be committed beyond their skills.

Except from the gained security knowledge, the last 5 weeks has been waste of time.

I will now try a different solution to my IT infrastructure.

Thank you all for your help.

Ps. Was your statement "Excalibre, you're runing it !" positive or negative for me, I can't tell the difference, as English is not my first language.

---

### Post by Excalibre on 2008-09-30
> **ekh said:**
> 20 years ago a Danish doctor with last name "Foss" being on the tobacco companys paylist ridiculed people stating that smoking is harmful to your health. One year ago the Danish government made a law forbidding smoking in public indoor places. Was the people giving early warnings suffering mental health problems ? The official estimated yearly deaths related to tobacco in Denmark is 12.000.
Really? In 1988? In Denmark?

Wow, Denmark must be basically a third world country, since that's at least 20 years after the dangers of smoking were widely understood in the civilized world.

---

### Post by ynell on 2008-09-30
Dude.. your not under attack.. chill out.. just get yourself a nice 128 bit wireless key and take a deep breath..

coming from an "embedded developer" with "22 years of experience" you should know SOMETHING of security and that if everyone is telling you that everything is ok.. chances are.. everything is ok.

if your afraid google is mining all your data then don't search anything you don't want people to know about if your so paranoid.. 



even after everything is said and done.. such a "successful 22 year developer vet" should know that if your doing something of such vast importance on your computer to at least back everything up and/or have a second ready and able computer.

---

### Post by Washer on 2008-09-30
> **ekh said:**
> Ps. Was your statement "Excalibre, you're runing it !" positive or negative for me, I can't tell the difference, as English is not my first language.
negative

although .... re-downloading the checksums with Tor? Dude..

---

### Post by RFXCasey on 2008-09-30
I would just like to add my 2 cents and say that I think we will all agree that this is one of the few peopler in the whole world that would probably be better off using Microsoft Windows. And just because you can develope and have read articles pertaining to the harmful effects for ES radiation this does not conclusively eliminate the posibility that he may be a delusional paranoid schizophrenic with an acute case of obsessive compulsive disorder. Oh yeah I almost forgot Mr. Developer. The last time the aliens from planet Zorg came to visit us they brought us knowledge of a technology that they created just for combatting such "Attacks". It's called a hardware firewall. Just blinking GOOGLE it and for goodness sake man, will you take the freaking tin foil wrap off your head.

---

### Post by RFXCasey on 2008-09-30
Can I get a witness??????

---

### Post by ekh on 2008-10-01
> **ynell said:**
> Dude.. your not under attack.. chill out.. just get yourself a nice 128 bit wireless key and take a deep breath..

coming from an "embedded developer" with "22 years of experience" you should know SOMETHING of security and that if everyone is telling you that everything is ok.. chances are.. everything is ok.

if your afraid google is mining all your data then don't search anything you don't want people to know about if your so paranoid.. 



even after everything is said and done.. such a "successful 22 year developer vet" should know that if your doing something of such vast importance on your computer to at least back everything up and/or have a second ready and able computer.

I do know something about security, but not enough, and yes chances are everything got OK lately.

Stored data can be misused. And why should a search machine company log so much for so long ? This has been questioned in several Danish articles.

I can assure you I have all the backups I need. I have lost no data, "just" time. Unfortunately my server was involved, so I have no subversion I trust. I have only one operational subversion server. But as I told I installed a new one a few days ago.

I have two computers not on the net and they have worked all the time.
I have tested using 4 computers on the internet.

I have had problems with both my computers and with my internet line.

My wife has the option of working at home. Her company uses a router/firewall, and she goes through VPN to connect to the company.
We have experienced that a newly company tested router/computer did not get access at our place when none of my equipment was connected and internet provider technician could see the provider ADSL router operational.

At the first attacks I saw the system monitor showning traffic approaching 100kByte/s
on attacked computers.

I then started using Ossec which has given both alerts and false positives. Having so much traffic on an not used computer makes Ossecs alerts look trustworthy, I did not question that.

After post #8 I started thinking about the possibility of no attacks. After installing a computer, I got some new security updates. This computer still gives ossec alerts, but the internet traffic is back to a normal pattern.

And yes, I need to calm down, what I have been through has been no fun.

We have computers in two separate rooms, and two routers for the same reason. Both are running WW-DRT and is firewalling my traffic. So most of the time I have been behind 2 firewalls as told in a previous thread.

So RFXCasey, if you wrote less and searched more you did't need to write 

[QUOTE=RFXCasey]
It's called a hardware firewall. Just @#$%@#ing GOOGLE it
[/QUOTE]

Talking about GOOGLE have you ever searched this:

[http://atlas.cc.itu.edu.tr/~tayfunakgul/ieee_code_of_ethics.htm](http://atlas.cc.itu.edu.tr/~tayfunakgul/ieee_code_of_ethics.htm)

----

Now I will monitor my latest install for some more days. As pointed out by several It may be over now, so I'm no longer attacked, at least not by hackers.

If Ubuntu forum support includes this type of "help", I must say I for the moment prefer allocating the necessary amount of time to do background reading, and mind my own business. That will be more constructive than writing posts like this.

I will express my thanks to all of you who helped me. I have no more to add.

@Moderator

Please consider closing this thread.

---

### Post by RFXCasey on 2008-10-01
Hey ekh, cool your jets man. I was just having some fun. I mean, when I was typing that at work I almost couldn't control myself. The people in the other cubicles must think I was crazy laughing out loud to myself. I mean common, even a dutchmen could see that that was hilarious.:D No hard feeling.

---

