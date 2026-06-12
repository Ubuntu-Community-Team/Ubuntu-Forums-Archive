---
title: "unable to run ppp from pptpd"
date: 2006-01-10
forum: Server Platforms
---

### Post by aazuike on 2006-01-10
when a client tries to establish a connection the pptpd server I set up on an ubuntu server. it disconnects soon as the ppp GRE negotiation starts and prints the following in the syslog file.   

CTRL: Starting call (launching pppd, opening GRE)
pppd[10281]: using the name option requires root privilege
pptpd[10280]: GRE: read(fd=4,buffer=804f580,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
pptpd[10280]: CTRL: PTY read or GRE write failed (pty,gre)=(4,-1)
pptpd[10280]: CTRL: Reaping child PPP[10281]

has anyone had this problem and how do I solve it. 

Thanks 
Alex

---

### Post by gabornagy on 2006-01-11
Should this be under the security talk? If so can an admin put it there.

Alex and I need to figure this out in order to avoid having to use another distro. If the pptpd daemon needs root access, why can't we run it as root? Is there a way to make a daemon run as root? I never had a problem like this with any other distro. If I want something to run as root I should be able to do it.

---

