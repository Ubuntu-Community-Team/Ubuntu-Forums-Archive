---
title: "UFW settings"
date: 2012-03-10
forum: Server Platforms
---

### Post by Loki57701 on 2012-03-10
Hello, I have an old desktop with Ubuntu server 10.04 LTS. Its being utilized as my home network file server. 

I'm seeing some log activity from UFW, and I'm not sure what settings I should apply to my firewall.

Log snippet:
```

Mar 10 02:17:56 odin kernel: [876091.990704] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.15 DST=192.168.1.255 LEN=233 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=213
Mar 10 02:29:59 odin kernel: [876814.760181] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.15 DST=192.168.1.255 LEN=256 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=236
Mar 10 02:29:59 odin kernel: [876814.760311] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.15 DST=192.168.1.255 LEN=233 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=213
Mar 10 02:41:59 odin kernel: [877535.480122] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.15 DST=192.168.1.255 LEN=256 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=236
Mar 10 02:41:59 odin kernel: [877535.480253] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.15 DST=192.168.1.255 LEN=233 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=213

```

Current UFW setting as seen with: ufw status verbose
```

Status: active
Logging: on (low)
Default: deny (incoming), deny (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
22                         LIMIT IN    Anywhere
192.168.1.15 135/tcp       ALLOW IN    192.168.1.0/24
192.168.1.15 137/udp       ALLOW IN    192.168.1.0/24
192.168.1.15 138/udp       ALLOW IN    192.168.1.0/24
192.168.1.15 139/tcp       ALLOW IN    192.168.1.0/24
192.168.1.15 445/tcp       ALLOW IN    192.168.1.0/24
192.168.1.15 22/tcp        ALLOW IN    192.168.1.0/24
53/udp                     ALLOW IN    Anywhere
53/tcp                     ALLOW IN    Anywhere
443/tcp                    ALLOW IN    Anywhere
443/udp                    ALLOW IN    Anywhere
123/tcp                    ALLOW IN    Anywhere
123/udp                    ALLOW IN    Anywhere
80/udp                     ALLOW IN    Anywhere
80/tcp                     ALLOW IN    Anywhere

53/udp                     ALLOW OUT   Anywhere
53/tcp                     ALLOW OUT   Anywhere
80/tcp                     ALLOW OUT   Anywhere
80/udp                     ALLOW OUT   Anywhere
443/udp                    ALLOW OUT   Anywhere
443/tcp                    ALLOW OUT   Anywhere
123/tcp                    ALLOW OUT   Anywhere
123/udp                    ALLOW OUT   Anywhere


```

I would appreciate any feedback on this.

Thanks!

---

### Post by Loki57701 on 2012-03-10
It looks like maybe I should add:

ufw allow out proto tcp from 192.168.1.0/24 to 192.168.1.0/24 port 138

---

### Post by Dangertux on 2012-03-10
> **Loki57701 said:**
> It looks like maybe I should add:

ufw allow out proto tcp from 192.168.1.0/24 to 192.168.1.0/24 port 138


That's broadcast traffic (hence the 192.168.1.255 address it's traffic bound for all machines on the subnet.

This is not necessarily something that is needed and you don't have to allow it if you don't want to. Also if you did want to allow it you need to change your command to

```

ufw allow out proto udp from 192.168.1.0/24 to 192.168.0/24 port 138

```

That traffic is UDP not TCP.

Hope this helps.

---

### Post by Loki57701 on 2012-03-10
Thank you Dangertux, I didn't catch that tcp/udp mix up.

I've added the firewall rule and now my syslog isn't filling up with errors.

I appreciate the help!

---

