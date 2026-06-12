---
title: "Trying, failing, to setup up PXE server"
date: 2015-01-07
forum: Server Platforms
---

### Post by tyler40 on 2015-01-07
Hi everyone.  So at the place I work we have a pxe server that we use to boot client machines with (ie, hook machine to network, pxe boot, select tool needed through pxeknife menu, tool is loaded from server).  Sadly the server died last week.  

I'm trying to get a new one setup but can't get things rolling.  Obviously new to this so keep that in mind!  Any help/tips/suggestions greatly appreciated, thanks!

[COLOR=#000000][FONT=verdana]Here is my /etc/default/tftpd-hpa:[/FONT][/COLOR][INDENT]RUN_DAEMON="yes"
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/var/lib/tftpboot"
TFTP_ADDRESS="[10.1.10.156]:69"
TFTP_OPTIONS="--secure"
INTERFACES="eth0"
OPTIONS="-l -s /var/lib/tftpboot"
[/INDENT]
[COLOR=#000000][FONT=verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=verdana]inetd.conf:[/FONT][/COLOR][INDENT]tftp dgram udp wait root /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot
9571 stream tcp nowait nobody /usr/sbin/tcpd /usr/sbin/ldminfod
9572 stream tcp nowait nobody /usr/sbin/tcpd /usr/sbin/sbdswapd
2000 stream tcp nowait nobody /usr/sbin/tcpd /usr/sbin/nbdrootd /opt/ltsp/images/i386.img


[/INDENT]
[COLOR=#000000][FONT=verdana]dhcpd.conf:[/FONT][/COLOR][INDENT]subnet 10.1.10.0 netmask 255.255.255.0 {
max-lease-time 21600;
default-lease-time 14400;
authorative;
allow client-updates;
option domain-name "xxxxxx.com";
option broadcast-address 10.1.10.255;
option domain-name-servers 10.1.10.1;
next-server 10.1.10.242
filename "/pxelinux.0"
range 10.1.10.10 10.1.10.219;
option routers 10.1.10.1;
range dynamic-bootp 10.1.10.220 10.1.10.240;
}  

[/INDENT]

---

### Post by newbie-user on 2015-01-09
In dhcpd.conf, filename line should be:

*filename = "pxelinux.0";*

---

### Post by seans2 on 2015-06-11
Hi.  Did this resolve the problem?

---

