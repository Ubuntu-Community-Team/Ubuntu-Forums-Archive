---
title: "VPN Configuration Troubles."
date: 2011-01-13
forum: Server Platforms
---

### Post by teejmya on 2011-01-13
I'm setting up a VPN server using openvpn. I installed it from the apt repos, configured it with a little help, and launched it with ```
sudo openvpn openvpn.conf
```
so it would tell me errors. It printed:

> teej@Ixion:/etc/openvpn$ sudo openvpn openvpn.conf
Thu Jan 13 10:18:02 2011 OpenVPN 2.1.4 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Nov  5 2010
Thu Jan 13 10:18:02 2011 IMPORTANT: OpenVPN's default port number is now 1194, based on an official port number assignment by IANA.  OpenVPN 2.0-beta16 and earlier used 5000 as the default port.
Thu Jan 13 10:18:02 2011 WARNING: --ping should normally be used with --ping-restart or --ping-exit
Thu Jan 13 10:18:02 2011 NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Thu Jan 13 10:18:02 2011 WARNING: file 'static.key' is group or others accessible
Thu Jan 13 10:18:02 2011 Static Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Thu Jan 13 10:18:02 2011 Static Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Jan 13 10:18:02 2011 Static Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Thu Jan 13 10:18:02 2011 Static Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Jan 13 10:18:02 2011 WARNING: normally if you use --mssfix and/or --fragment, you should also set --tun-mtu 1500 (currently it is 1200)
Thu Jan 13 10:18:02 2011 Socket Buffers: R=[114688->131072] S=[114688->131072]
Thu Jan 13 10:18:02 2011 TUN/TAP device tun0 opened
Thu Jan 13 10:18:02 2011 TUN/TAP TX queue length set to 100
Thu Jan 13 10:18:02 2011 /sbin/ifconfig tun0 10.1.0.1 pointopoint 10.1.0.2 mtu 1200
Thu Jan 13 10:18:02 2011 ./office.up tun0 1200 1244 10.1.0.1 10.1.0.2 init
Thu Jan 13 10:18:02 2011 script failed: could not execute external program
Thu Jan 13 10:18:02 2011 Exiting
teej@Ixion:/etc/openvpn$ 


I searched up, and found that this was a bug in the version of openvpn in the repos. ([https://bugs.launchpad.net/ubuntu/+source/openvpn/+bug/277447](https://bugs.launchpad.net/ubuntu/+source/openvpn/+bug/277447) So I updated using  the .deb on their site to the most recent stable version.

The problem is, it still prints the same log. Nothing appears to have changed. When I installed, the config file's permissions changed, but that's the only noticeable difference.


Any ideas?

---

### Post by Johnsie on 2011-01-14
I use pptp on Ubuntu for client and server and it works quite well:

[http://forums.bit-tech.net/showthread.php?t=132029](http://forums.bit-tech.net/showthread.php?t=132029)

---

### Post by chrislynch8 on 2011-01-14
Can you show us the output of cat /etc/openvpn/openvpn.conf

---

### Post by SeijiSensei on 2011-01-14
Are you talking about this error?

> 
Thu Jan 13 10:18:02 2011 ./office.up tun0 1200 1244 10.1.0.1 10.1.0.2 init
Thu Jan 13 10:18:02 2011 script failed: could not execute external program


If so, it's probably because /etc/openvpn/office.up isn't marked as executable by root.  Either that, or the script makes a call to a non-existent or non-executable file.

Try running the script from the command line manually.

---

### Post by teejmya on 2011-01-14
My openvpn.conf is as follows:

```


teej@Ixion:/etc/openvpn$ cat openvpn.conf 
dev tun
# Network interface used by the VPN server on WIFI_SUBNET
# eth1 (192.168.1.1) in the previous example
local 192.168.1.107
# The following line defines two new VPN interfaces
# ifconfig VPN_SERVER VPN_CLIENT
ifconfig 10.1.0.1 10.1.0.2
script-security 3
up ./office.up
secret static.key
ping 15
tun-mtu 1200
mssfix 1400
verb 3
teej@Ixion:/etc/openvpn$ 


```

Also, I'm not much of a scripter, so I don't know about office.up. Here's that:

```


teej@Ixion:/etc/openvpn$ cat office.up 
# office.up
#!/bin/sh
route add -net 10.0.1.0 netmask 255.255.255.0 gw $5
teej@Ixion:/etc/openvpn$ 

```

I don't see it accessing any other files, and I've run ```
sudo chmod a+x office.up
```

---

### Post by chrislynch8 on 2011-01-14
Is office.up in the correct location for openvpn.conf to execute it? I'm not sure but when you are starting openvpn will it execute the script as root or as the lower privlegded user. Try setting permissions on office.up to 777

Also can you manually run that command to add the route?

---

### Post by teejmya on 2011-01-14
I think we've found the problem. Running the command for the route doesn't succeed.

```


teej@Ixion:/etc/openvpn$ route add -net 10.0.1.0 netmask 255.255.255.0 gw $5
Usage: inet_route [-vF] del {-host|-net} Target[/prefix] [gw Gw] [metric M] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [gw Gw] [metric M]
                              [netmask N] [mss Mss] [window W] [irtt I]
                              [mod] [dyn] [reinstate] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [metric M] reject
       inet_route [-FC] flush      NOT supported
teej@Ixion:/etc/openvpn$ 


```

I think the command is formatted incorrectly? I have no idea how. Any ideas?

---

### Post by chrislynch8 on 2011-01-14
I assume that $5 is causing the issue and during the openvpn start is it getting the GateWay gw from somewhere.

Do you know what the gateway should be for the route you are adding?

---

### Post by chrislynch8 on 2011-01-14
I assume that $5 is causing the issue and during the openvpn start is it getting the GateWay gw from somewhere.

Do you know what the gateway should be for the route you are adding?

---

### Post by teejmya on 2011-01-14
Not a clue. Anywhere I can find that information?

---

### Post by teejmya on 2011-01-14
Not a clue. Anywhere I can find that information?

---

### Post by SeijiSensei on 2011-01-14
If you're just setting up a tunnel between the two machines, you probably don't need to add a route at all.  If you're trying to gain access to the entire remote network, you'll need to add the route.

If you need the route, try replacing $5 with 10.1.0.2, the address of the remote VPN client like this:

```
route add -net 10.1.0.0 netmask 255.255.255.0 gw 10.1.0.2
```

Then the route command will send all traffic for machines in 10.1.0.0/24 over the VPN. 

Did you create the office.up script intentionally, or were you copying someone else's configuration?

---

### Post by teejmya on 2011-01-14
Just copying a configuration from a wiki. I'm lost on making my own. 

Oddly enough, running ```
 sudo route add -net 10.0.1.0 netmask 255.255.255.0 gw 10.1.0.2 
```
gives me this:
```
teej@Ixion:/etc/openvpn$ route add -net 10.0.1.0 netmask 255.255.255.0 gw 10.1.0.2
SIOCADDRT: Operation not permitted
teej@Ixion:/etc/openvpn$ sudo !!
sudo route add -net 10.0.1.0 netmask 255.255.255.0 gw 10.1.0.2
SIOCADDRT: No such process

```

A quick google search on SIOCADDRT brought me to [http://www.digitalsanctum.com/2009/03/22/solution-to-siocaddrt-no-such-process-on-ubuntu/](http://www.digitalsanctum.com/2009/03/22/solution-to-siocaddrt-no-such-process-on-ubuntu/) , which made me double check my /etc/network/interfaces. It looks okay to me.

```
teej@Ixion:/etc/openvpn$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

teej@Ixion:/etc/openvpn$ 

```

The box is on a network that gave it a permanent DHCP lease 192.168.1.107.

---

### Post by spynappels on 2011-01-15
Are you running a server or desktop, and was that the entire /etc/network/interfaces file? It's just that there is no mention of eth0 or any other ethernet interfaces, which is a major problem.

Can you post the full output of ifconfig?

---

### Post by teejmya on 2011-01-16
It's the desktop edition, and yes that was the entire interfaces file. I just realized I'm running 11.04, could that be mucking something up?

Here's my ifconfig:
```


teej@Ixion:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:d1:25:31:17  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe25:3117/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:111599 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86571 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69059280 (69.0 MB)  TX bytes:41766099 (41.7 MB)
          Interrupt:17 Memory:d2100000-d2120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5150 (5.1 KB)  TX bytes:5150 (5.1 KB)

teej@Ixion:~$ 


```

Networking runs. The machine is connected to the internet and I can access it on my home network.

---

### Post by SeijiSensei on 2011-01-16
> **teejmya said:**
> Just copying a configuration from a wiki. I'm lost on making my own. 

I always start with the documentation from the project itself.  In this case, the [Static Key Mini-HOWTO]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") is your friend.

> Oddly enough, running ```
 sudo route add -net 10.0.1.0 netmask 255.255.255.0 gw 10.1.0.2 
```
gives me this:
```
teej@Ixion:/etc/openvpn$ route add -net 10.0.1.0 netmask 255.255.255.0 gw 10.1.0.2
SIOCADDRT: Operation not permitted
teej@Ixion:/etc/openvpn$ sudo !!
sudo route add -net 10.0.1.0 netmask 255.255.255.0 gw 10.1.0.2
SIOCADDRT: No such process

```


Let me ask my question again.  Do you need to access other remote machines other than the one running OpenVPN?  If not, then just delete the "up" command.

The "No such process" error indicates that 10.1.0.2 doesn't exist.  You can only run this command after the VPN connection is set up.

---

### Post by teejmya on 2011-01-16
I'll remember that. It should come in handy in the future. 
Meanwhile, my keys are already in place.

And yes, my reason for setting up VPN is to access my home network AND the internet. I'm starting to think that these conflict with each other.

---

### Post by SeijiSensei on 2011-01-16
> **teejmya said:**
> I'll remember that. It should come in handy in the future. 
Meanwhile, my keys are already in place.

And yes, my reason for setting up VPN is to access my home network AND the internet. I'm starting to think that these conflict with each other.

If you want to maintain connectivity with the home network, but use the Internet for everything else, then you do want a route command like the one posted earlier.  I'm guessing, though, that the home network resides in a different address space from 10.0.1.0/24.

Suppose your home network uses the very common 192.168.1.0/24.  Then the appropriate route command for office.up would be 

```
route add -net 192.168.1.0 netmask 255.255.255.0 gw 10.0.1.2
```

Now traffic for the 192.168.1.0/24 network will be sent over the tunnel and everything else will go out over the Internet-facing interface on the remote.

However here's the rub.  For this to work properly, traffic back to the remote has to pass through the OpenVPN server.  If you've got a standard router box, you'll need to add a "static route" on it as well.  Access the router's management interface (usually via a browser), and create a route for 10.0.0.0/8 via the address of the OpenVPN box within the router's network.  So, extending my example above, if the OpenVPN box has address 192.168.1.100, you'd add a route on your router sending all traffic for 10.0.0.0/255.0.0.0 via 192.168.1.100.  Now traffic from your local network will be forwarded through the router to the OpenVPN server whereupon it will be forwarded on to you.

One other thing...  If the OpenVPN server on your home network is doing routing, you'll need to enable IP routing in the kernel.  Edit the file /etc/sysctl.conf and enable the line that reads "net.ipv4.ip_forward=1".  Then reboot.

---

### Post by teejmya on 2011-01-17
Alright, we're so close to getting this thing running I can smell it.

I am using 192.168.1.0/24, and I modified office.up accordingly.

As far as editing the router's config, I have a basic Linksys G router. My options for static routing are as follows:
 	 
> 
 	 	 	Enter Route Name: 	 	 	 
 	 	 	Destination LAN IP: 	 .  .  .  	 	 
 	 	 	Subnet Mask: 	 .  .  .  	 	 
 	 	 	Gateway: 	 .  .  .  	 	 
 	 	 	Hop Count: 	 	 
 			 

Under Destination LAN IP, I have 192.168.1.107, which is the IP of the OpenVPN box.
Under Subnet Mask, I have 255.255.255.0.
Under Gateway, however, I have no clue what to use. At first I used 192.168.1.1, the IP of the router. It told me:
> Invalid destination IP or Subnet Mask! 
Then, I changed the Gateway to 10.0.0.0, to see if it would work. Then I got:
> value is illegal!
What's the issue here?

---

### Post by SeijiSensei on 2011-01-17
Try:

Enter Route Name: ToVPN
Destination LAN IP: 10.1.0.0
Subnet Mask: 255.255.255.0
Gateway: 192.168.1.107
Hop Count: 1

If "Hop Count: 1" doesn't work, try leaving it blank or otherwise forcing the router to provide a default.

You're telling the Linksys to send traffic for hosts with addresses between 10.1.0.0 and 10.1.0.255 to the OpenVPN box at 192.168.1.107.  (That range is determined by the IP and subnet mask.)  One of the hosts in that range is the remote at 10.1.0.1.  As I said, make sure IP forwarding is enabled on the OpenVPN box so it can pass this traffic to the remote.

---

