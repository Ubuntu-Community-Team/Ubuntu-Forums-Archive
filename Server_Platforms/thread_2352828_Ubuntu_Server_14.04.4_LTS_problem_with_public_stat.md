---
title: "Ubuntu Server 14.04.4 LTS problem with public static ip"
date: 2017-02-16
forum: Server Platforms
---

### Post by poliman-pl on 2017-02-16
I have server based on Ubuntu Server which has four network cards - from em1 to em4. In /etc/network/interfaces I put:
```
auto em1 em4
iface em1 inet static
        address 192.168.100.202
        network 192.168.100.0
        netmask 255.255.255.0
        broadcast 192.168.100.255
        gateway 192.168.100.2               #not sure that here should be gateway if below is another gateway, this is local router in company
        dns-nameservers 192.168.100.2

#values provided by isp
iface em4 inet static
        address 31.X.X.180
        network 31.X.X.176
        netmask 255.255.255.248
        gateway 31.X.X.177             #not sure that here should be gateway if above is another gateway
        dns-nameservers 193.106.244.10 193.106.244.20
``` [HR][/HR]**ifconfig command output:**
```
em1       Link encap:Ethernet  HWaddr d8:9d:67:2a:c9:18
          inet addr:192.168.100.202  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::da9d:67ff:fe2a:c918/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19310863 errors:0 dropped:1942387 overruns:0 frame:0
          TX packets:1929148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3446416045 (3.4 GB)  TX bytes:1699818696 (1.6 GB)
          Interrupt:59

em2       Link encap:Ethernet  HWaddr d8:9d:67:2a:c9:19
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:126662 (126.6 KB)  TX bytes:8408 (8.4 KB)
          Interrupt:60

em4       Link encap:Ethernet  HWaddr d8:9d:67:2a:c9:1b
          inet addr:31.X.X.180  Bcast:31.X.X.183  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:330135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20027 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:78394465 (78.3 MB)  TX bytes:2429561 (2.4 MB)
          Interrupt:60

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:270476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:85851060 (85.8 MB)  TX bytes:85851060 (85.8 MB)
```

[HR][/HR]**ip link show command output:**
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: em1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether d8:9d:67:2a:c9:18 brd ff:ff:ff:ff:ff:ff
3: em2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN mode DEFAULT group default qlen 1000
    link/ether d8:9d:67:2a:c9:19 brd ff:ff:ff:ff:ff:ff
4: em3: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether d8:9d:67:2a:c9:1a brd ff:ff:ff:ff:ff:ff
5: em4: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether d8:9d:67:2a:c9:1b brd ff:ff:ff:ff:ff:ff
```

[HR][/HR]**route command output:**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default           router            0.0.0.0           UG    0        0       0    em1
31.X.X.176      *               255.255.255.248 U      0       0        0    em4
192.168.100.0  *               255.255.255.0    U     0        0        0    em1
``` [HR][/HR]**route -n command output:**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0          192.168.100.2   0.0.0.0          UG    0      0        0     em1
31.X.X.176     0.0.0.0         255.255.255.248 U     0      0        0     em4
192.168.100.0   0.0.0.0         255.255.255.0  U     0      0        0     em1
``` [HR][/HR]**ufw status command output:**
```
Status: inactive
``` [HR][/HR]**tracert command output (from windows host from outside network):**
```
tracert 31.X.X.180

Tracing route to 31-X-X-180.noc.fibertech.net.pl [31.X.X.180]
over a maximum of 30 hops:

  1    <1 ms    <1 ms    <1 ms  192.168.101.1
  2     4 ms     3 ms     2 ms  1.1.1.1
  3     5 ms     7 ms     5 ms  host17201.internet-examps.pl [93.X.X.123]
  4    12 ms    10 ms    11 ms  vc3s.pl [89.25.159.158]
  5    11 ms    11 ms    11 ms  31-X-X-22.net.pl [31.X.X.22]
  6     *        *        *     Request timed out.
  7     *        *        *     Request timed out.
  8     *        *        *     Request timed out.
```

other steps like 6,7,8 until 30.
[HR][/HR]**ping command output (from windows host outside network):**
```
C:\Users\poli003>ping 31.X.X.180

Pinging 31.X.X.180 with 32 bytes of data:
Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 31.X.X.180:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),
```


[HR][/HR]And finally my problem (I suppose You know what's going on):
Server has local ip address and public ip address. But this public ip is not reachable in network. I can't ping this address, put this ip in web browser should show login panel but this not happen. Firewall (ufw) is disabled at the moment until I resolve this problem. Routes which show route command are default. What is configured wrong? Besides I have no idea why ifconfig command output shows em1, em2, em4 and lo if I have configured only em1, em4 and loopback. When I am logged via ssh to the server and ping this public ip I got output:

```
PING 31.X.X.180 (31.X.X.180) 56(84) bytes of data.
64 bytes from 31.X.X.180: icmp_seq=1 ttl=64 time=0.032 ms
64 bytes from 31.X.X.180: icmp_seq=2 ttl=64 time=0.033 ms
64 bytes from 31.X.X.180: icmp_seq=3 ttl=64 time=0.033 ms
^C
--- 31.X.X.180 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.032/0.032/0.033/0.006 ms
```


_If any more informations You need - say._

---

### Post by wildmanne39 on 2017-02-16
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by darkod on 2017-02-16
From em1 remove the gateway, usually you would put only one gateway and in this case it would be on your external interface.

About dns-nameservers I haven't used them on two interfaces so I don't know how it reacts. What I would do is decide first which dns you want to use, your internal or the ISP dns. Note that ISP dns will probably not have any internal records you have on your internal dns.

Regardless which dns you decide to use, I would configure it on em4 which can be considered your primary interface. Doesn't matter if the dns server is outside or inside, it is only an IP.

Reboot the server after these changes and test in this order:
```
ping 8.8.8.8   #shows you if you have routing towards internet
ping google.com   #shows you if dns is working correctly
```

Let us know how it goes...

---

### Post by poliman-pl on 2017-02-16
Should server be rebooted or just restart networking service would be enough?

---

### Post by darkod on 2017-02-16
Restarting the service should be OK. But I have seen cases where it says it can't restart it, if that happens I don't know if you have other options except reboot.

---

### Post by poliman-pl on 2017-02-17
Ok I will check this option. Problem is that I will have a problem with restart production server which is used almost 24/7. :/ maybe sudo ifdown interface_name && sudo ifup int_name. On another forum somebody suggested me that it can be firewall but ufw is inactive. Can be something in iptables?
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


```

And why I have 4 interfaces (lo, em1, em2, em4) in ifconfig but only 3 configured in /etc/network/interfaces (lo, em1, em4) and what is this line "auto em1 em4" (here /etc/network/interfaces)?

---

### Post by poliman-pl on 2017-02-17
> **darkod said:**
> From em1 remove the gateway, usually you would put only one gateway and in this case it would be on your external interface.

About dns-nameservers I haven't used them on two interfaces so I don't know how it reacts. What I would do is decide first which dns you want to use, your internal or the ISP dns. Note that ISP dns will probably not have any internal records you have on your internal dns.

Regardless which dns you decide to use, I would configure it on em4 which can be considered your primary interface. Doesn't matter if the dns server is outside or inside, it is only an IP.

Reboot the server after these changes and test in this order:
```
ping 8.8.8.8   #shows you if you have routing towards internet
ping google.com   #shows you if dns is working correctly
```

Let us know how it goes...

Tested above pings and they are working. But still nothing with ping external ip on em4 interface.

PS
Tracert from external windows host to gateway 31.X.X.177 is going well (it was working and this same is after change gateway and dns - so this is just one more information, which should be in my first post):
```

C:\Users\poli003>tracert 31.X.X186.177

Tracing route to 31-X-X-177.noc.fibertech.net.pl [31.172.186.177]
over a maximum of 30 hops:

  1    <1 ms     1 ms    <1 ms  192.168.101.1
  2     4 ms     3 ms     4 ms  1.1.1.1
  3     7 ms     4 ms     4 ms  host901c.3s.pl [93.179.192.201]
  4    12 ms    14 ms    11 ms  vc3s.pl [89.25.159.158]
  5    12 ms    13 ms    10 ms  31-X-X-177.net.pl [31.X.X.177]

Trace complete.

```

---

### Post by darkod on 2017-02-17
The auto is used for automatically bringing interfaces up during boot. If you also have auto em2 somewhere in /etc/network/interfaces that could show it in ifconfig even when you have no IP set up on it. Otherwise I have no idea why it shows up, but don't worry about it anyway, it's nothing bad.

If you have the external IP working now, and consider this solved please mark the thread as solved. You can do that in Thread Tools above the first post.

---

### Post by poliman-pl on 2017-02-17
> **darkod said:**
> The auto is used for automatically bringing  interfaces up during boot. If you also have auto em2 somewhere in  /etc/network/interfaces that could show it in ifconfig even when you  have no IP set up on it. Otherwise I have no idea why it shows up, but  don't worry about it anyway, it's nothing bad.

If you have the external IP working now, and consider this solved please  mark the thread as solved. You can do that in Thread Tools above the  first post.

No, this is not solved. I still can't ping external IP of the server. I can ping only gateway like I could. I added information about ping to gateway to provide more informations about situation. ;) And I have anywhere line auto em2. Very strange thing.

Below I attach next information from console:
[B]ip route command output:
[/B]```

default via 192.168.100.2 dev em1
31.X.X.176/29 dev em4  proto kernel  scope link  src 31.X.X.180
192.168.100.0/24 dev em1  proto kernel  scope link  src 192.168.100.202

```

In /etc/resolv.conf file I have:
nameserver 192.168.100.2

---

### Post by darkod on 2017-02-17
Why is the default route via em1? Did you leave the GW configured on the private or public interface? It seems like the private, and I thought you wanted it the other way around...

Why having a public IP unless using it as default route?

PS. The external ping to the server might be blocked by a FW on the router/gateway. In fact this is the preferred why. Do you want ping active for your public IP? Usually that's blocked by FW and it's best to be blocked. You will have many people attacking your public IP, no need to leave ping enabled for them.

---

### Post by poliman-pl on 2017-02-17
All routes are default. I didn't change anything there. I left GW configured on em4 interface which is public but You have right it seems like private. Before I setup this external IP address on Linux Server it was on Windows host (win 10 pro) and works well so I think firewall on the router/gateway not block traffic. Unfortunatelly I have to have public ip visible in network. Boss need access (to web application on the server) from home via web browser like before on Windows host.


EDIT
I decided to restart this server and funy thing happen. In /etc/network/interfaces on em1 interface I commented out GW and both DNS servers like below:
```
auto em1 em4
iface em1 inet static
        address 192.168.100.202
        network 192.168.100.0
        netmask 255.255.255.0
        broadcast 192.168.100.255
        #gateway 192.168.100.2
        #dns-nameservers 192.168.100.2

#values provided by isp
iface em4 inet static
        address 31.X.X.180
        network 31.X.X.176
        netmask 255.255.255.248
        gateway 31.X.X.177
        dns-nameservers 193.106.244.10 193.106.244.20


```
 
Ping 8.8.8.8 was't working and this same ping google.com. So probably ip route command shows proper GW - local router 192.168.100.2 - when is commented, server can't ping ip addres and domain name. Of course I still can't ping public ip of the server (from remote windows host).

---

### Post by poliman-pl on 2017-03-14
I resolved my problem by adding in console:
```
route add default gw 31.X.X.180
```

But how make this permanent after restart server? And how remove additional gateway which is ip 192.168.100.2?

---

### Post by darkod on 2017-03-14
Hmmm but that command would add .180 as a default GW and according to your network setup, you want .177 to be the default GW.

It is strange if it works like this. Are you sure all of it works, not just some traffic? Maybe later you will find traffic that is not routed correctly.

---

### Post by poliman-pl on 2017-03-14
.180 is network interface which is connected to public ISP network. I thought that by this interface packets go outside. I didn't check gw .177 address. And yes - I can login to web application when I put public ip address of the server (public interface) to web browser. But how make this permanent after restart server? And how remove additional gateway which is ip 192.168.100.2?

---

### Post by darkod on 2017-03-14
You have the other gateway commented out so it shouldn't apply. Can you post the output of:
```
route -n
```

For making a route permanent you can put it in /etc/network/interfaces too but with little different syntax compared to the command line. I don't remember the exact syntax now, you can google it.

Something continues to be very strange with your config/networking. It was supposed to work earlier and it didn't. And if 192.168.100.2 is still showing up as GW, it should not happen. When things are not acting like they should you should find the reason even if you think adding a static route helped you. It is better to search now then later after the server is in production and you start seeing problems.

PS. Yes, .180 is the public IP on your server ext interface, but in the route add command you usually specify the IP of the gateway where the traffic should go to, not the IP of your network card. That's why it looks strange to me.

PPS. Also, did you ever reboot the server when doing these changes or you are only trying to restart the networking service?

---

### Post by poliman-pl on 2017-03-14
route -n output:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         31.X.X.180  0.0.0.0         UG    0      0        0 em4
0.0.0.0          192.168.100.2   0.0.0.0          UG    0      0        0     em1
31.X.X.176     0.0.0.0         255.255.255.248 U     0      0        0     em4
192.168.100.0   0.0.0.0         255.255.255.0  U     0      0        0     em1
```

cat /etc/network/interfaces output:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto em1 em4
iface em1 inet static
        address 192.168.100.202
        network 192.168.100.0
        netmask 255.255.255.0
        broadcast 192.168.100.255
        #gateway 192.168.100.2
        #dns-nameservers 192.168.100.2

iface em4 inet static
        address 31.X.X.180
        network 31.X.X.176
        netmask 255.255.255.248
        gateway 31.X.X.177
        dns-nameservers 193.106.244.10 193.106.244.20
```

I didn't restart the server, because I don't know how to make permanent this setting. But after done 'route add' I can ping public ip address of the server etc.

---

### Post by darkod on 2017-03-14
Can you access it on the private interface? If you can, even if you lose connectivity on the public one you can still access it on the private interface and add the route manually.

If you haven't restarted and have been doing a number of changes to the network setup, you might get confusing results and not being sure what the current status is.

Is this a remote server or at your office?

I would restart it, but first make sure you have a way to reach it, either on public or private interface. For example the route -n still shows 192.168.100.2 as GW too, and it shouldn't. But just modifying the /etc/network/interfaces file doesn't help much if you never restarted. On restart the new networking settings will be applied. The public interface might work without adding any route, you have to try. If it is set up correctly according to the provider data, the public interface should work as it is without needing any static routes.

---

### Post by poliman-pl on 2017-03-15
I can access the server on private and public interface. This server is at client office not remote. I only have done three changes:
- commented default gw and dns servers on em1 (local) interface
- uncommented default gw and dns server on public interface em4
- execute command route add default gw 31.X.X.180

I have a problem with restarting it in any time, because this is my client server and it's in his office.

---

### Post by darkod on 2017-03-15
The window for restarting the server is between you and your client to decide.

I only want to point out that looking at your /etc/network/interfaces makes little sense if you have never restarted after making changes to it. That's why the private GW is still listed in route -n and the public GW was not until you added it manually. It should have been the opposite but if the server was never restarted then the current network settings in /etc/network/interfaces were never applied.

---

### Post by poliman-pl on 2017-03-15
Public GW have never been listed until I added it manually. After changes I have done restart networking.

---

### Post by darkod on 2017-03-15
When you restarted the networking service there were no errors reported right?

Sometimes I have seen that there are problems restarting the service and the server restart always works.

Can you post the output of the service restart?

According to the info in the route output, something is definitely not working correctly. You don't have any GUI installed on this server, it is command line only, right?

---

### Post by poliman-pl on 2017-03-15
There were no errors. I did /etc/init.d/networking/restart. I try provide output of the service restart. Not today but I hope it will be until friday.

---

