---
title: "SSH  Server Problem -- Not listening"
date: 2012-01-27
forum: Server Platforms
---

### Post by kevdog on 2012-01-27
Currently running 11.10.  I had the ssh server running once, but have made some configuration changes (such as adding a vpn server with bridge mode).

Here is what I have:
ifconfig:
br0       Link encap:Ethernet  HWaddr 00:15:60:9c:06:ec  
          inet addr:10.0.1.199  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::215:60ff:fe9c:6ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5633 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4940485 (4.9 MB)  TX bytes:1269432 (1.2 MB)

eth0      Link encap:Ethernet  HWaddr 00:15:60:9c:06:ec  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5872 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5054262 (5.0 MB)  TX bytes:1298489 (1.2 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1104 (1.1 KB)  TX bytes:1104 (1.1 KB)

tap0      Link encap:Ethernet  HWaddr c6:ca:3e:7f:54:3e  
          inet6 addr: fe80::c4ca:3eff:fe7f:543e/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:47543 (47.5 KB)

I'm running the ssh server listening on port 2223
(Snippet of sshd_config file):
# What ports, IPs and protocols we listen for
Port 2223
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2

lsof reports no listening ssh ports:
sudo lsof -i
COMMAND    PID   USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae 1119  avahi   13u  IPv4   7949      0t0  UDP *:mdns 
avahi-dae 1119  avahi   14u  IPv6   7950      0t0  UDP *:mdns 
avahi-dae 1119  avahi   15u  IPv4   7951      0t0  UDP *:37487 
avahi-dae 1119  avahi   16u  IPv6   7952      0t0  UDP *:36858 
cupsd     1152   root    9u  IPv4  10062      0t0  TCP *:ipp (LISTEN)
cupsd     1152   root   10u  IPv6  10063      0t0  TCP *:ipp (LISTEN)
cupsd     1152   root   12u  IPv4  10066      0t0  UDP *:ipp 
openvpn   1379 nobody    6u  IPv4   9221      0t0  UDP *:openvpn 

I've tried respawning the ssh daemon, but my syslog is littered with statements such as:
[ 3152.629402] init: ssh main process (2677) terminated with status 255
[ 3152.629456] init: ssh main process ended, respawning
[ 3152.640723] init: ssh main process (2680) terminated with status 255
[ 3152.640792] init: ssh main process ended, respawning
[ 3152.652747] init: ssh main process (2683) terminated with status 255
[ 3152.652799] init: ssh respawning too fast, stopped


Help??

Here is my /etc/network/interfaces file also:
auto lo
iface lo inet loopback

# Set up the bridge interface for OpenVPN
auto br0
iface br0 inet static
     address 10.0.1.199
     netmask 255.255.255.0
     gateway 10.0.1.1
     bridge_ports eth0

iface eth0 inet manual
     up ifconfig $IFACE 0.0.0.0 up
     up ip link set $IFACE promisc on
     down ip link set $IFACE promisc off
     down ifconfig $IFACE down

---

### Post by ruffEdgz on 2012-01-27
Have you tried pointing the SSH server to the bridged controller?
```

Port 2223
ListenAddress 10.0.1.199
Protocol 2

```

Cheers!

---

### Post by kevdog on 2012-01-27
I tried that -- Same result.

I also just went ahead and set my /etc/network/interfaces file back to default.  By default I mean:

iface lo inet loopback

auto eth0
iface eth0 inet dhcp

I reinstalled the openssh-server and put the port back to 22.  Same result.

---

### Post by kevdog on 2012-01-27
Solved my problem

There was an editing problem in my sshd_config file.  I had a semicolon starting one of the lines.  Once I removed this, everything worked.

Thanks for everyones helped.

---

