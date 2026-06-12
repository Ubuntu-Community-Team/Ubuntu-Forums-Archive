---
title: "After upgrade to 10.04 LTS ufw problem occurs."
date: 2010-05-03
forum: Server Platforms
---

### Post by mysteron on 2010-05-03
After upgrade to Ubuntu Server 10.04 LTS, ufw has started blocking some legitimate HTTP and FTP contacts.

What can I do to tell ufw not to block any HTTP and FTP requests.

This is what is shown in messages:

```
May  3 11:07:48 server kernel: [] [UFW BLOCK] IN=eth0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=192.168.1.100 DST=192.168.1.50 LEN=60 TOS=0x00 PREC=0x00 TTL=121 ID=9979 DF PROTO=TCP SPT=60191 DPT=80 WINDOW=16560 RES=0x00 ACK URGP=0
```

UFW has these settings:

```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
192.168.1.50 21/tcp       ALLOW IN    Anywhere
192.168.1.50 80/tcp       ALLOW IN    Anywhere
192.168.1.50 443/tcp      ALLOW IN    Anywhere
```


Thx,
/mysteron

---

### Post by mysteron on 2010-05-03
First I thought that it is UFW that causes this, but after some testing, I noticed that it is something else that causes it. I disabled ufw and made my own similar iptables settings. 

If a websurfer surfs to a site, and click on links on the sites too fast, a blocked message will show up in the messages log.

What could be causing this behaviour?


Thx,
/mysteron

---

### Post by DSmidgy on 2010-06-12
I too have noticed the entries in syslog.
In my case, not only users, accessing port 80 are getting blocked, but some search engines too.

Does anybody have an idea how to fix this?

---

### Post by sladekal on 2010-09-19
Anyone find a solution to this? I have the same problem.

---

### Post by windependence on 2010-09-19
Sounds like flood protection to me. It's blocking packets that come from the same place too fast and too many as in DDOS attack. Just a suggestion.
 
-Tim

---

