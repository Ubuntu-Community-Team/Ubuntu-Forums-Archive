---
title: "iptables question pptp"
date: 2011-01-27
forum: Security
---

### Post by Braese on 2011-01-27
Hi,

perhaps anyone can help me. Situation:
A VPS Server, i installed a PPTP Server on it, is working.
Client connecting to PPTP Server, working.

Now i only wanna one port thru the PPTP Connection, all other NOT. In example Port 52000 on Client. Users connecting to Serverip:52000 and should land on Client:52000, BUT and that is what is important for me, with their Real IP. If i do a POSTROUTING ppp0 MASQUERADE it is working, but the Users in my Log have the IP from the Server and not their Realip. It makes sense because i do Masquerading.

Anyone can Help me? That would be great! VPN IPs are 192.168.0.1 on Server and 192.168.0.234 on Client. I can ping each other. Server Interfaces: eth0 and if i connected with PPTP Client ppp0 (192.168.0.1).

I wanna not route all traffic through PPTP, only one or two Ports!

Greets.

---

### Post by bodhi.zazen on 2011-01-28
If you want to forward only 1 or 2 ports, why not ssh ?

---

### Post by Braese on 2011-01-28
No SSH, because i wanna have the real source IPs from Users in the application Log. If you do Masquerading or SSH Tunnel, in example Webserver on Client, Users that are connecting dont have their real ip they have IP from the Tunnel, in example from the Server.

I dont wanna route all traffic into VPN, only one or two or three, what matters, into VPN, so that Users can connect to SERVERIP:8080 and landing on CLIENT:8080 without they see the normal CLIENT IP. Possible?

---

### Post by bodhi.zazen on 2011-01-28
I am not really understanding what you want ...

I would log their "real ip" from iptables when they establish the ssh or vpn connection.

If you are running some kind of a web server, use a reverse proxy and log their ip on the reverse proxy.

---

### Post by Braese on 2011-01-29
Hi,

Webserver was only a Example. In example Appliaction A has a TCP Port where Users can connecting and a webif where i can monitoring this service. I dont wanna have that users know the IP of Server of this Service, in example 192.168.1.10. The Users should only connect to the Server that is providing PPTP to 192.168.1.10, in example 192.168.1.20. So, Users should connecto to 192.168.1.20 Port 52000 and NOT to 192.16.1.10. If i do it with SSH Tunnel and go into the webif of the service, i see the Users and IP address, but not from the users, from the pptp server. So every Users have IP 192.168.1.20. This make some things impossible, like fail2ban or anything other service that is checking IP Addresses. 192.168.1.10 should be available for me with own dyndns Host to check webif outside of LAN, but not routing over PPTP. Webif Port in example should not be available over 192.168.1.20.

So i wanna do it with PPTP oder OpenVPN. 192.168.1.10 should make a PPTP connection to 192.168.1.20. It is working. But i dont wanna route all traffic over PPTP, only traffic that i do allow. In example only TCP Traffic over Port 52000. In example only TCP Traffic over xxx and so on.

---

### Post by bodhi.zazen on 2011-01-30
NAT, route, or a reverse proxy perhaps.

See man route - When you establish a VPN you set the route, so, use a different route (define a default gw and a rout to the hosts in question).

One of the above 3 tools should do the trick.

---

