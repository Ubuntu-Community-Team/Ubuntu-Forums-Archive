---
title: "AFP cache issues"
date: 2012-04-03
forum: Server Platforms
---

### Post by sdmike6 on 2012-04-03
I'm running ubuntu 11.04 x64 and I use this server as a fileshare.

I can connect to it with smb or afp.

When I grants users permission to access a folder(usermod -a -G <group name> <user> it works with smb but it seems that afp doesn't see this update.

I restarted netatalk(afp) but the same thing happens.

Can anyone help me out with this?

Also is there a way to setup a log for AFP?

---

### Post by xdracco on 2012-09-20
To enable logs, add this to /etc/netatalk/afpd.conf:

```
# AFPd Logging
- -setuplog "AFPDaemon log_info /var/log/netatalk/afpd.log" \
  -setuplog "UAMSDaemon log_info /var/log/netatalk/uams.log" \
  -setuplog "Default log_info /var/log/netatalk/netatalk.log"
```I put that string of code underneath my defined service.

See this link: [http://netatalk.sourceforge.net/2.0/htmldocs/afpd.conf.5.html](http://netatalk.sourceforge.net/2.0/htmldocs/afpd.conf.5.html)

---

