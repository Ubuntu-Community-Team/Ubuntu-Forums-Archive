---
title: "openvpn in bridged mode server, single eth0"
date: 2015-07-24
forum: Server Platforms
---

### Post by bctechnzl on 2015-07-24
I've had a lot of success with openvpn, but recently am struggling with a server/client setup where my server is just a machine on the network as opposed to being the main router, how I've normally used openvpn.

I've decided also to use bridged mode  so that the client laptop appears on the network with an ip from the local lan, rather than the vpn supplied ip range, as this seems to be the suggested practise espcecially with a windows client needing to access shares.
I've tested the ssl key pairs and achieved login first (and with a tun adapter) then moved on to setting up bridging, and changing to tap, as required in the openvpn  howtos.
because I am ssh'd into the server from another machine, and the server has only one physical eth0 port, I end up having to get the device rebooted each time I test bridging.
The documentation   [https://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html]("https://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html") says "start the bridging, start the openvpn stop the bridging stop the openvpn" as an order, but if I'm ssh'd in, the eth0 port locks up when I run the bridge script and I can't control the box.  I guess they assume you are local.
The type of router (shg1500) on the net cannot have routes added.
Port 1194 is NAT'ed through to the openvpn server box.
Port 22 also, which is how I'm connected.
I'm needing to know, is bridging mode even possible from a single eth port server? Is the port (once its bridged) not free? I was assuming the br0 device created was the bridged adapter and eth0 was still in operation
Should I just add another port physically to the device?

---

### Post by David_Etcell on 2015-07-26
Hmm, I'm interested to see how this pans out, I have no idea.

Obviously for multiple IP addresses to one adapter, you can just use an alias, but I would be very interested to know if an alias can be used for a bridge! 

What happens if you try to create eth0:0 as an alias in [COLOR=#333333][FONT=Ubuntu]/etc/network/interfaces and br1 bridges port eth0:0?[/FONT][/COLOR]

---

### Post by bctechnzl on 2015-07-31
I had no luck with the alias device, I can assign it an ip address and ping it but when starting both ends of the vpn, I get locked out of ssh access.
After thinking about your idea, I go a hold of a usb/network adapter and connected it. This came up fine as a second network port and as I added it into interfaces, it was working fine.
So following this logic I set up the eth1 as the bridged adapter. All looked good - (*)I started the bridging script, started openvpn , used an external ubuntu server I had access to for checking that my remote access was still intact. 
I went back to the remote site and started up the openvpn client.
At that point I could not ssh back into the server. I'm at a loss. I cant really make this unit the router for the building, there's too much traffic going through for its limited hardware. I'm clearly missing some understanding of the bridging setup.

* The only subnote here is that the bridging starts up and I get two tap adapters, tap0 and tap1 - is this a clue?

---

### Post by volkswagner on 2015-07-31
I think whenever bridged is mentioned to OpenVPN gurus, they give the lemon face.

I tried it many years ago and found it slow and not as stable.  I just work in the
confines of the routed method. You can map network drives with tun/routed vpn.
What specific issue is requiring bridged?

If you want to keep your hair, you should be at the physical machine so you can run diagnostic commands.

It may help if you post your config for OpenVPN, /etc/network/interfaces and output of ifconfig.

As it seems you already know, there is no need for two tap adapters. Something seems wrong (again, you'll need physical access).

---

### Post by David_Etcell on 2015-08-02
Just out of interest.., when you start the vpn and it locks you out of ssh, can you physically get hands-on the server you are trying to ssh into?

I would be interested to see the output of an 'ifconfig -a' and see if you can ssh into any of the ip addresses associated with taps and tuns.

> [COLOR=#000000]It may help if you post your config for OpenVPN, /etc/network/interfaces and output of ifconfig.[/COLOR]

Also, your bridge-start script, since if you were using an alias, it would need to be specified here. (also might help with the tap0 & tap1 thing)

---

### Post by jason_p2 on 2015-08-03
I have a single port bridged OpenVPN server running in a VM. I was running a routed server for the longest time figuring out the bridged configuration myself. 

Here is my Interfaces config as an example.

Network: 10.10.0.0/24
OpenVPN Server: 10.10.0.250
Edge Router: 10.10.0.1

auto eth0
iface eth0 inet manual
        up ifconfig $IFACE 0.0.0.0 up
        up ip link set $IFACE promisc on
        down ip link set $IFACE promisc off
        down ifconfig $IFACE down


auto br0
        iface br0 inet static
        bridge_ports eth0 tap0
        address 10.10.0.250
        broadcast 10.10.0.255
        netmask 255.255.255.0
        gateway 10.10.0.1
        dns-nameservers 8.8.8.8 8.8.4.4


#### NOTE: If you are running OpenVPN in a virtual machine, then uncomment thes$
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

---

### Post by bctechnzl on 2015-08-11
These are all good suggestions, and I'm not easily at the physical machine so I'll retrieve and and set up a test network locally. Will post my results and setup - its been a heavy week on other jobs.

---

