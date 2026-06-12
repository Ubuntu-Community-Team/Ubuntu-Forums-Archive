---
title: "Suddenly becomes impossible to connect to"
date: 2008-09-04
forum: Server Platforms
---

### Post by t.roijers on 2008-09-04
Hello,

recently we moved our webhosting from Suse to Ubuntu.

I'm running Ubuntu Server 8.04.1 with kernel 2.6.24-19-server on a Intel S3000AH server board. The server runs perfect for about 20 minutes when it becomes unavailable. Sometimes it's possible to ping it's IP address but the ssh, ftp, http seems to be dead. nmap -r localhost shows the ports are all open.

The only way to get it running again is /etc/init.d/networking restart.

The server has 1 onboard nic and two PCI 3com NIC. This is the inferface file:

# The loopback network interface
auto lo
iface lo inet loopback

# ISP1
auto eth0
iface eth0 inet static
        address 212.115.204.36
        netmask 255.255.255.240
        gateway 212.115.204.33

# LOCAL LAN
auto eth1
iface eth1 inet static
        address 10.1.1.19
        netmask 255.255.255.0
        gateway 10.1.1.14

# ISP2
auto eth3
iface eth3 inet static
        address 172.16.0.18
        netmask 255.255.255.0
        gateway 172.16.0.5

I can connect with ssh to the local lan port but it takes forever to login, the two ISP ports are not responding to anything but a ping.

This is what is see in /var/log/syslog when the networks stalls and i manually restart the network

Sep  4 20:33:33 isp1 ntpd[5550]: Listening on interface #8 eth3, 172.16.0.18#123 Enabled
Sep  4 20:33:33 isp1 ntpd[5550]: kernel time sync status 0040
Sep  4 20:33:33 isp1 ntpd[5550]: frequency initialized 29.385 PPM from /var/lib/ntp/ntp.drift
Sep  4 20:33:34 isp1 ntpd[5550]: Listening on interface #9 eth0, fe80::215:17ff:fe67:cbdc#123 Enabled
Sep  4 20:33:36 isp1 ntpdate[5363]: the NTP socket is in use, exiting
Sep  4 20:33:36 isp1 ntpdate[5445]: the NTP socket is in use, exiting
Sep  4 20:33:41 isp1 kernel: [106296.312541] eth1: no IPv6 routers present
Sep  4 20:33:42 isp1 kernel: [106296.731459] eth0: no IPv6 routers present
Sep  4 20:36:48 isp1 ntpd[5550]: synchronized to 91.189.94.4, stratum 2
Sep  4 20:36:48 isp1 ntpd[5550]: kernel time sync status change 0001
Sep  4 20:39:01 isp1 /USR/SBIN/CRON[5666]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Sep  4 20:58:39 isp1 -- MARK --
Sep  4 21:00:01 isp1 /USR/SBIN/CRON[6261]: (root) CMD (/root/ispconfig/php/php /root/ispconfig/scripts/shell/check_services.php &> /dev/null)
Sep  4 21:09:01 isp1 /USR/SBIN/CRON[6375]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Sep  4 21:10:05 isp1 ntpd[5550]: no servers reachable
Sep  4 21:17:01 isp1 /USR/SBIN/CRON[6486]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  4 21:22:54 isp1 ntpd[5550]: synchronized to 91.189.94.4, stratum 2
Sep  4 21:30:01 isp1 /USR/SBIN/CRON[7257]: (root) CMD (/root/ispconfig/php/php /root/ispconfig/scripts/shell/check_services.php &> /dev/null)
Sep  4 21:39:01 isp1 /USR/SBIN/CRON[7374]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Sep  4 21:48:35 isp1 ntpd[5550]: no servers reachable
Sep  4 21:52:35 isp1 postfix/master[19119]: reload configuration /etc/postfix
Sep  4 21:52:35 isp1 last message repeated 2 times
Sep  4 21:52:35 isp1 kernel: [111018.267365] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep  4 21:52:35 isp1 ntpd[5550]: ntpd exiting on signal 15
Sep  4 21:52:35 isp1 postfix/master[19119]: reload configuration /etc/postfix
Sep  4 21:52:35 isp1 kernel: [111018.391852] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep  4 21:52:35 isp1 kernel: [111018.400818] e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex
Sep  4 21:52:35 isp1 kernel: [111018.402017] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Sep  4 21:52:36 isp1 postfix/master[19119]: reload configuration /etc/postfix
Sep  4 21:52:36 isp1 kernel: [111018.474386] eth3:  setting half-duplex.
Sep  4 21:52:36 isp1 kernel: [111018.475566] ADDRCONF(NETDEV_UP): eth3: link is not ready
Sep  4 21:52:36 isp1 postfix/master[19119]: reload configuration /etc/postfix
Sep  4 21:52:37 isp1 kernel: [111019.764527] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Sep  4 21:52:37 isp1 kernel: [111019.764530] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
Sep  4 21:52:37 isp1 kernel: [111019.766097] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Sep  4 21:52:38 isp1 ntpdate[7731]: step time server 91.189.94.4 offset -0.000917 sec
Sep  4 21:52:38 isp1 ntpd[7925]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Sep  4 21:52:38 isp1 ntpd[7926]: precision = 1.000 usec
Sep  4 21:52:38 isp1 ntpd[7926]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Sep  4 21:52:38 isp1 ntpd[7926]: Listening on interface #1 wildcard, ::#123 Disabled
Sep  4 21:52:38 isp1 ntpd[7926]: Listening on interface #2 lo, ::1#123 Enabled
Sep  4 21:52:38 isp1 ntpd[7926]: Listening on interface #3 eth1, fe80::202:b3ff:fe2b:98b9#123 Enabled
Sep  4 21:52:38 isp1 ntpd[7926]: bind() fd 20, family 10, port 123, scope 3, addr fe80::215:17ff:fe67:cbdc, in6_is_addr_multicast=0 flags=0x11 fails: Cannot assign requested address



I don't know what is happening, but i hope you can help me out.
I'm more than happy to provide more info if needed.

Tim Roijers

---

### Post by t.roijers on 2008-09-05
Well find the problem myself, remove 2 out of the three gateways and the problem was solved.. 


# LOCAL LAN
auto eth0
iface eth0 inet static
address 10.1.1.19
netmask 255.255.255.0
[COLOR="Lime"]gateway 10.1.1.14[/COLOR]

# ISP1
auto eth1
iface eth1 inet static
address 212.115.204.36
netmask 255.255.255.240
[COLOR="Red"]gateway 212.115.204.33[/COLOR]

# ISP2
auto eth2
iface eth2 inet static
address 172.16.0.18
netmask 255.255.255.0
[COLOR="Red"]gateway 172.16.0.5[/COLOR]


Installed iproute to route packets to the right gateways.

Tim Roijers

---

