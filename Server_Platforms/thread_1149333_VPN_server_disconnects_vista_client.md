---
title: "VPN server disconnects vista client"
date: 2009-05-05
forum: Server Platforms
---

### Post by mayco on 2009-05-05
I've been using pptpd since interpid, and it worked perfectly with vista.

Now, since i've upgraded to jaunty and after working around [https://bugs.launchpad.net/ubuntu/+source/pptpd/+bug/352622](https://bugs.launchpad.net/ubuntu/+source/pptpd/+bug/352622) , i can connect again from a vista machine. The problem is that after a few minutes, i get disconnected.

This is what i can find in my logfile:

... connection works fine ...

May  5 09:51:57 michelangelo pptpd[17696]: GRE: read(fd=7,buffer=6095a0,len=8260) from network failed: status = -1 error = Protocol not available
May  5 09:51:57 michelangelo pptpd[17696]: CTRL: GRE read or PTY write failed (gre,pty)=(7,6)
May  5 09:51:57 michelangelo pppd[17697]: Modem hangup
May  5 09:51:57 michelangelo pppd[17697]: pptpd-logwtmp.so ip-down ppp0
May  5 09:51:57 michelangelo pppd[17697]: Connect time 4.4 minutes.
May  5 09:51:57 michelangelo pppd[17697]: Sent 42837 bytes, received 71012 bytes.
May  5 09:51:57 michelangelo pptpd[17696]: CTRL: Reaping child PPP[17697]
May  5 09:51:57 michelangelo pppd[17697]: Script /etc/ppp/ip-down started (pid 17823)
May  5 09:51:57 michelangelo pppd[17697]: MPPE disabled
May  5 09:51:57 michelangelo pppd[17697]: sent [LCP TermReq id=0x2 "MPPE disabled"]
May  5 09:51:57 michelangelo pppd[17697]: Connection terminated.
May  5 09:51:57 michelangelo pppd[17697]: Waiting for 1 child processes...
May  5 09:51:57 michelangelo pppd[17697]:   script /etc/ppp/ip-down, pid 17823
May  5 09:51:57 michelangelo postfix/master[3209]: reload configuration /etc/postfix
May  5 09:51:57 michelangelo pptpd[17696]: CTRL: Client 87.***.***.142 control connection finished
May  5 09:51:57 michelangelo pppd[17697]: Script /etc/ppp/ip-down finished (pid 17823), status = 0x0
May  5 09:51:57 michelangelo pppd[17697]: Exit.

... disconnected ...



Google'ing on "from network failed: status = -1 error = Protocol not available" doesn't give any usefull results...

---

