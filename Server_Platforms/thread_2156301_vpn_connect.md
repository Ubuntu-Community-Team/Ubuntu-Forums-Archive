---
title: "vpn connect"
date: 2013-06-21
forum: Server Platforms
---

### Post by mirceabondar on 2013-06-21
On my ubuntu server i have install pptpd. From local network i connect succesfull but from internet no...in syslog have this error: gre:


Jun 21 14:26:06 andortipo pppd[4379]: pppd 2.4.5 started by root, uid 0
Jun 21 14:26:06 andortipo pppd[4379]: Using interface ppp0
Jun 21 14:26:06 andortipo pppd[4379]: Connect: ppp0 <--> /dev/pts/1
Jun 21 14:26:06 andortipo pptpd[4378]: GRE: Bad checksum from pppd.
Jun 21 14:26:31 andortipo postfix/smtpd[3516]: connect from localhost[127.0.0.1]
Jun 21 14:26:31 andortipo postfix/smtpd[3516]: disconnect from localhost[127.0.0                                                                                        .1]
Jun 21 14:26:36 andortipo pppd[4379]: LCP: timeout sending Config-Requests
Jun 21 14:26:36 andortipo pppd[4379]: Connection terminated.
Jun 21 14:26:36 andortipo pppd[4379]: Modem hangup
Jun 21 14:26:36 andortipo pppd[4379]: Exit.
Jun 21 14:26:36 andortipo pptpd[4378]: GRE: read(fd=6,buffer=6075c0,len=8196) fr                                                                                        om PTY failed: status = -1 error = Input/output error, usually caused by unexpec                                                                                        ted termination of pppd, check option syntax and pppd logs
Jun 21 14:26:36 andortipo pptpd[4378]: CTRL: PTY read or GRE write failed (pty,g                                                                                        re)=(6,7)
Jun 21 14:26:36 andortipo pptpd[4378]: CTRL: Reaping child PPP[4379]
Jun 21 14:26:36 andortipo pptpd[4378]: CTRL: Client 193.231.209.225 control conn                                                                                        ection finished

---

