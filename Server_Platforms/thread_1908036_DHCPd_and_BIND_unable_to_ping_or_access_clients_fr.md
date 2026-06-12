---
title: "DHCPd and BIND: unable to ping or access clients from server using hostname"
date: 2012-01-12
forum: Server Platforms
---

### Post by kmas on 2012-01-12
I have setup my dhcp and bind server (Ubuntu 11.10). The problem that I'm having is I'm unable to ping or nslookup any clients (my ubuntu 11.10 laptop and Windows 7, and XP PC) from the server using hostname. I'm able to ping my server from the client, and my server from anywhere on my network. My windows clients are able to ping each other using hostnames and they can ping my ubuntu laptop. What I'm I doing wrong. 

**[COLOR="Red"]Bind Setup[/COLOR]**
**named.conf.options**
```
administrator@ns:~$ cat /etc/bind/named.conf.options
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable 
        // nameservers, you probably want to use them as forwarders.  
        // Uncomment the following block, and insert the addresses replacing 
        // the all-0's placeholder.

        forwarders {
                192.168.1.1;
                8.8.8.8;                # google
                8.8.4.4;
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};


```

**named.conf.local**

```
administrator@ns:~$ cat /etc/bind/named.conf.local
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

#FOWARD LOOKUP ZONES - Holds A records, A records map host names to IP addresses
zone "mydomain.me"
{
        type master;
        file "/etc/bind/zones/db.mydomain.me";
        allow-update { key dhcpupdate; };
};

#REVERSE LOOKUP ZONES - Holds Pointer Records (PTR) Maps IP  to Hostname
#192.168.1
zone "1.168.192.in-addr.arpa"
{
        type master;
        notify no;
        file "/etc/bind/zones/db.192";
        allow-update { key dhcpupdate; };
};
```

**2 Zone files**
```
administrator@ns:~$ ls /etc/bind/zones
backup  db.192  db.mydomain.me

```

**Reverse**
```
administrator@ns:~$ cat /etc/bind/zones/db.192 
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.mydomain.me. root.mydomain.me. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
174     IN      PTR     ns.mydomain.me.
174     IN      PTR     ns.
175     IN      PTR     VM-Grinder.
56      IN      PTR     dnqmwb01.mydomain.me.       dnqmwb01.
57      IN      PTR     dnqmap01.mydomain.me.       dnqmap01.
58      IN      PTR     dnqmds01.mydomain.me.       dnqmds01.
59      IN      PTR     dnqmdb01.mydomain.me.       dnqmdb01.
61      IN      PTR     unqmop01.mydomain.me.       unqmop01. 
130     IN      PTR     cloudmgr.mydomain.me.       cloudmgr.
131     IN      PTR     cloudhost1.mydomain.me.     cloudhost1.

```

**data file**
```
administrator@ns:~$ cat /etc/bind/zones/db.mydomain.me 
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.mydomain.me. root.mydomain.me. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@               IN      NS      ns.mydomain.me.
@               IN      A       192.168.1.174
ns              IN      A       192.168.1.174
VM-Grinder      IN      A       192.168.1.175
dnqmwb01        IN      A       192.168.1.56
dnqmap01        IN      A       192.168.1.57
dnqmds01        IN      A       192.168.1.58
dnqmdb01        IN      A       192.168.1.59 
unqmop01        IN      A       192.168.1.61
cloudmgr        IN      A       192.168.1.130
cloudhost1      IN      A       192.168.1.131

```

**[COLOR="Red"]DHCP Options[/COLOR]**
**ifconfig on server**
```
administrator@ns:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:25:90:55:15:60  
          inet addr:192.168.1.174  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:90ff:fe55:1560/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1531089 errors:0 dropped:58 overruns:0 frame:0
          TX packets:682890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1406128970 (1.4 GB)  TX bytes:82035875 (82.0 MB)
          Interrupt:16 Memory:fb900000-fb920000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:782 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:106569 (106.5 KB)  TX bytes:106569 (106.5 KB)


```

**Interface selection**
```
administrator@ns:~$ cat /etc/default/isc-dhcp-server
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/isc-dhcp-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"

```

**DHCPD.CONF**
```
administrator@ns:~$ cat /etc/dhcp/dhcpd.conf
# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "mydomain.me";
option domain-name-servers ns.mydomain.me;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.1;
default-lease-time 600;
max-lease-time 7200;

subnet 192.168.1.0 netmask 255.255.255.0
{
        range 192.168.1.167 192.168.1.255;
}

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;


```

[COLOR="red"]**From my ubuntu Client**[/COLOR]
I know my ubuntu client is using the DNS and DHCP Server because I see the Handshake process from my DHCP server IP
```
kenneth@KM-Ubuntu:~$ sudo dhclient -v
Internet Systems Consortium DHCP Client 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:21:6a:8f:32:3a
Sending on   LPF/wlan0/00:21:6a:8f:32:3a
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.195 on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.1.174
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.214 from 192.168.1.174
DHCPREQUEST of 192.168.1.214 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.214 from 192.168.1.174
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd
bound to 192.168.1.214 -- renewal in 240 seconds.
kenneth@KM-Ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:27:13:66:40:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fc600000-fc620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2015 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:179103 (179.1 KB)  TX bytes:179103 (179.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6a:8f:32:3a  
          inet addr:192.168.1.214  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6aff:fe8f:323a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79628 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39004 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48627659 (48.6 MB)  TX bytes:6514573 (6.5 MB)


```

I can ping the Server from my client
```
kenneth@KM-Ubuntu:~$ ping ns
PING ns.mydomain.me (192.168.1.174) 56(84) bytes of data.
64 bytes from 192.168.1.174: icmp_req=1 ttl=64 time=1.29 ms
64 bytes from 192.168.1.174: icmp_req=2 ttl=64 time=0.797 ms
64 bytes from 192.168.1.174: icmp_req=3 ttl=64 time=0.832 ms
^C64 bytes from 192.168.1.174: icmp_req=4 ttl=64 time=0.828 ms

--- ns.mydomain.me ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 15016ms
rtt min/avg/max/mdev = 0.797/0.938/1.297/0.209 ms

```

I also know it is working because, my resolv.conf points to the correct nameserver and domain. 
```
kenneth@KM-Ubuntu:~$ cat /etc/resolv.conf
domain mydomain.me
search mydomain.me
nameserver 192.168.1.174

```

[COLOR="red"]**From my ubuntu Server**[/COLOR]

I however cannot ping my client from the server
```
administrator@ns:~$ ping KM-Ubuntu
ping: unknown host KM-Ubuntu

```

I also can't ping Windows client from server
```
administrator@ns:~$ ping newman
ping: unknown host newman
administrator@ns:~$ ping newman.mydomain.
ping: unknown host newman.mydomain.
administrator@ns:~$ ping newman.mydomain.me
ping: unknown host newman.mydomain.me
administrator@ns:~$ host newman
Host newman not found: 3(NXDOMAIN)

```

[COLOR="red"]**From my Windows 7 Host**[/COLOR]

I know everything here works the way its supposed to. It falls withing the ip range, its on the domain and it can ping my ubuntu client? 

```
C:\Users\John Doe>ipconfig

Windows IP Configuration


Wireless LAN adapter Wireless Network Connection 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Ethernet adapter Local Area Connection 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : mydomain.me
   Link-local IPv6 Address . . . . . : fe80::7cc1:6421:7325:31b4%14
   IPv4 Address. . . . . . . . . . . : 192.168.1.171
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1


C:\Users\John Doe>ping 3qy

Pinging 3qy [192.168.1.219] with 32 bytes of data:
Reply from 192.168.1.219: bytes=32 time=16ms TTL=128
Reply from 192.168.1.219: bytes=32 time=19ms TTL=128
Reply from 192.168.1.219: bytes=32 time=1ms TTL=128
Reply from 192.168.1.219: bytes=32 time=2ms TTL=128

Ping statistics for 192.168.1.219:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 1ms, Maximum = 19ms, Average = 9ms

C:\Users\John Doe>

C:\Users\John Doe>ping km-ubuntu

Pinging km-ubuntu [192.168.1.214] with 32 bytes of data:
Reply from 192.168.1.214: bytes=32 time=6ms TTL=64
Reply from 192.168.1.214: bytes=32 time=20ms TTL=64
Reply from 192.168.1.214: bytes=32 time=1ms TTL=64

Ping statistics for 192.168.1.214:
    Packets: Sent = 3, Received = 3, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 1ms, Maximum = 20ms, Average = 9ms
Control-C
^C
C:\Users\John Doe>

```

---

### Post by kmas on 2012-01-12
never mind I found my answer. 

```
All you have to do is:

sudo nano /etc/nsswitch.conf
change the line that says


hosts: files dns
to this:


hosts: files wins dns
(order does matter)

finally, you need to install winbind


sudo apt-get install winbind
To enable windows to ping ubuntu you then need to install samba:


sudo apt-get install samba

```

---

