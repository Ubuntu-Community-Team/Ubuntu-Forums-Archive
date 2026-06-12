---
title: "DHCP is ok but I can't ping"
date: 2016-03-24
forum: Server Platforms
---

### Post by YaPaY on 2016-03-24
Server Ubuntu 12.04
ifconfig:
```
em1       Link encap:Ethernet  HWaddr 98:4b:e1:0c:7c:a2
          inet addr:172.30.14.6  Bcast:172.30.14.255  Mask:255.255.255.0
          inet6 addr: fe80::9a4b:e1ff:fe0c:7ca2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102281907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45958367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:140250565446 (140.2 GB)  TX bytes:12155339470 (12.1 GB)

em2       Link encap:Ethernet  HWaddr 98:4b:e1:0c:7c:a4
          inet addr:172.30.14.7  Bcast:172.30.14.255  Mask:255.255.255.0
          inet6 addr: fe80::9a4b:e1ff:fe0c:7ca4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:751294 (751.2 KB)  TX bytes:26432 (26.4 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:197 errors:0 dropped:0 overruns:0 frame:0
          TX packets:197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:70244 (70.2 KB)  TX bytes:70244 (70.2 KB)

```

/etc/dhcp/dhcpd.conf

```
# Sample /etc/dhcpd.conf
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 172.30.14.254;
option routers 172.30.14.1;
option domain-name-servers 62.2.17.60, 62.2.24.158;
option domain-name "mydomain.example";
subnet 172.30.14.0 netmask 255.255.255.0 {
    range 172.30.14.10 172.30.14.20;
}

```

/etc/network/interfaces
```
# Sample /etc/dhcpd.conf
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 172.30.14.254;
option routers 172.30.14.1;
option domain-name-servers 62.2.17.60, 62.2.24.158;
option domain-name "mydomain.example";
subnet 172.30.14.0 netmask 255.255.255.0 {
    range 172.30.14.10 172.30.14.20;
}

```

I have a device in network it took IP from em2(172.30.14.7) but I can'T ping this machine:
```
From 172.30.14.6 icmp_seq=16 Destination Host Unreachable
From 172.30.14.6 icmp_seq=17 Destination Host Unreachable
From 172.30.14.6 icmp_seq=18 Destination Host Unreachable
From 172.30.14.6 icmp_seq=19 Destination Host Unreachable
From 172.30.14.6 icmp_seq=20 Destination Host Unreachable
From 172.30.14.6 icmp_seq=21 Destination Host Unreachable
From 172.30.14.6 icmp_seq=22 Destination Host Unreachable

```

What is the problem?

---

### Post by darkod on 2016-03-24
Firewall? Make sure the clients have no firewall enabled (for example in windows it is enabled by default and it does block the ping).

Also, you have both em1 and em2 in the same subnet. It shouldn't be a problem but in general I avoid such connections that seem unnecessary. You use two interfaces for connections to different subnets. For one subnet one interface is enough. Try without em2.

---

### Post by YaPaY on 2016-03-25
fw is out of option. I didnt understand try without em2.

---

### Post by darkod on 2016-03-25
You have connected both interfaces of the server to the same subnet (their IPs are 172.30.14.6 and 172.30.14.7). Why? There is no need to make multiple connections to the same network unless doing teaming or similar.

Like this you can create a situation of traffic going in and out on different interfaces which could lead to unexpected behavior. Disconnect em2 temporarily and try using only em1. If there are no applications using em2 specifically and even if there are, set them to use em1.

Also, does it work as expected from the client side? From the client can you ping the gateway 172.30.14.1 or the server em1 or em2 interfaces? Does internet (routing) work on the client?

---

### Post by darkod on 2016-03-25
Looking at your dhcpd.conf, remove the line 'option broadcast-address'. I don't think it's necessary, plus I think it might be wrong. For a netmask of 255.255.255.0 if I'm not mistaken the network address ends in .0 and the broadcast in .255. That might be giving you issues because you are sending broadcast of .254 to clients.

And usually these days there is no need to specify either network or broadcast IPs. They are all calculated automatically from the netmask. So try disabling that option, renew the dhcp lease from the client side (to receive the new settings lease) and try again.

Keep it simple and keep it at minimum. I have done dhcp with dnsmasq and never used broadcast options.

---

### Post by YaPaY on 2016-03-25
> **darkod said:**
> Disconnect em2 temporarily and try using only em1. If there are no applications using em2 specifically and even if there are, set them to use em1.

Also, does it work as expected from the client side? From the client can you ping the gateway 172.30.14.1 or the server em1 or em2 interfaces? Does internet (routing) work on the client?

In network I have got a linux machine. It has got two network adapter and eth0 is dhcp enabled. In my network structure I havent got router/switch. My first priority to give internet access to this machine but first of all I should connect it to server via em2. My server em1 is for access internet. In short I am forcing to server to work with as a router. 

Second question is no, I can'T ping to server from Linux machine either. I will try to remove broadcast option. thanks

edit: removing broadcast didn't help

---

### Post by darkod on 2016-03-25
Hold on, if you want this server to do routing then the setup is wrong...

Do you also control the 172.30.14.1 gateway/router, is it yours or it's an ISP or shared router? Because if it's on the ISP end or shared you can't be adding up dhcp ranges in the same 172.30.14.x subnet. It can mess up things for other users too if it goes out the em1 interface.

Then... I understand you don't have a router to use and you are trying to use your server as router, but if you don't even have a switch how do you plan to connect all the clients and create a network? Or you do have a simple switch? I assume you must have something like that...

If only your server can be connected to the internet from 172.30.14.1 then the first step is to configure the network correctly on em1 and make sure internet is working on the server itself. I assume this is done, and you can use the internet, apt-get etc.

Then on the em2 interface you need a different subnet, not the same as em1. For example, set up em2 to be 10.10.10.1. In your /etc/network/interface the part for em2 would be something like:
```
auto em2
iface em2 inet static
   address 10.10.10.1
   netmask 255.255.255.0
```

That should be enough.
Then modify the dhcpd.conf to issue the range 10.10.10.100-10.10.10.150 for example (depending how many clients you want to support), and the option routers should be 10.10.10.1 (the em2 of the server). That way the clients receiving the leases will use the server as GW. Also make sure the dhcp is issued only on em2, not on em1.

You also need modifications on the server to allow packet forwarding. I assume there is no firewall active on the server, right? You need to edit the /etc/sysctl.conf file and enable the option:
```
net.ipv4.ip_forward=1
```

That is the option allowing forwarding. Save and close the file.

You also need masquerading with iptables (NAT):
```
sudo iptables -t nat -A POSTROUTING -o em1 -s 10.10.10.0/24 -j MASQUERADE
```

After that renew the lease on the client, and test ping to 10.10.10.1, 8.8.8.8 and google.com. Post the results...

---

### Post by YaPaY on 2016-03-25
I will try it these settings but problem is my server doesn't get default gw (I added it to /etc/network/interfaces but it doesn't work) after restart/restart network and I should give this command every time after boot:

route add default gw 172.30.14.1

otherwise I can't access it from ssh/web and I should go physically to enter this command :(

If I server goes down my customers can't access the service for a few days. It would make really headache for me.

edit: I maked your suggestions and start dhcp. I didn't need the network service restart.

ifconfig:
```
em1       Link encap:Ethernet  HWaddr 98:4b:e1:0c:7c:a2
          inet addr:172.30.14.6  Bcast:172.30.14.255  Mask:255.255.255.0
          inet6 addr: fe80::9a4b:e1ff:fe0c:7ca2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:398582220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153174762 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:582648634525 (582.6 GB)  TX bytes:22084873149 (22.0 GB)

em2       Link encap:Ethernet  HWaddr 98:4b:e1:0c:7c:a4
          inet addr:10.10.10.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::9a4b:e1ff:fe0c:7ca4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:895 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:63484 (63.4 KB)  TX bytes:73422 (73.4 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:494246 (494.2 KB)  TX bytes:494246 (494.2 KB)

```

var/log/syslog
```
Mar 25 18:45:07 transcode01-ubuntu-server dhcpd: DHCPREQUEST for 172.30.14.12 from 00:22:ab:80:17:59 via em2
Mar 25 18:45:07 transcode01-ubuntu-server dhcpd: DHCPACK on 172.30.14.12 to 00:22:ab:80:17:59 via em2
Mar 25 18:45:18 transcode01-ubuntu-server dhcpd: DHCPREQUEST for 172.30.14.12 from 00:22:ab:80:17:59 via em2
Mar 25 18:45:18 transcode01-ubuntu-server dhcpd: DHCPACK on 172.30.14.12 to 00:22:ab:80:17:59 via em2
Mar 25 18:45:32 transcode01-ubuntu-server dhcpd: DHCPREQUEST for 172.30.14.12 from 00:22:ab:80:17:59 via em2
Mar 25 18:45:32 transcode01-ubuntu-server dhcpd: DHCPACK on 172.30.14.12 to 00:22:ab:80:17:59 via em2
Mar 25 18:45:39 transcode01-ubuntu-server dhcpd: DHCPREQUEST for 172.30.14.12 from 00:22:ab:80:17:59 via em2
Mar 25 18:45:39 transcode01-ubuntu-server dhcpd: DHCPACK on 172.30.14.12 to 00:22:ab:80:17:59 via em2
Mar 25 18:45:39 transcode01-ubuntu-server dhcpd: message repeated 5 times: [ DHCPREQUEST for 172.30.14.12 from 00:22:ab:80:17:59 via em2: unknown lease 172.30.14.12.]
Mar 25 18:45:50 transcode01-ubuntu-server dhcpd: DHCPDISCOVER from 00:22:ab:80:17:59 via em2
Mar 25 18:45:50 transcode01-ubuntu-server dhcpd: DHCPDISCOVER from 00:22:ab:80:17:59 via em2
Mar 25 18:45:50 transcode01-ubuntu-server dhcpd: DHCPOFFER on 172.30.14.12 to 00:22:ab:80:17:59 via em2
Mar 25 18:45:50 transcode01-ubuntu-server dhcpd: DHCPREQUEST for 172.30.14.12 (172.30.14.7) from 00:22:ab:80:17:59 via em2: ignored (not authoritative).
Mar 25 18:45:50 transcode01-ubuntu-server dhcpd: DHCPREQUEST for 172.30.14.12 (172.30.14.7) from 00:22:ab:80:17:59 via em2
Mar 25 18:45:50 transcode01-ubuntu-server dhcpd: DHCPACK on 172.30.14.12 to 00:22:ab:80:17:59 via em2
Mar 25 18:45:51 transcode01-ubuntu-server dhcpd: DHCPOFFER on 10.10.10.100 to 00:22:ab:80:17:59 via em2

```

dhcpd.conf

```
# Sample /etc/dhcpd.conf
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option routers 10.10.10.1;
option domain-name "mydomain.example";
subnet 10.10.10.0 netmask 255.255.255.0 {
    range 10.10.10.100 10.10.10.105;
}


```

It seems my linux machine can't get IP from DHCP (I don'T know the reason)

---

### Post by darkod on 2016-03-25
So, you have multiple issues.

You need to sort out why the gateway setting is not working. But ifconfig does not show all details of the network setup, please post the output of:
```
cat /etc/network/interfaces
```

That will show your network config.

After doing the change in /etc/sysctl.conf you do need to restart the server, before the change is active. So you better do it, it might help with the dhcp issues too.

Then on the client side you need to double check why it does not receive automatic IP by dhcp. Make sure the network setting is to use dhcp (not manual/static address), and also make sure you have connected the clients and the server em2 interface correctly in the same local network, in the same switch, etc, depending how you have the network connected.

In that last /var/log/syslog entry you can see the server started to offer dhcp using the new subnet, so from server side it looks like OK. If you want to wait with rebooting the server until you verify the network settings, post the /etc/network/interfaces content first so we can take a look.

---

### Post by YaPaY on 2016-03-25
etc/network/interfaces:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto em1
iface em1 inet static
address 172.30.14.6
gateway 172.30.14.1
netmask 255.255.255.0
network 172.30.14.0
broadcast 172.30.14.255
dns-nameservers 62.2.17.60
dns-nameservers 62.2.24.158

auto em2
iface em2 inet static
address 10.10.10.1
netmask 255.255.255.0

```

 Ihaven't got any file as /etc/sysctl.conf

Client have got DHCP and connected via directly with cat5e to server em2. I haven't got any switch.

---

### Post by darkod on 2016-03-25
The config for em1 looks correct but if it doesn't work you need to discuss it with the administrator of that network. Is the 172.30.14.6 assigned to you by the admin? You can't simply select IP and use it, so I assume someone told you how to set it up and which IP to use...

You can't connect the client directly to em2, at least not with standard network (patch) cable. Standard network cables are straight and are designed to be used with switches. To connect two computers directly you would need a cross-over network cable. That's why the client is not receiving the dhcp correctly.

If you plan to use more clients you need a switch anyway, so maybe go and buy a simply cheaper switch.

Or if you plan to use only one client then you don't need a dhcp server at all, just set static IP on the client too. But you will need to connect with cross-over cable for that...

Ubuntu Server does have /etc/sysctl.conf by default. You should have it.

---

### Post by YaPaY on 2016-03-25
yes i think you are right. I need a simple 5 port gigabit switch. Without this everything being complicated. 172.130.14.6 assigned from the Administrator. He gave me only the gw, internal IP, dns, etc. I configured my server according to the them. Thanks for your help. I think a switch would make things easier.

---

### Post by MAFoElffen on 2016-03-27
> **YaPaY said:**
> etc/network/interfaces:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto em1
iface em1 inet static
address 172.30.14.6
gateway 172.30.14.1
netmask 255.255.255.0
network 172.30.14.0
broadcast 172.30.14.255
dns-nameservers 62.2.17.60
dns-nameservers 62.2.24.158

auto em2
iface em2 inet static
address 10.10.10.1
netmask 255.255.255.0

```

 Ihaven't got any file as /etc/sysctl.conf

[COLOR=#ff0000]Client have got DHCP and connected via directly with cat5e to server em2. [/COLOR][COLOR=#ff0000]I haven't got any switch.[/COLOR]
About what I have highlighted-- Please described your network in your own terms.

You say you have 10.10.10.0 and 172.30.14.0 as NID's???

- What is your router that is making the jump from one NID to another?

*** You say you have to machines directly connected to each other without a switch (an adhoc network > directly connected with a "straight" (normal) Ethernet cable... That will not work. If you want to wired to machines directly to each other, or two high-end routers together, then you must use a cross-over Ethernet cable. That means that the transmit (out) needs to go to a receive (in) connections. A crossover cable will make that work. But a cross-over cable is not something you can buy in a computer store. We usually have to make them ourselves. Otherwise, you need to connect a cable from each machine, to a switch, which will make those physically converted connections for you.

*** In an adhoc network, there is no gateway present. That is only a physical connection with a port assigned as that address. You can only go from one end to the other, unless you have a router setup on one of those machines via a router table "default hop" or "other." Both sides of the adhoc network have to have static settings (unless the host side of that network has dhcp server setup for that adhoc network to support the settings of that one directly connected client. (I doubt you did that...) If you set a default hop between NID's in one machine, between the adhoc and the main NID, then the other side of the adhoc network can use that other end as a gateway... But you have no "physical connection" yet.

Note: The way you have 10.10.10.1 set up... 10.x.x.x is a class A address. that would normally be an NID of 10.0.0.0, with mask of 255.0.0.0. (/8)You have it subnetted as 10.10.10.0 with a subnet of 255.255.255.0 (/24) ... Did you mean to subnet it that way?

It is easier if darkod has all the info laid out, so he can advise you have to make what you have work. Things are possible, if we know what we are working with.

---

### Post by YaPaY on 2016-04-07
I got a router and configured according to the my first post (Select Static-IP= 172.30.14.6 + DNS + GW=172.30.14.1 ) and my router connected to the Internet. After that I setup all my machines to DHCP. I checked it, every machine in network has IP with 192.168 and can connect to internet. That was the first part. After that I setup for port forwarding for my first server. It has got a special web based program which works on port 8000. I tested it and it was working. The last thing was the eaisest and latest part. my second server has apache which works on port 80, and for the telnet 22 I have opened but the port forwarding for this second machine didn't work. Putty, apache, etc. I setup this server as DMZ to be sure but DMZ didn't work for this machine either.

any idea would be great

---

### Post by darkod on 2016-04-07
Make sure you are forwarding to the correct 192.168 address of the second server. Also are you sure the ports are forwarded to your router by the previous router?

Since you have private IP of 172.30.14.6 on the router, that means there is another router in front with 172.30.14.1. Maybe when port 80 arrives on this router it forwards it somewhere else, not to your router?

When your router is directly on the internet and has a public IP, you can be sure that all traffic sent to that IP is arriving to your router.
When your router is in a chain with previous routers, you can't know which traffic exactly is arriving to your router unless you have the data of the previous router setup.

---

### Post by YaPaY on 2016-04-07
I think there is a front router before. I can use the system according to below rules without my router.

currently:
server1: 8000,22 (172.30.14.6)
server2: 80 (172.30.14.7)

I have been requested this port forwarding from my datacenter. They have set them

I connected my router and set dhcp for server and server 2
I setup my router 172.30.14.6) internet ok
server 1: port forwarded to 8000 and 22: pfor and internet ok IP (192.168.1.30)
server 2: port forwarded to 80: pfor is not ok but internet ok (192.168.1.27) I setup this machine to DMZ but It didn't work. After many hours I have been decided that router doesn't work properly but you mean if somebody make some port forwarding before my router would some problems occur.

I will ask to cancel my pfor from my datacenter but as a router IP (172.30.14.6) is ok? what do you mean?

---

### Post by darkod on 2016-04-07
Has the DC confirmed they can forward port 80 just for you to your router? You need to check that because that is a well known port and if they have other clients sharing the same networking infrastructure they can't forward 80 just to you. In fact they shouldn't even be offering services if you can't get a public IP for your router. Otherwise with sharing with other customers, where is the traffic going to?

Can you set your app/web to work on custom port, like you have port 8000 on the other server? In that case they should be able to forward this custom port to your router without problems, and you only need to add a rule for the same port on your router. Like you did for 8000.

Also you have to think about port 22 and ssh access. If your both servers work on 22 then your router has no way of knowing which you want to access. You need either to set ssh to different ports, of a forwarding rule that will switch custom incoming port to outgoing port 22. That way you can access one server on one custom port and the other on another...

---

### Post by YaPaY on 2016-04-08
> **darkod said:**
> Has the DC confirmed they can forward port 80 just for you to your router? You need to check that because that is a well known port and if they have other clients sharing the same networking infrastructure they can't forward 80 just to you. In fact they shouldn't even be offering services if you can't get a public IP for your router. Otherwise with sharing with other customers, where is the traffic going to?



port 80 has been forwarded only for me. I don't know what kind of network infrastructure is there. Every customer has got own portforw rules. I asked the cancel from dc to disable allf of my porfor rules to disable. I will check again

---

### Post by darkod on 2016-04-08
But if they disable all pfor rules then no traffic destined for your servers will arrive at your router. If your router is not directly on the internet with public IP, the previous router need to do pfor to it so that the traffic can reach it. And also those ports need to be open in their firewalls (if they have any).

---

