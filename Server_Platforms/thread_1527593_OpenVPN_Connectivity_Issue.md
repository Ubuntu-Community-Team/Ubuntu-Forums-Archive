---
title: "OpenVPN Connectivity Issue"
date: 2010-07-09
forum: Server Platforms
---

### Post by mlvest on 2010-07-09
We are using v2.1.1 of the OpenVPN server on an Ubuntu machine (desktop lucid) and we are testing it with the v1.0.3 Windows client.

The clients connect properly and are assigned appropriate IP addresses for the local network, but when they attempt to access some of the sites hosted on the server locally (via Apache, also on the server), they use their external IP instead of the local one assigned to them through the VPN. Because of this, they are blocked by our firewall.

As an example, one user with the external IP 75.75.75.75 and the local IP (given by the VPN) 192.168.1.105 would be seen as 75.75.75.75 by the server. They are being recognized by the wrong IP.

I looked into pushing redirect-gateway, but I couldn't get it working and it seemed like a roundabout solution to a problem that is probably a stupid mistake.

If anyone has any ideas or input, I'd be glad to hear it.

---

### Post by spynappels on 2010-07-10
Are you running the VPN in bridged mode?
Running it in routed mode may work better, but you will probably have to change the subnet of your LAN to something a little less common than 192.168.1.x such as 192.168.50.x
Running in routed mode means that the server has another IP address for the tun0 interface (10.8.0.1 or similar), which can be firewalled independently of the eth0 interface. Also, any http or other requests come from the client's VPN IP rather than any other.

---

### Post by mlvest on 2010-07-12
Sorry for the delayed response, I am using bridged mode and I don't want to switch. Is there a way to make it work similarly? I looked into packet forwarding, but we're using UFW and it seems a bit more complex to enable for UFW than it does for standard iptables.

---

### Post by spynappels on 2010-07-12
Are you sure it is more complex? I thought that UFW was just front-end for iptables and will not interfere with separately added rules?

---

### Post by mlvest on 2010-07-12
I played around with iptables and iptables rules via UFW (in before.rules) and was only able to allow all traffic through as opposed to just people connecting via the VPN (or subnet), which is certainly not what I want. It still thinks of the clients as their external address instead of the assigned subnet one, which is strange, because wireshark pick them up as using their subnet address as the source when I capture on the bridge interface.

---

### Post by spynappels on 2010-07-12
Ok, I'm a little confused now, but that is probably because I am tired.

Can you please elaborate a little on what you are trying to do? Maybe a diagram? 

I think you are trying to have remote worker connect to a server through a VPN, but the server is firewalled from the Net, correct?

If you are using OpenVPN, it creates a second network interface, either tap0 or tun0. This interface can be firewalled independently of the eth0, eth1,... etc interfaces using iptables, but I am not sure if it can be done through UFW, I suspect it cannot.

I use the following rule to allow VPN traffic into my servers:

```
-A INPUT -i tun0 -j ACCEPT 
-A INPUT -i lo -j ACCEPT 
-A INPUT -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT 
-A INPUT -i eth0 -p tcp -m tcp --dport 443 -j ACCEPT 
-A INPUT -i eth0 -m state --state ESTABLISHED -j ACCEPT 
-A INPUT -i eth0 -m state --state RELATED -j ACCEPT
-A INPUT -i eth0 -j DROP 
```

and it does what I've described, i.e. SSH from eth0 is not permitted, but it is permitted through the tun0 (VPN) interface.

You may need to look at binding services to a specific interface or IP in the .conf file for the specific service.

---

### Post by mlvest on 2010-07-12
It is really a simple setup, I'm sure I just have something configured wrong. I mocked up a basic diagram. It is a bit big, so I'm not embedding it. You can find it: [here.]("http://img138.imageshack.us/img138/4592/vpnbridgesetup.jpg")

UFW does support iptables-style rules, but I tried using them (very similar to the rules you listed) with no success. I could do something tedious like add an allow for the mac address of each computer that will have a client on it, but that really isn't the way to go. The firewall on the sever box denies all by default and only allows IP addresses on the local subnet to access the various services and local sites, with the exception of port 1194 UDP which allows all, since it is secured by cert authentication.

Should it really recognize the connections from the clients as their external IP and not their subnet IP given by the VPN when using a bridge? Why would anyone want that by default?

---

### Post by spynappels on 2010-07-12
If the requests are coming in on the VPN interface, that server should recognise them as being from the LAN IP.

Have you tried disabling the firewall completely to see if it works then?

Then try creating your rules and applying them without using UFW, so create an iptables.rules file and use iptables-apply to apply these rules, you can do without UFW then.

---

### Post by mlvest on 2010-07-12
When I disable UFW, it lets the connection through. I tested giving UFW a rule to allow the external client IP and it works. Some of the apache virtual hosts also use auth that checks the make sure the IP is on the local subnet, which can't be connected to when the firewall is enabled and is forbidden when it isn't (it got to the page but failed auth). Adding a specific allow for the IP in the auth lets it pass through.

I glanced at some basic exchanges with wireshark on br0. It looks like it is using the external address to communicate with openvpn and the local one for everything else, including pings, which fail for the client only when the firewall is up.

I would like to avoid switching from UFW to iptables if possible.

---

### Post by mlvest on 2010-07-14
Going to change up my question a bit. Is there a way to have all traffic that comes from a client's computer be NATed to a local address with iptables? I looked into masquerading and forwarding again with little luck. I also had it forwarding all connections through the VPN and it functioned correctly (using the server's gateway when accessing the internet, for example), but it still recognized them clients by their external addresses. Maybe some combination of masquerading/snat on the tap interfaces and forwarding all connections through the VPN?

---

### Post by YesWeCan on 2010-07-14
[QUOTE=mlvest]Going to change up my question a bit. Is there a way to have all traffic that comes from a client's computer be NATed to a local address with iptables? I looked into masquerading and forwarding again with little luck. I also had it forwarding all connections through the VPN and it functioned correctly (using the server's gateway when accessing the internet, for example), but it still recognized them clients by their external addresses. Maybe some combination of masquerading/snat on the tap interfaces and forwarding all connections through the VPN?[/QUOTE]
I think I have a setup that does what you are trying to do. You shouldn't need to do masquerading or any stuff like that. It may help to post your client and server config files here.

It is crucial that the client (laptop) subnet is different from the server subnet.
The client.conf has to have the line "redirect-gateway def1" in it.
The openVPN client app on Windows has to be run with admin privileges or it won't be able to change the routing table.

Re your diagram. The red vpn connection is not the bridge. It is a tap tunnel. The bridge is at the server where the server LAN interface should be bridged with the tap tunnel. The tap tunnel obviously goes through both routers and the WAN (internet).

When you talk about the laptop appearing to have address 75.75.75.75 I presume this is the WAN address of the laptop's local router. If so, this suggests that the laptop's gateway is not being re-routed properly via the tap tunnel. If you connect the laptop to the tap and then open a browser and check your IP what is the result?

Note with the tap tunnel and bridge that the laptop sees both the server's LAN and its local LAN at the same time. So if there are any IP clashes this will cause malfunction.

---

