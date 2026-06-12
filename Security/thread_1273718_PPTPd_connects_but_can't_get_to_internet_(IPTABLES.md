---
title: "PPTPd connects but can't get to internet (IPTABLES)"
date: 2009-09-23
forum: Security
---

### Post by injate on 2009-09-23
I setup pptpd on my ubuntu server with little difficulty.  I can connect through my windows client with encryption disabled (I don't care about that, I just wanted a working VPN for something simple) but I can't browse the internet through the VPN - I can only see the internal subnet.

Although it's not 100% necessary to get to the internet through this VPN it's a huge inconvenience to have to disconnect every time I want to get online.  I know I could customize my client's routes to only send the 192.168.x.x IPs to the VPN gateway and everything else to the internet connection's gateway, but that's more work then should be necessary too since it needs to be done after every connection.

I setup PPTPd in a pretty standard way, installing it with apt-get, configuring the files, since I only have 1 NIC I setup a subint eth0:0 with 192.168.x.x, and allowed 1723 tcp and Protocol 47/GRE through my firewall.  I also turned on net.ipv4.conf.all.forwarding=1 in the sysctl.conf and the /proc system variable and rebooted for good measure to make sure it saved.  PPTPd connects and VPN members can see one another but nothing outside the VPN.

My question is how can I allow the VPN users who get a 192.168.x.x IP to get back out my IPTables on my WAN IP address and the succesfully route the return traffic back to them?  I'm sick of trying page after page on Google not finding a solutions so I'm breaking down and asking for help :( I've been to close 50 sources now and tried many variations on IPTables prerouting, postrouting, DNAT, masquerading with no success.  The only small success I had was using a DNAT command which caused certain sites to redirect to my own apache "It Works!" splash page.

My current IPTables is just using [iptablesrocks.org's template]("http://www.iptablesrocks.org/guide/ruleset.php") with custom src/dest/ports allowed in/out.  I don't think there's anything in there that could be conflicting with the forwarding/masquerading commands.  I'd be willing to try a simplified iptables configuration if it can get this to work too.

---

### Post by Lars Noodén on 2009-09-24
You'll probably have to step through it step by step.  
Think of the connection as a program to debug.  

Use iptables-save iptables-restore to backup your original configuration, use it also for your test rules.  

Using and moving around the [LOG target](http://linux.die.net/man/8/iptables) will help you see where packets are getting through or where they are getting blocked.  Track the packets progress through the decision tree in either the INPUT or OUTPUT chain.  Then the other.  


--

PS.  If you are playing with VPNs you may want to evaluate the secure options instead.  These would be [SSL and IPSec](http://www.vpnc.org/vpn-standards.html), not PPTP or L2TP.

---

