---
title: "Can't explain some BLOCK FORWARD log messages"
date: 2008-04-28
forum: Security
---

### Post by rmorison on 2008-04-28
I'm using ufw to configure ubuntu 8.04 server as a router w/ IP Masquerade per [http://doc.ubuntu.com/ubuntu/serverguide/C/firewall.html](http://doc.ubuntu.com/ubuntu/serverguide/C/firewall.html). All works well, but I see quite a few BLOCK FORWARD log messages that I don't expect/can't explain. The two below cite port 2223 from an inside machine (192.168.1.159) to the IP of a hosted server of mine (65.111.165.123). Port 2223 is a valid service port on 65.111.165.123 and the traffic seems to flow just fine from the client side.

If I didn't notice the log messages, I wouldn't know any packets were being dropped. But why are packets being dropped at all? The connection is open over a long period and the messages are consistent, 1-3 such log messages per minute. I see similar BLOCKs for some port 80 traffic, too.

Can anyone help explain, or suggest further investigation as to why? 

Apr 28 11:13:13 bolet kernel: [79716.969503] [UFW BLOCK FORWARD]: IN=eth1 OUT=eth0 SRC=65.111.165.123 DST=192.168.1.159 LEN=52 TOS=0x00 PREC=0x20 TTL=49 ID=18291 DF PROTO=TCP SPT=2223 DPT=3029 WINDOW=13464 RES=0x00 ACK PSH URGP=0  
Apr 28 11:13:31 bolet kernel: [79735.186914] [UFW BLOCK FORWARD]: IN=eth0 OUT=eth1 SRC=192.168.1.159 DST=65.111.165.123 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=40375 DF PROTO=TCP SPT=3029 DPT=2223 WINDOW=65535 RES=0x00 ACK URGP=0 

My /etc/ufw/before.rules is attached, which should be stock plus the IP Masquerade rules.

---

