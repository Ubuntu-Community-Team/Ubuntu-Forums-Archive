---
title: "Problem with xl2tpd"
date: 2012-06-05
forum: Server Platforms
---

### Post by inckiekage on 2012-06-05
Im trying to setup a l2tp server, to be able to connect a Linksys WRP400 with.

It seems that the router successfully connects to the l2tp server, but I'm not able to get any packet to flow through the tunnel:

[SIZE="3"]Configuration:[/SIZE]

**xl2tpd.conf**
```
kimse@l2tptest:~$ cat /etc/xl2tpd/xl2tpd.conf 
; I'm content with default settings
[global]
; Let define some default LNS config - our peer will use it
[lns default]
ip range = 192.168.2.20 - 192.168.2.100
local ip = 192.168.2.1
require chap = yes
refuse pap = yes
require authentication = yes
unix authentication = no
name = home
ppp debug = no
pppoptfile = /etc/ppp/options.l2tpd
```

**PPP Option file:**
```
kimse@l2tptest:~$ cat /etc/ppp/options.l2tpd
refuse-eap
noccp
noauth
nodefaultroute
crtscts
idle 1800
mtu 1410
mru 1410
lock
connect-delay 5000
```

[SIZE="3"]Debugging information:[/SIZE]

**My routers web interface:**
```
Connection Type : 	L2TP 	  	 
Connection State :  	Connected   	  	 
Internet IP Address :  	192.168.2.20 	  	 
Default Gateway :  	192.168.2.1
```

**ifconfig**
```
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.2.1  P-t-P:192.168.2.20  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1410  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:62 (62.0 B)  TX bytes:1490 (1.4 KB)
```

**ip route**
```
kimse@l2tptest:~$ ip route get 192.168.2.20
192.168.2.20 dev ppp0  src 192.168.2.1 
    cache  ipid 0x2d29
```

**Syslog:**
```
Jun  5 10:44:42 l2tptest xl2tpd[3488]: Connection established to 172.16.100.1, 1701.  Local: 9362, Remote: 26279 (ref=0/0).  LNS session is 'default'
Jun  5 10:44:42 l2tptest xl2tpd[3488]: start_pppd: I'm running: 
Jun  5 10:44:42 l2tptest xl2tpd[3488]: "/usr/sbin/pppd" 
Jun  5 10:44:42 l2tptest xl2tpd[3488]: "passive" 
Jun  5 10:44:42 l2tptest xl2tpd[3488]: "nodetach" 
Jun  5 10:44:42 l2tptest xl2tpd[3488]: "192.168.2.1:192.168.2.20" 
Jun  5 10:44:42 l2tptest xl2tpd[3488]: "refuse-pap" 
Jun  5 10:44:42 l2tptest xl2tpd[3488]: "auth" 
Jun  5 10:44:42 l2tptest xl2tpd[3488]: "require-chap" 
Jun  5 10:44:42 l2tptest xl2tpd[3488]: "name" 
Jun  5 10:44:42 l2tptest xl2tpd[3488]: "home" 
Jun  5 10:44:42 l2tptest xl2tpd[3488]: "file" 
Jun  5 10:44:42 l2tptest xl2tpd[3488]: "/etc/ppp/options.l2tpd" 
Jun  5 10:44:42 l2tptest xl2tpd[3488]: "ipparam" 
Jun  5 10:44:42 l2tptest xl2tpd[3488]: "172.16.100.1" 
Jun  5 10:44:42 l2tptest xl2tpd[3488]: "/dev/pts/2" 
Jun  5 10:44:42 l2tptest xl2tpd[3488]: Call established with 172.16.100.1, Local: 12509, Remote: 31114, Serial: 0
Jun  5 10:44:42 l2tptest pppd[3742]: pppd 2.4.5 started by root, uid 0
Jun  5 10:44:42 l2tptest pppd[3742]: Using interface ppp0
Jun  5 10:44:42 l2tptest pppd[3742]: Connect: ppp0 <--> /dev/pts/2
Jun  5 10:44:45 l2tptest pppd[3742]: local  IP address 192.168.2.1
Jun  5 10:44:45 l2tptest pppd[3742]: remote IP address 192.168.2.20
Jun  5 10:45:47 l2tptest xl2tpd[3488]: Maximum retries exceeded for tunnel 9362.  Closing.
Jun  5 10:45:47 l2tptest xl2tpd[3488]: Terminating pppd: sending TERM signal to pid 3742
Jun  5 10:45:47 l2tptest xl2tpd[3488]: Connection 26279 closed to 172.16.100.1, port 1701 (Timeout)
```

---

