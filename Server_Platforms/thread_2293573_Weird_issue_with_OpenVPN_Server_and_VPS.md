---
title: "Weird issue with OpenVPN Server and VPS"
date: 2015-09-05
forum: Server Platforms
---

### Post by Bob_Burges on 2015-09-05
Hey guys,

This is my first time posting here and I did tons of research on this and googling and even read some threads here with similar problem and for some reason I still cannot get this to work right. I setup a OpeVPN Server following this tutorial: [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-14-04)

I have a VPS with Digital Ocean that this is running on and if I set the protocol to TCP in my server.conf, I can connect to the VPN and get internet access. However if I set the protocol to UDP and connect using UDP, it connects fine, but I can only SSH into my VPS and ping it, I can't ping any other hosts, or ip addresses and there is no internet access. I did a tcpdump on eth0 with TCP as the protocol and I see packets going to openvpn, and when I do a tcpdump on tun0 I see packets incoming from my VPN Clients IP 10.8.0.0.6 or something and data coming into the tun0 and going to 10.8.0.0.6, so that looks right. I did the same thing with the protocol set to UDP and I see packets coming in through eth0 and going to openvpn but when I look at tun0 nothing comes in from my VPN.

So I can't figure this out, I am connecting to my VPN using a DD-WRT Router, and like I said if the protocol is set to TCP there isn't any issues, but when set to UDP I don't get internet access and I can't ping anything outside of my VPS. I don't have any firewalls enabled either.

Server.conf
port 1194
proto tcp
dev tun
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh2048.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
keepalive 10 120
comp-lzo no
persist-key
persist-tun
status openvpn-status.log
verb 3
tun-mtu 1000
tcp-nodelay

Client conf:
resolv-retry infinite
persist-key
persist-tun
ns-cert-type server
verb 3

Routing Table:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         107.170.235.1   0.0.0.0         UG        0 0          0 eth0
10.8.0.0        10.8.0.2        255.255.255.0   UG        0 0          0 tun0
10.8.0.2        0.0.0.0         255.255.255.255 UH        0 0          0 tun0
107.170.235.0   0.0.0.0         255.255.255.0   U         0 0          0 eth0



Thank you for the help,

I have been at this for a week now and cannot seem to make this work.

---

### Post by darkod on 2015-09-06
From your post and the conf files it looks like you are trying to use the VPN as gateway for your home machines, right?

Few things to have in mind (only being connected to the VPN is not enough).

On the DO VPS did you:
1. Allow forwarding in /etc/sysctl.conf?
2. Setup iptables for forwarding/natting?

On the client side, you also need to set options for natting, but in your case if you are using a router to do this, that might be enough.

Also, did you post all of your client.conf? There are no lines for certificates, are you connecting without client certificates? And in the client.conf it's better to drop the persist-tun option because that makes an issue for the client to try to reconnect. I only discovered that myself when investigating why clients are not reconnecting after dropping a connection. And you also need something like the keepalive 10 120 on the client side to tell it to try and reconnect automatically.

In general, everything works great over UDP too, so you are missing something. I actually have that setup over a DO VPS too, but I connect client machines, not a single router only. Yoy are trying to connect only the router and everything behind it will use the VPN automatically right?

---

### Post by darkod on 2015-09-06
PS. If you will only be connecting your home router to this vpn, you have another option for the configuration. Instead of using server-client which is planned when multiple clients need to connect to the same vpn server, you can simply have a "direct" vpn tunnel between your DO VPS and your home router.

It should work fine either way. Basically openvpn is quite easy to set up, there are just few important things that one shouldn't miss. It mostly fails on routing and/or NAT masquerading.

---

### Post by volkswagner on 2015-09-06
Perhaps your firewall/iptables is allowing/forwarding only tcp not udp?

What does your iptables look like?

---

### Post by Bob_Burges on 2015-09-06
> **darkod said:**
> From your post and the conf files it looks like you are trying to use the VPN as gateway for your home machines, right?

Few things to have in mind (only being connected to the VPN is not enough).

On the DO VPS did you:
1. Allow forwarding in /etc/sysctl.conf?
2. Setup iptables for forwarding/natting?

On the client side, you also need to set options for natting, but in your case if you are using a router to do this, that might be enough.

Also, did you post all of your client.conf? There are no lines for certificates, are you connecting without client certificates? And in the client.conf it's better to drop the persist-tun option because that makes an issue for the client to try to reconnect. I only discovered that myself when investigating why clients are not reconnecting after dropping a connection. And you also need something like the keepalive 10 120 on the client side to tell it to try and reconnect automatically.

In general, everything works great over UDP too, so you are missing something. I actually have that setup over a DO VPS too, but I connect client machines, not a single router only. Yoy are trying to connect only the router and everything behind it will use the VPN automatically right?

Basically yes,

I'm just trying to use the VPN to route all my internet traffic through. I DD-WRT on my router and the OpenVPN Client so that all the machines behind my router use the VPN too, which has worked fine when I used a VPN service that offered OpenVPN, and it would connect using UDP just fine. However I'm trying to use Digital Ocean on my own VPS for learning and so I can manage it better.

1. In /etc/sysctl.conf its set to net.ipv4.ip_forward=1
So yes forwarding has been allowed.

2. You know I believe I did set that up correctly (hopefully). I'm kinda new to iptables but here is my iptable config, I got this by running (iptables -L -v)

Chain INPUT (policy ACCEPT 791K packets, 132M bytes)
 pkts bytes target     prot opt in     out     source               destination
1627K  263M ufw-before-logging-input  all  --  any    any     anywhere             anywhere
1627K  263M ufw-before-input  all  --  any    any     anywhere             anywhere
1573K  256M ufw-after-input  all  --  any    any     anywhere             anywhere
1573K  256M ufw-after-logging-input  all  --  any    any     anywhere             anywhere
1573K  256M ufw-reject-input  all  --  any    any     anywhere             anywhere
1573K  256M ufw-track-input  all  --  any    any     anywhere             anywhere
    6   252 ACCEPT     udp  --  eth0   any     anywhere             anywhere             state NEW udp dpt:openvpn
    0     0 ACCEPT     all  --  tun+   any     anywhere             anywhere
    0     0 ACCEPT     udp  --  eth0   any     anywhere             anywhere             state NEW udp dpt:openvpn


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
2402K 1706M ufw-before-logging-forward  all  --  any    any     anywhere             anywhere
2402K 1706M ufw-before-forward  all  --  any    any     anywhere             anywhere
2334K 1645M ufw-after-forward  all  --  any    any     anywhere             anywhere
2334K 1645M ufw-after-logging-forward  all  --  any    any     anywhere             anywhere
2334K 1645M ufw-reject-forward  all  --  any    any     anywhere             anywhere
2334K 1645M ufw-track-forward  all  --  any    any     anywhere             anywhere
 603K   62M ACCEPT     all  --  tun+   any     anywhere             anywhere
    0     0 ACCEPT     all  --  tun+   eth0    anywhere             anywhere             state RELATED,ESTABLISHED
 548K  757M ACCEPT     all  --  eth0   tun+    anywhere             anywhere             state RELATED,ESTABLISHED
    0     0 ACCEPT     all  --  tun0   any     anywhere             anywhere


Chain OUTPUT (policy ACCEPT 576K packets, 806M bytes)
 pkts bytes target     prot opt in     out     source               destination
1156K 1751M ufw-before-logging-output  all  --  any    any     anywhere             anywhere
1156K 1751M ufw-before-output  all  --  any    any     anywhere             anywhere
1109K 1685M ufw-after-output  all  --  any    any     anywhere             anywhere
1109K 1685M ufw-after-logging-output  all  --  any    any     anywhere             anywhere
1109K 1685M ufw-reject-output  all  --  any    any     anywhere             anywhere
1109K 1685M ufw-track-output  all  --  any    any     anywhere             anywhere
    0     0 ACCEPT     all  --  any    tun+    anywhere             anywhere

That was all my client.conf and I am using just the default certificate setup with CA, Public Key, and Private Key.

Thank you so much for your reply

---

### Post by darkod on 2015-09-06
I see you are using ufw. I also have used it few years back thinking iptables it too complex. In fact, ufw is much more complex to control and you can learn iptables more easily. ufw is based on iptables but in most cases more complex to understand. For example from your output I can't see if all is good because I'm not used to ufw syntax.

Apart from the main chains (INPUT, FORWARD and OUTPUT) you need to also check the nat table, because that is where prerouting and postrouting rules are.
```
sudo iptables -t nat -L -n -v
```

But again, I might not understand the ufw layout. In iptables it's easy, the command to allow masquerade should be like:
```
sudo iptables -t nat -A POSTROUTING -o eth0 -s 10.8.0.0/24 -j MASQUERADE
```

That should allow natting for traffic leaving on eth0. I think this is the bit you are missing.

As for the ca, cert and key options, they are correct in server.conf, but in such cases you need client certificate in client.conf too. The client should not even connect like this. Are you sure you are connecting it successfully?

On the server you create client cert and key with:
```
build-key <client-name>
```

Then you need to copy the client-name.crt and client-name.key to the client, along with the ca.crt, and in client conf add like:
```
ca ca.crt
cert client-name.crt
key client-name.key
```

That's how the client gets authenticated by the server. Check the Public Key Infrastructure setup instructions here, note the Client Certificates subsection:
[https://help.ubuntu.com/lts/serverguide/openvpn.html](https://help.ubuntu.com/lts/serverguide/openvpn.html)

Going back to iptables, we can help if you want to drop ufw and use directly iptables. Much cleaner.

---

### Post by Bob_Burges on 2015-09-06
> **darkod said:**
> I see you are using ufw. I also have used it few years back thinking iptables it too complex. In fact, ufw is much more complex to control and you can learn iptables more easily. ufw is based on iptables but in most cases more complex to understand. For example from your output I can't see if all is good because I'm not used to ufw syntax.

Apart from the main chains (INPUT, FORWARD and OUTPUT) you need to also check the nat table, because that is where prerouting and postrouting rules are.
```
sudo iptables -t nat -L -n -v
```

But again, I might not understand the ufw layout. In iptables it's easy, the command to allow masquerade should be like:
```
sudo iptables -t nat -A POSTROUTING -o eth0 -s 10.8.0.0/24 -j MASQUERADE
```

That should allow natting for traffic leaving on eth0. I think this is the bit you are missing.

As for the ca, cert and key options, they are correct in server.conf, but in such cases you need client certificate in client.conf too. The client should not even connect like this. Are you sure you are connecting it successfully?

On the server you create client cert and key with:
```
build-key <client-name>
```

Then you need to copy the client-name.crt and client-name.key to the client, along with the ca.crt, and in client conf add like:
```
ca ca.crt
cert client-name.crt
key client-name.key
```

That's how the client gets authenticated by the server. Check the Public Key Infrastructure setup instructions here, note the Client Certificates subsection:
[https://help.ubuntu.com/lts/serverguide/openvpn.html](https://help.ubuntu.com/lts/serverguide/openvpn.html)

Going back to iptables, we can help if you want to drop ufw and use directly iptables. Much cleaner.

Thank you for the reply,

So with ufw it is inactive. I agree ufw seems more complex. I went ahead and an iptables -t nat -L -n -v and got this:

```
Chain PREROUTING (policy ACCEPT 176 packets, 16508 bytes) pkts bytes target     prot opt in     out     source               destination


Chain INPUT (policy ACCEPT 17 packets, 924 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 7 packets, 498 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain POSTROUTING (policy ACCEPT 7 packets, 498 bytes)
 pkts bytes target     prot opt in     out     source               destination
 152K   10M SNAT       all  --  *      *       10.8.0.0/24          0.0.0.0/0            to:107.170.235.55
    0     0 MASQUERADE  all  --  *      eth0    10.0.0.0/8           0.0.0.0/0
    0     0 SNAT       all  --  *      *       10.8.0.0/24          0.0.0.0/0            to:107.170.235.55
    0     0 SNAT       all  --  *      *       10.8.0.0/24          0.0.0.0/0            to:107.170.235.55
    0     0 SNAT       all  --  *      *       10.8.0.0/24          0.0.0.0/0            to:107.170.235.55
    0     0 SNAT       all  --  *      *       10.8.0.0/24          0.0.0.0/0            to:107.170.235.55
    0     0 SNAT       all  --  *      venet0  10.8.0.0/24          0.0.0.0/0            to:107.170.235.55
    0     0 SNAT       all  --  *      eth0    10.8.0.0/24          0.0.0.0/0            to:107.170.235.55
    0     0 MASQUERADE  all  --  *      eth0    10.8.0.0/24          0.0.0.0/0
    0     0 MASQUERADE  all  --  *      eth0    10.8.0.0/24          0.0.0.0/0
    0     0 MASQUERADE  all  --  *      eth0    10.8.0.0/24          0.0.0.0/0
    0     0 MASQUERADE  all  --  *      eth0    10.8.0.0/24          0.0.0.0/0



```

Now I went ahead and ran ```
sudo iptables -t nat -A POSTROUTING -o eth0 -s 10.8.0.0/24 -j MASQUERADE
``` and then changed the protocol to udp in the server.conf and restarted opevpn on my server and changed the protocol to udp on my router, and it connects, (says connected, I get assigned 10.8.0.6 for local and it says 10.8.0.5 for remote) and I can SSH into my vps that is running OpenVPN and can even ping its ip address, but I cannot ping any hosts, ip addresses and there isn't any internet. So interestingly enough it still isn't working although any traffic that's destination is the VPS goes through, that's why I can SSH and ping it. Any other ip address doesn't work. 

You mentioned dropping ufw, do you mean uninstalling it with apt-get remove?

As far as connectivity and authentication I am using a client certificate, so that part is setup properly. I followed the OpenVPN tutorial in my first post that I linked out to. Still odd that if I set the protocol to TCP on both the server and client then I can get internet. There must be something wrong with the UDP routing.

Thanks

---

### Post by darkod on 2015-09-07
1. UFW.
No need to remove the package. ufw is included in ubuntu but until you do 'ufw enable' it doesn't do anything. If I remember correctly you can simply do 'sudo ufw disable', that will disable it and it stays disabled over reboots. So that is all you need. Of course that will leave your VPS without firewall so you need to have iptables file prepared before doing that. I can give you my VPS iptables file as sample later. And the command to load it on reboot.

2. Just to be clear on the /etc/sysctl.conf and forwarding. You need to do that both on the home router and the VPS. The router should have it as default, routing works. If your VPS also has it, good. If not, do it and reboot. Did you reboot after enabling it?

---

### Post by Bob_Burges on 2015-09-07
> **darkod said:**
> 1. UFW.
No need to remove the package. ufw is included in ubuntu but until you do 'ufw enable' it doesn't do anything. If I remember correctly you can simply do 'sudo ufw disable', that will disable it and it stays disabled over reboots. So that is all you need. Of course that will leave your VPS without firewall so you need to have iptables file prepared before doing that. I can give you my VPS iptables file as sample later. And the command to load it on reboot.

2. Just to be clear on the /etc/sysctl.conf and forwarding. You need to do that both on the home router and the VPS. The router should have it as default, routing works. If your VPS also has it, good. If not, do it and reboot. Did you reboot after enabling it?

Okay so I ran ```
sudo ufw disable
``` but it didn't seem to affect my VPN any. I almost wonder if there was no firewall to begin with, I think Digital Ocean said all ports are open by default. If you could provide me with your iptables file that would be awesome, maybe that will take care of my issue. Home router and VPS have it enabled in /etc/sysctl.conf and I saved my iptables using ```
[COLOR=#111111][FONT=Consolas]sudo apt-get install iptables-persistent[/FONT][/COLOR]
``` and did a reboot and nothing has changed. Still having the same issue when using the UDP protocol option, however TCP is still working fine.

Thanks

---

### Post by darkod on 2015-09-07
I was just about to comment on that. If you look at your iptables/ufw rules you posted in post #5, you can see that for all three chains you have policy ACCEPT. So yes, you basically had no firewall enabled even though ufw was enabled. With a policy of ACCEPT it lets everything through.

But lets put that aside, I will send you the iptables later. I don't have them at hand at work.

---

### Post by darkod on 2015-09-07
Sorry for the delay, here it is.

With your favourite editor create as sudo a file called for example /etc/iptables.rules. Copy this content:
```
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]


-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p udp --dport 1194 -j ACCEPT
-A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
-A FORWARD -i tun0 -s 10.8.0.0/24 -j ACCEPT
-A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
-A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j DROP
-A INPUT -i eth0 -p tcp --dport 22 -j ACCEPT


COMMIT


*nat
:POSTROUTING ACCEPT [0:0]


-A POSTROUTING -o eth0 -s 10.8.0.0/24 -j MASQUERADE


COMMIT
```

That is a basic iptables file with rules to allow SSH on port 22 from anywhere, and openvpn on udp 1194 also from anywhere. If you have static public IP for your home connection, you can further limit ssh and openvpn access only from your IP, if that fits into your needs. With firewalls the first rule is: allow only what you need to.

You can flush (delete all rules) iptables manually and load those rules from the file with:
```
sudo iptables-restore < /etc/iptables.rules
```

After you test and if you are happy how it works, you can load them manually at boot by adding a command in /etc/network/interfaces. The eth0 will have lines for static IP like:
```
iface eth0 inet static
   address ...
   netmask ...
   ...
```

Within that goup just add at the end:
```
post-up iptables-restore < /etc/iptables.rules
```

That command will load your rules on each interface activation (like when you restart your networking, or reboot).

On my VPS those rules are enough for openvpn to work, without issues. Also I want to point out that in my server.conf I use 'dev tun0' instead of only 'dev tun'. That makes sure the tunnel will always start as tun0. Because I have it like that in iptables for the FORWARD. The general used in tutorials, dev tun, will also open the tunnel as tun0 if there are no other tunnels running, otherwise it will use sequential tunX. You can control better your tunnels by using dev tunX.

Test this and let us know. If all is good on the router end, this should work. Also, when testing test both ping to well known public IP like 8.8.8.8 and also to domain like yahoo.com. If ping works to 8.8.8.8 but not to yahoo.com, then it might be problem with DNS, not with the routing/vpn setup.

---

### Post by Bob_Burges on 2015-09-07
> **darkod said:**
> Sorry for the delay, here it is.

With your favourite editor create as sudo a file called for example /etc/iptables.rules. Copy this content:
```
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]


-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p udp --dport 1194 -j ACCEPT
-A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
-A FORWARD -i tun0 -s 10.8.0.0/24 -j ACCEPT
-A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
-A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j DROP
-A INPUT -i eth0 -p tcp --dport 22 -j ACCEPT


COMMIT


*nat
:POSTROUTING ACCEPT [0:0]


-A POSTROUTING -o eth0 -s 10.8.0.0/24 -j MASQUERADE


COMMIT
```

That is a basic iptables file with rules to allow SSH on port 22 from anywhere, and openvpn on udp 1194 also from anywhere. If you have static public IP for your home connection, you can further limit ssh and openvpn access only from your IP, if that fits into your needs. With firewalls the first rule is: allow only what you need to.

You can flush (delete all rules) iptables manually and load those rules from the file with:
```
sudo iptables-restore < /etc/iptables.rules
```

After you test and if you are happy how it works, you can load them manually at boot by adding a command in /etc/network/interfaces. The eth0 will have lines for static IP like:
```
iface eth0 inet static
   address ...
   netmask ...
   ...
```

Within that goup just add at the end:
```
post-up iptables-restore < /etc/iptables.rules
```

That command will load your rules on each interface activation (like when you restart your networking, or reboot).

On my VPS those rules are enough for openvpn to work, without issues. Also I want to point out that in my server.conf I use 'dev tun0' instead of only 'dev tun'. That makes sure the tunnel will always start as tun0. Because I have it like that in iptables for the FORWARD. The general used in tutorials, dev tun, will also open the tunnel as tun0 if there are no other tunnels running, otherwise it will use sequential tunX. You can control better your tunnels by using dev tunX.

Test this and let us know. If all is good on the router end, this should work. Also, when testing test both ping to well known public IP like 8.8.8.8 and also to domain like yahoo.com. If ping works to 8.8.8.8 but not to yahoo.com, then it might be problem with DNS, not with the routing/vpn setup.

Thank you again for the help,

I followed your instructions and set the iptables, I could tell they worked because the TCP protocol option no longer works because of the iptables setting, I went ahead and added that so that both UDP and TCP are allowed for testing. I switched the protocol to UDP and connected again, authentication goes through fine, connection is successful, but still no internet. Pinging 8.8.8.8 doesn't work, and now I can't ping the VPS ip address, although thats because of the iptables I assume. SSH still works though while I'm connected in UDP, which it should since we allowed it. So I wonder if the VPS is setup fine, maybe its somehow the router or an OpenVPN setting not being pushed to the router? I have used this same router for OpenVPN using the UDP protocol and it worked fine when I went through ExpressVPN or Private Internet Access as the provider. Any ideas on what could be wrong on the router side? Or is this still maybe something with the VPS?

Thanks

---

### Post by darkod on 2015-09-07
Yes, ping is not allowed by those iptables rules. You can't test your hosts with ping unless you add a rule for that. But that would allow everyone else to do it too.

I don't know DD-WRT, but I'm still confused by the client config you mentioned in your first post. Not only that it doesn't have options for the client certificate and key, but also it has no data for the remote host (the VPS), etc. Should I assume you are entering that data somewhere in the web GUI of the router? Maybe that is messing things up?

Can you access the router by plain ssh too and have admin access? In that case, you can test the following: Remove any vpn settings in the GUI (again, assuming you have them there), then login by ssh and try to work only with the client.conf in /etc/openvpn in the router. Is that possible on DD-WRT? I believe it is basically like linux on your router...

To confirm any client is connecting correctly, can you see it in /etc/openvpn/openvpn-status.log on the VPS?

---

### Post by Bob_Burges on 2015-09-08
> **darkod said:**
> Yes, ping is not allowed by those iptables rules. You can't test your hosts with ping unless you add a rule for that. But that would allow everyone else to do it too.

I don't know DD-WRT, but I'm still confused by the client config you mentioned in your first post. Not only that it doesn't have options for the client certificate and key, but also it has no data for the remote host (the VPS), etc. Should I assume you are entering that data somewhere in the web GUI of the router? Maybe that is messing things up?

Can you access the router by plain ssh too and have admin access? In that case, you can test the following: Remove any vpn settings in the GUI (again, assuming you have them there), then login by ssh and try to work only with the client.conf in /etc/openvpn in the router. Is that possible on DD-WRT? I believe it is basically like linux on your router...

To confirm any client is connecting correctly, can you see it in /etc/openvpn/openvpn-status.log on the VPS?

I have good news!

Yes DD-WRT has a GUI for OpenVPN. I went ahead and SSH'd into my router and attempted to load the client.ovpn profile into my router. I run OpenVPN and in the SSH session it would connect and everything but it wasn't working even with TCP, no internet once again. But I noticed when I enabled OpenVPN in the GUI and ran ```
top
``` it was displaying all the processes and OpenVPN was running but it was passing some different arguments than what I was using. Here are the two args:

```
--route-up /tmp/openvpncl/route-up.sh --down-pre /tmp/openvpncl/route-down.sh
```

Now I went ahead copied those files, and duplicated the same args my router was doing through the GUI. Same thing no internet but I had to add ```
--script-security 2
``` to get it to work. So I was puzzled why when enabled in the GUI I could get internet with at least TCP but no internet when I ran it in the terminal. This puzzled me so I took a look at route-up.sh and route-down.sh

route-down.sh

```
#!/bin/shiptables -D INPUT -i tun1 -j ACCEPT
iptables -D POSTROUTING -t nat -o tun1 -j MASQUERADE

```

route-up.sh

```
#!/bin/sh
iptables -I POSTROUTING -t nat -o tun1 -j MASQUERADE
iptables -I INPUT -i tun1 -j ACCEPT
iptables -I FORWARD -i tun1 -j ACCEPT
iptables -I FORWARD -o tun1 -j ACCEPT

```

Now I noticed something.. ```
tun1
``` however when OpenVPN would run it would say ```
TUN/TAP device tun0 opened
``` on my router. Then it dawned on me, shouldn't my router be using tun0 in the route-up.sh and route-down.sh if it's opening tun0 when OpenVPN runs?

So I changed it in those files, and run my final command ```
openvpn --config client.ovpn --route-up route-up.sh --down-pre route-down.sh --script-security 2
``` with UDP set both on the router as the protocol in the config and on the VPN server and guess what.... INTERNET!!!

In the end I learned "routers lie". Just kidding, but thank you so much guys for helping me, I learned IPTables and I was even able to solve my own issue, although darkod if you hadn't suggested SSHing I wouldn't have caught this!

Thanks,

and hopefully this will help someone else in the future!

---

### Post by darkod on 2015-09-08
Good job. Glad you got it sorted out...

---

