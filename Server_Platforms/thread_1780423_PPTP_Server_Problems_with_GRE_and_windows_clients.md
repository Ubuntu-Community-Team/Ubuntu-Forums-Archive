---
title: "PPTP Server Problems with GRE and windows clients"
date: 2011-06-12
forum: Server Platforms
---

### Post by niallm90 on 2011-06-12
I have PPTP and PPPoE server setup with freeradius & mysql for authentication. They have been working fine for months and without any change, yesterday they started playing up. I am getting strange GRE errors when Windows clients (have only tested Windows 7) are connecting to the PPTP server but not the PPPoE server. It caused the server to drop windows clients after a few min or not even accept the connection sometimes. Ubuntu desktop clients seam to have no problems at all.

I did an upgrade to natty to see if it would help. It didn't.

Here are some log dumps. Help would really be appreciated.

Syslog:
```

Jun 12 17:02:59 router pppd[18442]: Plugin /usr/lib/pppd/2.4.5/radius.so loaded.
Jun 12 17:02:59 router pppd[18442]: RADIUS plugin initialized.
Jun 12 17:02:59 router pppd[18442]: Plugin /usr/lib/pppd/2.4.5/radattr.so loaded.
Jun 12 17:02:59 router pppd[18442]: RADATTR plugin initialized.
Jun 12 17:02:59 router pppd[18442]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Jun 12 17:02:59 router pppd[18442]: pptpd-logwtmp: $Version$
Jun 12 17:02:59 router pppd[18442]: pppd 2.4.5 started by root, uid 0
Jun 12 17:02:59 router pppd[18442]: using channel 32
Jun 12 17:02:59 router pppd[18442]: Using interface ppp3
Jun 12 17:02:59 router pppd[18442]: Connect: ppp3 <--> /dev/pts/4
Jun 12 17:02:59 router pppd[18442]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth pap> <magic 0x21f6725e>]
Jun 12 17:02:59 router pptpd[18440]: GRE: accepting packet #0
Jun 12 17:02:59 router pptpd[18440]: GRE: read(fd=7,buffer=80524c0,len=8260) from network failed: status = -1 error = Protocol not available
Jun 12 17:02:59 router pptpd[18440]: CTRL: GRE read or PTY write failed (gre,pty)=(7,6)
Jun 12 17:02:59 router pppd[18442]: Modem hangup
Jun 12 17:02:59 router pppd[18442]: Connection terminated.
Jun 12 17:02:59 router avahi-daemon[911]: Withdrawing workstation service for ppp3.
Jun 12 17:02:59 router pptpd[18440]: CTRL: Reaping child PPP[18442]
Jun 12 17:02:59 router pptpd[6807]: GRE: accepting packet #409114
Jun 12 17:02:59 router pptpd[6807]: GRE: accepting packet #409115
Jun 12 17:02:59 router pppd[18442]: RADATTR plugin removed file /var/run/radattr.ppp3.
Jun 12 17:02:59 router pppd[18442]: Exit.
Jun 12 17:02:59 router pptpd[18440]: CTRL: Client 192.168.1.219 control connection finished
Jun 12 17:02:59 router pptpd[18440]: CTRL: Exiting now
Jun 12 17:02:59 router pptpd[6570]: MGR: Reaped child 18440

```PPTP
```

Plugin /usr/lib/pppd/2.4.5/radius.so loaded.
RADIUS plugin initialized.
Plugin /usr/lib/pppd/2.4.5/radattr.so loaded.
RADATTR plugin initialized.
Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
pptpd-logwtmp: $Version$
using channel 29
Using interface ppp5
Connect: ppp5 <--> /dev/pts/6
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth pap> <magic 0x15ec3df7>]
rcvd [LCP ConfReq id=0x0 <mru 1400> <magic 0x11e527bf> <pcomp> <accomp> <callback CBCP>]
sent [LCP ConfRej id=0x0 <pcomp> <accomp> <callback CBCP>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <auth pap> <magic 0x15ec3df7>]
rcvd [LCP ConfReq id=0x1 <mru 1400> <magic 0x11e527bf>]
sent [LCP ConfAck id=0x1 <mru 1400> <magic 0x11e527bf>]
sent [LCP EchoReq id=0x0 magic=0x15ec3df7]
rcvd [LCP Ident id=0x2 magic=0x11e527bf "MSRASV5.20"]
rcvd [LCP Ident id=0x3 magic=0x11e527bf "MSRAS-0-MEDIA"]
rcvd [LCP Ident id=0x4 magic=0x11e527bf "U\37777777654\n\37777777650Mr\37777777700K\37777777653\37777777744uk\37777777773\37777777601\37777777674\37777777631"]
rcvd [PAP AuthReq id=0xf user="niall" password=<hidden>]
RADATTR plugin wrote 0 line(s) to file /var/run/radattr.ppp5.
sent [PAP AuthAck id=0xf ""]
PAP peer authentication succeeded for niall
sent [IPCP ConfReq id=0x1 <addr 10.1.1.1>]
rcvd [LCP EchoRep id=0x0 magic=0x11e527bf]
rcvd [IPV6CP ConfReq id=0x5 <addr fe80::68c1:9d33:c5f3:cca4>]
Unsupported protocol 'IPv6 Control Protocol' (0x8057) received
sent [LCP ProtRej id=0x2 80 57 01 05 00 0e 01 0a 68 c1 9d 33 c5 f3 cc a4]
rcvd [IPCP ConfReq id=0x6 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-wins 0.0.0.0> <ms-dns2 0.0.0.0> <ms-wins 0.0.0.0>]
sent [IPCP ConfRej id=0x6 <ms-wins 0.0.0.0> <ms-wins 0.0.0.0>]
rcvd [IPCP ConfAck id=0x1 <addr 10.1.1.1>]
rcvd [IPCP ConfReq id=0x7 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
sent [IPCP ConfNak id=0x7 <addr 10.1.2.4> <ms-dns1 192.168.1.1> <ms-dns2 192.168.1.1>]
rcvd [IPCP ConfReq id=0x8 <addr 10.1.2.4> <ms-dns1 192.168.1.1> <ms-dns2 192.168.1.1>]
sent [IPCP ConfAck id=0x8 <addr 10.1.2.4> <ms-dns1 192.168.1.1> <ms-dns2 192.168.1.1>]
Cannot determine ethernet address for proxy ARP
local  IP address 10.1.1.1
remote IP address 10.1.2.4
pptpd-logwtmp.so ip-up ppp5 niall 192.168.1.102
Script /etc/ppp/ip-up started (pid 15319)
Script /etc/ppp/ip-up finished (pid 15319), status = 0x0
Modem hangup
pptpd-logwtmp.so ip-down ppp3
Connect time 5.5 minutes.
Sent 17075 bytes, received 39061 bytes.
Script /etc/ppp/ip-down started (pid 16709)
Connection terminated.
Waiting for 1 child processes...
  script /etc/ppp/ip-down, pid 16709
Hangup (SIGHUP)
sending SIGTERM to process 16709
RADATTR plugin removed file /var/run/radattr.ppp3.
Hangup (SIGHUP)
Modem hangup
pptpd-logwtmp.so ip-down ppp5
Connect time 5.5 minutes.
Sent 713 bytes, received 37076 bytes.
Script /etc/ppp/ip-down started (pid 16831)
Connection terminated.
Waiting for 1 child processes...
  script /etc/ppp/ip-down, pid 16831
Script /etc/ppp/ip-down finished (pid 16831), status = 0x0
RADATTR plugin removed file /var/run/radattr.ppp5.

```Thanks all help is much appreciated,
Niall

---

