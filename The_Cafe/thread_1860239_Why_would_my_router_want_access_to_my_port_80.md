---
title: "Why would my router want access to my port 80?"
date: 2011-10-14
forum: The Cafe
---

### Post by vajorie on 2011-10-14
This is most probably not the place to ask this, but where else could I ask this? :)

For some reason, my verizon dsl router sends packets to computers connected to it with a destination port of 80... Here's an example (redacted) from my logs: 

```

localhost kernel: [UFW BLOCK] IN=wlan0 OUT= MAC=bla SRC=192.168.x.router DST=192.168.x.me LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=44920 DF PROTO=TCP SPT=1114 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 

```

Why do you think it would be doing this? I don't have any special services running on this router and its firewall has no port forwarding rule for port 80...

---

### Post by SoFl W on 2011-10-14
Port 80 is the port for webpages.  Your browser defaults to 80.

---

### Post by tigerplug on 2011-10-14
> **SoFl W said:**
> Port 80 is the port for webpages.  Your browser defaults to 80.

Thats the destination.
The source port is dynamic.

---

### Post by CharlesA on 2011-10-14
Try resetting the router to factory defaults and see if it does the same thing.

I haven't seen any router do that.

---

