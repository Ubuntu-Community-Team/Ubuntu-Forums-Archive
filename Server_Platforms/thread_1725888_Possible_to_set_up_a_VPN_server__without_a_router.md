---
title: "Possible to set up a VPN server  without a router?"
date: 2011-04-10
forum: Server Platforms
---

### Post by molgan on 2011-04-10
Is it possible to set up a (Open)VPN server without havning the server behind a router (NAT)?

My ISP allows me to have multiple IP addresses (assigned by DHCP).

---

### Post by SeijiSensei on 2011-04-10
> **molgan said:**
> Is it possible to set up a (Open)VPN server without havning the server behind a router (NAT)?

Sure.  In fact it's a lot easier that way.  My Linux router supports half-a-dozen static-key tunnels with various clients' sites.  

You obviously will need to configure a firewall on the box.  Just make sure that you have rules to permit access from the remote OpenVPN clients to whatever ports you're using.

If your IPs are assigned by DHCP, do they nevertheless remain relatively static?  It's tough to contact a server if you don't know where it is.

Also you can run all the tunnels through one public IP address.  Just use a different port for each tunnel.

---

### Post by molgan on 2011-04-10
Nice, thanks for the response. Do you have a link to a tutorial how to set up such a VPN? All guides I found are for those with a router set up, or they don't state what kind of setup they have.

Do I just comment out the setting
```
server-brigde ip netmask fromip toip
```in my/etc/openvpn/server.conf

Or what do I put in *fromip *and *toip *when I'm not aware of what addresses it's gonna be?

---

### Post by spynappels on 2011-04-11
Hi,

I'd suggest reading through this link, and looking for a Routed VPN setup.
[http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html)
A Routed VPN does not mean it is accessed through a router, it means it acts as a router between the VPN subnet and any other subnets such as a LAN or the Internet in general.

If the Public IP of the VPN server is going to change (DHCP), you could also look at a DynDNS domain name to point to your OpenVPN server.

---

### Post by HermanAB on 2011-04-11
Howdy,

Depending on what exactly you need it for, you could also look at using the VPN feature of SSH.  It is good for creating ad hoc secure connections where you bring the VPN up when you need it and take it down immediately after using it.  

Alternatively, just use straight ssh and scp by using the Nautilus file browser 'Connect to server' feature.  Setting up a ssh server on one machine and then connecting to it using Nautilus is easy as pie.  So easy, in fact that I never use VPNs anymore.

---

### Post by SeijiSensei on 2011-04-11
I recommend starting with one server and one client and following [this guide](http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html).  All the tunnels I maintain use shared keys as described here.  Each tunnel has a separate .conf file in /etc/openvpn with a unique port defined.

---

### Post by molgan on 2011-04-13
Thanks for all responses. I will be using it for my android phone (and later on for one laptop). Already have a ddns, so that's not gonna be a problem. Plus the IP address it's not changing unless I reboot the server.

1. Will I be using more than one IP address from my ISP with the static key setup?

2. One of the static key disadvantages: "Lack of perfect forward secrecy" - what does it really mean?

3. Do I have any alternatives to static key setup, when I just have one network interface, directly connected to the internet?

---

