---
title: "routing eth0 data to eth1 with netplan"
date: 2018-03-05
forum: Server Platforms
---

### Post by carnagelan on 2018-03-05
Hi All,

I am busy learning Ubuntu administrating and i have managed to setup dhcp server, dns, server, samba servers.

I have now got an Ubuntu 17.10 server installed and everything is setup correctly. 
This server has got 2 NIC cards.

eth0 --> local area network, setup with a static IP.
eth1 --> connected to the router, this NIC is using DHCP which i get from the router.

From the server i can connect to the NET. from the client pcs i can ping the Eth0 device fine.

I need to create routes so all the clients can access the internet. 

eth0 has ip of 192.168.0.254/24
eth1 has ip of 127.20.10.12/28 via DHCP Gatwway is 127.20.10.1

They are are 2 different subnets to i take it i have to use vlans? 

I have googled and i am not coming right.

I am not sure how to add routes for this to work in my netplan file

---

### Post by darkod on 2018-03-05
You don't need any routes. You need to enable ipv4 forwarding on your server, and any client that uses 192.168.0.254 as gateway IP will automatically get the traffic routed through your server.

After the server has forwarding enabled it is enough clients to send traffic to its eth0 interface and all traffic arriving there which is destined for the internet will go out through eth1 automatically.

---

### Post by The Cog on 2018-03-05
127.*.*.* is the IPV4 loopback network. You should not be able to connect to anywhere using that address. Did you mean 172?

The clients on 192.168.0 need to have a route (via 192.168.0.254) to whatever address they want to get to. A default route via 192.168.0.254 is probably the easiest thing to arrange. These routes need adding to the clients.

As they are separate NICs, separate networks, no need to worry about VLANs.

As darkod says, you need to enable IP forwarding in the server [https://linuxconfig.org/how-to-turn-on-off-ip-forwarding-in-linux](https://linuxconfig.org/how-to-turn-on-off-ip-forwarding-in-linux)

---

### Post by carnagelan on 2018-03-05
Thank you for the replies,

I am still struggling and not coming right.

My IP forwarder is set to 1 so that is enabled.

This is the setup i have in  /etc/netplan*.yaml file
Please note i have setup a DHCP server which gives the clients a default gateway of 192.168.0.254 and a primary and secondary DNS of 8.8.8.8, 8.8.4.4
> 
ethernets:
    eth0
       addresses: [192.168.0.254/24]
    eth1
       dhcp: true 


the eth1 address is 172.20.10.12/28 and the gateway is 172.20.10.1/28

The client ip details are
> 
IP Address 192.168.0.20/24
gateway 192.168.0.254
dns 8.8.8.8


I need to route internet traffic from the local lan(eth0) through to eth1 which has the internet connection

---

### Post by The Cog on 2018-03-06
Let's do some basic debugging. Please run these commands on both the server and on one of the clients, and post the output:
```
ip addr
ip route
host google.com 8.8.8.8
```
127.*.*.* is the IPV4 loopback network. You should not be able to connect to anywhere using that address. Did you mean 172?

---

### Post by darkod on 2018-03-06
You are probably missing one thing for forwarding too. Just enabling it in /etc/sysctl.conf is not enough. When traffic goes from eth0 to eth1 it doesn't know to come back without NAT.

On the server, try this iptables temporary rule to see if it helps:
```
sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
```

Then check if the clients have internet access. If you are using iptables firewall on the server you will need more rules, not just that one.

If it works, you have to make that rule load on each boot. The easiest way for a single rule is putting it in /etc/rc.local for example. Note that it runs as root so you don't need the sudo in front when putting things in /etc/rc.local.

If it still doesn't work, show us current iptables rules:
```
sudo iptables -L -n -v
sudo iptables -t nat -L -n -v
```

---

### Post by carnagelan on 2018-03-06
Thank you Darkhog, the iptables rule has worked:) Thank you both for helping me, I am learning Linux administrating and a section at a time. I defiantly need to read up on iptables.

---

### Post by pelgrim on 2019-01-04
Hi,
I hope to attract someones attention here, I have that same problem that routing doesn't work from my server.
The topic I made for it seems to get no response, I hope to get it here.

[https://ubuntuforums.org/showthread.php?t=2408862](https://ubuntuforums.org/showthread.php?t=2408862)

---

### Post by slickymaster on 2019-01-04
Thread closed.

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

