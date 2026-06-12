---
title: "what vpn's work with ubuntu 10.04?"
date: 2010-08-01
forum: Security
---

### Post by dogdo on 2010-08-01
ive tried pptp based vpn connections with 10.04 and the connection is always rejected/or times out. What other vpn's style connections work with ubuntu?

---

### Post by dogdo on 2010-08-02
so no vpn connection works with ubuntu?

---

### Post by FuturePilot on 2010-08-02
I use a pptp VPN and it works fine. Can you post the output of

```
tail /var/log/messages
```

after the connection fails?

---

### Post by dogdo on 2010-08-02
where are connection var logs stored -ive looked in the 'log file viewer' but i cant find that name anywhere...

---

### Post by dogdo on 2010-08-02
oh did you mean the terminal??

well this is what i got back then-

daddy@ubuntu:~$ tail /var/log/messages
Aug  2 18:38:45 ubuntu kernel: [ 6691.315759] [UFW AUDIT] IN=eth1 OUT= MAC=78:e4:00:69:ed:97:00:26:f2:40:19:6a:08:00 SRC=91.189.94.12 DST=192.168.0.2 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=60641 DF PROTO=TCP SPT=80 DPT=45240 WINDOW=119 RES=0x00 ACK FIN URGP=0 
Aug  2 18:38:45 ubuntu kernel: [ 6691.316293] [UFW AUDIT] IN=eth1 OUT= MAC=78:e4:00:69:ed:97:00:26:f2:40:19:6a:08:00 SRC=91.189.94.12 DST=192.168.0.2 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=37120 DF PROTO=TCP SPT=80 DPT=45242 WINDOW=104 RES=0x00 ACK FIN URGP=0 
Aug  2 18:38:45 ubuntu kernel: [ 6691.318061] [UFW AUDIT] IN=eth1 OUT= MAC=78:e4:00:69:ed:97:00:26:f2:40:19:6a:08:00 SRC=91.189.94.12 DST=192.168.0.2 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=32752 DF PROTO=TCP SPT=80 DPT=45243 WINDOW=89 RES=0x00 ACK FIN URGP=0 
Aug  2 18:38:45 ubuntu kernel: [ 6691.353401] [UFW AUDIT] IN= OUT=eth1 SRC=192.168.0.2 DST=91.189.94.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=40161 DF PROTO=TCP SPT=45240 DPT=80 WINDOW=500 RES=0x00 ACK URGP=0 
Aug  2 18:38:45 ubuntu kernel: [ 6691.353486] [UFW AUDIT] IN= OUT=eth1 SRC=192.168.0.2 DST=91.189.94.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=6093 DF PROTO=TCP SPT=45242 DPT=80 WINDOW=80 RES=0x00 ACK URGP=0 
Aug  2 18:38:45 ubuntu kernel: [ 6691.353533] [UFW AUDIT] IN= OUT=eth1 SRC=192.168.0.2 DST=91.189.94.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=53162 DF PROTO=TCP SPT=45243 DPT=80 WINDOW=562 RES=0x00 ACK URGP=0 
Aug  2 18:38:45 ubuntu kernel: [ 6691.412322] [UFW AUDIT] IN=eth1 OUT= MAC=78:e4:00:69:ed:97:00:26:f2:40:19:6a:08:00 SRC=91.189.94.12 DST=192.168.0.2 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=12381 DF PROTO=TCP SPT=80 DPT=45239 WINDOW=158 RES=0x00 ACK FIN URGP=0 
Aug  2 18:38:45 ubuntu kernel: [ 6691.443204] [UFW AUDIT] IN= OUT=eth1 SRC=192.168.0.2 DST=91.189.94.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=56183 DF PROTO=TCP SPT=45239 DPT=80 WINDOW=500 RES=0x00 ACK URGP=0 
Aug  2 18:38:45 ubuntu kernel: [ 6691.477872] [UFW AUDIT] IN=eth1 OUT= MAC=78:e4:00:69:ed:97:00:26:f2:40:19:6a:08:00 SRC=91.189.94.12 DST=192.168.0.2 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=10605 DF PROTO=TCP SPT=80 DPT=45241 WINDOW=134 RES=0x00 ACK FIN URGP=0 
Aug  2 18:38:45 ubuntu kernel: [ 6691.512811] [UFW AUDIT] IN= OUT=eth1 SRC=192.168.0.2 DST=91.189.94.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=60038 DF PROTO=TCP SPT=45241 DPT=80 WINDOW=282 RES=0x00 ACK URGP=0 
daddy@ubuntu:~$ 

oddly enough it did connect there once a minute ago...but then i disconnected it on purpose and now it wont connect anymore (could have been a once off).

---

### Post by FuturePilot on 2010-08-02
Hmm wasn't expecting all that. Try

```
grep pppd /var/log/messages
```

---

### Post by dogdo on 2010-08-02
sorry but i got all this with that last command-

daddy@ubuntu:~$ grep pppd /var/log/messages
Aug  1 22:18:48 ubuntu pppd[4086]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug  1 22:18:48 ubuntu pppd[4086]: pppd 2.4.5 started by root, uid 0
Aug  1 22:18:48 ubuntu pppd[4086]: Using interface ppp0
Aug  1 22:18:48 ubuntu pppd[4086]: Connect: ppp0 <--> /dev/pts/0
Aug  1 22:18:49 ubuntu pppd[4086]: CHAP authentication succeeded
Aug  1 22:18:49 ubuntu pppd[4086]: MPPE 128-bit stateless compression enabled
Aug  1 22:18:49 ubuntu pppd[4086]: local  IP address 93.182.139.7
Aug  1 22:18:49 ubuntu pppd[4086]: remote IP address 93.182.139.2
Aug  1 22:18:49 ubuntu pppd[4086]: primary   DNS address 93.182.182.85
Aug  1 22:18:49 ubuntu pppd[4086]: secondary DNS address 93.182.182.85
Aug  1 22:19:29 ubuntu pppd[4086]: Terminating on signal 15
Aug  1 22:19:29 ubuntu pppd[4086]: Connect time 0.7 minutes.
Aug  1 22:19:29 ubuntu pppd[4086]: Sent 0 bytes, received 7556 bytes.
Aug  1 22:19:29 ubuntu pppd[4086]: Child process /usr/sbin/pptp pptp.relakks.com --nolaunchpppd --logstring nm-pptp-service-4083 (pid 4088) terminated with signal 15
Aug  1 22:19:30 ubuntu pppd[4086]: Connection terminated.
Aug  1 22:19:30 ubuntu pppd[4086]: Exit.
Aug  1 22:19:34 ubuntu pppd[4155]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug  1 22:19:34 ubuntu pppd[4155]: pppd 2.4.5 started by root, uid 0
Aug  1 22:19:34 ubuntu pppd[4155]: Using interface ppp0
Aug  1 22:19:34 ubuntu pppd[4155]: Connect: ppp0 <--> /dev/pts/0
Aug  1 22:19:35 ubuntu pppd[4155]: CHAP authentication succeeded
Aug  1 22:19:35 ubuntu pppd[4155]: MPPE 128-bit stateless compression enabled
Aug  1 22:19:36 ubuntu pppd[4155]: local  IP address 93.182.134.37
Aug  1 22:19:36 ubuntu pppd[4155]: remote IP address 93.182.134.2
Aug  1 22:19:36 ubuntu pppd[4155]: primary   DNS address 93.182.182.85
Aug  1 22:19:36 ubuntu pppd[4155]: secondary DNS address 93.182.182.85
Aug  1 22:20:16 ubuntu pppd[4155]: Terminating on signal 15
Aug  1 22:20:16 ubuntu pppd[4155]: Connect time 0.7 minutes.
Aug  1 22:20:16 ubuntu pppd[4155]: Sent 0 bytes, received 16209 bytes.
Aug  1 22:20:16 ubuntu pppd[4155]: Child process /usr/sbin/pptp pptp.relakks.com --nolaunchpppd --logstring nm-pptp-service-4083 (pid 4156) terminated with signal 15
Aug  1 22:20:16 ubuntu pppd[4155]: Connection terminated.
Aug  1 22:20:16 ubuntu pppd[4155]: Exit.
Aug  1 23:01:29 ubuntu pppd[4513]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug  1 23:01:29 ubuntu pppd[4513]: pppd 2.4.5 started by root, uid 0
Aug  1 23:01:29 ubuntu pppd[4513]: Using interface ppp0
Aug  1 23:01:29 ubuntu pppd[4513]: Connect: ppp0 <--> /dev/pts/0
Aug  1 23:02:00 ubuntu pppd[4513]: LCP: timeout sending Config-Requests
Aug  1 23:02:00 ubuntu pppd[4513]: Connection terminated.
Aug  1 23:02:01 ubuntu pppd[4513]: Modem hangup
Aug  1 23:02:06 ubuntu pppd[4513]: Exit.
Aug  2 02:52:44 ubuntu pppd[7474]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug  2 02:52:44 ubuntu pppd[7474]: pppd 2.4.5 started by root, uid 0
Aug  2 02:52:44 ubuntu pppd[7474]: Using interface ppp0
Aug  2 02:52:44 ubuntu pppd[7474]: Connect: ppp0 <--> /dev/pts/1
Aug  2 02:52:45 ubuntu pppd[7474]: CHAP authentication succeeded
Aug  2 02:52:45 ubuntu pppd[7474]: MPPE 128-bit stateless compression enabled
Aug  2 02:52:46 ubuntu pppd[7474]: local  IP address 93.182.157.5
Aug  2 02:52:46 ubuntu pppd[7474]: remote IP address 93.182.157.2
Aug  2 02:52:46 ubuntu pppd[7474]: primary   DNS address 93.182.182.85
Aug  2 02:52:46 ubuntu pppd[7474]: secondary DNS address 93.182.182.85
Aug  2 02:53:26 ubuntu pppd[7474]: Terminating on signal 15
Aug  2 02:53:26 ubuntu pppd[7474]: Connect time 0.7 minutes.
Aug  2 02:53:26 ubuntu pppd[7474]: Sent 0 bytes, received 620 bytes.
Aug  2 02:53:26 ubuntu pppd[7474]: Child process /usr/sbin/pptp pptp.relakks.com --nolaunchpppd --logstring nm-pptp-service-7472 (pid 7476) terminated with signal 15
Aug  2 02:53:26 ubuntu pppd[7474]: Connection terminated.
Aug  2 02:53:26 ubuntu pppd[7474]: Exit.
Aug  2 16:57:51 ubuntu pppd[1872]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug  2 16:57:51 ubuntu pppd[1872]: pppd 2.4.5 started by root, uid 0
Aug  2 16:57:51 ubuntu pppd[1872]: Using interface ppp0
Aug  2 16:57:51 ubuntu pppd[1872]: Connect: ppp0 <--> /dev/pts/0
Aug  2 16:57:53 ubuntu pppd[1872]: CHAP authentication succeeded
Aug  2 16:57:53 ubuntu pppd[1872]: MPPE 128-bit stateless compression enabled
Aug  2 16:57:53 ubuntu pppd[1872]: local  IP address 93.182.158.82
Aug  2 16:57:53 ubuntu pppd[1872]: remote IP address 93.182.158.2
Aug  2 16:57:53 ubuntu pppd[1872]: primary   DNS address 93.182.182.85
Aug  2 16:57:53 ubuntu pppd[1872]: secondary DNS address 93.182.182.85
Aug  2 16:58:33 ubuntu pppd[1872]: Terminating on signal 15
Aug  2 16:58:33 ubuntu pppd[1872]: Connect time 0.7 minutes.
Aug  2 16:58:33 ubuntu pppd[1872]: Sent 0 bytes, received 13510 bytes.
Aug  2 16:58:33 ubuntu pppd[1872]: Child process /usr/sbin/pptp pptp.relakks.com --nolaunchpppd --logstring nm-pptp-service-1869 (pid 1874) terminated with signal 15
Aug  2 16:58:33 ubuntu pppd[1872]: Connection terminated.
Aug  2 16:58:33 ubuntu pppd[1872]: Exit.
Aug  2 18:23:50 ubuntu pppd[2536]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug  2 18:23:50 ubuntu pppd[2536]: pppd 2.4.5 started by root, uid 0
Aug  2 18:23:50 ubuntu pppd[2536]: Using interface ppp0
Aug  2 18:23:50 ubuntu pppd[2536]: Connect: ppp0 <--> /dev/pts/0
Aug  2 18:23:52 ubuntu pppd[2536]: CHAP authentication succeeded
Aug  2 18:23:52 ubuntu pppd[2536]: MPPE 128-bit stateless compression enabled
Aug  2 18:23:52 ubuntu pppd[2536]: local  IP address 93.182.139.62
Aug  2 18:23:52 ubuntu pppd[2536]: remote IP address 93.182.139.2
Aug  2 18:23:52 ubuntu pppd[2536]: primary   DNS address 93.182.182.85
Aug  2 18:23:52 ubuntu pppd[2536]: secondary DNS address 93.182.182.85
Aug  2 18:24:32 ubuntu pppd[2536]: Terminating on signal 15
Aug  2 18:24:32 ubuntu pppd[2536]: Connect time 0.7 minutes.
Aug  2 18:24:32 ubuntu pppd[2536]: Sent 0 bytes, received 5984 bytes.
Aug  2 18:24:32 ubuntu pppd[2536]: Child process /usr/sbin/pptp pptp.relakks.com --nolaunchpppd --logstring nm-pptp-service-2534 (pid 2538) terminated with signal 15
Aug  2 18:24:32 ubuntu pppd[2536]: Connection terminated.
Aug  2 18:24:32 ubuntu pppd[2536]: Exit.
Aug  2 18:36:51 ubuntu pppd[2677]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug  2 18:36:51 ubuntu pppd[2677]: pppd 2.4.5 started by root, uid 0
Aug  2 18:36:51 ubuntu pppd[2677]: Using interface ppp0
Aug  2 18:36:51 ubuntu pppd[2677]: Connect: ppp0 <--> /dev/pts/0
Aug  2 18:36:52 ubuntu pppd[2677]: CHAP authentication succeeded
Aug  2 18:36:53 ubuntu pppd[2677]: MPPE 128-bit stateless compression enabled
Aug  2 18:36:53 ubuntu pppd[2677]: local  IP address 93.182.156.65
Aug  2 18:36:53 ubuntu pppd[2677]: remote IP address 93.182.156.2
Aug  2 18:36:53 ubuntu pppd[2677]: primary   DNS address 93.182.182.85
Aug  2 18:36:53 ubuntu pppd[2677]: secondary DNS address 93.182.182.85
Aug  2 18:37:36 ubuntu pppd[2677]: Terminating on signal 15
Aug  2 18:37:36 ubuntu pppd[2677]: Connect time 0.8 minutes.
Aug  2 18:37:36 ubuntu pppd[2677]: Sent 84567 bytes, received 622243 bytes.
Aug  2 18:37:37 ubuntu pppd[2677]: Child process /usr/sbin/pptp pptp.relakks.com --nolaunchpppd --logstring nm-pptp-service-2675 (pid 2679) terminated with signal 15
Aug  2 18:37:37 ubuntu pppd[2677]: Connection terminated.
Aug  2 18:37:37 ubuntu pppd[2677]: Exit.
Aug  2 18:37:41 ubuntu pppd[2733]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug  2 18:37:41 ubuntu pppd[2733]: pppd 2.4.5 started by root, uid 0
Aug  2 18:37:41 ubuntu pppd[2733]: Using interface ppp0
Aug  2 18:37:41 ubuntu pppd[2733]: Connect: ppp0 <--> /dev/pts/0
Aug  2 18:37:42 ubuntu pppd[2733]: CHAP authentication succeeded
Aug  2 18:37:42 ubuntu pppd[2733]: MPPE 128-bit stateless compression enabled
Aug  2 18:37:42 ubuntu pppd[2733]: local  IP address 93.182.158.134
Aug  2 18:37:42 ubuntu pppd[2733]: remote IP address 93.182.158.2
Aug  2 18:37:42 ubuntu pppd[2733]: primary   DNS address 93.182.182.85
Aug  2 18:37:42 ubuntu pppd[2733]: secondary DNS address 93.182.182.85
Aug  2 18:38:22 ubuntu pppd[2733]: Terminating on signal 15
Aug  2 18:38:22 ubuntu pppd[2733]: Connect time 0.7 minutes.
Aug  2 18:38:22 ubuntu pppd[2733]: Sent 0 bytes, received 0 bytes.
Aug  2 18:38:22 ubuntu pppd[2733]: Child process /usr/sbin/pptp pptp.relakks.com --nolaunchpppd --logstring nm-pptp-service-2675 (pid 2734) terminated with signal 15
Aug  2 18:38:23 ubuntu pppd[2733]: Connection terminated.
Aug  2 18:38:23 ubuntu pppd[2733]: Exit.
Aug  2 18:41:08 ubuntu pppd[2823]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug  2 18:41:08 ubuntu pppd[2823]: pppd 2.4.5 started by root, uid 0
Aug  2 18:41:08 ubuntu pppd[2823]: Using interface ppp0
Aug  2 18:41:08 ubuntu pppd[2823]: Connect: ppp0 <--> /dev/pts/1
Aug  2 18:41:29 ubuntu pppd[2823]: Modem hangup
Aug  2 18:41:29 ubuntu pppd[2823]: Connection terminated.
Aug  2 18:41:29 ubuntu pppd[2823]: Exit.
Aug  2 18:41:41 ubuntu pppd[2853]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug  2 18:41:41 ubuntu pppd[2853]: pppd 2.4.5 started by root, uid 0
Aug  2 18:41:41 ubuntu pppd[2853]: Using interface ppp0
Aug  2 18:41:41 ubuntu pppd[2853]: Connect: ppp0 <--> /dev/pts/0
Aug  2 18:41:42 ubuntu pppd[2853]: CHAP authentication succeeded
Aug  2 18:41:42 ubuntu pppd[2853]: MPPE 128-bit stateless compression enabled
Aug  2 18:41:43 ubuntu pppd[2853]: local  IP address 93.182.158.28
Aug  2 18:41:43 ubuntu pppd[2853]: remote IP address 93.182.158.2
Aug  2 18:41:43 ubuntu pppd[2853]: primary   DNS address 93.182.182.85
Aug  2 18:41:43 ubuntu pppd[2853]: secondary DNS address 93.182.182.85
Aug  2 18:42:23 ubuntu pppd[2853]: Terminating on signal 15
Aug  2 18:42:23 ubuntu pppd[2853]: Connect time 0.7 minutes.
Aug  2 18:42:23 ubuntu pppd[2853]: Sent 0 bytes, received 28554 bytes.
Aug  2 18:42:23 ubuntu pppd[2853]: Child process /usr/sbin/pptp pptp.relakks.com --nolaunchpppd --logstring nm-pptp-service-2851 (pid 2855) terminated with signal 15
Aug  2 18:42:23 ubuntu pppd[2853]: Connection terminated.
Aug  2 18:42:23 ubuntu pppd[2853]: Exit.
Aug  2 19:28:02 ubuntu pppd[3401]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug  2 19:28:02 ubuntu pppd[3401]: pppd 2.4.5 started by root, uid 0
Aug  2 19:28:02 ubuntu pppd[3401]: Using interface ppp0
Aug  2 19:28:02 ubuntu pppd[3401]: Connect: ppp0 <--> /dev/pts/0
Aug  2 19:28:03 ubuntu pppd[3401]: CHAP authentication succeeded
Aug  2 19:28:04 ubuntu pppd[3401]: MPPE 128-bit stateless compression enabled
Aug  2 19:28:04 ubuntu pppd[3401]: local  IP address 93.182.136.123
Aug  2 19:28:04 ubuntu pppd[3401]: remote IP address 93.182.136.2
Aug  2 19:28:04 ubuntu pppd[3401]: primary   DNS address 93.182.182.85
Aug  2 19:28:04 ubuntu pppd[3401]: secondary DNS address 93.182.182.85
Aug  2 19:28:44 ubuntu pppd[3401]: Terminating on signal 15
Aug  2 19:28:44 ubuntu pppd[3401]: Connect time 0.7 minutes.
Aug  2 19:28:44 ubuntu pppd[3401]: Sent 0 bytes, received 0 bytes.
Aug  2 19:28:44 ubuntu pppd[3401]: Child process /usr/sbin/pptp pptp.relakks.com --nolaunchpppd --logstring nm-pptp-service-3399 (pid 3403) terminated with signal 15
Aug  2 19:28:44 ubuntu pppd[3401]: Connection terminated.
Aug  2 19:28:44 ubuntu pppd[3401]: Exit.
daddy@ubuntu:~$

---

### Post by FuturePilot on 2010-08-02
That's fine. That's what I was expecting. It seems that it's disconnecting immediately after connecting. Possibly a server side issue. Have you tested a different VPN?

---

### Post by dogdo on 2010-08-02
you mean another pptp based vpn? no i havent. What vpn do you use if you dont mind me asking?

The vpn i use at the moment (realakks) works fine on windows 7 and opensuse 11.2. Its only on ubuntu that the vpn doesent work.

---

### Post by FuturePilot on 2010-08-02
I've been using [http://itshidden.com/]("http://itshidden.com/")

Though if yours works on Windows and Suse then it might possibly be a bug. Can't tell for sure. Might also be a settings issue. Double check your settings just to be sure.

---

### Post by The Cog on 2010-08-03
I see you have ufw enabled. It might be worth disabling it for long enough to see if that fixes your problem. If so then you need to open something else in the firewall.

But more likely, I see that you are locally on 192.168.0.2. So you are using NAT to access the internet. I believe that you can only pass a single PPTP connection through NAT at a time, after which you must wait for the router to timeout that connection and remove its NAT entry before you can establish a different PPTP connection out through the NAT router. This fits with your description of having been able to establish a connection once but not again. Try rebooting your router in between connections, to clear its NAT tables.

I believe that OpenVPN doesn't have this one-NAT-connection-only problem, if you are in a position to change which VPN server to use.

---

### Post by dogdo on 2010-08-03
By any chance are there well known open vpn providers online? All i want is a vpn for private home use-browsing etc.

---

### Post by wacky_sung on 2010-08-03
> **FuturePilot said:**
> I've been using [http://itshidden.com/]("http://itshidden.com/")

Though if yours works on Windows and Suse then it might possibly be a bug. Can't tell for sure. Might also be a settings issue. Double check your settings just to be sure.

The VPN encryption which they offered are not reliable and can easy be crack through dictionary attack.

---

### Post by FuturePilot on 2010-08-03
> **wacky_sung said:**
> The VPN encryption which they offered are not reliable and can easy be crack through dictionary attack.

Have any reading material about that? I'm curious.

---

