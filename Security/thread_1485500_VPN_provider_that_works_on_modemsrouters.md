---
title: "VPN provider that works on modems/routers?"
date: 2010-05-16
forum: Security
---

### Post by dogdo on 2010-05-16
Hi  Can anyone recommend me a vpn provider that encrypts all traffic (http, https, ftp, etc) and has a proxy ip address different from my own actual address? What this type of configuration be suitable for use on a router so that all connected devices could benefit?

---

### Post by The Cog on 2010-05-17
I'm not sure what you are asking for there. Can you explain further what it is you are looking for - what problem you are trying to solve?

---

### Post by dogdo on 2010-05-24
ok 

So I just signed up with these guys [https://www.relakks.com/](https://www.relakks.com/) and im now connected via a my isp to this vpn service. Can someone please explain to me in  simple terms how secure this connection is?

If i download torrents via firefox and transmission it is safe to assume thats its my vpn service ip address that is collected and not my real ip address?

---

### Post by OpSecShellshock on 2010-05-24
> **dogdo said:**
> ok 

So I just signed up with these guys [https://www.relakks.com/](https://www.relakks.com/) and im now connected via a my isp to this vpn service. Can someone please explain to me in  simple terms how secure this connection is?

If i download torrents via firefox and transmission it is safe to assume thats its my vpn service ip address that is collected and not my real ip address?

Your VPN IP address will be the one that's visible to everything you connect with after having acquired it, yes. The VPN server itself may retain log data of dates, times, users, and originating IP addresses, though. If you're wondering if anyone can identify you specifically, then yes they can, so long as the service provider is amenable to it/forced to.

---

### Post by dogdo on 2010-05-25
Ok most times when i try to use 10.04 to connect to a vpn i get this error message-see attachment 


On the same pc with dual boot i can connect all the time with windows 7. 

Anyone know how to fix this? google seems to be littered with people with this same problem but no solution [http://www.google.ie/search?hl=en&source=hp&q=ubuntu+vpn+connection+timed+out+&meta=&btnG=Google+Search](http://www.google.ie/search?hl=en&source=hp&q=ubuntu+vpn+connection+timed+out+&meta=&btnG=Google+Search)

---

### Post by 0xyg3n on 2010-05-25
You can test a solution by trying another free VPN service.  There's tons out there, just search "top 5 free VPN" with a Google search.  Some do provide for Linux support.

Also, the only thing a VPN does is create a secure tunnel connection through the internet and refers the IP address from which you have established the connection.  It does not at all equate to "anonymity."

---

### Post by dogdo on 2010-05-26
> **0xyg3n said:**
> You can test a solution by trying another free VPN service.  There's tons out there, just search "top 5 free VPN" with a Google search.  Some do provide for Linux support.

Also, the only thing a VPN does is create a secure tunnel connection through the internet and refers the IP address from which you have established the connection.  It does not at all equate to "anonymity."

Thats hardly a solution. Ive paid into this for 3 months now so i want to use my vpn on ubuntu. It worked out of the box on windows. I dont understand why its not working on 10.04. Annoying as hell.

---

### Post by Rnd227 on 2010-05-26
I also have a issue using relakks.

I know it can work : I got it to work twice. Since then, I can't get any connection to/through relakks.

I use Ubuntu 10.4

Included : system log 

```
May 26 14:26:57 linolivier NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
May 26 14:26:57 linolivier NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 5070
May 26 14:26:57 linolivier NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
May 26 14:26:57 linolivier NetworkManager: <info>  VPN plugin state changed: 1
May 26 14:26:57 linolivier NetworkManager: <info>  VPN plugin state changed: 3
May 26 14:26:57 linolivier NetworkManager: <info>  VPN connection 'ors' (Connect) reply received.
May 26 14:26:57 linolivier pppd[5072]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
May 26 14:26:57 linolivier pppd[5072]: pppd 2.4.5 started by root, uid 0
May 26 14:26:57 linolivier NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 26 14:26:57 linolivier NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
May 26 14:26:57 linolivier pppd[5072]: Using interface ppp0
May 26 14:26:57 linolivier pppd[5072]: Connect: ppp0 <--> /dev/pts/1
May 26 14:26:57 linolivier pptp[5075]: nm-pptp-service-5070 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
May 26 14:27:18 linolivier pptp[5080]: nm-pptp-service-5070 warn[open_inetsock:pptp_callmgr.c:329]: connect: Connection timed out
May 26 14:27:18 linolivier pptp[5080]: nm-pptp-service-5070 fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to 93.182.131.2
May 26 14:27:18 linolivier pptp[5075]: nm-pptp-service-5070 fatal[open_callmgr:pptp.c:479]: Call manager exited with error 256
May 26 14:27:18 linolivier pppd[5072]: Modem hangup
May 26 14:27:18 linolivier pppd[5072]: Connection terminated.
May 26 14:27:18 linolivier NetworkManager: <info>  VPN plugin failed: 1
May 26 14:27:18 linolivier NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 26 14:27:18 linolivier pppd[5072]: Exit.
May 26 14:27:18 linolivier NetworkManager: <info>  VPN plugin failed: 1
May 26 14:27:18 linolivier NetworkManager: <info>  VPN plugin failed: 1
May 26 14:27:18 linolivier NetworkManager: <info>  VPN plugin state changed: 6
May 26 14:27:18 linolivier NetworkManager: <info>  VPN plugin state change reason: 0
May 26 14:27:18 linolivier NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
May 26 14:27:18 linolivier NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
May 26 14:27:31 linolivier NetworkManager: <debug> [1274876851.000230] ensure_killed(): waiting for vpn service pid 5070 to exit
May 26 14:27:31 linolivier NetworkManager: <debug> [1274876851.000319] ensure_killed(): vpn service pid 5070 cleaned up
```

I wish someone could explain to me what I can do to get the service to work.

In advance, thank you !

---

### Post by dogdo on 2010-05-26
Hate to sound like a total traitor here but ive been playing around with some live cd's for the past few hours...ubuntu 9.10 and linux mint 9 wont let me connect to the Relakks vpn. 

However Open Suse 11.2 connects and i can use the Relakks vpn with this!! Without sounding too two faced is open suse as good as ubuntu? I couldnt help but notice that apparmor has a gui here and it gives the user notifications when something is happening! Joy.

---

### Post by bigbaraboom on 2010-07-27
> **dogdo said:**
> Ok most times when i try to use 10.04 to connect to a vpn i get this error message-see attachment 


On the same pc with dual boot i can connect all the time with windows 7. 

Anyone know how to fix this? google seems to be littered with people with this same problem but no solution [http://www.google.ie/search?hl=en&source=hp&q=ubuntu+vpn+connection+timed+out+&meta=&btnG=Google+Search](http://www.google.ie/search?hl=en&source=hp&q=ubuntu+vpn+connection+timed+out+&meta=&btnG=Google+Search)

Are you using PPTP or OpenVPN? Are you using network-manager as a client?

---

### Post by delwinv on 2010-11-10
This may help:

[http://ubuntuforums.org/showpost.php?p=10099463&postcount=3](http://ubuntuforums.org/showpost.php?p=10099463&postcount=3)

---

### Post by fanturo on 2011-03-22
Try [http://www.vpnmaster.com](http://www.vpnmaster.com)

They support DD-WRT based routers and provide easy setup.

---

