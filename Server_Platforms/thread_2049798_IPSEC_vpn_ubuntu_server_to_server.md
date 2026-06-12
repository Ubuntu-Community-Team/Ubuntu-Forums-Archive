---
title: "IPSEC vpn ubuntu server to server"
date: 2012-08-29
forum: Server Platforms
---

### Post by netmonky on 2012-08-29
Hi All,

I am quite new to the linux community and have a system at home and another system elsewhere. I would like to be able to create an IPSEC L2TP VPN between the two sites that have dyndns. I have looked at openswan but i dont think it supports dyndns names :-( 

Can anyone help or provide me with a tutorial or some ideas to get around this - am sure you guys have set something similar up ;-)



Mark

---

### Post by SeijiSensei on 2012-08-29
Unless you have some masochistic attachment to IPSEC, I strongly suggest using OpenVPN instead.  I run point-to-point tunnels between machines all the time.  Take a look at this [HOWTO]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") for the simplest method, a tunnel where both ends use a predefined encryption key.  The configuration file is only about a dozen lines long.  Here's an example from the server end:

```

dev tun
ifconfig 10.1.1.1 10.1.1.2
up /etc/openvpn/add_routes
secret /etc/openvpn/mykey
port 43434 
user nobody
group nogroup
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key
verb 3
no-replay
comp-lzo

```

The client end adds a "remote" directive with the IP address or hostname of the server and reverses the order of IP addresses in the "ifconfig" directive.  The "up" directive is optional; it defines a script that is run after the connection is set up.  Usually it's used to configure static routes.

Because OpenVPN uses SSL, the client can be behind a firewall and still connect.  I use this to manage servers in client offices.  When the client's machine boots up, it sets up the tunnel to my public server.

OpenVPN uses port 1194 by default, but you can change that with the "port" directive.  If you need to maintain tunnels with multiple remotes, you just use a different port for each tunnel.

---

### Post by netmonky on 2012-08-29
thanks SeijiSensei, Thats great  - ideally wanted IPSEC as I eventually wanted to connect another site as well which has a Cisco router as the DF.

---

### Post by SeijiSensei on 2012-08-29
> **netmonky said:**
> thanks SeijiSensei, Thats great  - ideally wanted IPSEC as I eventually wanted to connect another site as well which has a Cisco router as the DF.

If you can put an old box running Linux behind the Cisco, you can have it create the tunnel by configuring the machine as a client.

---

### Post by netmonky on 2012-08-29
Ok, looks easy but I doesnt appear to work for me. 

Current setup

PC1 -->NetgearGW---((INTERNET)) ----NetgearGW<-- PC2


for testing I have port forwarded port 43434 on both GW's.

PC1 - CLient
_______________

#server hostname
remote xxxx.homeip.net

dev tun
ifconfig 10.0.0.2 10.0.0.1

#add static routes, key and port
#up /etc/openvpn/add_routes
secret /etc/openvpn/static.key
port 43434 

#UID's (optional)
user nobody
group nogroup

#Timeouts
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key

#Verbose
verb 4
no-replay

#compression
comp-lzo



PC2 - server
-----------

dev tun
ifconfig 10.0.0.1 10.0.0.2

#add static routes, key and port
#up /etc/openvpn/add_routes
secret /etc/openvpn/static.key
port 43434 

#UID's (optional)
user nobody
group nogroup

#Timeouts
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key

#Verbose
verb 4
no-replay
comp-lzo

Logs
--------

Aug 30 00:37:21 [3235]: LZO compression initialized
Aug 30 00:37:21 [3235]: Socket Buffers: R=[163840->131072] S=[163840->131072]
Aug 30 00:37:21 [3235]: Preserving previous TUN/TAP instance: tun0
Aug 30 00:37:21 [3235]: Data Channel MTU parms [ L:1537 D:1450 EF:37 EB:135 ET:0 EL:0 AF:3/1 ]
Aug 30 00:37:21 [3235]: Local Options String: 'V4,dev-type tun,link-mtu 1537,tun-mtu 1500,proto UDPv4,ifconfig 10.0.0.1 10.0.0.2,comp-lzo,cipher BF-CBC,auth SHA1,keysize 128,secret,no-replay'
Aug 30 00:37:21 [3235]: Expected Remote Options String: 'V4,dev-type tun,link-mtu 1537,tun-mtu 1500,proto UDPv4,ifconfig 10.0.0.2 10.0.0.1,comp-lzo,cipher BF-CBC,auth SHA1,keysize 128,secret,no-replay'
Aug 30 00:37:21 [3235]: Local Options hash (VER=V4): '51f25623'
Aug 30 00:37:21 [3235]: Expected Remote Options hash (VER=V4): 'b592b799'
Aug 30 00:37:21 [3235]: UDPv4 link local (bound): [undef]
Aug 30 00:37:21 [3235]: UDPv4 link remote: [AF_INET]72.99.72.10:43434


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.0.0.2  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:1092 (1.0 KB


Tunnel is up but I am unable to pass traffic over it - both system firewalls have been disabled for now. 


PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
^C
--- 10.0.0.2 ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 7010ms

Can you help please :-) 



Thanks in Advance

---

### Post by netmonky on 2012-08-30
Ahhh, fixed. Typo on client remote end ;)


THanks for help !

---

