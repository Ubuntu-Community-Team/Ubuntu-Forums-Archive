---
title: "Internet sharing the hardway :("
date: 2006-08-28
forum: Server Platforms
---

### Post by ashrack on 2006-08-28
I've installed DAPPER SERVER here.
And on it I installed DNSMASQ which assigns the IP to a client computer.
But I would also like the client computer to have unrestrictet internet access. Meaning no PORTS are firewalled.
So I've install IPMASQ which took care of that problem. But latter found out that internet access was restricted. ANd thus I could not get HIGH ID in emule, and MSN Messenger wont connect to it,etc

So what must I do to get unrestricted InternetSharing??

ps. I also tried the following:
```
/etc/init.d/ipmasq stop
iptables -F -t nat
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
echo 1 >/proc/sys/net/ipv4/ip_forward
```
which I got from this site:
[https://help.ubuntu.com/ubuntu/serverguide/C/firewall-configuration.html](https://help.ubuntu.com/ubuntu/serverguide/C/firewall-configuration.html)
But then the internetsharing didnt even work on the client computer.

Here's my ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:08:A1:75:1C:87
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe75:1c87/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4806 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:542416 (529.7 KiB)  TX bytes:2041535 (1.9 MiB)
          Interrupt:10 Base address:0xe400

eth1      Link encap:Ethernet  HWaddr 00:08:A1:0E:0A:F9
          inet6 addr: fe80::208:a1ff:fe0e:af9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13032 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10599183 (10.1 MiB)  TX bytes:1710600 (1.6 MiB)
          Interrupt:3 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4820 (4.7 KiB)  TX bytes:4820 (4.7 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:193.77.18.232  P-t-P:213.250.19.90  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:12996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:10275701 (9.7 MiB)  TX bytes:1421921 (1.3 MiB)

```

---

### Post by ashrack on 2006-08-28
I've disabled IPV6, removed IPMASQ rebooted LINUX and then pasted this line into terminal:
```
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
```
and the net started working on the client machine:) Tanx M8

Now another big questions is, how do I make this permenant, so I wont have to paste the same line everytime I reboot linux??

---

### Post by Woei on 2006-08-28
> **ashrack said:**
> I've installed DAPPER SERVER here.
And on it I installed DNSMASQ which assigns the IP to a client computer.
But I would also like the client computer to have unrestrictet internet access. Meaning no PORTS are firewalled.
So I've install IPMASQ which took care of that problem. But latter found out that internet access was restricted. ANd thus I could not get HIGH ID in emule, and MSN Messenger wont connect to it,etc

So what must I do to get unrestricted InternetSharing??

ps. I also tried the following:
```
/etc/init.d/ipmasq stop
iptables -F -t nat
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
echo 1 >/proc/sys/net/ipv4/ip_forward
```
which I got from this site:
[https://help.ubuntu.com/ubuntu/serverguide/C/firewall-configuration.html](https://help.ubuntu.com/ubuntu/serverguide/C/firewall-configuration.html)
But then the internetsharing didnt even work on the client computer.

Here's my ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:08:A1:75:1C:87
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe75:1c87/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4806 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:542416 (529.7 KiB)  TX bytes:2041535 (1.9 MiB)
          Interrupt:10 Base address:0xe400

eth1      Link encap:Ethernet  HWaddr 00:08:A1:0E:0A:F9
          inet6 addr: fe80::208:a1ff:fe0e:af9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13032 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10599183 (10.1 MiB)  TX bytes:1710600 (1.6 MiB)
          Interrupt:3 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4820 (4.7 KiB)  TX bytes:4820 (4.7 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:193.77.18.232  P-t-P:213.250.19.90  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:12996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:10275701 (9.7 MiB)  TX bytes:1421921 (1.3 MiB)

```

A bit of a confusing story, as I can't make out conclusively what your current configuration is. Please provide the output of iptables -t nat -L -v and iptables -L -v. Moreover, what is the configuration of the client machine that is trying to access the internet ? Does it get an IP assigned through a DHCP server or does it have a static IP ? Are you running a forwarding DNS on the gateway, are the DNS settings on the client correct ?

Also, while that POSTROUTING entry is sufficient if the default policy for the firewall is ACCEPT, no ports will be forwarded to the client, which will have to be done explicitly with a PREROUTING clause, preferably to a static IP.

Something like
```

iptables -t nat -A PREROUTING -p tcp -m multiport 1-65535 -j DNAT --to-destination in.ter.nal.ip
``` will do.

---

### Post by Woei on 2006-08-29
> **ashrack said:**
> I've disabled IPV6, removed IPMASQ rebooted LINUX and then pasted this line into terminal:
```
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
```
and the net started working on the client machine:) Tanx M8

Now another big questions is, how do I make this permenant, so I wont have to paste the same line everytime I reboot linux??

Check the bottom of [this document](http://doc.gwos.org/index.php/IptablesFirewall), more specifically the section on /etc/init.d/firewall. You should read it entirely actually, to get a firm grip on iptables' possibilities.

---

