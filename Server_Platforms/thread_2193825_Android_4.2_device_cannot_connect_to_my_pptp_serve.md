---
title: "Android 4.2 device cannot connect to my pptp server"
date: 2013-12-14
forum: Server Platforms
---

### Post by lethalfang on 2013-12-14
I've set up a pptp server, and iOS7 devices and my linux laptop can connect to it, but my Android device cannot. 
Anyone with any ideas?

Here is the syslog after I enabled debug:

```

 pptpd[3110]: CTRL: Client 58.35.14.99 control connection started
 pptpd[3110]: CTRL: Starting call (launching pppd, opening GRE)
 pppd[3111]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
 pppd[3111]: pptpd-logwtmp: $Version$
 pppd[3111]: pppd 2.4.5 started by root, uid 0
 pppd[3111]: using channel 16
 pppd[3111]: Using interface ppp1
 NetworkManager[1159]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
 pppd[3111]: Connect: ppp1 <--> /dev/pts/4
 NetworkManager[1159]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp1, iface: ppp1): no ifupdown configuration found.
 pppd[3111]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0xa9fbf5aa> <pcomp> <accomp>]
 pptpd[3110]: GRE: Bad checksum from pppd.
 pppd[3111]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0xa9fbf5aa> <pcomp> <accomp>]
 pppd[3111]: last message repeated 8 times
 pppd[3111]: LCP: timeout sending Config-Requests
 pppd[3111]: Connection terminated.
 avahi-daemon[1101]: Withdrawing workstation service for ppp1.
 NetworkManager[1159]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
 pppd[3111]: Modem hangup
 pppd[3111]: Exit.
 pptpd[3110]: GRE: read(fd=6,buffer=6075a0,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
 pptpd[3110]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
 pptpd[3110]: CTRL: Reaping child PPP[3111]
 pptpd[3110]: CTRL: Client 58.35.14.99 control connection finished


```



Here is the pptpd-option:

```
name pptpd
refuse-pap
refuse-chap
refuse-mschap
require-mschap-v2
require-mppe-128
ms-dns 128.218.87.135
ms-dns 128.218.241.16
ms-wins 128.218.87.135
ms-wins 128.218.241.16
proxyarp
nodefaultroute
debug
lock
nobsdcomp 
noipx

```

And the pptpd.conf:
```
option /etc/ppp/pptpd-options
logwtmp
localip 192.168.11.1
remoteip 192.168.11.201-238,192.168.11.245

```


Any idea why the Android device failed where everything else succeeded?
Thanks.

---

