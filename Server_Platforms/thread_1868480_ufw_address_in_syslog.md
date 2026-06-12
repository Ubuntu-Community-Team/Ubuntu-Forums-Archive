---
title: "ufw address in syslog"
date: 2011-10-24
forum: Server Platforms
---

### Post by parisv on 2011-10-24
Can anyone tell me why I'm getting this in my syslog?

```
Oct 24 06:58:09 myserv kernel: [39618.931305] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=192.168.20.2 DST=239.0.0.250 LEN=49 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=39811 DPT=32412 LEN=29
Oct 24 06:58:29 myserv kernel: [39638.905447] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=192.168.20.2 DST=239.0.0.250 LEN=49 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=39811 DPT=32412 LEN=29
Oct 24 06:58:49 myserv kernel: [39658.879591] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=192.168.20.2 DST=239.0.0.250 LEN=49 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=39811 DPT=32412 LEN=29
Oct 24 06:59:09 myserv kernel: [39678.853734] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=192.168.20.2 DST=239.0.0.250 LEN=49 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=39811 DPT=32412 LEN=29
```

I'm running avahi on it, I'm wondering if it's something to do with this?

but in /etc/avahi/avahi-daemon.conf I have

```
use-ipv6=no
```

---

### Post by sheldonl on 2011-12-18
I saw this too, it's related to the Plex Media Server. Are you running that?

---

### Post by Toz on 2011-12-18
Looks alot like ufw (firewall) logging. What does the following return?
```
sudo ufw status verbose
```

If you get:
> 
...
Logging: on (low)
...
in the response, then thats it. You can turn it (logging) off by:
```
sudo ufw logging off
```

---

### Post by parisv on 2011-12-19
> **sheldonl said:**
> I saw this too, it's related to the Plex Media Server. Are you running that?

yeah I have narrowed it down to plex as when I stop the service the log messages stop. So somehow I need to disable this option on plex that uses ipv6 i posted a thread in plex forums but not to many people use the forums so I haven't had a reply. So for now I've disabled the ufw logging

---

