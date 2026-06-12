---
title: "Cannot get OpenVPN to work in Ubuntu - in XP works fine."
date: 2010-10-16
forum: Security
---

### Post by zozza on 2010-10-16
This is one of these "I can do it in XP but not in Ubuntu."

I am trying to use a VPN.  I am on my University network and therefore do not control the network settings (e.g. DNS).  There is no NAT.  

I am using the test service from Swiss VPN - [www.swissvpn.net](www.swissvpn.net)

In XP I download the Openvpn .exe, install it, then download the ca.crt and swissvpn.ovpn files, put the in the correct directory in Program Files/Openvpn/config, and connect using the GUI.  Using ipconfig /all I see a new IP, new DNS, new gateway, etc.  

In Ubuntu I sudo apt-get install Openvpn.  The I download the same ca.crt and swissvpn.ovpn files and put them in my ~ directory.  

I run sudo openvpn --configure swissvpn.ovpn and enter the test username and password.  I get:

Sat Oct 16 21:57:46 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Sat Oct 16 21:57:46 2010 RESOLVE: NOTE: connect-openvpn.swissvpn.net resolves to 2 addresses, choosing one by random
Sat Oct 16 21:57:46 2010 Attempting to establish TCP connection with [AF_INET]80.254.79.87:443 [nonblock]
Sat Oct 16 21:57:47 2010 TCP connection established with [AF_INET]80.254.79.87:443
Sat Oct 16 21:57:47 2010 TCPv4_CLIENT link local: [undef]
Sat Oct 16 21:57:47 2010 TCPv4_CLIENT link remote: [AF_INET]80.254.79.87:443
Sat Oct 16 21:57:47 2010 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Sat Oct 16 21:57:49 2010 [server] Peer Connection Initiated with [AF_INET]80.254.79.87:443
Sat Oct 16 21:57:51 2010 TUN/TAP device tun0 opened
Sat Oct 16 21:57:51 2010 /sbin/ifconfig tun0 80.254.76.242 netmask 255.255.255.128 mtu 1500 broadcast 80.254.76.255
Sat Oct 16 21:57:51 2010 Initialization Sequence Completed

This seems fine.  

If I do ifconfig I now have:

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:80.254.76.242  P-t-P:80.254.76.242  Mask:255.255.255.128
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:62 (62.0 B)


However, unlike in XP, when I try to load the [www.swissvpn.net](www.swissvpn.net) website it always times out.  (For the test you can only load the swissvpn.net site). 

As I mentioned I do not control my DNS.  But I don't think this should matter if the VPN remotely deals with the DNS (at the end of the tunnel).  Anyhow, when I checked in Windows SwissVPN gave me a new DNS.

What am I doing wrong in Ubuntu?

Thanks

---

### Post by P4man on 2010-10-16
I dont know much about VPN, but can you access the site by IP? If so, then at least you know the VPN is working and its just a matter of getting DNS to work.

Also.. network manager has a VPN client built in. I dont know if its any good, but its certainly easy to configure (just click the network tray icon, . 
edit: on swissVPN thats exactly what they propose for ubuntu 8.10:

[http://www.swissvpn.net/sub.html](http://www.swissvpn.net/sub.html)

---

### Post by zozza on 2010-10-17
> **P4man said:**
> I dont know much about VPN, but can you access the site by IP? If so, then at least you know the VPN is working and its just a matter of getting DNS to work.

No, I cannot access it via IP.  When I do [http://80.254.79.210](http://80.254.79.210) Firefox starts "looking" for the URL but gets stuck.

> /Also.. network manager has a VPN client built in. I dont know if its any good, but its certainly easy to configure (just click the network tray icon, . 
edit: on swissVPN thats exactly what they propose for ubuntu 8.10:

[http://www.swissvpn.net/sub.html](http://www.swissvpn.net/sub.html)The network manager seems to be for PPTP only - not OpenVPN.

----

Also, I am a bit confused about how VPNs and DNS work together.  

Either:

a) the ISPs DNS is replaced by the VPNs DNS in by /etc/resolv.conf file or; 

b)  like with Tor, all DNS queries are done at the end of the VPN tunnel - in this case in Switzerland. 

If the answer is a) then this could be a problem because I do not control my DNS settings.  I have tried, in the past, to use the OpenDNS settings in the /etc/resolv.conf but this meant I had no connection.  According to the people at the OpenDNS forum, this is because I do not control the network - my University does.

Thanks.

---

### Post by P4man on 2010-10-17
There is a network manager plugin in synaptic for openvpn :
```
network-manager-openvpn-gnome

```

That should enable openvpn settings in networkmanager.
Give that a try. 

If that fails, perhaps try WiCD.  I suspect you cant use network manager to manage your network connection (and DNS) and have something else at the same time trying to establish a VPN.

---

