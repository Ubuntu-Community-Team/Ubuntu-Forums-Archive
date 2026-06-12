---
title: "PPTP Routing (PopTop)"
date: 2006-09-25
forum: Server Platforms
---

### Post by Sprinker on 2006-09-25
Hi Guys,

I have been looking for this everywhere, but have not had any luck, so now I am posting here.  I have PPTPD installed in my Ubuntu Linux Server, and I can connect to it and authenticate, and that works a treat.  However, there is a issue when I try to get to the Internet through the VPN Server.  There is a router running on the network, 192.168.1.1, and it has PPTP passthrough enabled.  However, when I try to connect to the Internet, thats where the problems start.  I can't even ping the VPN Server.  I DO have Shorewall Firewall running on the VPN server, with VPN traffic through cleared.  Do  I need to add a network interface to Shorewall or anything.  So it looks like IP forwarding is not enabled, but I have enabled it.  I will post the pptpd-options and every configuration file here when I have physical  access to the server.

Cheers,

Nat Vink

---

### Post by chrisfay on 2006-09-25
When you get access to the server, post output for these commands while pptpd is running and preferably while the interface is up and connected to a client:

```
route
```

```
ifconfig
```


Also, at the bottom of your pptpd.conf file you should see a section like this:

```
#
# (Recommended)
#localip 192.168.0.1
#remoteip 192.168.0.234-238,192.168.0.245
# or
#localip 192.168.0.234-238,192.168.0.245
#remoteip 192.168.1.234-238,192.168.1.245
```

Did you allocate a server/client subnet that uses your actual LAN subnet? I was having the same problem until I realized I had used the same subnet for both networks which was causing route problems. 

If you did the same thing, change your VPN subnet to something else and retest your client's internet connection.

---

### Post by censu67 on 2006-12-09
Hi, new to this site and relatively new to linux. 

I've managed to setup poptop on a box running FC5. Initially I had some issues with the Dlink appliance firewall, but got that working . Now I can connect to the VPN server with no errors. But once connected I cannot see anything. I cannot ping anything on the local(remote) lan or the internet. However, I have routing enabled on the box as I can see everything when I ssh in.

The remote network is 192.168.0.x, the vpn ip range is 10.10.0.x

I looked thru the doc on here for setting up poptop in slackware and from what I can tell I've followed all the steps.

I tried using TCPDUMP, but to be honest didn't know how to read the results.

I know this has to be an easy fix, but I need help with it all the same.

Any suggestions?

Thanks

---

