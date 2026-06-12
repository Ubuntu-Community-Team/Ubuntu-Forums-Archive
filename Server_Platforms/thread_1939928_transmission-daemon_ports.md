---
title: "transmission-daemon ports"
date: 2012-03-12
forum: Server Platforms
---

### Post by Loki57701 on 2012-03-12
I'm currently running Ubuntu server 11.10, and one of the services I have running is transmission-daemon. I've found some helpful guides online to get this up and running correctly, but I'm seeing several log entries from ufw concerning transmission. When I shutdown the service the log entries stop.

**#tail -f /var/log/syslog**
```

Mar 12 17:36:57 odin kernel: [137627.255290] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.15 DST=91.121.60.42 LEN=86 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20691 DPT=6881 LEN=66
Mar 12 17:37:15 odin kernel: [137644.849613] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.15 DST=88.190.242.141 LEN=86 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20691 DPT=6881 LEN=66
Mar 12 17:38:04 odin kernel: [137694.000865] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.15 DST=88.190.242.141 LEN=86 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20691 DPT=6881 LEN=66
Mar 12 17:38:18 odin kernel: [137707.674068] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.15 DST=91.121.60.42 LEN=86 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20691 DPT=6881 LEN=66
Mar 12 17:38:57 odin kernel: [137747.121716] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.15 DST=91.121.60.42 LEN=86 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20691 DPT=6881 LEN=66
Mar 12 17:39:08 odin kernel: [137758.331905] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.15 DST=88.190.242.141 LEN=86 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20691 DPT=6881 LEN=66
Mar 12 17:39:52 odin kernel: [137801.988393] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.15 DST=88.190.242.141 LEN=86 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20691 DPT=6881 LEN=66
Mar 12 17:40:03 odin kernel: [137813.266597] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.15 DST=91.121.60.42 LEN=86 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20691 DPT=6881 LEN=66
Mar 12 17:40:54 odin kernel: [137864.350841] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.15 DST=91.121.60.42 LEN=86 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20691 DPT=6881 LEN=66
Mar 12 17:41:03 odin kernel: [137873.104056] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.15 DST=88.190.242.141 LEN=86 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20691 DPT=6881 LEN=66

```

Just about every guide I've found has a different port or port-range I should open in my firewall.

These ports are specified in */etc/transmissiondaemon/settings.json*:

20500:20599/tcp 
20500:20599/udp
9091/tcp
9091/udp

Just opening the above ports didn't work, so in a separate guide I found these:

49152:65535/tcp
49152:65535/udp

Opening all the above ports allows me to download torrents, but I still get a ton of log entries.

I found this one in a post here: [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

6969/tcp

But I haven't applied it yet. I'd really appreciate some feed back on this.

**#ufw status verbose**
```

Status: active
Logging: on (low)
Default: deny (incoming), deny (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
22                         LIMIT IN    Anywhere
192.168.1.15 137,138/udp (Samba) ALLOW IN    192.168.1.0/24
192.168.1.15 139,445/tcp (Samba) ALLOW IN    192.168.1.0/24
20500:20599/tcp            ALLOW IN    Anywhere
20500:20599/udp            ALLOW IN    Anywhere
192.168.1.15 22/tcp        ALLOW IN    192.168.1.0/24
192.168.1.15 22/udp        ALLOW IN    192.168.1.0/24
192.168.1.15 9091/tcp      ALLOW IN    192.168.1.0/24
192.168.1.15 9091/udp      ALLOW IN    192.168.1.0/24
49152:65535/tcp            ALLOW IN    Anywhere
192.168.1.15 10000/tcp     ALLOW IN    192.168.1.0/24
192.168.1.15 10000/udp     ALLOW IN    192.168.1.0/24
20500:20599/tcp            ALLOW IN    Anywhere (v6)
20500:20599/udp            ALLOW IN    Anywhere (v6)
49152:65535/tcp            ALLOW IN    Anywhere (v6)

192.168.1.0/24 22/tcp      ALLOW OUT   192.168.1.15
192.168.1.0/24 22/udp      ALLOW OUT   192.168.1.15
192.168.1.0/24 137,138/udp (Samba) ALLOW OUT   192.168.1.15
192.168.1.0/24 139,445/tcp (Samba) ALLOW OUT   192.168.1.15
20500:20599/tcp            ALLOW OUT   Anywhere
20500:20599/udp            ALLOW OUT   Anywhere
192.168.1.0/24 9091/tcp    ALLOW OUT   192.168.1.15
192.168.1.0/24 9091/udp    ALLOW OUT   192.168.1.15
80/udp                     ALLOW OUT   Anywhere
80/tcp                     ALLOW OUT   Anywhere
443/tcp                    ALLOW OUT   Anywhere
443/udp                    ALLOW OUT   Anywhere
123/tcp                    ALLOW OUT   Anywhere
123/udp                    ALLOW OUT   Anywhere
53/tcp                     ALLOW OUT   Anywhere
53/udp                     ALLOW OUT   Anywhere
49152:65535/tcp            ALLOW OUT   Anywhere
192.168.1.0/24 10000/udp   ALLOW OUT   192.168.1.15
192.168.1.0/24 10000/tcp   ALLOW OUT   192.168.1.15
20500:20599/tcp            ALLOW OUT   Anywhere (v6)
20500:20599/udp            ALLOW OUT   Anywhere (v6)
80/udp                     ALLOW OUT   Anywhere (v6)
80/tcp                     ALLOW OUT   Anywhere (v6)
443/tcp                    ALLOW OUT   Anywhere (v6)
443/udp                    ALLOW OUT   Anywhere (v6)
123/tcp                    ALLOW OUT   Anywhere (v6)
123/udp                    ALLOW OUT   Anywhere (v6)
53/tcp                     ALLOW OUT   Anywhere (v6)
53/udp                     ALLOW OUT   Anywhere (v6)
49152:65535/tcp            ALLOW OUT   Anywhere (v6)

```

Thanks!

---

### Post by papibe on 2012-03-12
I'm not very familiar with ufw, but I use transmission-daemon extensively.

The port 51413 is for incoming connections. That is the one you need to forward from your router to your server. You would need to open the port (ufw) to incoming connections if you want to share your data (typical behaviour of a torrent client).

The port 9091 is for accessing the web interface. If you are not going to access the web interface outside your LAN, then it does not need to be forward it on the router. However you would need to open the port (ufw) for accessing the web interface from another computer on the LAN.

As far as outgoing connections, transmission-daemon dynamically open several ports to establish connections with other peers. They are in the range  49152 - 65535, and they should not be blocked otherwise you won't be able to receive data.

I hope that helps.
Regards.

---

### Post by Loki57701 on 2012-03-12
Thank you papibe.

My transmission config file was slightly different from the standard for some reason, so I set everything back to its default and opened the appropriate firewall ports.

I appreciate your help.

---

