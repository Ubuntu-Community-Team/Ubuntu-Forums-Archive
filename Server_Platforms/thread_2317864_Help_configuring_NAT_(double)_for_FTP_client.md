---
title: "Help configuring NAT (double) for FTP client"
date: 2016-03-20
forum: Server Platforms
---

### Post by AJSA on 2016-03-20
Hello

I have been studying iptables and NAT but I have not found a solution.

I have to access an internet FTP server from an ftp client inside an OpenStack tenant
That FTP server allows only connections from a restricted number of public IPs

[B][FONT=courier new]BEGIN Architecture diagram

                                        ........................................+--[Tenant Default Gateway]--[Company ]--(PublicIP-gw)-->
........................................|............................[Common  ]
[Firewalling Server](IntranetIP-fw)-----+=====(FloatingIP-fw)========[Firewall]--(PublicIP-fw)<---->(PublicIP-ftp) [Remote FTP Server] 
........................................|
[Data Processing Server](IntranetIP-dp)-+
........................................|
[other servers...] (Other IntranetIPs)--+

END architecture diagram[/FONT][/B]

The remote FTP server only allows connections from (PublicIP-fw) That IP is translated from (Floating IP-fw) by the [Company Common Firewall]
I have tested the connection from [Firewalling Server] and is ok.
I need to move some FTP clients from [Firewalling Server] to [Data Processing Server]

My idea was to:

1) add a host route in [Data processing Server] to **PublicIP-ftp** using **IntranetIP-fw**  as a qateway

sudo route add -host **PublicIP-ftp** gw **IntranetIP-fw**

2) Configure [Firewalling Server] as NAT for [Data Processing Server]

sudo iptables -t nat -A POSTROUTING -s **IntranetIP-dp**/32 -j MASQUERADE
sudo iptables -A FORWARD -i eth0 -j ACCEPT

But is not working. When I try to connect from [Data Processing Server] to [Remote FTP Server] no connection.

Context:
- Pasive ftp

Do I need to configure something else in [Firewalllling Server]?

Thanks,
AJ.

---

### Post by darkod on 2016-03-20
Wouldn't a VPN be more suitable to connect to such a protected environment? Is that a possibility?

As far as I know, basic iptables rules can't help you "mask" the IP so that it appears as one of the allowed source IPs.

Is the Firewalling Server allowed to be GW to other computers in the private LAN, and is it in the same private LAN? If it is, you might be able to use it as a route like you are trying, but you have to adjust the iptables on it also...

For any machine to forward/route traffic (in this case the Firewalling Server, you need to:
1. Allow the tcp forwarding. If the machine is ubuntu server, in /etc/sysctl.conf it needs to have enabled the option net.ipv4.ip_forward=1. That allows tcp packets to be forwarded.
2. In iptables, you need the FORWARD chain to have ACCEPT policy, or if it has a DROP policy you need to configure the needed iptables rules to allow the forwarded traffic between the interfaces.
3. In iptables nat table, you need to use MASQUERADE rule so that the traffic knows to find its way back to the client.

Also, the Firewalling Server needs to have its default GW set to the FloatingIP FW so that all traffic goes out that way. Is that so?

---

### Post by AJSA on 2016-04-15
Finally I have figure out the solution.
It was not about the firewall/router
It was about antispoofing rules inside OpenStack

The reference is:

[https://albertomolina.wordpress.com/2015/11/22/playing-around-with-openstack-using-an-instance-as-router/](https://albertomolina.wordpress.com/2015/11/22/playing-around-with-openstack-using-an-instance-as-router/)

---

