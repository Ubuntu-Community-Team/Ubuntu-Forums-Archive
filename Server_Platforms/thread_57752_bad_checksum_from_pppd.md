---
title: "bad checksum from pppd"
date: 2005-08-17
forum: Server Platforms
---

### Post by homerglemkin on 2005-08-17
I installed pptpd and I'm trying to vpn to it from winxp sp 2. the server is hoary install
here is the error from /var/syslog

Aug 17 16:15:05 eskimo pptpd[7320]: CTRL: Starting call (launching pppd, opening GRE)
Aug 17 16:15:05 eskimo pppd[7321]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Aug 17 16:15:05 eskimo pppd[7321]: pptpd-logwtmp: $Version$
Aug 17 16:15:05 eskimo pppd[7321]: pppd options in effect:
Aug 17 16:15:05 eskimo pppd[7321]: debug^I^I# (from /etc/ppp/pptpd-options)
Aug 17 16:15:05 eskimo pppd[7321]: dump^I^I# (from /etc/ppp/pptpd-options)
Aug 17 16:15:05 eskimo pppd[7321]: plugin /usr/lib/pptpd/pptpd-logwtmp.so^I^I# (from command line)
Aug 17 16:15:05 eskimo pppd[7321]: require-mschap-v2^I^I# (from /etc/ppp/pptpd-options)
Aug 17 16:15:05 eskimo pppd[7321]: refuse-pap^I^I# (from /etc/ppp/pptpd-options)
Aug 17 16:15:05 eskimo pppd[7321]: refuse-chap^I^I# (from /etc/ppp/pptpd-options)
Aug 17 16:15:05 eskimo pppd[7321]: refuse-mschap^I^I# (from /etc/ppp/pptpd-options)
Aug 17 16:15:05 eskimo pppd[7321]: name pptpd^I^I# (from /etc/ppp/pptpd-options)
Aug 17 16:15:05 eskimo pppd[7321]: pptpd-original-ip ***.***.***.*** ^I^I# (from command line)
Aug 17 16:15:05 eskimo pppd[7321]: 115200^I^I# (from command line)
Aug 17 16:15:05 eskimo pppd[7321]: lock^I^I# (from /etc/ppp/pptpd-options)
Aug 17 16:15:05 eskimo pppd[7321]: crtscts^I^I# (from /etc/ppp/options)
Aug 17 16:15:05 eskimo pppd[7321]: local^I^I# (from command line)
Aug 17 16:15:05 eskimo pppd[7321]: asyncmap 0^I^I# (from /etc/ppp/options)
Aug 17 16:15:05 eskimo pppd[7321]: lcp-echo-failure 4^I^I# (from /etc/ppp/options)
Aug 17 16:15:05 eskimo pppd[7321]: lcp-echo-interval 30^I^I# (from /etc/ppp/options)
Aug 17 16:15:05 eskimo pppd[7321]: hide-password^I^I# (from /etc/ppp/options)
Aug 17 16:15:05 eskimo pppd[7321]: ipparam ***.***.***.***^I^I# (from command ine)
Aug 17 16:15:05 eskimo pppd[7321]: nodefaultroute^I^I# (from /etc/ppp/pptpd-options)
Aug 17 16:15:05 eskimo pppd[7321]: proxyarp^I^I# (from /etc/ppp/pptpd-options)
Aug 17 16:15:05 eskimo pppd[7321]: 192.168.0.2:192.168.0.21^I^I# (from command line)
Aug 17 16:15:05 eskimo pppd[7321]: nobsdcomp^I^I# (from /etc/ppp/pptpd-options)
Aug 17 16:15:05 eskimo pppd[7321]: require-mppe-128^I^I# (from /etc/ppp/pptpd-options)
Aug 17 16:15:05 eskimo pppd[7321]: noipx^I^I# (from /etc/ppp/options)
Aug 17 16:15:05 eskimo pppd[7321]: pppd 2.4.2 started by root, uid 0
Aug 17 16:15:05 eskimo pppd[7321]: using channel 2
Aug 17 16:15:05 eskimo pppd[7321]: Using interface ppp0
Aug 17 16:15:05 eskimo pppd[7321]: Connect: ppp0 <--> /dev/pts/0
Aug 17 16:15:05 eskimo pppd[7321]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x71bdc9d7> <pcomp> <accomp>]
[COLOR=Red]Aug 17 16:15:05 eskimo pptpd[7320]: GRE: Bad checksum from pppd.[/COLOR]

my pptpd-options:
# Encryption
# Debian: on systems with a kernel built with the package
# kernel-patch-mppe >= 2.4.2 and using ppp >= 2.4.2, ...
# {{{
refuse-pap
refuse-chap
refuse-mschap
# Require the peer to authenticate itself using MS-CHAPv2 [Microsoft
# Challenge Handshake Authentication Protocol, Version 2] authentication.
require-mschap-v2
# Require MPPE 128-bit encryption
# (note that MPPE requires the use of MSCHAP-V2 during authentication)
require-mppe-128

thanks,
homer

---

