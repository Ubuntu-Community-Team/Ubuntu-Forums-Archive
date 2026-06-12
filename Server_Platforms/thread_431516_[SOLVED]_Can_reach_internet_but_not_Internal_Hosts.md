---
title: "[SOLVED] Can reach internet but not Internal Hosts."
date: 2007-05-03
forum: Server Platforms
---

### Post by Dzenhax on 2007-05-03
Hi folks.

   I have built a server for internal email using Zimbra.  After I built it I cannot connect to it from any host.  I can connect to the internet through my gateway, but ping shows :

From 192.168.2.30 icmp_seq=397 Destination Host Unreachable
From 192.168.2.30 icmp_seq=399 Destination Host Unreachable
From 192.168.2.30 icmp_seq=400 Destination Host Unreachable

     This is the reply from pinging the gateway.  Since I can get onto the internet I know TCPIP is functioning.  No host on my network can ping my Ubuntu server and the server cannot ping them.  Traceroute works outside my network and even lists the gateway that it cannot ping, but again, not for internal hosts.  

traceroute to 80.80.200.50 (80.80.200.50), 30 hops max, 40 byte packets
** 1  gateway.168.192.in-addr.arpa (192.168.2.2)  3.485 ms  3.578 ms  3.510 ms**
 2  nc-71-52-136-1.dhcp.embarqhsd.net (71.52.136.1)  47.036 ms  46.970 ms  47.654 ms
 3  nc-69-69-52-249.sta.embarqhsd.net (69.69.52.249)  48.146 ms  48.374 ms  48.057 ms
and so on

     The hosts are windows clients.  They can ping each other and the gateway, but cannot ping the Ubuntu server.  The server can ping itself.

     Naturally, as a result I cannot connect to the mail server to pull mail.  Mail clients time out waiting for a response from the server.  This one stumps me.  How can I reach the internet and not recieve ping replies from the gateway?

     I am using static IP addresses for the gateway, the server and most hosts.  I am using bind9 on the server for DNS and all hostnames resolve normally.  DHCP is handled at the gateway for hosts that use it.  Any suggestions?

---

### Post by lloyd_b on 2007-05-03
Could you post some additional info, please:

1.  The output from running the "ifconfig" command (in a terminal window)
2.  The output from running the "route -n" command (in a terminal window)
3.  The contents of the file "/etc/network/interfaces).

My first guess is a bizarre routing issue, but that's just a wild guess based on insufficient info.  Hopefully once you post the info I requested, I (or somebody) will spot something that explains the problem.

Lloyd B.

---

### Post by Dzenhax on 2007-05-03
Lloyd_B

Thanks,

     Your requests in order:


dzenhax@cncv01:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:03:2F:2F:4F:63  
          inet addr:192.168.2.30  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::203:2fff:fe2f:4f63/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3580580 (3.4 MiB)  TX bytes:274995 (268.5 KiB)

eth0      Link encap:Ethernet  HWaddr 00:04:5A:7D:32:EF  
          inet addr:192.168.2.30  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::204:5aff:fe7d:32ef/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:4 dropped:0 overruns:0 carrier:8
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x2400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:91292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28153117 (26.8 MiB)  TX bytes:28153117 (26.8 MiB)

wifi0     Link encap:UNSPEC  HWaddr 00-03-2F-2F-4F-63-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1345764 errors:0 dropped:0 overruns:0 frame:95537
          TX packets:6854 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:104642532 (99.7 MiB)  TX bytes:567905 (554.5 KiB)
          Interrupt:19 

dzenhax@cncv01:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.2     0.0.0.0         UG    0      0        0 ath0
0.0.0.0         192.168.2.2     0.0.0.0         UG    0      0        0 eth0

dzenhax@cncv01:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
network 192.168.2.0
broadcast 192.168.2.255
address 192.168.2.30
netmask 255.255.255.0
gateway 192.168.2.2


iface ath0 inet static
wireless-essid CONCLAVE
wireless-key XXXXXXXXXXXXXX
address 192.168.2.30
netmask 255.255.255.0
gateway 192.168.2.2

auto ath0

After looking at the output I saw the duplcate IP address (eth0 was not connected).  I changed that to another ip and restarted networking.  Still have the problem, so it wasn't that.

Hope you see something.  I asked around and everyone seems stumped.  But I live in a world of Microsoft admins.  I'm the only Linux guy at the office.

Grazie Mille.

---

### Post by lloyd_b on 2007-05-03
> After looking at the output I saw the duplcate IP address (eth0 was not connected). I changed that to another ip and restarted networking. Still have the problem, so it wasn't that.

I think you've spotted the problem, but I don't think that simply changing the IP for eth0 will be enough.  The issue is that you have two different interfaces that have been told that they're connected to the 192.168.2.x network - so how is the system supposed to decide which to use for a given packet?

Let's take a closer look at the issue:
```
dzenhax@cncv01:~$ route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.2.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
192.168.2.0 0.0.0.0 255.255.255.0 U 0 0 0 ath0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
0.0.0.0 192.168.2.2 0.0.0.0 UG 0 0 0 ath0
0.0.0.0 192.168.2.2 0.0.0.0 UG 0 0 0 eth0
```
So if you're sending a packet to the 192.168.2.x subnet, the first routing entry that matches that description is for eth0, so packets destined for the local network will be sent that way.  On the other hand, if the destination is outside of the local network, the first gateway entry is for ath0, so that packets destined for the internet will travel via that route.   

Suggestion:  Remove/comment out the "auto eth0" line in "/etc/network/interfaces", then restart networking ("sudo /etc/init.d/networking restart").  This should prevent the system from automatically bringing up that interface, and block the interference between eth0 and ath0.  

Lloyd B.

---

### Post by Dzenhax on 2007-05-05
Thanks again Lloyd_b

     Commenting out the interface didn't work.  However removing eth0 from the routing table did.  The network now works fine.  

     eth0 is not actually hooked up and I just use it for a backup in case I fry my wireless.  In fact it was still configured from the original installation, since until now I had no reason to change it.

     In any case, I wouldn't have found it if not for your help.  Thanks alot.

---

### Post by Dzenhax on 2007-05-24
Here we go again.

I have found that after rebooting that the problem returns.  If I type:

route del -net 192.168.2.0 netmask 255.255.255.0 dev eth0

then I all is immediately well.  But on reboot, I have to re input the command.  I don't wanna make a boot time script.  There has to be a file that keeps putting eth0 back in front of ath0.  Anyone know where I go to fix it?

Thanks.

---

### Post by lloyd_b on 2007-05-24
The route is being generated by the info in "/etc/network/interfaces".

Try this - In that file, under the "eth0" entry, change the "netmask" to "255.255.255.255".  This should suppress the creation of that pesky route.

I'd also suggest commenting/removing the "gateway ..." line associated with "eth0" as well.

After changing the file, in a terminal window:
```
sudo /etc/init.d/networking restart
```
Will restart networking so you can see if the fix "took" (without having to reboot).

Lloyd B.

---

### Post by Dzenhax on 2007-05-24
Whelp, here are the results,

     I changed the file with just deleting the gateway statement and restarting the service.  It worked, but on reboot I got the problem back.  Next I changed the mask and that works even through reboot.

     I'm still not clear on why Ubuntu wants to use that interface so bad.  I've done everything but comment it out!!

      Thanks again.

---

### Post by lloyd_b on 2007-05-24
> I'm still not clear on why Ubuntu wants to use that interface so bad. I've done everything but comment it out!!

Because you're telling it to do so.  By having that "static" definition for the interface in the "interfaces" file, you are telling the system:
1.  The interface should be brought up.
2.  It should have the specified IP address.
3.  Use the netmask to determine which network routes to add for the interface.
4.  If specified, add a route for the given gateway.

If you don't plan on using that interface, perhaps you should abandon the "static" entries altogether - simply change it to:
```
auto eth0
iface eth0 inet dhcp
```
If there's no cable attached, then DHCP will fail, and the interface won't receive an IP or set any routes.

At any rate, it seems we've got your problem resolved.  And hopefully it'll *stay* resolved this time :-)

Lloyd B.

---

