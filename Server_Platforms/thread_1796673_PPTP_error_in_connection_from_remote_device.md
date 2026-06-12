---
title: "PPTP error in connection from remote device"
date: 2011-07-04
forum: Server Platforms
---

### Post by licaonr on 2011-07-04
Hello

I've setup a pptp vpn server on my ubuntu server 11.04, using this guide: [http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html]("http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html")

but when i try to connect from my devices i get the folowing error in /var/log/syslog:

From my Ubuntu 11.04 laptop:

Jul  4 10:49:42 ubuntuserver pptpd[4255]: CTRL: Starting call (launching pppd, opening GRE)
Jul  4 10:49:42 ubuntuserver pppd[4257]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Jul  4 10:49:42 ubuntuserver pppd[4257]: pppd 2.4.5 started by root, uid 0
Jul  4 10:49:42 ubuntuserver pppd[4257]: Using interface ppp0
Jul  4 10:49:42 ubuntuserver pppd[4257]: Connect: ppp0 <--> /dev/pts/5
Jul  4 10:49:42 ubuntuserver pptpd[4255]: GRE: Bad checksum from pppd.
Jul  4 10:50:11 ubuntuserver pptpd[4255]: CTRL: Reaping child PPP[4257]
Jul  4 10:50:11 ubuntuserver pppd[4257]: Hangup (SIGHUP)
Jul  4 10:50:11 ubuntuserver pppd[4257]: Modem hangup
Jul  4 10:50:11 ubuntuserver pppd[4257]: Connection terminated.
Jul  4 10:50:11 ubuntuserver pppd[4257]: Exit.

From my iPhone and Android phone same error:

Jul  4 10:54:10 ubuntuserver pptpd[4325]: CTRL: Starting call (launching pppd, opening GRE)
Jul  4 10:54:10 ubuntuserver pppd[4327]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Jul  4 10:54:10 ubuntuserver pppd[4327]: pppd 2.4.5 started by root, uid 0
Jul  4 10:54:10 ubuntuserver pppd[4327]: Using interface ppp0
Jul  4 10:54:10 ubuntuserver pppd[4327]: Connect: ppp0 <--> /dev/pts/5
Jul  4 10:54:10 ubuntuserver pptpd[4325]: GRE: Bad checksum from pppd.
Jul  4 10:54:40 ubuntuserver pppd[4327]: LCP: timeout sending Config-Requests
Jul  4 10:54:40 ubuntuserver pppd[4327]: Connection terminated.
Jul  4 10:54:40 ubuntuserver pppd[4327]: Modem hangup
Jul  4 10:54:40 ubuntuserver pppd[4327]: Exit.
Jul  4 10:54:40 ubuntuserver pptpd[4325]: GRE: read(fd=6,buffer=611660,len=8196) from PTY failed: status = -1 error = Input/output error, usually cause$
Jul  4 10:54:40 ubuntuserver pptpd[4325]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Jul  4 10:54:40 ubuntuserver pptpd[4325]: CTRL: Reaping child PPP[4327]

If anybody has any ideea?

---

