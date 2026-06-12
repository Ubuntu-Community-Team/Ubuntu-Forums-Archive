---
title: "pptpd not responding when connecting"
date: 2012-01-03
forum: Server Platforms
---

### Post by tom.davidson58 on 2012-01-03
I have been trying to set up VPN services on my ubuntu 11.10 server.  according to every tutorial I have found, I have everything set up correctly, but every time I try to connect to it (over WAN or LAN) it says that the server did not respond.  The only thing I have been able to find that I haven't done is that it has been suggested to enable GRE protocol 47 on my firewall, but firewall is disabled (both on the server and the router).  VPN passthrough is enabled on my router and port 1723 is forwarded through my router.  All other network services work (SSH, VNC, etc...) I just can't connect to my VPN.  Any ideas?

---

### Post by tom.davidson58 on 2012-01-09
I seem to have made some progress.  I have been able to connect intermittently, though I cannot access any of the machines on my VPN while connected.  Here is the output from /var/log/syslog:

Jan  9 14:20:11 tom-server pptpd[2245]: CTRL: Client xxx.xxx.xxx.xxx control connection started 
Jan  9 14:20:11 tom-server pptpd[2245]: CTRL: Starting call (launching pppd, opening GRE) 
Jan  9 14:20:11 tom-server pppd[2246]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded. 
Jan  9 14:20:11 tom-server pppd[2246]: pppd 2.4.5 started by root, uid 0 
Jan  9 14:20:11 tom-server pppd[2246]: Using interface ppp0 
Jan  9 14:20:11 tom-server pppd[2246]: Connect: ppp0 <--> /dev/pts/0 
Jan  9 14:20:11 tom-server pptpd[2245]: GRE: Bad checksum from pppd. 
Jan  9 14:20:11 tom-server NetworkManager[1090]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0) 
Jan  9 14:20:11 tom-server NetworkManager[1090]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found. 
Jan 9 14:20:41 tom-server pppd[2246]: LCP: timeout sending Config-Requests 
Jan  9 14:20:41 tom-server pppd[2246]: Connection terminated. 
Jan  9 14:20:41 tom-server NetworkManager[1090]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0) 
Jan  9 14:20:41 tom-server pppd[2246]: Modem hangup 
Jan  9 14:20:41 tom-server pppd[2246]: Exit. 
Jan  9 14:20:41 tom-server pptpd[2245]: GRE: read(fd=6,buffer=6075a0,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs 
Jan  9 14:20:41 tom-server pptpd[2245]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7) 
Jan  9 14:20:41 tom-server pptpd[2245]: CTRL: Reaping child PPP[2246] 
Jan  9 14:20:41 tom-server pptpd[2245]: CTRL: Client xxx.xxx.xxx.xxx control connection finished

I'm really hoping someone out there will have a suggestion as this is driving me nuts...

---

### Post by jonobr on 2012-01-09
I would recommend doing a trace on the target side

If its a wondows you could download wireshark with libpcpap and snoop on the interface

if it ubuntu/*nix then you could (if I remember)

```
sudo tcpdump -i any proto GRE 
```

You could also use a filter like that in your windows wireshark

If you start the tunnel, you should see packets been spit out.

You could then try filtering on GRE and port number.

If you still see packets you know that your setup through the firewalls are ok.

If you dont see anything
try the same command on the intitating side.
If you see stuff leaving, you know its trying to get there.

If you see none on the other end, then its either being lost, blocked or removed.

---

