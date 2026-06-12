---
title: "2 Instances of OpenVPN (also how should a bridge config look in interfaces)"
date: 2010-04-06
forum: Server Platforms
---

### Post by onyxwolf on 2010-04-06
Hi all,

I've been trying to figure out exactly how to run 2 instances of openvpn on my Ubuntu Server [Karmic]. I want to do this so I will have my UDP instance whenever I want to log in to it over any "open" network (one without decent firewall rules), but when that fails, I want to be able to access it via TCP. My understanding is that to have it listen to TCP also, requires two instances running. I've been trying to find a decent how to but the only one that seemed reasonable quickly got me confused, and was for a different flavor of Linux (although I doubt that would have made a difference if I understood it). 

Also, if possible, I want them to run from start (init.d style).


Does anybody know where a good how to is? Or can someone please explain how to do this?

Also, I want to make sure my bridge interface setup is correct, can someone post the correct configs? (I will post mine after I get home). Any and all help is greatly appreciated.

---

### Post by fang0654 on 2010-04-06
The two instances just need to be different .conf files.  The easiest thing to try would be to set up one config file for UDP, copy it and modify it for TCP, and restart openvpn.  It may fire up two instances, since the init scripts scan the /etc/openvpn folder for all .conf files.  I haven't tested this, so I can be wrong (it has happened once or twice before!)

If you use dev tun in the config, you don't need to do any bridging.  You need to enable ip forwarding on your server, and set up any firewalling you may want.

Also, I am not sure if you need to create a separate set of keys for each configuration.  You can try it to see.

---

### Post by onyxwolf on 2010-04-06
Thank you for that. I'll try just using two conf files for it. Now pertaining to the tun vs tap. I prefer having the bridging capability, mainly because switching is less resource consuming than routing, but I may try the other way if I run into problems. 

As promised my /etc/network/interfaces:

```
auto lo
iface lo inet loopback

# The primary network interface
 auto eth0
 iface eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
  down ip link set $IFACE promisc off
  down ifconfig $IFACE down


# Bridge Interface
auto br0
iface br0 inet static
 address 192.168.1.4
 network 192.168.1.0
 netmask 255.255.255.0
 broadcast 192.168.1.255
 gateway 192.168.1.1
 nameserver 127.0.0.1
 bridge_ports eth0

```

---

### Post by spynappels on 2010-04-07
As Fang said, just use 2 separate server.conf files, one for UDP and one for TCP. just make sure they are listening on different ports eg. UDP 1194, TCP 1195, and that they hand out IPs in different subnets eg. UDP scope is 10.20.0.x and TCP scope is 10.20.1.x

You can use the same ca.crt and generate client keys and certs using the same easy-rsa instance, just create 2 different client.conf or client.ovpn files (depending on whether you are using *nix or Windows clients), one for each protocol.

On the server.conf files you need to uncomment out the 

```
#client-to-client
```

line to allow each client to talk to all other clients and you also need to place a line in each pushing a static route to each client to access the other subnet (UDP or TCP)

Finally, make sure IP-Forwarding is enabled on your OpenVPN server.

This setup works well, I have deployed several of them for work and have had no problems at all.

If you need any more specific help, just ask and I'll do my best to give you a hand.

---

### Post by onyxwolf on 2010-04-08
THANKS!!! ;) That did it. How easy was that. I tested my TCP instance and it worked perfect! I haven't had the chance to try out the UDP and I just replaced my router (with full IOS Cisco Router and forwarded the ports, but dumb me forgot to list them as ok in my ACLs), so I broke my TCP, but for that one day I experienced happiness, and now know its doable! Thanks spynappels I didn't even think to make sure to keep the given addresses not the same, I'm certain that would have eventually bitten me! Something I did have a problem with, I had to change the second .conf file to have a different dev (tap0 for UDP and tap1 for TCP).

I didn't need to configure routes or anything like that, is that because I am using switching? I was able to ssh to my vpn box as well as (when I configured to send all traffic across) http to my old router to config it. I guess the one thing that I'm really interested in seeing is if I can see another client without that client-to-client conf, and see if that works because it is still just switching. We'll see...

---

### Post by spynappels on 2010-04-08
Glad it worked for you!

Without the client-to-client setup you would not be able to access any other clients on the same subnet, and to access clients on another subnet such as the other VPN instance, you do need to push routes to clients, but the config file can do all that for you.
The VPN server is routing rather than switching when you access the LAN the VPN server is on, but with client-to-client function it is acting as a virtual switch.

Have fun trying out the different options, OpenVPN rocks.

---

