---
title: "PPTPD and Windows Connecting problem?"
date: 2008-04-26
forum: Server Platforms
---

### Post by amfpg on 2008-04-26
i have installed PPTPD at Ubuntu 7.10 for my vpn server, this server has running.

i have tried to connect  from windows xp machine, but i got a problem, because windows report duplicate computer name,

[[img]http://img2.freeimagehosting.net/uploads/c8674a91f5.jpg[/img]](http://www.freeimagehosting.net/)

i have tried to change computer name, but the problems still same.

this output from /var/log/message

```

Apr 27 07:12:53 gateway pppd[4337]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Apr 27 07:12:53 gateway pppd[4337]: pptpd-logwtmp: $Version$
Apr 27 07:12:53 gateway pppd[4337]: pppd options in effect:
Apr 27 07:12:53 gateway pppd[4337]: debug^I^I# (from /etc/ppp/pptpd-options)
Apr 27 07:12:53 gateway pppd[4337]: dump^I^I# (from /etc/ppp/pptpd-options)
Apr 27 07:12:53 gateway pppd[4337]: plugin /usr/lib/pptpd/pptpd-logwtmp.so^I^I# (from command line)
Apr 27 07:12:53 gateway pppd[4337]: require-mschap-v2^I^I# (from /etc/ppp/pptpd-options)
Apr 27 07:12:53 gateway pppd[4337]: refuse-pap^I^I# (from /etc/ppp/pptpd-options)
Apr 27 07:12:53 gateway pppd[4337]: refuse-chap^I^I# (from /etc/ppp/pptpd-options)
Apr 27 07:12:53 gateway pppd[4337]: refuse-mschap^I^I# (from /etc/ppp/pptpd-options)
Apr 27 07:12:53 gateway pppd[4337]: name pptpd^I^I# (from /etc/ppp/pptpd-options)
Apr 27 07:12:53 gateway pppd[4337]: pptpd-original-ip 192.168.0.20^I^I# (from command line)
Apr 27 07:12:53 gateway pppd[4337]: 115200^I^I# (from command line)
Apr 27 07:12:53 gateway pppd[4337]: lock^I^I# (from /etc/ppp/pptpd-options)
Apr 27 07:12:53 gateway pppd[4337]: crtscts^I^I# (from /etc/ppp/options)
Apr 27 07:12:53 gateway pppd[4337]: local^I^I# (from command line)
Apr 27 07:12:53 gateway pppd[4337]: asyncmap 0^I^I# (from /etc/ppp/options)
Apr 27 07:12:53 gateway pppd[4337]: lcp-echo-failure 4^I^I# (from /etc/ppp/options)
Apr 27 07:12:53 gateway pppd[4337]: lcp-echo-interval 30^I^I# (from /etc/ppp/options)
Apr 27 07:12:53 gateway pppd[4337]: hide-password^I^I# (from /etc/ppp/options)
Apr 27 07:12:53 gateway pppd[4337]: ipparam 192.168.0.20^I^I# (from command line)
Apr 27 07:12:53 gateway pppd[4337]: nodefaultroute^I^I# (from /etc/ppp/pptpd-options)
Apr 27 07:12:53 gateway pppd[4337]: proxyarp^I^I# (from /etc/ppp/pptpd-options)
Apr 27 07:12:53 gateway pppd[4337]: 192.168.0.11:192.168.0.234^I^I# (from command line)
Apr 27 07:12:53 gateway pppd[4337]: nobsdcomp^I^I# (from /etc/ppp/pptpd-options)
Apr 27 07:12:53 gateway pppd[4337]: require-mppe-128^I^I# (from /etc/ppp/pptpd-options)
Apr 27 07:12:53 gateway pppd[4337]: noipx^I^I# (from /etc/ppp/options)
Apr 27 07:12:53 gateway pppd[4337]: pppd 2.4.4 started by root, uid 0
Apr 27 07:12:53 gateway pppd[4337]: Using interface ppp0
Apr 27 07:12:53 gateway pppd[4337]: Connect: ppp0 <--> /dev/pts/0
Apr 27 07:12:56 gateway pppd[4337]: MPPE 128-bit stateless compression enabled
Apr 27 07:12:57 gateway pppd[4337]: found interface eth0 for proxy arp
Apr 27 07:12:57 gateway pppd[4337]: local  IP address 192.168.0.11
Apr 27 07:12:57 gateway pppd[4337]: remote IP address 192.168.0.20
Apr 27 07:12:57 gateway pppd[4337]: pptpd-logwtmp.so ip-up ppp0 testing 192.168.0.20
Apr 27 07:13:00 gateway pppd[4337]: pptpd-logwtmp.so ip-down ppp0
Apr 27 07:13:00 gateway pppd[4337]: Connect time 0.1 minutes.
Apr 27 07:13:00 gateway pppd[4337]: Sent 12643058 bytes, received 10 bytes.
Apr 27 07:13:01 gateway pppd[4337]: found interface eth0 for proxy arp
Apr 27 07:13:01 gateway pppd[4337]: local  IP address 192.168.0.11
Apr 27 07:13:01 gateway pppd[4337]: remote IP address 192.168.0.20
Apr 27 07:13:01 gateway pppd[4337]: pptpd-logwtmp.so ip-up ppp0 testing 192.168.0.20
Apr 27 07:13:01 gateway pppd[4337]: IPCP terminated by peer (^KM-Jdu^@<M-Mt^@^@^@4)
Apr 27 07:13:01 gateway pppd[4337]: pptpd-logwtmp.so ip-down ppp0
Apr 27 07:13:01 gateway pppd[4337]: Connect time 0.0 minutes.
Apr 27 07:13:01 gateway pppd[4337]: Sent 0 bytes, received 0 bytes.
Apr 27 07:13:01 gateway pppd[4337]: LCP terminated by peer (^KM-Jdu^@<M-Mt^@^@^@^@)
Apr 27 07:13:01 gateway pppd[4337]: Modem hangup
Apr 27 07:13:01 gateway pppd[4337]: Connection terminated.
Apr 27 07:13:01 gateway pppd[4337]: Connect time 0.0 minutes.
Apr 27 07:13:01 gateway pppd[4337]: Sent 4 bytes, received 0 bytes.
Apr 27 07:13:01 gateway pppd[4337]: Exit.

```

what wrong with my pptpd server?

---

### Post by jfmays on 2008-07-16
Did you ever figure this one out? I'm having the same problem.

---

