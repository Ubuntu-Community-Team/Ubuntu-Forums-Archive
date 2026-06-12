---
title: "Openvz with 8.04 networking problems"
date: 2009-08-24
forum: Server Platforms
---

### Post by dragos2 on 2009-08-24
I am running  2.6.24-24-openvz, then I created a new container with
```
 
vzctl create 777 --ostemplate ubuntu-8.04-x86

```

then
```

 vzctl set 777 --ip 193.*.*.*  --hostname mydomain.anotherdomain.com --nameserver 193.x.y.z  --save

```

But inside the ve I don't have connectivity

Inside the 777 VE:
```

root@deb01:/# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12404 (12.4 KB)  TX bytes:12404 (12.4 KB)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:127.0.0.1  P-t-P:127.0.0.1  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:175 (175.0 B)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:193.*.*.*  P-t-P:193.*.*.*  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

```

Openvz kernel:
```

root@deb01:~# ifconfig
eth1      Link encap:Ethernet  t 00:1e:68:04:69:08
          inet addr:193.*.*.*  Bcast:193.*.*.*  Mask:255.255.255.0
          inet6 addr: fe80::21e*************/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:229918 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:336621427 (321.0 MB)  TX bytes:8892247 (8.4 MB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:88 (88.0 B)  TX bytes:88 (88.0 B)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:175 (175.0 B)  TX bytes:0 (0.0 B)

```

The sysctl.conf

```

..................
# Always defragment packets
#net/ipv4/ip_always_defrag = 1


 # On Hardware Node we generally need
 # packet forwarding enabled and proxy arp disabled

 net.ipv4.conf.default.forwarding=1
 net.ipv4.conf.default.proxy_arp=1
 net.ipv4.ip_forward=1

 # Enables source route verification
 net.ipv4.conf.all.rp_filter = 1

 # Enables the magic-sysrq key
 kernel.sysrq = 1

 # TCP Explict Congestion Notification
 #net.ipv4.tcp_ecn = 0

 # we do not want all our interfaces to send redirects
 net.ipv4.conf.default.send_redirects = 1
 net.ipv4.conf.all.send_redirects = 0
root@deb01:~#


```

What should I do in order to have internet access(expose to the internet) from 777 VE ?

---

### Post by dragos2 on 2009-08-25
Bump.

Any suggestions please ?

---

### Post by bodhi.zazen on 2009-08-26
Your commands work fine fo rme :

> root@wyverin:~# vzctl create 111 --ostemplate ubuntu-9.10-amd64-minimal
Creating container private area (ubuntu-9.10-amd64-minimal)
Performing postcreate actions
Container private area was created

root@wyverin:~# vzctl set 111 --ip 192.168.1.111 --hostname testing.com --nameserver 192.168.1.1 --save
Saved parameters for CT 111

root@wyverin:~# vzctl start 111
Starting container ...
Container is mounted
Adding IP address(es): 192.168.1.111
Setting CPU units: 1000
Configure meminfo: 65536
Set hostname: testing.com
File resolv.conf was modified
Container start in progress...

root@wyverin:~# ping 192.168.1.111                           
PING 192.168.1.111 (192.168.1.111) 56(84) bytes of data.
64 bytes from 192.168.1.111: icmp_seq=1 ttl=64 time=0.079 ms
64 bytes from 192.168.1.111: icmp_seq=2 ttl=64 time=0.067 ms

--- 192.168.1.111 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.067/0.073/0.079/0.006 ms

root@wyverin:~# vzctl enter 111                               
entered into CT 111

root@testing:/# ping google.com
PING google.com (74.125.127.100) 56(84) bytes of data.
64 bytes from pz-in-f100.google.com (74.125.127.100): icmp_seq=1 ttl=51 time=39.5 ms
64 bytes from pz-in-f100.google.com (74.125.127.100): icmp_seq=2 ttl=51 time=33.8 ms

--- google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1003ms
rtt min/avg/max/mdev = 33.803/36.658/39.513/2.855 ms

root@testing:/# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:127.0.0.1  P-t-P:127.0.0.1  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1064 (1.0 KB)  TX bytes:538 (538.0 B)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:192.168.1.111  P-t-P:192.168.1.111  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1And my sysctl.conf is similar, the only difference I highlighted in blue :

```
#-- OpenVZ begin --#

# On Hardware Node we generally need
# packet forwarding enabled and proxy arp disabled
net.ipv4.conf.default.forwarding=1
[COLOR=navy]**net.ipv4.conf.default.proxy_arp = 0**[/COLOR]

# Enables source route verification
net.ipv4.conf.all.rp_filter = 1

# Enables the magic-sysrq key
kernel.sysrq = 1

# TCP Explict Congestion Notification
#net.ipv4.tcp_ecn = 0

# we do not want all our interfaces to send redirects
net.ipv4.conf.default.send_redirects = 1
net.ipv4.conf.all.send_redirects = 0

#-- OpenVZ end --#
```I suggest you try another template ;)

The Ubuntu templates have some problems with networking, I had to re-write a few things to get them working.

To fix networking I added this to /etc/init.d/networking (IN THE TEMPLATE)

```
[ -d /var/run/network ] || mkdir /var/run/network
```Add that line near the top of the file, I added it just after

[ -x /sbin/ifup ] || exit 0

---

### Post by dragos2 on 2009-08-26
> **bodhi.zazen said:**
> Your commands work fine fo rme :


Thank you bodhi.zazen. In my case I am using a public IP on the hardware
vz and then I used iptables NAT in order to allow access to internet for
the container. My mistake was that I confused the external interface eth1
with eth0 and I did not knew that I have to use NAT or bridge.

Thank you again, also thanks to the guys from openvz forums who
helped me.

Example of iptables NAT that worked for me

193.19.x.y - is the server's public static ip
192.168.1.1 - is the container associated ip

This will expose the port 80 in the container,
and also will allow the container to access the internet
for updates.

```
iptables -t nat -A PREROUTING -p tcp -d 193.19.x.y  --dport 80 -i eth1 -j DNAT --to-destination [192.168.1.1:80]("http://192.168.1.1/") 
iptables -t nat -A POSTROUTING -s 192.168.1.1 -o eth1 -j SNAT --to 193.19.x.y

```

---

### Post by bodhi.zazen on 2009-08-26
If it helps, this is how I build Ubuntu Templates :

[http://blog.bodhizazen.net/linux/openvz-ubuntu-templates/](http://blog.bodhizazen.net/linux/openvz-ubuntu-templates/)

---

