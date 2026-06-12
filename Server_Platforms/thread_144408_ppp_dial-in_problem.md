---
title: "ppp dial-in problem?"
date: 2006-03-14
forum: Server Platforms
---

### Post by Nucleus on 2006-03-14
I need to share my ethernet connection with remote users with dial-up modems.

I have used mgetty+pppd to do this. I am getting this failure message when I dial from remote machine.

```

Mar 14 14:51:45 localhost pppd[9917]: pppd 2.4.3 started by pppuser, uid 0
Mar 14 14:51:45 localhost pppd[9917]: using channel 29
Mar 14 14:51:45 localhost pppd[9917]: Using interface ppp0
Mar 14 14:51:45 localhost pppd[9917]: Connect: ppp0 <--> /dev/ttyS0
Mar 14 14:51:45 localhost pppd[9917]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth eap> <magic 0x2b74288a> <pcomp> <accomp>]
Mar 14 14:51:48 localhost pppd[9917]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth eap> <magic 0x2b74288a> <pcomp> <accomp>]
Mar 14 14:51:48 localhost pppd[9917]: rcvd [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0x38f93b21> <pcomp> <accomp> <callback CBCP>]
Mar 14 14:51:48 localhost pppd[9917]: sent [LCP ConfRej id=0x2 <callback CBCP>]
Mar 14 14:51:49 localhost pppd[9917]: rcvd [LCP ConfReq id=0x3 <asyncmap 0x0> <magic 0x38f93b21> <pcomp> <accomp>]
Mar 14 14:51:49 localhost pppd[9917]: sent [LCP ConfAck id=0x3 <asyncmap 0x0> <magic 0x38f93b21> <pcomp> <accomp>]
Mar 14 14:51:51 localhost pppd[9917]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth eap> <magic 0x2b74288a> <pcomp> <accomp>]
Mar 14 14:51:52 localhost pppd[9917]: rcvd [LCP ConfReq id=0x4 <asyncmap 0x0> <magic 0x38f93b21> <pcomp> <accomp>]
Mar 14 14:51:52 localhost pppd[9917]: sent [LCP ConfAck id=0x4 <asyncmap 0x0> <magic 0x38f93b21> <pcomp> <accomp>]
Mar 14 14:51:54 localhost pppd[9917]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth eap> <magic 0x2b74288a> <pcomp> <accomp>]
Mar 14 14:51:56 localhost pppd[9917]: rcvd [LCP ConfReq id=0x5 <asyncmap 0x0> <magic 0x38f93b21> <pcomp> <accomp>]
Mar 14 14:51:56 localhost pppd[9917]: sent [LCP ConfAck id=0x5 <asyncmap 0x0> <magic 0x38f93b21> <pcomp> <accomp>]
Mar 14 14:51:57 localhost pppd[9917]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth eap> <magic 0x2b74288a> <pcomp> <accomp>]
Mar 14 14:52:00 localhost pppd[9917]: rcvd [LCP ConfReq id=0x6 <asyncmap 0x0> <magic 0x38f93b21> <pcomp> <accomp>]
Mar 14 14:52:00 localhost pppd[9917]: sent [LCP ConfAck id=0x6 <asyncmap 0x0> <magic 0x38f93b21> <pcomp> <accomp>]
Mar 14 14:52:00 localhost pppd[9917]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth eap> <magic 0x2b74288a> <pcomp> <accomp>]
Mar 14 14:52:03 localhost pppd[9917]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth eap> <magic 0x2b74288a> <pcomp> <accomp>]
Mar 14 14:52:04 localhost pppd[9917]: rcvd [LCP ConfReq id=0x7 <asyncmap 0x0> <magic 0x38f93b21> <pcomp> <accomp>]
Mar 14 14:52:04 localhost pppd[9917]: sent [LCP ConfAck id=0x7 <asyncmap 0x0> <magic 0x38f93b21> <pcomp> <accomp>]
Mar 14 14:52:06 localhost pppd[9917]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth eap> <magic 0x2b74288a> <pcomp> <accomp>]
Mar 14 14:52:08 localhost pppd[9917]: rcvd [LCP ConfReq id=0x8 <asyncmap 0x0> <magic 0x38f93b21> <pcomp> <accomp>]
Mar 14 14:52:08 localhost pppd[9917]: sent [LCP ConfAck id=0x8 <asyncmap 0x0> <magic 0x38f93b21> <pcomp> <accomp>]
Mar 14 14:52:09 localhost pppd[9917]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth eap> <magic 0x2b74288a> <pcomp> <accomp>]
Mar 14 14:52:12 localhost pppd[9917]: rcvd [LCP ConfReq id=0x9 <asyncmap 0x0> <magic 0x38f93b21> <pcomp> <accomp>]
Mar 14 14:52:12 localhost pppd[9917]: sent [LCP ConfAck id=0x9 <asyncmap 0x0> <magic 0x38f93b21> <pcomp> <accomp>]
Mar 14 14:52:12 localhost pppd[9917]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth eap> <magic 0x2b74288a> <pcomp> <accomp>]
Mar 14 14:52:15 localhost pppd[9917]: LCP: timeout sending Config-Requests
Mar 14 14:52:15 localhost pppd[9917]: Connection terminated.
Mar 14 14:52:15 localhost pppd[9917]: using channel 30
Mar 14 14:52:15 localhost pppd[9917]: Using interface ppp0
Mar 14 14:52:15 localhost pppd[9917]: Connect: ppp0 <--> /dev/ttyS0
Mar 14 14:52:16 localhost pppd[9917]: sent [LCP ConfReq id=0x2 <asyncmap 0x0> <auth eap> <magic 0x300f5aea> <pcomp> <accomp>]
Mar 14 14:52:16 localhost pppd[9917]: sent [LCP TermReq id=0x3]
Mar 14 14:52:16 localhost pppd[9917]: tcflush failed: Bad file descriptor
Mar 14 14:52:16 localhost pppd[9917]: tcsetattr: Invalid argument (line 1011)
Mar 14 14:52:16 localhost pppd[9917]: Exit.

```

this is my /etc/inittab line for mgetty:

```
T0:23:respawn:/sbin/mgetty -x 9 -s 38400 ttyS0
```

this is my /etc/mgetty/login.config:

```
/AutoPPP/ - a_ppp /usr/sbin/pppd file /etc/ppp/options
```

this is my /etc/ppp/options file:

```

ms-dns xxx.xxx.xxx.xxx
asyncmap 0
auth
crtscts
lock
hide-password
modem
netmask 255.255.255.0
debug
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

```

this is my /etc/ppp/options.ttyS0 file:

```
192.168.1.1:192.168.1.2
```

I need urgent help. Thanks everybody.

---

