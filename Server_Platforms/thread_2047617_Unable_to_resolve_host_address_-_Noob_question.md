---
title: "Unable to resolve host address - Noob question"
date: 2012-08-25
forum: Server Platforms
---

### Post by andre.maldonado on 2012-08-25
Hi. I'm new to Ubuntu Server, this is my first attempt.

This is the cenario:

I'm connected to internet and the connection go to my D-Link DI-524 good and old router. 

I have 2 computers (Win7 and Linux) cabble connected in the router and one mobile device wirelless connected. The Win7 computer connects to the internet without problems, the same thing happens with mobile device.

The linux 12.04 fresh installed server can't connect. FYI, in the router I configured DHCP to give an static IP to the linux server (192.168.0.102).

I can connect via ssh from windows to linux without any problem. But I can't reach internet from linux. So, when I do: 

```
wget www.google.com
```

I get this error:

```
--2012-08-25 09:42:35--  http://www.google.com/
Resolving www.google.com (www.google.com)... failed: Temporary failure in name resolution.
wget: unable to resolve host address `www.google.com'

```

This is the /etc/network/interfaces:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

This is the ifconfig output:

```
eth0      Link encap:Ethernet  HWaddr 00:1a:80:bb:62:32
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:80ff:febb:6232/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7767 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1162542 (1.1 MB)  TX bytes:1085352 (1.0 MB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1613 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:127782 (127.7 KB)  TX bytes:127782 (127.7 KB)
```

And this is the resolv.conf:

```
nameserver 201.46.240.40
nameserver 201.46.240.45
nameserver 192.168.0.100
```

Where 192.168.0.100 is my router.

So, why I can't reach internet from linux server?

Thank's a lot!

---

### Post by rubylaser on 2012-08-25
It's either a gateway issue, or a DNS issue.  The first step is to determine which one.  First try to ping an ip on the internet with needing DNS resolution, something like this.

```
ping 74.125.225.180
```
^ This is one of Google's servers.  
You can also try a traceroute to the same ip.
```
route -n
```
If you get replies, then it's just a DNS issue.

Those first two DNS servers work fine for me, so if it's not the gateway, there are a few more steps to troubleshooting your issue.  Have you tried DHCP without the static DHCP lease?

---

### Post by andre.maldonado on 2012-08-25
Thank's for your reply.

Let's go:

```
ping 74.125.225.180
PING 74.125.225.180 (74.125.225.180) 56(84) bytes of data.
From 192.168.0.102 icmp_seq=1 Destination Host Unreachable
From 192.168.0.102 icmp_seq=2 Destination Host Unreachable
From 192.168.0.102 icmp_seq=3 Destination Host Unreachable
From 192.168.0.102 icmp_seq=4 Destination Host Unreachable
From 192.168.0.102 icmp_seq=5 Destination Host Unreachable
From 192.168.0.102 icmp_seq=6 Destination Host Unreachable
^C
--- 74.125.225.180 ping statistics ---
9 packets transmitted, 0 received, +6 errors, 100% packet loss, time 7999ms
pipe 4
```

Can't reach host... I don't have traceroute installed and, without internet, I can't figure out how to do this. 

The second test:

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.100   0.0.0.0         UG    100    0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

```

After that, I disabled the DHCP static ip configuration in router, restarted network in Linux and tried ping the same IP. Same results.

I think it's just a simple configuration I didn't do or some simple wrong configuration.

Thank's

---

### Post by darkod on 2012-08-25
And if you try to ping the router?

ping 192.168.0.100

You are not getting out at all, the ping to that IP you tried failed. With the above see if you can ping the router at least.

---

### Post by andre.maldonado on 2012-08-26
If I try to ping the router:


ping 192.168.0.100
PING 192.168.0.100 (192.168.0.100) 56(84) bytes of data.
From 192.168.0.102 icmp_seq=2 Destination Host Unreachable
From 192.168.0.102 icmp_seq=3 Destination Host Unreachable
From 192.168.0.102 icmp_seq=5 Destination Host Unreachable
From 192.168.0.102 icmp_seq=6 Destination Host Unreachable
^C
--- 192.168.0.100 ping statistics ---
7 packets transmitted, 0 received, +4 errors, 100% packet loss, time 6030ms
pipe 2

Nothing...

Thank's

---

### Post by Doug S on 2012-08-26
I looked at the manual for your router, and I think internal ping defaults to enabled, but maybe it is disabled. (ping response is disabled by default on my old linksys router.)
 
You appear to be connected as you get the static IP address (or did you set that yourself in the ubuntu box? I think no, based on your interfaces file) and you can see sent and received packets.
What is the IP address of your windows box? Try to ping it.
Is there anything in your arp table? (type "arp")

---

### Post by andre.maldonado on 2012-08-26
Nothing in arp table. I can ping my Win7 box normally:

```
ping 192.168.0.101
PING 192.168.0.101 (192.168.0.101) 56(84) bytes of data.
64 bytes from 192.168.0.101: icmp_req=1 ttl=128 time=0.436 ms
64 bytes from 192.168.0.101: icmp_req=2 ttl=128 time=0.454 ms
64 bytes from 192.168.0.101: icmp_req=3 ttl=128 time=0.453 ms
64 bytes from 192.168.0.101: icmp_req=4 ttl=128 time=0.442 ms
^C
--- 192.168.0.101 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.436/0.446/0.454/0.016 ms
```

I even configured a samba server with everything working. I'm connected to the linux box via ssh (putty).

But I can't ping the router or access internet.

Thank's

---

### Post by SeijiSensei on 2012-08-26
Are you sure the router has address 192.168.0.100 and not, say, 192.168.0.1?  Can you connect to the router with a web browser and see its configuration pages?  On the Windows machine, use the Run box from the Start menu and type in "cmd" then hit enter.  You'll get a terminal window.  Type "ipconfig /all" at the prompt and see what it reports as the default gateway.

---

### Post by andre.maldonado on 2012-08-27
Thank's for your reply. 

Certainly it is 192.168.0.100. I connect in the router everytime to check and manage configurations.

Thank's

---

### Post by Doug S on 2012-08-27
Can you ping the router from the windows box? If you do not know how to make a terminal window (Command Prompt) in windows, use the method Seiji described above. The point here is to know if your router even replies to pings or not.
 
Is the only static IP address that your router gives out, the 192.168.1.102 one for the linux box? I wonder if that difference is somehow effecting things. For a test, try to set it to give an address the same way it does for the windows box (I assume normal dynamic).

---

### Post by andre.maldonado on 2012-08-28
Thank's for all you guys who tried to help me.

Just for the record, the problem was solved with a hard reset in the router.

Don't know why, but its worked for another guy and worked for me too.

Thank's

---

