---
title: "there is a ufw block log for the ip address which i already allowed by ufw"
date: 2024-01-31
forum: Security
---

### Post by jimmynug-song on 2024-01-31
Hello,
I am facing an issue when using ubuntu 22.04, i add the ip blocks 192.168.0.0/16 to the ufw by runing ufw allow from 192.168.0.0/16 and ufw reload, but i still sees some request has been blocked by ufw, what should i do now?
```

Jan 31 20:42:05 104-243-131-236 kernel: [154851.602221] [UFW BLOCK] IN=eth1 OUT= MAC= 00:25:90:ca:7f:41:00:25:90:da:7e:f9:08:00 SRC=192.168.100.82 DST=192.168.100.236 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=2193 DF PROTO=TCP SPT=45212 DPT=8200 WINDOW=501 RES=0x00 ACK FIN URGP=0 
Jan 31 20:42:25 104-243-131-236 kernel: [154871.570864] [UFW BLOCK] IN=eth1 OUT= MAC= 00:25:90:ca:7f:41:00:25:90:da:7e:f9:08:00 SRC=192.168.100.82 DST=192.168.100.236 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=2195 DF PROTO=TCP SPT=45212 DPT=8200 WINDOW=501 RES=0x00 ACK FIN URGP=0 
Jan 31 20:42:45 104-243-131-236 kernel: [154891.384921] [UFW BLOCK] IN=eth1 OUT= MAC=00:25:90:ca:7f:41:00:24:ec:f1:9b:56:08:00 SRC=192.168.100.83 DST=192.168.100.236 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=28402 DF PROTO=TCP SPT=8300 DPT=33120 WINDOW=0 RES=0x00 RST URGP=0 
Jan 31 20:43:04 104-243-131-236 kernel: [154910.865960] [UFW BLOCK] IN=eth1 OUT= MAC=00:25:90:ca:7f:41:00:24:ec:f0:c4:36:08:00 SRC=192.168.100.175 DST=192.168.100.236 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=42992 DF PROTO=TCP SPT=49780 DPT=8400 WINDOW=237 RES=0x00 ACK FIN URGP=0 
Jan 31 20:43:24 104-243-131-236 kernel: [154930.746950] [UFW BLOCK] IN=eth1 OUT= MAC=00:25:90:ca:7f:41:00:24:ec:f2:16:62:08:00 SRC=192.168.100.176 DST=192.168.100.236 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=56128 DF PROTO=TCP SPT=43944 DPT=8400 WINDOW=237 RES=0x00 ACK FIN URGP=0 
Jan 31 20:43:44 104-243-131-236 kernel: [154950.685814] [UFW BLOCK] IN=eth1 OUT= MAC=00:25:90:ca:7f:41:00:25:90:ca:80:3d:08:00 SRC=192.168.100.237 DST=192.168.100.236 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=10399 DF PROTO=TCP SPT=50480 DPT=8500 WINDOW=501 RES=0x00 ACK FIN URGP=0 
Jan 31 20:44:06 104-243-131-236 kernel: [154972.442206] [UFW BLOCK] IN=eth1 OUT= MAC= 00:25:90:ca:7f:41:00:25:90:da:7e:f9:08:00 SRC=192.168.100.82 DST=192.168.100.236 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=4213 DF PROTO=TCP SPT=49330 DPT=8100 WINDOW=501 RES=0x00 ACK FIN URGP=0 
Jan 31 20:44:45 104-243-131-236 kernel: [155011.279906] [UFW BLOCK] IN=eth1 OUT= MAC=00:25:90:ca:7f:41:00:25:90:ca:7f:5b:08:00 SRC=192.168.100.174 DST=192.168.100.236 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=55173 DF PROTO=TCP SPT=35028 DPT=8200 WINDOW=501 RES=0x00 ACK FIN URGP=0 
Jan 31 20:45:05 104-243-131-236 kernel: [155031.073737] [UFW BLOCK] IN=eth1 OUT= MAC=00:25:90:ca:7f:41:b6:ac:92:22:61:d0:08:00 SRC=192.168.100.190 DST=192.168.100.236 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=60318 DF PROTO=TCP SPT=8401 DPT=43514 WINDOW=0 RES=0x00 RST URGP=0 
Jan 31 20:45:44 104-243-131-236 kernel: [155070.681473] [UFW BLOCK] IN=eth1 OUT= MAC= 00:25:90:ca:7f:41:00:25:90:da:7e:f9:08:00 SRC=192.168.100.82 DST=192.168.100.236 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=61034 DF PROTO=TCP SPT=34166 DPT=8100 WINDOW=501 RES=0x00 ACK FIN URGP=0 
Jan 31 20:46:04 104-243-131-236 kernel: [155090.914832] [UFW BLOCK] IN=eth1 OUT= MAC= 00:25:90:ca:7f:41:00:25:90:da:7e:f9:08:00 SRC=192.168.100.82 DST=192.168.100.236 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=28873 DF PROTO=TCP SPT=57298 DPT=8400 WINDOW=501 RES=0x00 ACK FIN URGP=0&#8310;
```

---

### Post by ajgreeny on 2024-02-01
Please use code tags (see my signature below for a how-to) as it makes terminal output much easier to read and understand.

---

### Post by Doug S on 2024-02-02
As far as I can tell, those are nothing to worry about because they are all related to tcp session close stuff, "ACK FIN" or "RST".

For TCP connections, Linux tends to use a "half-duplex" close sequence where either side of the session can initiate connection termination via a single 2 way FIN-ACK handshake (which puts the connection into the CLOSE_WAIT state), instead of a full 4 way FIN-ACK handshake. It is common for the connection to have been closed and forgotten about by the connection tracker and then another packet arrives.

I incredibly annoying thing about ufw is that they use the same log prefix for multiple rules that block, making it difficult to know the actual rule that made the log entry.

You should be concerned if you see blocked packets that are attempting to create a new TCP session, with SYN.

---

