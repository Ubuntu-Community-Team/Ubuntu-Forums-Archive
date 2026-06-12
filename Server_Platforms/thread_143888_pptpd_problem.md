---
title: "pptpd problem"
date: 2006-03-13
forum: Server Platforms
---

### Post by t0m on 2006-03-13
hello,

i'm using ubuntu breezy as a server for my lan at home and so far i'm quite satisfied and got working all the things i needed. until now...

now I want to be able to connect with winxp clients to my lan over a vpn. 
so I installed pptpd (I know it's not the latest in matters of security) as a server for the winxp clients, but I can't get it to work. :/
I used the package from apt...

can somebody give me a hint what i may have done wrong? 
chap secret is set, only auth protocoll allowed is chap v2... uhm would it help if i post config files?

this is what my syslog contains:

pptpd[15141]: CTRL: Client xxx.xxx.xxx.xxx control connection started
pptpd[15141]: CTRL: Starting call (launching pppd, opening GRE)
pppd[15142]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
pppd[15142]: pptpd-logwtmp: $Version$
pppd[15142]: pppd 2.4.3 started by root, uid 0
pppd[15142]: using channel 56
pppd[15142]: Using interface ppp1
pppd[15142]: Connect: ppp1 <--> /dev/pts/3
pppd[15142]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x5f925a37> <pcomp> <accomp>]
pptpd[15141]: GRE: Bad checksum from pppd.
pppd[15142]: rcvd [LCP ConfReq id=0x0 <mru 1400> <magic 0x5cc80bda> <pcomp> <accomp> <callback CBCP>]
pppd[15142]: sent [LCP ConfRej id=0x0 <callback CBCP>]
pppd[15142]: rcvd [LCP ConfReq id=0x1 <mru 1400> <magic 0x5cc80bda> <pcomp> <accomp> <callback CBCP>]
pppd[15142]: sent [LCP ConfRej id=0x1 <callback CBCP>]
pppd[15142]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x5f925a37> <pcomp> <accomp>]
pppd[15142]: rcvd [LCP ConfReq id=0x2 <mru 1400> <magic 0x5cc80bda> <pcomp> <accomp> <callback CBCP>]
pppd[15142]: sent [LCP ConfRej id=0x2 <callback CBCP>]
pppd[15142]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x5f925a37> <pcomp> <accomp>]
pppd[15142]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x5f925a37> <pcomp> <accomp>]
pppd[15142]: rcvd [LCP ConfReq id=0x3 <mru 1400> <magic 0x5cc80bda> <pcomp> <accomp> <callback CBCP>]
pppd[15142]: sent [LCP ConfRej id=0x3 <callback CBCP>]
pppd[15142]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x5f925a37> <pcomp> <accomp>]
pppd[15142]: rcvd [LCP ConfReq id=0x4 <mru 1400> <magic 0x5cc80bda> <pcomp> <accomp> <callback CBCP>]
pppd[15142]: sent [LCP ConfRej id=0x4 <callback CBCP>]
pppd[15142]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x5f925a37> <pcomp> <accomp>]
pppd[15142]: rcvd [LCP ConfReq id=0x5 <mru 1400> <magic 0x5cc80bda> <pcomp> <accomp> <callback CBCP>]
pppd[15142]: sent [LCP ConfRej id=0x5 <callback CBCP>]
pppd[15142]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x5f925a37> <pcomp> <accomp>]
pppd[15142]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x5f925a37> <pcomp> <accomp>]
pppd[15142]: rcvd [LCP ConfReq id=0x6 <mru 1400> <magic 0x5cc80bda> <pcomp> <accomp> <callback CBCP>]
pppd[15142]: sent [LCP ConfRej id=0x6 <callback CBCP>]
pppd[15142]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x5f925a37> <pcomp> <accomp>]
pppd[15142]: rcvd [LCP ConfReq id=0x7 <mru 1400> <magic 0x5cc80bda> <pcomp> <accomp> <callback CBCP>]
pppd[15142]: sent [LCP ConfRej id=0x7 <callback CBCP>]
pppd[15142]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x5f925a37> <pcomp> <accomp>]
pppd[15142]: rcvd [LCP ConfReq id=0x8 <mru 1400> <magic 0x5cc80bda> <pcomp> <accomp> <callback CBCP>]
pppd[15142]: sent [LCP ConfRej id=0x8 <callback CBCP>]
pppd[15142]: LCP: timeout sending Config-Requests 
pppd[15142]: Connection terminated.
pppd[15142]: using channel 57
pppd[15142]: Using interface ppp1
pppd[15142]: Connect: ppp1 <--> /dev/pts/3
pppd[15142]: sent [LCP ConfReq id=0x2 <asyncmap 0x0> <auth chap MS-v2> <magic 0x5307ef93> <pcomp> <accomp>]
pppd[15142]: sent [LCP TermReq id=0x3]
pppd[15142]: tcflush failed: Bad file descriptor
pppd[15142]: tcsetattr: Invalid argument (line 1011)
pppd[15142]: Exit.
pptpd[15141]: GRE: read(fd=4,buffer=804f580,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
pptpd[15141]: CTRL: PTY read or GRE write failed (pty,gre)=(4,5)
pptpd[15141]: CTRL: Reaping child PPP[15142]
pptpd[15141]: CTRL: Client xxx.xxx.xxx.xxx control connection finished

thanks a lot for any useful advice! :)

---

### Post by t0m on 2006-03-14
anyone? :-k

---

