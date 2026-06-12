---
title: "Firewall rules based on logged in user possible?"
date: 2017-12-12
forum: Security
---

### Post by rhen84 on 2017-12-12
Dear all,

I would like to ask if is it possible to create firewall rules based on the logged in user.

The task would be to make a "jump server" for a protected network.
This "server" would have access to certain resources, but every user who login to the computer should have different access rights to the protected network.

For example one user can connect to a certain IP address on a certain port and another not. They can be logged in in the same time.

This can be achieved somehow?

Thank you,
Tamas

---

### Post by TheFu on 2017-12-12
Welcome to the forums.

When I need to accomplish something like this, I use different openvpn groups to control subnet access.

I suppose you _could_ try to have iptables setup different rules by the userid, but this isn't a well-traveled, well-tested, path.  -m owner and the user-id options are in iptables.  [https://www.cyberciti.biz/tips/block-outgoing-network-access-for-a-single-user-from-my-server-using-iptables.html](https://www.cyberciti.biz/tips/block-outgoing-network-access-for-a-single-user-from-my-server-using-iptables.html)  I don't know of any GUI which will use those options.  It would be CLI only.

Another option is to run the processes inside a container that has limited access to the network.  Linux containers are getting better and better at this. Today, I wouldn't hesitate to do it with non-GUI programs.

So, I guess the answer to the title question is yes, but not without difficulty.


Jump servers are often a security nightmare, IME.  I would avoid this deployment for more than 5-10 users.  Of course, there are exceptions and the technical skills of the people using the system would greatly impact how and whether I set this up.

openvpn is how I'd solve it unless everyone were using ssh for everything.

---

### Post by rhen84 on 2017-12-12
Hello TheFu,

Thank you for your answer, this is exactly what I've searched for.

The protected network is separated from office LAN with a physical firewall, but the issue is that I can setup rules based on computers only (mac address, ip address), not based on users in the firewall.
The machines have different interfaces (lan, wlan), they are trying to connect from different networks, 3 VLAN in the office and one for VPN (Cisco AnyConnect). On VPN it is hard to manage the access especially that we don't have access to it (there is a separate group to handle it).
So it is hard to maintain the rules, the fixed IP addresses etc.

Primary use of the server would be that the users could connect to some of the PCs in the protected network via RDP and/or VNC.

So I have to evaluate the possible solutions.
Thank you for the OpenVPN suggestion, I will look at it.

BR,
Tamas

---

### Post by The Cog on 2017-12-12
I did something like this once. I configured an OpenVPN server (on Linux) with per-user confiugration that always assigned a fixed IP address to each user based on their common name. 
As an added complication we used LDAP authentication and used their LDAP username as their "common name". The "common name" in their certificate was their laptop name.
With that sorted, it was just a case of configuring iptables access lists to allow each user only the protocols and hosts they were approved for. 

The admin overhead maintaining rules and certificates was bearable for just a couple of dozen users. The nice thing about using LDAP was that it was tied to their corporate account and it didn't help if they borrowed each other's laptop - their SSL certificate only got them as far as checking their username/password. And we could be a little slower with the certificate revocations.

Of course, there's nothing stopping them from using a machine they have access to as a stepping stone to the rest of the network.

---

### Post by TheFu on 2017-12-12
RDP or VNC are not secure without a full VPN, IMHO.  That would require 2FA to even be considered possible where I've worked.  wifi-lan devices were never trusted. They connected as if each were on the internet and forced to use the 2FA VPN to gain access back into the corporate network based on their individual access rights.

The Cog's answer about using static IPs for each individual is closest to what I've done.  We had different access groups and forced them into specific subnets provided by openvpn, then those were firewalled as needed.  Usually, we used /29 subnets for the small groups of users. The was before everyone had smartphones AND laptops and expected both to connect to the corporate LAN over VPN.

Layering openvpn inside a Cisco VPN would be slow.  I'd challenge the corporate VPN group to help solve the problem.

Lastly, NX protocol tools (x2go) feel 2-3x faster than VNC or RDP. Just sayin'. Of course, x2go has some limitations which might not work for your needs.  I always connect to a Linux system from the outside world, then can use LAN-based RDP to get into Windows systems.  The internet part is secured by the built-in ssh tunnel that NX provides (mandates).

---

### Post by rhen84 on 2017-12-13
Hello guys,

Thank you for your answers, but I'm a little uncertain how you use OpenVPN.
You are/would use it on (office) LAN to able to assign IP addresses to the computer based on the user who are using it and than using a regular firewall to filter traffic between the office LAN and the protected network?
From the internet it is clear that a VPN connection is needed and as TheFu said, proper Cisco VPN groups with fixed IP addresses would be the best solution to this.
I've tried this before, but I was not able to achieve the desired configuration with the team handles corporate VPN connection.

x2go looks good. I will have a look at it. Thanks.

BR,
Tamas

---

### Post by HermanAB on 2017-12-13
It is possible to set up rules based on the group, but not based on the user - a slight difference.

---

