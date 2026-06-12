---
title: "UFW Help"
date: 2022-10-16
forum: Security
---

### Post by overcon on 2022-10-16
Hi All,

I need some help with UFW. A brief of the situation. I have a VirtualBox Guest VM that runs Apache and acts as a Reverse Proxy (192.168.1.6) for websites. I have another server that runs my Weather Station, it runs Apache and has a website on it that points to the public (192.168.1.12). I run UFW on all my servers and I am OK with it (I thought), I can usually google enough to figure out what I need. Alas, I haven't had much luck figuring this out and so I find myself here, asking for help!

On my Weewx server, I see these messages in the syslog constantly and I don't know why. I have a rule to alllow TCP in on port 443 on the Weewx server. Then I set a rule to allow TCP/443 from ANYWHERE and I still see these messages. So I also tried setting UFW to allow all traffic from the R-Proxy (UFW allow from 192.168.1.6), but I am still getting these blocks. Can someone tell me what exactly is happening and how do I resolve it? The messages pop up when someone accesses the webpage. 

Oct 16 11:30:09 weewx-pi kernel: [ 6090.144470] [UFW BLOCK] IN=enp9s0 OUT= MAC=xx:23:aex:a5:30x:00:27:ac:db:cc:08:00 SRC=192.168.1.6 DST=192.168.1.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=29415 DF PROTO=TCP SPT=53350 DPT=443 WINDOW=501 RES=0x00 ACK FIN URGP=0
Oct 16 11:30:10 weewx-pi kernel: [ 6090.507401] [UFW BLOCK] IN=enp9s0 OUT= MAC=xx:23:aex:a5:30x:00:27:ac:db:cc:08:00 SRC=192.168.1.6 DST=192.168.1.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=20772 DF PROTO=TCP SPT=33468 DPT=443 WINDOW=501 RES=0x00 ACK FIN URGP=0
Oct 16 11:30:10 weewx-pi kernel: [ 6090.560900] [UFW BLOCK] IN=enp9s0 OUT= MAC=xx:23:aex:a5:30x:00:27:ac:db:cc:08:00 SRC=192.168.1.6 DST=192.168.1.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=29416 DF PROTO=TCP SPT=53350 DPT=443 WINDOW=501 RES=0x00 ACK FIN URGP=0
Oct 16 11:30:10 weewx-pi kernel: [ 6090.729311] [UFW BLOCK] IN=enp9s0 OUT= MAC=xx:23:aex:a5:30x:00:27:ac:db:cc:08:00 SRC=192.168.1.6 DST=192.168.1.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=20773 DF PROTO=TCP SPT=33468 DPT=443 WINDOW=501 RES=0x00 ACK FIN URGP=0
Oct 16 11:30:10 weewx-pi kernel: [ 6090.945112] [UFW BLOCK] IN=enp9s0 OUT= MAC=xx:23:aex:a5:30x:00:27:ac:db:cc:08:00 SRC=192.168.1.6 DST=192.168.1.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=20774 DF PROTO=TCP SPT=33468 DPT=443 WINDOW=501 RES=0x00 ACK FIN URGP=0
Oct 16 11:30:11 weewx-pi kernel: [ 6091.386577] [UFW BLOCK] IN=enp9s0 OUT= MAC=xx:23:aex:a5:30x:00:27:ac:db:cc:08:00 SRC=192.168.1.6 DST=192.168.1.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=20775 DF PROTO=TCP SPT=33468 DPT=443 WINDOW=501 RES=0x00 ACK FIN URGP=0
Oct 16 11:30:11 weewx-pi kernel: [ 6091.423729] [UFW BLOCK] IN=enp9s0 OUT= MAC=xx:23:aex:a5:30x:00:27:ac:db:cc:08:00 SRC=192.168.1.6 DST=192.168.1.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=29417 DF PROTO=TCP SPT=53350 DPT=443 WINDOW=501 RES=0x00 ACK FIN URGP=0
Oct 16 11:30:12 weewx-pi kernel: [ 6092.352268] [UFW BLOCK] IN=enp9s0 OUT= MAC=xx:23:aex:a5:30x:00:27:ac:db:cc:08:00 SRC=192.168.1.6 DST=192.168.1.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=20776 DF PROTO=TCP SPT=33468 DPT=443 WINDOW=501 RES=0x00 ACK FIN URGP=0
Oct 16 11:30:13 weewx-pi kernel: [ 6093.386597] [UFW BLOCK] IN=enp9s0 OUT= MAC=xx:23:aex:a5:30x:00:27:ac:db:cc:08:00 SRC=192.168.1.6 DST=192.168.1.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=29418 DF PROTO=TCP SPT=53350 DPT=443 WINDOW=501 RES=0x00 ACK FIN URGP=0

Status: active


     To                         Action      From
     --                         ------      ----
[ 1] 22/tcp                ALLOW IN      Anywhere             # Allow SSH port 22
[ 2] Apache Full         ALLOW IN      Anywhere             # Apache Traffic 80,443/TCP
[COLOR=#FF0000][ 3] Anywhere           ALLOW IN      192.168.1.6          # Allow ANYTHING from 192.168.1.6[/COLOR]
[ 4] 22/tcp (v6)         ALLOW IN      Anywhere (v6)      # Allow SSH port 22
[ 5] Apache Full (v6)  ALLOW IN      Anywhere (v6)      # Apache Traffic 80,443/TCP

---

### Post by Doug S on 2022-10-17
It is important to note the TCP flags in your example syslog lines, "ACK FIN".

It is also important to know that for TCP connections, Linux tends to use a "half-duplex" close sequence where either side of the session can initiate connection termination via a single 2 way FIN-ACK handshake, instead of a full 4 way FIN-ACK handshake.

The blocked packets are likely due to some extra packets at the end of a TCP session where the connection tracking table has already forgotten about the session, and therefore they are considered to be incorrectly formed NEW packets. They are nothing to worry about, and the actual TCP session likely worked just fine.

The very annoying thing with UFW is that it uses the same log prefix "UFW BLOCK" for every type of log entry instead of a descriptive log prefix, indicating the reason for the block.

---

### Post by overcon on 2022-10-17
Awesome, thanks for that explanation. I was getting frustrated. I wasn't noticing anything not working, but no matter what I tried, they won't go away and beyond the security concern, it clutters up the log file.

---

### Post by Doug S on 2022-10-17
> **overcon said:**
> ... it clutters up the log file.Yes, agreed. Very annoying.

---

