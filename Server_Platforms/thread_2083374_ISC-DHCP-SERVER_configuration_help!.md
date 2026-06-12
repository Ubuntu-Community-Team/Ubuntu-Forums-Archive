---
title: "ISC-DHCP-SERVER configuration help!"
date: 2012-11-12
forum: Server Platforms
---

### Post by lestertorres on 2012-11-12
Hi everyone I am a noob to Linux but have created a squid proxy server already but it is not working when I connect other computers to the router, so I am using instead a ISC-DHCP-SERVER in order to give other pc's internet. I am running Ubuntu 12.10 and I am trying to set up a ISC-DHCP-SERVER through "eth0" being the internet nic and "eth0" the router to give other pc's internet. I have read many forums online on how to do this but for some reason cannot get it working. My ifconfig is 

[PHP]eth0      Link encap:Ethernet  HWaddr 00:14:85:45:8f:62  
          inet addr:192.168.1.93  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:304:499b:5ea9:29ff:f662:61c9:fe9f/64 Scope:Global
          inet6 addr: 2602:304:499b:5ea9:214:85ff:fe45:8f62/64 Scope:Global
          inet6 addr: fe80::214:85ff:fe45:8f62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11013 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10470262 (10.4 MB)  TX bytes:853099 (853.0 KB)

eth1      Link encap:Ethernet  HWaddr 00:50:fc:55:27:7a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1:avahi Link encap:Ethernet  HWaddr 00:50:fc:55:27:7a  
          inet addr:169.254.7.70  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9921214 (9.9 MB)  TX bytes:9921214 (9.9 MB)[/PHP]


Can someone please advise what I should do next? When I... 

sudo service isc-dhcp-server stop

I get a *unknown instance:*

But when I start I get a  *start/running, process 5080*

Please help...thank you all.

---

### Post by darkod on 2012-11-12
First of all, I think you should split the "job".

1. Are the clients receiving IPs or not? (probably not since the process doesn't seem to be running correctly). Check the IPs on the clients also with ifconfig (or ipconfig on windows).

2. If this squid machine is supposed to be a router also, you need to configure both eth0 and eth1 interfaces, one external and the other internal. From your ifconfig eth1 doesn't seem to be configured with any IP, public or private.

3. Also, for a machine to be a router it needs to have the ip_forward set to 1 in /etc/sysctil.conf. The line is commented by default so you need to remove the # at the start. The line is something like:
/net/ipv4/ip_forward=1

And you need at least one POSTROUTING rule in iptables so that it can act as a router. How you apply that rule will depend whether you are using a firewall on this machine or not. If not using a firewall, it's enough to edit /etc/rc.local and before the exit 0 add:
iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE

where ethX is the external interface.

---

### Post by lestertorres on 2012-11-13
Hi Darko,

Thanks for the reply. 

Well...

1. The clients are not recieving IP addresses yet because I have not been able to get the DHCP running therefore I have not connect any other pc's to the eth0.

2. Well the static eth0 I put in recently but when I had configured the proxy I had only the eth1 as a static and have toggled the eth1 with dhcp and static. 

3. I have done this as well making eth0 as the external interface. I did allow the ip_forward and the iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

I am going to keep giving it a shot but this has seem to be a bit more challenging than expected.

---

### Post by darkod on 2012-11-13
What you did when you had only one interface is not very relevant. Since now you have two, I think it will work best if you dedicate one as external (towards your internet router, etc), and the other as internal (towards your LAN).

So, set them up with static IPs in different subnets (ranges).

What got me confused is in ifconfig in the eth1:avahi section you can see the IP like 169.254.x.x. Usualy that's an automatic IP when there is no other option available. Or you are using this IP on purpose?

On the dhcp side, post /etc/dhcp/dhcp.conf the configuration file.

Also, if I'm not mistaken, the daemon is still dhcpd so you can try:
sudo service dhcpd start/stop/restart

PS. Maybe this can help you:
[http://askubuntu.com/questions/140126/how-do-i-configure-a-dhcp-server](http://askubuntu.com/questions/140126/how-do-i-configure-a-dhcp-server)

---

### Post by lestertorres on 2012-11-13
I was actually confused with how the eth1:avahi came about. I do not recall setting that up or installing anything like that so I did not know how to approach it. 

I am trying to dedicate eth1 as the internet routerto give clients their IP's with eth0 as the internal that provides the internet. I should put both in the interface with different subnet ranges? Can eth0 be 192.168.1.93 which is the address?

Thanks a bunch, again.

---

### Post by darkod on 2012-11-13
Yes, they can. So, you want eth0 to be 192.168.1.93 and 192.168.1.1 is the router that goes to the internet?

For eth1 lets select 10.10.10.1 for example, with netmask 255.255.255.0 which covers the whole 10.10.10.x range.

In that case /etc/network/interfaces would be like:
```
auto eth0
iface eth0 inet static
   address 192.168.1.93
   netmask 255.255.255.0
   gateway 192.168.1.1
   dns-nameservers 8.8.8.8 8.8.4.4 (or you can use the ISP DNS servers instead)

auto eth1
iface eth1 inet static
   address 10.10.10.1
   netmask 255.255.255.0
```

That's it.

In the dhcp config you will have to tell it to use only eth1 to serve the dhcp clients. It's better not to send any dhcp traffic towards the internet router. :)

This is just an example. In the /etc/network/interfaces code I didn't mention the lo interface, leave it as default as it is. Only make changes to eth0 and eth1.

---

### Post by lestertorres on 2012-11-13
For some reason now I do not have any internet connection when I configured the interfaces to the way you advised. Although now when i do *ifconfig* i get...

> eth0      Link encap:Ethernet  HWaddr 00:14:85:45:8f:62  
          inet addr:192.168.1.93  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:304:499b:5ea9:214:85ff:fe45:8f62/64 Scope:Global
          inet6 addr: fe80::214:85ff:fe45:8f62/64 Scope:Link
          inet6 addr: 2602:304:499b:5ea9:9c7e:357d:66af:16ed/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:750 errors:0 dropped:0 overruns:0 frame:0
          TX packets:739 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:431123 (431.1 KB)  TX bytes:146711 (146.7 KB)

eth1      Link encap:Ethernet  HWaddr 00:50:fc:55:27:7a  
          inet addr:10.10.10.1  Bcast:10.10.10.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:59872 (59.8 KB)  TX bytes:59872 (59.8 KB)



I seem to get internet when I...

#auto eth0
#iface eth0 inet static
#   address 192.168.1.93
#   netmask 255.255.255.0
#   gateway 192.168.1.1
#   dns-nameservers 8.8.8.8 8.8.4.4

auto eth1
iface eth1 inet static
   address 10.10.10.1
   netmask 255.255.255.0

Where in the *dhcp.conf* do I tell it to use only *eth1* to server the dhcp clients?

---

### Post by darkod on 2012-11-13
Well, you have to help us out. Is eth0 connected to the internet router or eth1? How you configure the interfaces will depend on which one you connect to the internet router and which one to the local LAN.

First of all, how do you plan the server to go out to the internet? What will you connect it to?

---

### Post by lestertorres on 2012-11-13
eth0 is connected to the internet router. 

I plan for the server to go out to the internet through eth1. I plan on connecting it to a switch where I can then connect different clients to. I acutally got everything working with DHCP but when I connected another pc to eth1 it will show it is connected but without internet.

---

### Post by darkod on 2012-11-13
You are confusing me now. If eth0 is connected to the internet router how do you plan it to go out to the internet using eth1?

If you want the server itself to be a router and dhcp server for the clients on the LAN, it should be the device between the internet router and the local LAN. Other machines on the LAN should have no physical access to the internet and the router, only through this server machine.

Otherwise, if clients can reach and use the internet router, you don't need this server to route them.

I think you have it connected wrongly, that's why the clients didn't have internet. Otherwise, if the routing on the server is configured properly, the clients should have internet.

---

### Post by SeijiSensei on 2012-11-14
To tell the DHCP server to use eth1, add the line 

```
INTERFACES=eth1
```

to /etc/default/dhcp3-server.

The interface assignment does not happen in dhcpd.conf.  It is a command-line parameter so it is controlled by the file in /etc/default.

---

### Post by lestertorres on 2012-11-14
I think I might not be explaining myself correctly. Sorry darkod for the noobness lol well the eth0 is connected to a router which is also the modem that gives me internet. The eth1 is going to give internet to the clients. That is my ultimate goal. I actually got the DHCP to work but had the wrong config so that would explain why the internet would not work. I need to keep making some configs but now my internet is gone completely from eth0 so now I have to figure that out as well.

---

### Post by lestertorres on 2012-11-14
Seiji...
Thank you for the help and I have done that already it worked, thanks again. The issue I'm having is that the clients are not receiving internet. There is a connection established but it does not give out a internet connection. But that was great info...thanks again!

---

### Post by TheMightyGirth on 2012-11-14
Hi lestertorres,

It looks to me like you have 3 problems here;

1/ No internet access on your "server" via eth0

2/ DHCP is not serving to your clients on eth1

3/ The server is not routing traffic from eth1 to eth0 (although that may be working but you can't tell as the other 2 things are broken.

You need to solve these 1 at a time.

For 1/
can you ping your router?
can you ping the internet (using and IP address)
can you ping the internet (using a dns name)

I would bring down eth1 for the time being and get the net working again first.

---

### Post by darkod on 2012-11-14
OK, if the clients have no internet, the order in which I would check things is:
1. On any clients try ping 8.8.8.8 to see if you really have no internet or it's only a DNS problem.

2. If there is no reply, first check whether internet on the server is working. If it's not, try pinging the router IP. On the server's eth0 we used 192.168.1.93 but are you sure that can work with the router? And does the router have the 192.168.1.1 IP or another one?

3. If internet on the server is working, check the forwarding configuration you did, the ip_forward enabled in /etc/sysctl.conf and the iptables MASQUERADE rule. Remember they are needed if you want the server to be able to forward packets between eth0 and eth1.

---

### Post by lestertorres on 2012-11-14
TheMightyGirth...

1) Yes I can ping the router using 192.168.1.93

2) I cannot ping the internet using an IP address using 199.181.132.250 for espn. It states the destination host unreachable.

3) I cannot ping the dns using 8.8.8.8 it says the destination host unreachable as well. 

I tried bringing down eth1 but it said it was not configured. I went back to interfaces and # on all eth0 and did a network restart, then reboot and still got no wired connection to the internet through eth0.

---

### Post by lestertorres on 2012-11-14
Darkod...

1) When I did a ping I did get a response so it has to be a DNS config problem. 

2) I honestly do not think that eth0 192.168.1.93 can work with the router because that is the address I have for eth0.  The router at this time does not have 192.168.1.1 but if I recall when I had on there 10.10.10.1 it might have worked. 

3) In the sysctl.conf file I do have net.ipv4.ip_forwarding=1 active but I do not see a section where it states MASQUERADE. Should I add that line somewhere in there?

---

### Post by darkod on 2012-11-14
Can you post the results of pinging the router?

Also, don't comment out with # the eth0 interface. If you do, it will not work definitely. Leave it as it is configured with 192.168.1.93 and post the ping results.

PS VERY IMPORTANT: What address does the router have? This is very important and you need to know it, you can't just invent IPs. Using the 192.168.1.93 for the eth0 interface and the 192.168.1.1 as gateway was under the assumption the router is 192.168.1.1. If it isn't, of course the server will not have working internet access.

---

### Post by lestertorres on 2012-11-14
> ping 192.168.0.1
ping 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.1.50 icmp_seq=1 Destination Host Unreachable
From 192.168.1.50 icmp_seq=1 Destination Host Unreachable
From 192.168.1.50 icmp_seq=1 Destination Host Unreachable
From 192.168.1.50 icmp_seq=1 Destination Host Unreachable
From 192.168.1.50 icmp_seq=1 Destination Host Unreachable
From 192.168.1.50 icmp_seq=1 Destination Host Unreachable
From 192.168.1.50 icmp_seq=1 Destination Host Unreachable
^C
--- 192.168.0.1 ping statistics ---
7 packets transmitted, 0 received, +6 errors, 100% packet loss, time 6031ms pipe 3

I put the address 192.168.0.1 for the router being that it is a netgear and I found out that is the typical address for the router.

---

### Post by lestertorres on 2012-11-14
I am going to give in and nuke the pc and just start again from scratch :(. I do want to thank everyone that has helped me and ubuntu is great...i just need to figure it out more. I am only on my third week using ubuntu and i really like it. Thanks everyone.

---

### Post by darkod on 2012-11-14
No need to destroy the ubuntu installation, there doesn't seem to be anything wrong with it.

If the router is 192.168.0.1 you need to set for example the 192.168.0.10 address on eth0, and internet should work.

---

### Post by lestertorres on 2012-11-14
Alright Darkod you convinced me to continue on with my challenge. Does it matter that I am also using a squid proxy server for the dhcp as well? I did as you advised with using 192.168.0.10 as the address for eth0 but still cannot connect to the internet. I even tried 192.168.1.10 on eth0 and still nothing. I first need to get the internet back on working. I have toggled with the interfaces quiet a few times but I do not think that, that is where the problem relies. Any ideas?

---

### Post by darkod on 2012-11-14
Hmm, I am not sure how it would work with a proxy in the picture. Usually you would leave servers outside the proxy but it depends if the network can accept this configuration and allow the server to go out only using the router and without the proxy.

If it doesn't allow it, yes, you have to take that into account too. Because in that case the internet goes through the proxy which would apply for this server too. From the router point of view, the server will be just a client.

So even if you reinstall the OS, you will still have the same issue.

Also, the 192.168.0.10 I suggested is just an example. Make sure another machine is not using the same IP address. It's best to select a static IP which is outside the router dhcp range so that it can't be delegated to another machine.

PS. In /etc/network/interfaces you did change the gateway to 192.168.0.1 right? And you have to either restart the server or just the networking with:
sudo /etc/init.d/networking restart

so that the changes take effect.

---

### Post by SeijiSensei on 2012-11-15
It sounds to me like all you are missing is "masquerading" or "network address translation."  You've already taken care of the problem of enabling packet forwarding, but you don't seem to have a masquerading rule.  

I've lost track of which interface points to the Internet and which to the local network, but if eth0 points to the Internet, try adding this rule to iptables:

```
sudo iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to [your machine's external IP address]
```

replacing "[your machine's external IP address]" with the IP assigned to eth0.  That tells the computer to "masquerade" all traffic sent out the eth0 interface and pretend that the traffic is coming from this machine's externally-facing address.

If this works, add the command (without sudo) to /etc/rc.local so it will be run any time the machine boots up.

---

### Post by lestertorres on 2012-11-19
Thank you guys for all the help with everything! I was able to get the DHCP working with some configuring within my interfaces. I figured out how to get my subnet add and also did some changes in the dhcpd.conf file. Thanks you all a million! Darokod you are awesome. Now the my squid3 proxy is acting up but I can figure that out through some configuring. Thank you all again, you guys have no idea how grateful I am.

---

