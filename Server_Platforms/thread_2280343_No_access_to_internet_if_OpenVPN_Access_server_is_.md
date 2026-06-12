---
title: "No access to internet if OpenVPN Access server is running"
date: 2015-05-30
forum: Server Platforms
---

### Post by Robertjm on 2015-05-30
Hi all,

Tonight I installed OpenVPN Access Server, and ran the configuration program. When the server is actively running I have absolutely no internet connectivity, nor can I resolve other machines on the local network, except for my HP wireless printer. The moment I stop the server, I can access the internet again.

Mind you, I'm NOT talking about accessing the Internet through a client. But, on the server machine itself.

I have "Should client Internet traffic be routed through the VPN?" set to No, if that matters, and under DNS Settings I've tried both "Do not alter clients' DNS server settings" as well as telling it to use Google's DNS servers at 8.8.8.8 and 8.8.4.4

Anyone else experience this? If so, how'd you fix it?

Thanks!

Robert

---

### Post by darkod on 2015-05-30
I have used pure OpenVPN but never the OpenVPN AS, so I don't know if it has any specific details. The basics should be the same. It is weird that activating the AS messes up your machine networking. Even if something is wrong and clients can't connect, it should not mess up the server networking.

The configuration items you mentioned are for the client side also, so they shouldn't matter for the server.

Things to check or have in mind...

1. The subnet you selected for the vpn is different from your local LAN subnet right? The vpn subnets always have to be different from local subnets.

2. After you start the AS try to check the IPs assigned to the main interface (usually eth0) and to the vpn tunnel (usually tun0). You can do that with ifconfig. Also try a ping to your router local IP, for example if it's 192.168.1.1 (maybe you already tried this). And also print the routing table which can give you clues.
```
ifconfig
ping 192.168.1.1
route
```

That will show you if you can reach the router at all and aybe give you some clue with the IPs.

3. Next you can try traceroute to a public IP like 8.8.8.8 (you might need to install the traceroute package first). But if the ping to the router doesn't work, this test is pointless because you already know you are not reaching your router at all. Otherwise it can tell you possibly where the traffic stops.
```
traceroute 8.8.8.8
```

That would be about it to start with.

Is there a specific reason you didn't use pure openvpn? The issue might be related to AS but I can't be sure of course...

---

