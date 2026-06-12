---
title: "Weird Network/Apache problem"
date: 2006-03-10
forum: Server Platforms
---

### Post by jhughes on 2006-03-10
I really hope I am posting this (long) question in the right forum, if not I appologize in advance and please move it where it should be...

I just installed Kubuntu on an older Dell P3 box with the intention of setting it up as a webserver.  I installed Apache, PHP and MySQL with no problems.  During the Kubuntu install it defaulted to DHCP, but using the assigned IP I was able to connect to the Apache server from a Windows box on the network (using Firefox) with no problems.  

I then changed this to a static IP initially using the GUI (Settings -> Network -> Network Settings).  Looking in /etc/network/interfaces it does not fill in all the required values and I was unable to even ping my router (172.16.21.1) even though I had specified a default gateway in the GUI:
```

# The primary network interface
auto eth0
iface eth0 inet static
address 172.16.21.20
netmask 255.255.255.0

```
So I manually updated the entries in the /etc/network/interfaces file:
```

# The primary network interface
auto eth0
iface eth0 inet static
address 172.16.21.20
netmask 255.255.255.0
network 172.16.21.0
broadcast 172.16.21.255
gateway 172.16.21.1
```
Now I could ping my gateway, but from the Windows box that was able to connect to the Kubuntu Apache server earlier, Firefox first reported that the connection was reset by the peer, subsequent tries result in Firefox reporting that it could not establish a connection to 172.16.21.20 (the IP of the Windows box is 172.16.21.207).  

Now if I ping that box from the Kubuntu box (that initial ping response takes about 10 seconds and then it is fine), now all of a sudden I can access the webpage on the Kubuntu box!  

Any ideas what could be wrong with my setup?
```

jhughes@aus-webserver:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:4F:4C:4A:7E
          inet addr:172.16.21.20  Bcast:172.16.21.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:4fff:fe4c:4a7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:106103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17862013 (17.0 MiB)  TX bytes:1925725 (1.8 MiB)
          Interrupt:11 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1656 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:138527 (135.2 KiB)  TX bytes:138527 (135.2 KiB)

jhughes@aus-webserver:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.16.21.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         172.16.21.1     0.0.0.0         UG        0 0          0 eth0
jhughes@aus-webserver:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.21.0     *               255.255.255.0   U     0      0        0 eth0
default         172.16.21.1     0.0.0.0         UG    0      0        0 eth0
jhughes@aus-webserver:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#       script grep
#       map eth0

# The primary network interface
auto eth0
iface eth0 inet static
address 172.16.21.20
netmask 255.255.255.0
network 172.16.21.0
broadcast 172.16.21.255
gateway 172.16.21.1

```

---

### Post by sudo-fu on 2007-04-04
Is there any solution to this? I think I have a similar problem...

I use Ubuntu Server 6.06 and Apache2 as my LAN server. After starting the server, I cannot access the intranet-website immediately. Firefox shows "Unable to connect" and while I can successfully ping the router from the server, the pings from the other clients to the server all time out.

Only after repeatedly pinging the server from the client computer several times, Apache wakes up.

But then again, when I don't access the intranet for a couple of minutes, the problem reappears. Pinging the server always gets it running temporarily.

This is weird. Does anybody know how I can solve this?

---

