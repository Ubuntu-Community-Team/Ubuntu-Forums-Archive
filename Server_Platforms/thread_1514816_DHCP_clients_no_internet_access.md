---
title: "DHCP clients no internet access"
date: 2010-06-21
forum: Server Platforms
---

### Post by Leppie on 2010-06-21
i must be very thick as i cannot seem to get my dhcp clients to connect to the internet properly.
on my lucid server i installed dhcp3 server and bind9, i can ping and dig all on the local network. on the clients however, as soon as i go out of the local network there's messages like "unknown host www.google.com" or "network is unreachable".

any ideas?

---

### Post by sanderj on 2010-06-21
On a client, open a terminal, run "mtr -n -r -c4 8.8.8.8" and post the output. 
After that, run "mtr -r -c4 8.8.8.8" (note the missing '-n') and post the output here.

Here's mine.

```

sander@quirinius:~$ mtr -n -r -c4 8.8.8.8
HOST: quirinius                   Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 192.168.2.254                 0.0%     4    1.6   1.8   1.3   2.9   0.7
  2. 192.168.1.254                 0.0%     4    3.7   4.0   3.0   6.3   1.5
  3. 82.169.22.54                  0.0%     4   30.4  29.0  26.4  31.5   2.3
  4. 195.69.144.247                0.0%     4   47.9  43.0  37.2  47.9   4.9
  5. 209.85.248.93                 0.0%     4   95.0  99.5  70.6 137.2  27.7
  6. 64.233.175.246                0.0%     4   44.0  40.5  34.5  48.9   7.1
  7. 72.14.239.199                 0.0%     4   62.3  44.4  32.7  62.3  13.6
  8. 209.85.255.126                0.0%     4   43.5  44.9  33.9  51.7   8.2
  9. 8.8.8.8                       0.0%     4   59.2  47.4  37.6  59.2  10.8
sander@quirinius:~$ 



```

---

### Post by Leppie on 2010-06-21
thanks for your help.
the results are very exciting...
```
mtr -n -r -c4 8.8.8.8
HOST: hfprod                     Loss%   Snt   Last   Avg  Best  Wrst StDev
```
and without the n switch:
```
mtr -r -c4 8.8.8.8
HOST: hfprod                     Loss%   Snt   Last   Avg  Best  Wrst StDev
```

---

### Post by sanderj on 2010-06-21
Aha. Show the output of 'ifconfig', 'ip addr show' and 'ip route show' to check wheter you have got an IP address (and routing) at all.

---

### Post by Leppie on 2010-06-21
Sander, bedankt voor het snelle reageren :)

here's the results:
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:2d:1e:21:dc  
          inet addr:192.168.33.71  Bcast:192.168.33.255  Mask:255.255.255.0
          inet6 addr: fe80::226:2dff:fe1e:21dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81214 (81.2 KB)  TX bytes:14120 (14.1 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:197 errors:0 dropped:0 overruns:0 frame:0
          TX packets:197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21734 (21.7 KB)  TX bytes:21734 (21.7 KB)
```
```
ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 00:26:2d:1e:21:dc brd ff:ff:ff:ff:ff:ff
    inet 192.168.33.71/24 brd 192.168.33.255 scope global eth0
    inet6 fe80::226:2dff:fe1e:21dc/64 scope link 
       valid_lft forever preferred_lft forever
3: vboxnet0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 0a:00:27:00:00:00 brd ff:ff:ff:ff:ff:ff
```
```
ip route show
192.168.33.0/24 dev eth0  proto kernel  scope link  src 192.168.33.71 
169.254.0.0/16 dev eth0  scope link  metric 1000 
```

---

### Post by sanderj on 2010-06-21
Your "ip route show" shows you have no 'default'-route, which is causing your problem. See mine below.

So, how to solve this? You can manually add a default route ("ip route add" or something like that), but it's more interesting and useful to get it right in the ... right way. So, check your DHCP *server*; it should tell the default gateway. The default gateway could be your modem/router/NAT, or the DHCP-server-machine itself if you do some kind of Internet Sharing via that machine.

BTW: Doesn't your modem/router do DHCP-server? 

```

sander@quirinius:~$ ip route show
192.168.2.0/24 dev wlan1  proto kernel  scope link  src 192.168.2.163  metric 2 
169.254.0.0/16 dev wlan1  scope link  metric 1000 
default via 192.168.2.254 dev wlan1  proto static 
sander@quirinius:~$ 

```

---

### Post by Leppie on 2010-06-21
> **sanderj said:**
> Your "ip route show" shows you have no 'default'-route, which is causing your problem. See mine below.

So, how to solve this? You can manually add a default route ("ip route add" or something like that), but it's more interesting and useful to get it right in the ... right way. So, check your DHCP *server*; it should tell the default gateway. The default gateway could be your modem/router/NAT, or the DHCP-server-machine itself if you do some kind of Internet Sharing via that machine.
all network traffic routes through the server which is the only machine with direct access (exept for my lappie which has wireless internet access through the adsl modem/router as well).
i have set the adsl modem/router (through which the server accesses the internet) in the global directives area in the dhcpd.conf:
```
option routers 192.168.2.1;
```i set this option in the subnet section as well.

> **sanderj said:**
> BTW: Doesn't your modem/router do DHCP-server?
it does, but it's connected to a different nic on the server and uses another network address.

---

### Post by Leppie on 2010-06-21
so, i'm one step further. i now get a default route after placing the lan nic as the router in the dhcpd.conf under the subnet section.
```
subnet 192.168.33.0 netmask 255.255.255.0 {
        option subnet-mask 255.255.255.0;
        option routers 192.168.33.1;       ##nic connected to lan
        range 192.168.33.130 192.168.33.140;
        }
```

and i do get a network address when trying to ping google.com from a clien machine, but after that, it just sits there and does nothing. after stopping pinging, results are 100% packet loss (surprise, surprise):
```
ping www.google.com
PING www.l.google.com (209.85.229.104) 56(84) bytes of data.
^C
--- www.l.google.com ping statistics ---
74 packets transmitted, 0 received, 100% packet loss, time 73577ms
```

---

### Post by sanderj on 2010-06-21
Run 'mtr -r -c4 [www.google.com](www.google.com)'

My guess is that your default gateway is not reachable / not functioning / not correct.

---

### Post by Leppie on 2010-06-21
indeed, the results are the same as before.
here's my setup:
internet <-> router 192.168.2.1 <-> 192.168.2.254 :server: 192.168.33.1 <-> lan

i've read several howto's for dhcp and they all state that the actual router should be set in the dhcpd.conf, but if i put "option router 192.168.2.1" the clients end up without default gateway.
and if i use the lan ip (which appears to be the only ip address with result that a gateway is assigned to the clients), it still doesn't do anything.

any ideas?

---

### Post by sanderj on 2010-06-21
from the client can you 'ping 192.168.33.1'?

---

### Post by Leppie on 2010-06-21
> **sanderj said:**
> from the client can you 'ping 192.168.33.1'?
yes, and i can even do a dig <network> axfr or ping other clients on the lan.
this is however very slow, it takes about 24 seconds to send and receive 4 packets...

---

### Post by sanderj on 2010-06-21
Well, run all command I gave, and post the output here, including "ip route show"

---

### Post by Leppie on 2010-06-21
here we go:
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:2d:1e:21:dc  
          inet addr:192.168.33.71  Bcast:192.168.33.255  Mask:255.255.255.0
          inet6 addr: fe80::226:2dff:fe1e:21dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17264 (17.2 KB)  TX bytes:11908 (11.9 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:197 errors:0 dropped:0 overruns:0 frame:0
          TX packets:197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21734 (21.7 KB)  TX bytes:21734 (21.7 KB)

```
```
ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 00:26:2d:1e:21:dc brd ff:ff:ff:ff:ff:ff
    inet 192.168.33.71/24 brd 192.168.33.255 scope global eth0
    inet6 fe80::226:2dff:fe1e:21dc/64 scope link 
       valid_lft forever preferred_lft forever
3: vboxnet0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 0a:00:27:00:00:00 brd ff:ff:ff:ff:ff:ff
```
```
ip route show
192.168.33.0/24 dev eth0  proto kernel  scope link  src 192.168.33.71 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.33.1 dev eth0  metric 100 
```

---

### Post by sanderj on 2010-06-21
> **Leppie said:**
> indeed, the results are the same as before.
here's my setup:
internet <-> router 192.168.2.1 <-> 192.168.2.254 :server: 192.168.33.1 <-> lan



Is your server doing NAT between the LANs?

If not: does your router know where the network 192.168.33 is? If not, you have a problem ...

---

### Post by Leppie on 2010-06-21
> **sanderj said:**
> Is your server doing NAT between the LANs?
most howto's state that only ip4 forwarding needs to be enabled in the sysctl.conf.

> **sanderj said:**
> If not: does your router know where the network 192.168.33 is? If not, you have a problem ...
fraid not... :(

please some advice?

---

### Post by sanderj on 2010-06-21
> **Leppie said:**
> most howto's state that only ip4 forwarding needs to be enabled in the sysctl.conf.


fraid not... :(

please some advice?

Probably easiest to do NAT on your Ubuntu server. See [http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874)

FYI: I've never done this myself.

---

### Post by Leppie on 2010-06-21
many thanks, the clients now have internet access :)
the only thing is that now i can no longer ping between the clients.

---

### Post by sanderj on 2010-06-21
> **Leppie said:**
> many thanks, the clients now have internet access :)
the only thing is that now i can no longer ping between the clients.

You now do NAT?

Which clients can't ping eachother? On the same LAN, you should be able to ping. Between the different LANs not, because the .33. LAN is not known on the main LAN *and* because you do NAT. ;-(

If you follow my signature, and do 'sudo apt-get install miredo' on the different machines, I expect you can ping6 between the LANs. Can you do that? I'm curious about the result.

---

### Post by Leppie on 2010-06-21
> **sanderj said:**
> You now do NAT?
yup, up and running :)

> **sanderj said:**
> Which clients can't ping eachother?
the clients on the lan (connected to the .33.0 network)

> **sanderj said:**
> On the same LAN, you should be able to ping. Between the different LANs not, because the .33. LAN is not known on the main LAN *and* because you do NAT. ;-(
yes, i know. that's what i find so weird...

> **sanderj said:**
> If you follow my signature, and do 'sudo apt-get install miredo' on the different machines, I expect you can ping6 between the LANs. Can you do that? I'm curious about the result.
since you helped me, i'm going to give it a try and post back :)

---

### Post by Leppie on 2010-06-21
so these are the results of the test page:
```
Let's check your IPv6 connectivity:

Check #1: OK, you have IPv6 network connectivity! Your IPv6 address is 2001:0:53aa:64c:1889:6937:a7fc:95f4. 

You have IPv6 via Teredo / Miredo. Teredo is built-in in Windows Vista and Windows 7.



Check #2: Congratulations: you have IPv6 name resolving, too. This means you have full IPv6 connectivity.



Done checking your IPv6 connectivity.
```

and the google page opens fine :)

---

### Post by sanderj on 2010-06-21
> **Leppie said:**
> so these are the results of the test page:
```
Let's check your IPv6 connectivity:

Check #1: OK, you have IPv6 network connectivity! Your IPv6 address is 2001:0:53aa:64c:1889:6937:a7fc:95f4. 

You have IPv6 via Teredo / Miredo. Teredo is built-in in Windows Vista and Windows 7.



Check #2: Congratulations: you have IPv6 name resolving, too. This means you have full IPv6 connectivity.



Done checking your IPv6 connectivity.
```

Good. If you install miredo (or teredo) on the other machines, you can ping6 between those machines using the IPv6 address ...

---

### Post by sanderj on 2010-06-21
> **Leppie said:**
> 
yes, i know. that's what i find so weird...


On second thought: you're right; you should be able to ping from the .33. LAN to the .2. LAN machines. 
Reason: from .33. to .2. the ping-packet will get NATed and will arrive with source IP address 192.168.2.254 on the .2. LAN. The .2. machine will then ping back 192.168.2.254, which will then NAT-forward it to the .33. LAN. 
Have you tried it in that direction.

The other way around won't work: if a .2. machine pings to 192.168.33.something, it will send that packet to the default gateway (=wrong direction), which does not know how to handle it and will drop it.
Maybe if the first setup works, you could add .33. subnet with default gateway 192.168.2.254, and it might work ...

Better: IPv6! ;-)

---

### Post by Leppie on 2010-06-21
well, apparently i just chose the wrong machine to ping from... it doesn't ping at all (neither ipv4 nor ipv6) while all other machines ping fine :)
something seems to be wrong in that machine's config.

many thanks for your help :)

---

### Post by sanderj on 2010-06-21
> **Leppie said:**
> 

many thanks for your help :)

Graag gedaan. Nu nog je IPv6 gaan gebruiken!

---

### Post by Leppie on 2010-06-21
zal ik zeker doen :)

---

