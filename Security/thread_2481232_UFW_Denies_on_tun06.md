---
title: "UFW Denies on tun06"
date: 2022-11-23
forum: Security
---

### Post by pat-grogotech.com on 2022-11-23
I am running an openvpn tunnel as my default route and am getting the following denies:

```
Nov 23 17:49:19 cronin kernel: [UFW BLOCK] IN=tun06 OUT= MAC= SRC=24.57.13.171 DST=10.13.110.12 LEN=52 TOS=0x00 PREC=0x20 TTL=44 ID=9072 DF PROTO=TCP SPT=57984 DPT=49530 WINDOW=1369 RES=0x00 ACK FIN URGP=0 
Nov 23 17:49:38 cronin kernel: [UFW BLOCK] IN=tun06 OUT= MAC= SRC=154.159.237.134 DST=10.13.110.12 LEN=40 TOS=0x08 PREC=0x20 TTL=107 ID=10152 DF PROTO=TCP SPT=10435 DPT=49530 WINDOW=259 RES=0x00 ACK FIN URGP=0 
Nov 23 17:49:58 cronin kernel: [UFW BLOCK] IN=tun06 OUT= MAC= SRC=175.138.117.9 DST=10.13.110.12 LEN=52 TOS=0x00 PREC=0x00 TTL=49 ID=12740 DF PROTO=TCP SPT=53747 DPT=49530 WINDOW=1369 RES=0x00 ACK FIN URGP=0 

```

I have attempted to add rules in UFW to allow this traffic:
```
ufw insert 1 allow out on tun06 to any port 20000:60000 proto tcp
ufw insert 1 allow in to any port 20000:60000 proto tcp


```Here is my ruleset:
     ```
To                         Action      From
     --                         ------      ----
[ 1] 20000:60000/tcp            ALLOW IN    Anywhere                  
[ 2] 20000:60000/tcp            ALLOW OUT   Anywhere on tun06          (out)
[ 3] 33434:33524/udp            ALLOW OUT   Anywhere on wlan0          (out) # Allow traceroute traffic outgoing
[ 4] 124.187.44.34 1194         ALLOW OUT   Anywhere on wlan0          (out) # Allow openvpn traffic to Isabella
[ 5] 192.168.0.3 22             ALLOW OUT   Anywhere on wlan0          (out) # cronin Allow ssh to cronin kodi
[ 6] 10.0.10.0/24 22            ALLOW OUT   Anywhere on wlan0          (out) # chapman Allow ssh to chapman subnet
[ 7] 10.0.10.0/24 137           ALLOW OUT   Anywhere on wlan0          (out) # chapman Allow cifs to chapman subnet
[ 8] 10.0.10.0/24 138           ALLOW OUT   Anywhere on wlan0          (out) # chapman Allow cifs to chapman subnet
[ 9] 10.0.10.0/24 139           ALLOW OUT   Anywhere on wlan0          (out) # chapman Allow cifs to chapman subnet
[10] 10.0.10.0/24 445           ALLOW OUT   Anywhere on wlan0          (out) # chapman Allow cifs to chapman subnet
[11] 180.92.192.0/24            DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Sydney PIA gateway
[12] 202.130.32.0/24            DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Sydney PIA gateway
[13] 117.120.10.0/24            DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Sydney PIA gateway
[14] 221.121.146.0/24           DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Sydney PIA gateway
[15] 118.127.60.0/24            DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Sydney PIA gateway
[16] 103.13.102.0/24            DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Sydney PIA gateway
[17] 117.120.9.0/24             DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Sydney PIA gateway
[18] 27.50.82.0/24              DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Melbourne PIA gateway
[19] 43.250.204.0/24            DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Melbourne PIA gateway
[20] 221.121.139.0/24           DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Melbourne PIA gateway
[21] 43.242.68.0/24             DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Melbourne PIA gateway
[22] 43.242.69.0/24             DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Melbourne PIA gateway
[23] 118.127.62.0/24            DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Melbourne PIA gateway
[24] 181.214.215.0/24           DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Melbourne PIA gateway
[25] 43.250.205.0/24            DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Perth PIA gateway
[26] 202.60.86.0/24             DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the New Zealand PIA gateway
[27] 43.250.207.0/24            DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the New Zealand PIA gateway
[28] 86.107.104.0/24            DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Hong Kong PIA gateway
[29] 91.219.213.0/24            DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Hong Kong PIA gateway
[30] 188.241.80.0/24            DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the China PIA gateway
[31] 185.253.163.0/24           DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Mongolia PIA gateway
[32] 188.214.106.0/24           DENY OUT    Anywhere on wlan0          (out) # Block Traffic to the Tawain PIA gateway
[33] 1197                       ALLOW OUT   Anywhere on wlan0          (out) # Allow vpn traffic to anywhere
[34] 443                        ALLOW OUT   Anywhere on wlan0          (out) # Allow https traffic to anywhere
[35] 80                         ALLOW OUT   Anywhere on wlan0          (out) # Allow http traffic to anywhere
[36] Anywhere                   DENY OUT    Anywhere on wlan0          (out)
[37] 20000:60000/tcp (v6)       ALLOW OUT   Anywhere (v6) on tun06     (out)
[38] 33434:33524/udp (v6)       ALLOW OUT   Anywhere (v6) on wlan0     (out) # Allow traceroute traffic outgoing
[39] 1197 (v6)                  ALLOW OUT   Anywhere (v6) on wlan0     (out) # Allow vpn traffic to anywhere
[40] 443 (v6)                   ALLOW OUT   Anywhere (v6) on wlan0     (out) # Allow https traffic to anywhere
[41] 80 (v6)                    ALLOW OUT   Anywhere (v6) on wlan0     (out) # Allow http traffic to anywhere
[42] Anywhere (v6)              DENY OUT    Anywhere (v6) on wlan0     (out)
[43] 20000:60000/tcp (v6)       ALLOW IN    Anywhere (v6)             


```I have attempted many other combinations of rules and don't seem to be able to allow the traffic.

Any ideas?

Thanks,

Pat

---

### Post by Doug S on 2022-11-25
You need to look at the TCP flags in the log entries. "ACK FIN" is session termination related. Your TCP session actually worked fine. For TCP connections, Linux tends to use a "half-duplex" close sequence where either side of the session can initiate connection termination via a single 2 way FIN-ACK handshake (which puts the connection into the CLOSE_WAIT state), instead of a full 4 way FIN-ACK handshake. Often intermediaries, such a UFW in this case, have already closed and forgotten about the connection and therefore "see" the packet as attempting to make a new connection without the appropriate TCP flag settings.

---

