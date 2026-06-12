---
title: "Help needed with my squid server"
date: 2007-12-13
forum: Server Platforms
---

### Post by wolfe on 2007-12-13
So I have a new squid server with dansguardian.  Everything is running very well on it, but with one remaining issue.  my client computers MUST have the IP address of the server in order for dansguardian to properly block addresses.  I would like this to work even if the proxy information is not entered into the browser config on the client machines.

A little bit about the server and the network it is on.  It is shaped like the following:

internet > router > proxyserver w/ Dan's > switch > client computer

The proxy server has 2 nic's that are configured as a bridge, This was in theory to allow it to sit in between the LAN and the outside world with 0 configuration changes required at the client computers.  The nic's have no IP addresses, but the virtual bridge is assigned an IP so that remote configuration is possible.  It is this IP address that must be entered as the proxy address in order for the proxy / dan's to work.

Thanks in advance!  Any suggestions will be greatly appreciated.

---

### Post by foolsh on 2007-12-13
not sure what the command is, its been awhile but google something about iptables redirecting to port 80
I dont think you should use the network bridge between WAN and LAN it allows a computer to completly bipass the danG box altogether.
look at firestarter for an easy to use internet sharing firewall setup.
not sure but I only use bridging on the LAN side to make routers out of old 486s

what you have with a bridge is

internet"WAN" 
      |
      |------------dans guardina
      |
  switch-------computer
      |
computer



what you need

Internet"WAN"
   |
dans guardin
   |
switch--------comupter
   |
computer


Oh and google up "transparent squid proxy" lots of usefull stuff
and please post back any falures or achivements it would help th next chap out in you situation

---

### Post by wolfe on 2007-12-13
We're pretty set on the machine being configured the way it is in regards to the bridge.  If this works out well, we'd like to start installing this installation on a small form factor box and start offering it to our clients as a security appliance.  It needs to be able to plug into any network and just start blocking bad sites.

To clarify, the machine with the bridge, squid, and dan'sg are all on the same box.  I'm learning as I go with this project, so I wouldn't be surprised to find a few errors in the configuration.

Attached is the script I made to configure the bridge and ports at boot time.  I named it /etc/rc.bridge.  It does it job with the exception that client machines must be manually configured with the bridge's IP address.  But it is my understanding that it should work without assigning an IP to the bridge.

```
#!/bin/sh

###Date: 12-Oct-2007

###tekbdrlimbu@hotmail.com####

brctl addbr br0
brctl addif br0 eth1
brctl addif br0 eth2
ifconfig eth1 0.0.0.0 promisc up
ifconfig eth2 0.0.0.0 promisc up
ifconfig br0 192.168.0.33 netmask 255.255.255.0 up
route add default gw 192.168.0.1 dev br0

#/sbin/ebtables -t broute -A BROUTING -p 0x800 --ip-protocol 6 \
/sbin/ebtables -t broute -A BROUTING -p 0x800  --ip-protocol 6 \
--ip-destination-port 80 -j redirect --redirect-target ACCEPT
/sbin/iptables -t nat -A PREROUTING -i br0 -p tcp --dport 80 -j REDIRECT --to-port 3128
/sbin/iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-ports 3128
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-ports 3128
/sbin/iptables -t nat -A PREROUTING -i br0 -p tcp --dport 80 -j REDIRECT --to-ports 3128

######### End of rc.bridge script #####
```

---

### Post by foolsh on 2007-12-13
yes but with a bridge the two or more interfaces act as a hub of sorts,
there is no switcting routing or any of that involved

what would really work if one nic was toward the internet with its own ip and the other towrd the LAN with its own ip
any computer trying to get to the internet would have to pass throught the dansG box to get out side then you could redirect anything going to port 80 to the squid port

with your bridge setup if the packet is not told to go to the dansG box it is simply passed on to the internet.

I wish  I could help more but I know It just wont work the way you have it configured with a bridge.

---

