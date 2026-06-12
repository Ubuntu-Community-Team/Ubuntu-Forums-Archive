---
title: "Unable to connect to PPTP"
date: 2010-12-30
forum: Server Platforms
---

### Post by kingv on 2010-12-30
I have PPTPD installed and I'm unable to connect to it. My buddy(osx) is able to connect without any problems. I'm connecting from Ubuntu to a Ubuntu server that has PPTPD. Here's the log that server spits out after I try connecting from my Ubuntu machine:

tail -f /var/log/syslog:

```
Dec 30 18:41:43 ubuntu pppd[2476]: pppd 2.4.5 started by root, uid 0
Dec 30 18:41:43 ubuntu pppd[2476]: Using interface ppp0
Dec 30 18:41:43 ubuntu pppd[2476]: Connect: ppp0 <--> /dev/pts/1
Dec 30 18:41:43 ubuntu pptpd[2474]: GRE: Bad checksum from pppd.
Dec 30 18:42:13 ubuntu pppd[2476]: LCP: timeout sending Config-Requests
Dec 30 18:42:13 ubuntu pppd[2476]: Connection terminated.
Dec 30 18:42:13 ubuntu pppd[2476]: Modem hangup
Dec 30 18:42:13 ubuntu pppd[2476]: Exit.
Dec 30 18:42:13 ubuntu pptpd[2474]: GRE: read(fd=6,buffer=611640,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Dec 30 18:42:13 ubuntu pptpd[2474]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Dec 30 18:42:13 ubuntu pptpd[2474]: CTRL: Reaping child PPP[2476]
Dec 30 18:42:13 ubuntu pptpd[2474]: CTRL: Client **MYIP** control connection finished

```

Here's the server's Encryption section from /etc/ppp/pptd-options


```
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
#Require MPPE 128-bit encryption
# (note that MPPE requires the use of MSCHAP-V2 during authentication)
require-mppe-128
# }}}
```

I've done ton of Googling and no luck. I must be blind. Any help would be more than appreciated. Thanks!!

---

### Post by kenm_uk on 2011-07-22
Hi. Did you ever solve this issue?

I am also getting the error
```
 GRE: Bad checksum from pppd.
```
when I try to connect to my recent attempt to set up a VPN server.

I followed the instructions here:
[http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html)

---

### Post by Zoasterboy on 2012-06-05
> **kenm_uk said:**
> Hi. Did you ever solve this issue?

I am also getting the error
```
 GRE: Bad checksum from pppd.
```
when I try to connect to my recent attempt to set up a VPN server.

I followed the instructions here:
[http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html)

I had the same problem. Thought i'd share in-case anyone is looking here for answers.

Not sure if this was a problem but it seemed to change the results in syslog, only used one tab between columns when configuring users.

What fixed it for me was enabling MTSE in the client configuration settings. It's disabled by default in Ubuntu's network manager.

---

### Post by psecker on 2012-09-13
Ensure you enable *MPPE* in the client configuration  settings (under Advanced).  It's disabled by default in Ubuntu's network manager. Turn verbose debugging on (pptpd --debug) to get a better idea of what is wrong (in syslog).

---

