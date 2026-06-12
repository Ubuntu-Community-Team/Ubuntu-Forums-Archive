---
title: "I need a VPN / Nagios box. Is Ubuntu the right choice?"
date: 2011-06-24
forum: Server Platforms
---

### Post by joker535 on 2011-06-24
I have a bunch of Windows servers and they all connect to 2 networks. One of them is all public IPs (an entire /24) which is protected by a pfsense firewall. The other network is just a 48 port gigabit switch that each machine accesses using a private (192.168) static IP on a separate nic. There is no gateway/DNS/DHCP server on this private network and we want to keep it that way. 

I want to deploy a ubuntu server that will connect to both networks. This server will not sit behind our firewall. It will have a public IP address from our /24 and be connected to the switch that feeds our firewall and a second nic with a static private IP that will be connected to our private network. This server will need to run nagios, run a few command line items that grep log files and serve the output via apache, and act as a VPN to allow an outside machine secure access to the private network. Sitting on this private network are various web based GUIs for the switches, UPS boxes, etc that we do not want exposed directly to the Internet. Both of these networks are mission critical so I can't change any existing settings and I can't add anything to the existing firewall. There would only be a couple of VPN connections at a time.

**Do you think that ubuntu 10.04 LTS server (32 bit) would be able to handle this?** I am looking at running it on a supermicro Atom D525 box with 3G of ram and a small SSD for storage.

This machine would be dedicated to the tasks listed above and nothing else. I already have nagios running on one ubuntu server and the command line/grep stuff running on 2 others. I need to retire these dinosaurs and combine them all into one new box that can also do the VPN. The load on all of the other boxes is minimal. I am sure the hardware listed can do it. I just don't know if ubuntu server is the right choice. I am also considering FreeBSD but I am more familiar with Ubuntu.

Opinions?

Thanks

Bob

---

### Post by Beacon11 on 2011-06-24
If I were you, I'd actually use Debian for this purpose. You would be able to utilize your Ubuntu knowledge, but have the advantages of a slow-moving release cycle and solid, well-tested software. I use Ubuntu for my desktop so I can have all the new flashy things, but I always use Debian for my servers. You will get a lot of different opinions here, this is just one.

---

### Post by SeijiSensei on 2011-06-25
What kind of VPN?  PPTP?  OpenVPN?  Both of those are well-supported by all Linux distributions.  IPSec is a pain in the butt to configure; I've given up on it in favor of OpenVPN.  If you're using a proprietary VPN, odds are good the server won't run on Linux.

---

### Post by joker535 on 2011-07-05
> **SeijiSensei said:**
> What kind of VPN?  PPTP?  OpenVPN?  Both of those are well-supported by all Linux distributions.  IPSec is a pain in the butt to configure; I've given up on it in favor of OpenVPN.  If you're using a proprietary VPN, odds are good the server won't run on Linux.

It would be OpenVPN. I want to keep it as simple as possible. I just want to connect a remote workstation to the VPN and access the web based GUIs without any security issues.

Anyone here running Ubuntu on a supermicro atom D525 server?

---

### Post by spynappels on 2011-07-07
> **joker535 said:**
> It would be OpenVPN. I want to keep it as simple as possible. I just want to connect a remote workstation to the VPN and access the web based GUIs without any security issues.


That will work fine then, but you will need to have the Firewall allow port 1194 (or whatever port you set) allowed and forwarded to your VPN machine. Not sure if that will cause a problem as you said you cannot add anything to the existing firewall?

I use an identical setup to get into one of our remote networks securely.

I'm sorry, but I have no experience with the Atom board.

---

### Post by joker535 on 2011-07-07
I am going to set this machine outside the existing firewall so the ports won't be a problem. I don't want vpn traffic passing through the firewall. Its got enough to do with traffic its handling now.

Since my private network has no gateway, will there be any problem with the vpn? Also can the OpenVPN box be a DHCP server to just the vpn clients? All the machines already on the network have static addresses so I don't have/need a DHCP server for them.

---

### Post by spynappels on 2011-07-07
Now I'm a little confused.

Will the VPN/Nagios box have 2 interfaces? One with a public IP and one with a (Private) LAN IP? If it does not have a gateway, you may have trouble accessing it as well as setting a static route for the traffic to come back out to your VPN Client.

Can you draw a diagram of how you want this network to look?

---

### Post by joker535 on 2011-07-07
> **spynappels said:**
> Now I'm a little confused.

Will the VPN/Nagios box have 2 interfaces? One with a public IP and one with a (Private) LAN IP? If it does not have a gateway, you may have trouble accessing it as well as setting a static route for the traffic to come back out to your VPN Client.

Can you draw a diagram of how you want this network to look?

Yep 2 interfaces. One interface connected to the network wth public ips and using the gateway from our provider. The other interface connected to the other network with private ips and no gateway.

---

### Post by Grenage on 2011-07-07
There's no reason it shouldn't work fine, I built a test Nagios system on an Ubuntu base; I used Debian in the production build (it's more stable).

VPN shouldn't be an issue, we actually use a PfSense box for our VPNs.  Having it on an Ubuntu server should be fine; I'd use Debian, but you shouldn't have any problems.  Just be careful of the updates.

---

### Post by spynappels on 2011-07-07
Ok, then I'd use OpenVPN in routed mode and listening to the public interface. Use IPTables to firewall that public interface and only allow traffic in on port 1194 (or whatever you set) to allow you to connect.

You will need to create a static route on each machine that you want to access using the VPN to push traffic for the VPN IP (10.8.0.x for example) back to the VPN machine and use the routing capabilities of the VPN server to push the traffic back out to your VPN client. So if you want to use a web GUI on application server at 192.168.1.200 and your VPN is at 192.168.1.100 on the private LAN and has given the client 10.8.0.5, you need a route on the application server to send traffic to the 10.8.0.0 network through 192.168.1.100

And enable IPv4 routing in the OpenVPN server kernel.

---

