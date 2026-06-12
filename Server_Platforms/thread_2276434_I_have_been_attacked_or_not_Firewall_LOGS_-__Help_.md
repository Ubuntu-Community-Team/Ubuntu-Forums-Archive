---
title: "I have been attacked or not? Firewall LOGS -  Help please !!!"
date: 2015-05-02
forum: Server Platforms
---

### Post by rhandy2 on 2015-05-02
Ok I have every second this report on firewall logs

```
May  2 15:12:37 localhost kernel: [41569.982559] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22766 DF PROTO=2
May  2 15:12:57 localhost kernel: [41590.092677] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22767 DF PROTO=2
May  2 15:13:17 localhost kernel: [41610.080303] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22770 DF PROTO=2
May  2 15:13:37 localhost kernel: [41630.065430] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22772 DF PROTO=2
May  2 15:13:57 localhost kernel: [41650.064304] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22773 DF PROTO=2
May  2 15:14:17 localhost kernel: [41670.049445] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22776 DF PROTO=2
May  2 15:14:37 localhost kernel: [41690.043329] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22778 DF PROTO=2
May  2 15:14:57 localhost kernel: [41710.029703] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22779 DF PROTO=2
May  2 15:15:17 localhost kernel: [41730.133570] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22791 DF PROTO=2
May  2 15:15:37 localhost kernel: [41750.122464] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22793 DF PROTO=2
May  2 15:15:57 localhost kernel: [41770.108825] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22814 DF PROTO=2
May  2 15:16:17 localhost kernel: [41790.097716] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22817 DF PROTO=2
May  2 15:16:37 localhost kernel: [41810.072832] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22819 DF PROTO=2
May  2 15:16:57 localhost kernel: [41830.166708] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22820 DF PROTO=2
May  2 15:17:17 localhost kernel: [41850.129328] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22823 DF PROTO=2
May  2 15:17:37 localhost kernel: [41870.109472] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22825 DF PROTO=2
May  2 15:17:57 localhost kernel: [41890.103334] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22826 DF PROTO=2
May  2 15:18:17 localhost kernel: [41910.098487] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22828 DF PROTO=2
May  2 15:18:37 localhost kernel: [41930.183596] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22831 DF PROTO=2
May  2 15:18:57 localhost kernel: [41950.194980] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22832 DF PROTO=2
May  2 15:19:17 localhost kernel: [41970.188848] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22834 DF PROTO=2
May  2 15:19:37 localhost kernel: [41990.173971] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22837 DF PROTO=2
May  2 15:19:57 localhost kernel: [42010.172864] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22838 DF PROTO=2
May  2 15:20:17 localhost kernel: [42030.175478] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22840 DF PROTO=2
May  2 15:20:37 localhost kernel: [42050.161851] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22843 DF PROTO=2
May  2 15:20:57 localhost kernel: [42070.164486] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22846 DF PROTO=2
May  2 15:21:17 localhost kernel: [42090.150877] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22848 DF PROTO=2
May  2 15:21:37 localhost kernel: [42110.242242] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22851 DF PROTO=2
May  2 15:21:57 localhost kernel: [42130.228612] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22853 DF PROTO=2
May  2 15:22:17 localhost kernel: [42150.202495] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22855 DF PROTO=2
May  2 15:22:37 localhost kernel: [42170.186375] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22858 DF PROTO=2
May  2 15:22:57 localhost kernel: [42190.170250] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22865 DF PROTO=2
May  2 15:23:17 localhost kernel: [42210.272871] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22867 DF PROTO=2
May  2 15:23:37 localhost kernel: [42230.271760] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22869 DF PROTO=2
May  2 15:23:57 localhost kernel: [42250.258134] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22871 DF PROTO=2
May  2 15:24:17 localhost kernel: [42270.253254] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22881 DF PROTO=2
May  2 15:24:37 localhost kernel: [42290.258389] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22883 DF PROTO=2
May  2 15:24:57 localhost kernel: [42310.244759] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22905 DF PROTO=2
May  2 15:25:17 localhost kernel: [42330.242393] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22907 DF PROTO=2
May  2 15:25:37 localhost kernel: [42350.230009] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22924 DF PROTO=2
May  2 15:25:57 localhost kernel: [42370.335136] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22926 DF PROTO=2
May  2 15:26:17 localhost kernel: [42390.325273] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22930 DF PROTO=2
May  2 15:26:37 localhost kernel: [42410.315401] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22932 DF PROTO=2
May  2 15:26:57 localhost kernel: [42430.281774] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22934 DF PROTO=2
May  2 15:27:17 localhost kernel: [42450.258145] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:b1:45:26:08:00 SRC=172.31.32.33 DST=224.0.0.1 LEN=36 TOS=0x08 PREC=0x80 TTL=1 ID=22936 DF PROTO=2
```

---

### Post by darkod on 2015-05-02
If the machine is published on the internet, attack attempts are normal. You will keep getting them... The important thing is that they are not getting through.

---

### Post by rhandy2 on 2015-05-02
Ok, thanks!!!

---

### Post by Doug S on 2015-05-02
The IP address, 172.31.32.33, is private and only useable on a LAN. The destination address is a [multicast IP address]("http://tldp.org/HOWTO/Multicast-HOWTO-2.html").
I am saying that the entire event is of your own doing on your own LAN.

---

### Post by The Cog on 2015-05-02
It's an IGMP multicast once every 20 seconds. I think it's harmless.

---

### Post by rhandy2 on 2015-05-02
Ok thanks !!!!

---

### Post by rhandy2 on 2015-05-02
> The IP address, 172.31.32.33, is private and only useable on a LAN. The destination address is a [multicast IP address]("http://tldp.org/HOWTO/Multicast-HOWTO-2.html").
 I am saying that the entire event is of your own doing on your own LAN.
The strange thing, isn´t my own lan. my lan is configured on 192.168.x.x/24

---

### Post by Doug S on 2015-05-02
> **rhandy2 said:**
> The strange thing, isn´t my own lan. my lan is configured on 192.168.x.x/24I would then assume that your ISP is using that sub-net. My ISP uses 10.197.248.13 to do the same thing. I have an iptables rule to DROP the packets so as not to clog my log file. 
As the Cog mentioned, they are harmless, just annoying.

---

### Post by rhandy2 on 2015-05-02
I put one rule on ufw firewall to deny all from that ip.

---

### Post by Habitual on 2015-05-04
> **rhandy2 said:**
> I put one rule on ufw firewall to deny all from that ip.
If you have ufw enabled, I use this```

ufw deny from 224.0.0.1
```

---

