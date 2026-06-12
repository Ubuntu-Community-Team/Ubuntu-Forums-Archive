---
title: "Can't seem to access OpenVPN AS remotely"
date: 2013-05-03
forum: Server Platforms
---

### Post by japtar on 2013-05-03
Hello, everyone.  I'm using Ubuntu 12.04.2 LTS server to host my site.  I've installed OpenVPN AS v1.8.4 for Ubuntu 10.  I'm attempting to connect from it with a remote server, but when I do, the client indicates I can connect to it, yet I can't access any of the PHP pages or Fossil repositories using HTTP.  The connectivity test result below seems to suggest some sort of connectivity problem as well.

 [ATTACH=CONFIG]242149[/ATTACH]

I want to know what I can do to debug this problem.  I'm currently not sure whether this is due to server configuration or my Verizon Fios router configuration.  What can I do to figure this out?

Thanks in advance!

---

### Post by sandyd on 2013-05-03
Hi, have you forwarded any ports/done NAT on the router?

If not, you will have to forward port 80 (for HTTP) and other ports that you may need to use to your servers LAN address.

---

### Post by japtar on 2013-05-03
I am forwarding the HTTPS port so I can connect and access to the VPN site.  However, I'd like to keep HTTP private, and only accessible to VPN.  Is there a way to do that?

---

### Post by sandyd on 2013-05-03
> **japtar said:**
> I am forwarding the HTTPS port so I can connect and access to the VPN site.  However, I'd like to keep HTTP private, and only accessible to VPN.  Is there a way to do that?
Assuming openvpn and the http server are on the same computer:
[LIST=1]
[*]OpenVPN must be started before the webserver
[*]Make sure that apache2 is listening on all IPs, and is not bound to a single IP. 
[*]Forward the OpenVPN ports (normally 1194 UDP)
[*]If you used the default openVPN configuration, the site will be accessable at 10.8.0.1 when you are connected to the VPN
[*]
[/LIST]

Few things you may need:
```

netstat -l
```
will show what IPs apache2 is listening on. There should be a 0.0.0.0:80

---

### Post by japtar on 2013-05-04
> **sandyd said:**
> Assuming openvpn and the http server are on the same computer:
[LIST=1]
[*]OpenVPN must be started before the webserver
[*]Make sure that apache2 is listening on all IPs, and is not bound to a single IP.
[*]Forward the OpenVPN ports (normally 1194 UDP)
[*]If you used the default openVPN configuration, the site will be accessable at 10.8.0.1 when you are connected to the VPN
[/LIST]

Few things you may need:
```

netstat -l
```
will show what IPs apache2 is listening on. There should be a 0.0.0.0:80
I've attempted to stop both services, and start openvpnas and apache2 in that order.  Furthermore, I've setup the router to forward 1194 UDP.  Still, neither [https://10.8.0.1](https://10.8.0.1) is accessible, nor apache2 appear in the netstat list.  The latter is weird since I can still access the HTTPS site openvpnas creates through my DynDNS URL.
```

$ sudo netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:943                   *:*                     LISTEN
tcp        0      0 *:914                   *:*                     LISTEN
tcp        0      0 *:915                   *:*                     LISTEN
tcp        0      0 *:ssh                   *:*                     LISTEN
tcp        0      0 localhost:904           *:*                     LISTEN
tcp        0      0 localhost:905           *:*                     LISTEN
tcp        0      0 localhost:906           *:*                     LISTEN
tcp        0      0 localhost:mysql         *:*                     LISTEN
tcp        0      0 localhost:907           *:*                     LISTEN
tcp        0      0 localhost:908           *:*                     LISTEN
tcp        0      0 localhost:909           *:*                     LISTEN
tcp6       0      0 [::]:http               [::]:*                  LISTEN
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN
tcp6       0      0 [::]:microsoft-ds       [::]:*                  LISTEN
tcp6       0      0 [::]:netbios-ssn        [::]:*                  LISTEN
udp        0      0 192.168.1.25:netbios-ns *:*
udp        0      0 Kyoto.home:netbios-ns   *:*
udp        0      0 *:netbios-ns            *:*
udp        0      0 192.168.1.2:netbios-dgm *:*
udp        0      0 Kyoto.home:netbios-dgm  *:*
udp        0      0 *:netbios-dgm           *:*
udp        0      0 *:916                   *:*
udp        0      0 *:917                   *:*
udp        0      0 *:bootpc                *:*
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     12620    /usr/local/openvpn_as/etc/sock/sagent
unix  2      [ ACC ]     STREAM     LISTENING     9472     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     12623    /usr/local/openvpn_as/etc/sock/sagent.localroot
unix  2      [ ACC ]     STREAM     LISTENING     12624    /usr/local/openvpn_as/etc/sock/sagent.api
unix  2      [ ACC ]     STREAM     LISTENING     10242    /var/run/php5-fpm.soc
unix  2      [ ACC ]     STREAM     LISTENING     8975     /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     10012    /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     6765     @/com/ubuntu/mountall/server/
unix  2      [ ACC ]     STREAM     LISTENING     10197    /tmp/memcached.sock
unix  2      [ ACC ]     STREAM     LISTENING     6746     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     10298    /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     8773     /var/run/samba/unexpected
unix  2      [ ACC ]     STREAM     LISTENING     10297    /tmp/.winbindd/pipe
unix  2      [ ACC ]     SEQPACKET  LISTENING     6853     /run/udev/control

```

---

### Post by darkod on 2013-05-04
What is the difference between openvpn and openvpnas? There might be differences in the configuration, something you missed...

On the server, can you see the tun0 interface established if you run:
ifconfig

Also, it might be better to see all listening services with:
sudo netstat -plunt

---

### Post by japtar on 2013-05-04
> **darkod said:**
> What is the difference between openvpn and openvpnas? There might be differences in the configuration, something you missed...

On the server, can you see the tun0 interface established if you run:
ifconfig

Also, it might be better to see all listening services with:
sudo netstat -plunt

OpenVPN Access Server is basically OpenVPN with a web-interface for admin-related things.  I'm using it after seeing my colleague install it on Windows (with VM) that worked seemingly with little modifications.

Anyway, for ifconfig, do you mean while a client is (attempting to) connect to the server?  Here's what it looks when there isn't any client connecting to the server:
```

$ ifconfig
as0t0     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00                                                                                         -00
          inet addr:5.5.0.1  P-t-P:5.5.0.1  Mask:255.255.252.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


as0t1     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00                                                                                         -00
          inet addr:5.5.4.1  P-t-P:5.5.4.1  Mask:255.255.252.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


as0t2     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00                                                                                         -00
          inet addr:5.5.8.1  P-t-P:5.5.8.1  Mask:255.255.252.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


as0t3     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00                                                                                         -00
          inet addr:5.5.12.1  P-t-P:5.5.12.1  Mask:255.255.252.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth0      Link encap:Ethernet  HWaddr 00:15:58:2d:dd:8d
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fd00::215:58ff:fe2d:dd8d/64 Scope:Global
          inet6 addr: fe80::215:58ff:fe2d:dd8d/64 Scope:Link
          inet6 addr: fd00::b4f9:ee55:f675:8298/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11315 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4669 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1394147 (1.3 MB)  TX bytes:959464 (959.4 KB)
          Interrupt:16 Memory:ee000000-ee020000


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:616 errors:0 dropped:0 overruns:0 frame:0
          TX packets:616 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:493975 (493.9 KB)  TX bytes:493975 (493.9 KB)

```

Likewise, netstat when no client is connecting to the server.

```

$ sudo netstat -plunt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:943             0.0.0.0:*               LISTEN      1942/python
tcp        0      0 0.0.0.0:914             0.0.0.0:*               LISTEN      1954/openvpn
tcp        0      0 0.0.0.0:915             0.0.0.0:*               LISTEN      1961/openvpn
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1058/sshd
tcp        0      0 127.0.0.1:904           0.0.0.0:*               LISTEN      1942/python
tcp        0      0 127.0.0.1:905           0.0.0.0:*               LISTEN      1942/python
tcp        0      0 127.0.0.1:906           0.0.0.0:*               LISTEN      1942/python
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1174/mysqld
tcp        0      0 127.0.0.1:907           0.0.0.0:*               LISTEN      1942/python
tcp        0      0 127.0.0.1:908           0.0.0.0:*               LISTEN      1942/python
tcp        0      0 127.0.0.1:909           0.0.0.0:*               LISTEN      1942/python
tcp6       0      0 :::80                   :::*                    LISTEN      1997/apache2
tcp6       0      0 :::22                   :::*                    LISTEN      1058/sshd
tcp6       0      0 :::445                  :::*                    LISTEN      870/smbd
tcp6       0      0 :::139                  :::*                    LISTEN      870/smbd
udp        0      0 192.168.1.255:137       0.0.0.0:*                           1004/nmbd
udp        0      0 192.168.1.100:137       0.0.0.0:*                           1004/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1004/nmbd
udp        0      0 192.168.1.255:138       0.0.0.0:*                           1004/nmbd
udp        0      0 192.168.1.100:138       0.0.0.0:*                           1004/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1004/nmbd
udp        0      0 0.0.0.0:916             0.0.0.0:*                           1968/openvpn
udp        0      0 0.0.0.0:917             0.0.0.0:*                           1974/openvpn
udp        0      0 0.0.0.0:68              0.0.0.0:*                           942/dhclient3

```

---

### Post by sandyd on 2013-05-04
From openvpnas FAQ - ports that should be open
> Short answer: TCP 443, TCP 943, UDP 1194

Long answer: By default OpenVPN Access Server has 2 OpenVPN daemons running. One of them on UDP port 1194 and another on TCP 443. We recommend that you use the UDP port because this functions better for an OpenVPN tunnel. However, many public locations block all sorts of ports except very common ones like http, https, ftp, pop3, and so on. Therefore we also have TCP 443 as an option. TCP port 443 is the default port for https:// (SSL) traffic and so this is usually allowed through at the user&#8217;s location.

TCP port 943 is the port where the web server interface is listening by default. You can either approach this directly using a URL like [https://yourserverhostnamehere:943/](https://yourserverhostnamehere:943/) **or by approaching it through the standard https:// port TCP 443, since the OpenVPN daemon will automatically internally route browser traffic to TCP 943 by default**. ([https://yourserverhostnamehere/](https://yourserverhostnamehere/)).


---

### Post by darkod on 2013-05-04
That FAQ says UDP port 1194 but your netstat shows the openvpn service listening on tcp/914, tcp/915, udp/916 and udp/917. Did you modify this during installation? If you did, is the client trying to connect to the correct ports or trying the default udp/1194? If the client is trying udp/1194 it will never connect.

Also, the default vpn server IP for openvpn is 10.8.0.1 but your ifconfig shows something like 5.5.0.1 and other addresses/tunnels. With OpenVPN you get single tun0 tunnel, there is no need for more. Not sure why you have multiple as0tN tunnels.

Make sure your firewall is allowing the ports you are using for the service, and the client is connecting to the correct ports.

But in general, I would say drop the program and use plain standard OpenVPN without the GUI. I understand many people want to depend on a GUI but that is one more security risk. Imagine if someone takes over your VPN GUI?

I just recently installed openvpn server for a friend and it was really easy, peace of cake. It simply works. I don't know if this AS version is making things more complicated, or you changed the ports and are not using the correct ones in the client, or your firewall is blocking you...

It looks like installing the AS version was supposed to be the easier way but it turned out more complicated. I would still not leave a GUI on a VPN especially if you are not limiting the access by IP. Any brute force attack can break in.

---

### Post by japtar on 2013-05-04
> **darkod said:**
> That FAQ says UDP port 1194 but your netstat shows the openvpn service listening on tcp/914, tcp/915, udp/916 and udp/917. Did you modify this during installation? If you did, is the client trying to connect to the correct ports or trying the default udp/1194? If the client is trying udp/1194 it will never connect.

Also, the default vpn server IP for openvpn is 10.8.0.1 but your ifconfig shows something like 5.5.0.1 and other addresses/tunnels. With OpenVPN you get single tun0 tunnel, there is no need for more. Not sure why you have multiple as0tN tunnels.

Make sure your firewall is allowing the ports you are using for the service, and the client is connecting to the correct ports.

But in general, I would say drop the program and use plain standard OpenVPN without the GUI. I understand many people want to depend on a GUI but that is one more security risk. Imagine if someone takes over your VPN GUI?

I just recently installed openvpn server for a friend and it was really easy, peace of cake. It simply works. I don't know if this AS version is making things more complicated, or you changed the ports and are not using the correct ones in the client, or your firewall is blocking you...

It looks like installing the AS version was supposed to be the easier way but it turned out more complicated. I would still not leave a GUI on a VPN especially if you are not limiting the access by IP. Any brute force attack can break in.
To all of your questions, and to be completely honest...I don't know.  I've been trying to setup [COLOR=#ff0000]LDAP[/COLOR] (Edit: whoops, I meant PPTP, not LDAP!), OpenVPN, and OpenVPN AS with no luck on this server.  I may have changed settings I do not recognize while going through numerous online How-Tos.

I'm no IT person, but my needs were simple: create a private version control server.  I'm half-way there.  The server works wonders in the internal network.  I just need to make it work externally via private access like VPN (if there are other options, do mention it!).

---

### Post by sandyd on 2013-05-04
If its a server, use clearos/zentyal (ClearOS runs a LDAP server, never tried Zentyal)
Pfsense works as well, but not sure if it works with LDAP (never tried)

OpenVPN +LDAP also works on plain old OpenVPN -> see [http://code.google.com/p/openvpn-auth-ldap/](http://code.google.com/p/openvpn-auth-ldap/)

---

### Post by darkod on 2013-05-04
Before you take drastic decisions, did you rule out firewall and vpn client problems?

Can you confirm there is no firewall on the server (or in front of it) blocking incoming ports 914-917?
Can you confirm the vpn client you are using to connect uses those ports?

OpenVPN is easy to set up, but you do need some basic knowledge. I am not an expert myself.

For example, if you want to give openvpn a shot this instructions should be enough:
[https://help.ubuntu.com/12.04/serverguide/openvpn.html](https://help.ubuntu.com/12.04/serverguide/openvpn.html)

But note that later administration might be complicated for you without GUI. You will have to create and download client keys over SSH or similar. Additionally if you want to use password authentication, it depends how do you create and control users on the server.
If you plan to try openvpn first deinstall the SA version you installed.

---

### Post by japtar on 2013-05-04
> **darkod said:**
> Can you confirm there is no firewall on the server (or in front of it) blocking incoming ports 914-917?
Can you confirm the vpn client you are using to connect uses those ports?
How do I check if there's a firewall at all on the server?

The firewall on the router is blocking ports from 914-917.  Should I port forward TCP or UDP with these ports?

How do I check which port the VPN client is connecting from?  I'm using Windows 7 for the client (which is unfortunately necessary).

It's worth noting that AS provides a GUI for the client as well, which I found to be very convenient.  Since it's settings is generated from the server, I'd assume it's configured correctly.

---

### Post by darkod on 2013-05-05
On the server there is no firewall enabled by default unless you did it. So, there shouldn't be one. You can check iptables chains with:
```
sudo iptables -L -v -n
```

If all chains INPUT, FORWARD and OUTPUT say ACCEPT then the firewall is not active. It lets all traffic pass.

Yes, open 914-917 on the router, and forward tcp/914, tcp/915, udp/916 and udp/917 to the server private IP. By using netstat on the server you see which service is listening where. If you have a router with a firewall in front of the server, you need that port open and forwarded in order for the specific service to work, otherwise it has no route to reach the server.

Their AS client should be set up by default to use the correct ports, if you didn't change any ports on the server side, but it's worth double checking. There might be an option in the client GUI that displays the port. For example, if you do change the AS server port, you need to have a way to change the port in the client GUI too, right? So there might be something in the options/preferences in the client GUI.

For OpenVPN client usually it uses a configuration text file and the port is there, easy to check or change. For this AS client you will have to look around its GUI or consult the documentation.

---

### Post by japtar on 2013-05-05
> **darkod said:**
> On the server there is no firewall enabled by default unless you did it. So, there shouldn't be one. You can check iptables chains with:
```
sudo iptables -L -v -n
```

If all chains INPUT, FORWARD and OUTPUT say ACCEPT then the firewall is not active. It lets all traffic pass.

Yes, open 914-917 on the router, and forward tcp/914, tcp/915, udp/916 and udp/917 to the server private IP. By using netstat on the server you see which service is listening where. If you have a router with a firewall in front of the server, you need that port open and forwarded in order for the specific service to work, otherwise it has no route to reach the server.

Their AS client should be set up by default to use the correct ports, if you didn't change any ports on the server side, but it's worth double checking. There might be an option in the client GUI that displays the port. For example, if you do change the AS server port, you need to have a way to change the port in the client GUI too, right? So there might be something in the options/preferences in the client GUI.

For OpenVPN client usually it uses a configuration text file and the port is there, easy to check or change. For this AS client you will have to look around its GUI or consult the documentation.
OK, I'll open the ports in the router, and see if that worked tomorrow night. Also, I just noticed I used "LDAP" when I meant "PPTP", the other VPN protocol!  My bad!

In the meanwhile, here's what the IP table results were:
```

$ sudo iptables -L -v -n
Chain INPUT (policy ACCEPT 5 packets, 583 bytes)
 pkts bytes target     prot opt in     out     source               destination                                                                                           
  208 97705 AS0_ACCEPT  all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                      state RELATED,ESTABLISHED
    4   240 AS0_ACCEPT  all  --  lo     *       0.0.0.0/0            0.0.0.0/0                                                                                            
    0     0 AS0_IN_PRE  all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                      mark match 0x2000000/0x2000000
    0     0 AS0_ACCEPT  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                      state NEW tcp dpt:915
    4   208 AS0_ACCEPT  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                      state NEW tcp dpt:914
    0     0 AS0_ACCEPT  udp  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                      state NEW udp dpt:917
    0     0 AS0_ACCEPT  udp  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                      state NEW udp dpt:916
    0     0 AS0_WEBACCEPT  all  --  *      *       0.0.0.0/0            0.0.0.0/                                                                                          0            state RELATED,ESTABLISHED
    0     0 AS0_WEBACCEPT  tcp  --  *      *       0.0.0.0/0            0.0.0.0/                                                                                          0            state NEW tcp dpt:943
    1    52            tcp  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                      tcp dpt:22 state NEW recent: SET name: DEFAULT side: source
    0     0 LOG_AND_DROP  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                      tcp dpt:22 state NEW recent: UPDATE seconds: 60 hit_count: 4 name: D                                                                                          EFAULT side: source
    1    52 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                      tcp dpt:22


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination                                                                                           
    0     0 AS0_ACCEPT  all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                      state RELATED,ESTABLISHED
    0     0 AS0_IN_PRE  all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                      mark match 0x2000000/0x2000000
    0     0 AS0_OUT_S2C  all  --  *      as0t+   0.0.0.0/0            0.0.0.0/0                                                                                           


Chain OUTPUT (policy ACCEPT 223 packets, 151K bytes)
 pkts bytes target     prot opt in     out     source               destination                                                                                           
    0     0 AS0_OUT_LOCAL  all  --  *      as0t+   0.0.0.0/0            0.0.0.0/                                                                                          0


Chain AS0_ACCEPT (7 references)
 pkts bytes target     prot opt in     out     source               destination                                                                                           
  216 98153 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                             


Chain AS0_IN (4 references)
 pkts bytes target     prot opt in     out     source               destination                                                                                           
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            5.5.0.1                                                                                               
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            192.168.1.0/                                                                                          24
    0     0 AS0_IN_POST  all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                           


Chain AS0_IN_POST (1 references)
 pkts bytes target     prot opt in     out     source               destination                                                                                           
    0     0 AS0_OUT    all  --  *      as0t+   0.0.0.0/0            0.0.0.0/0                                                                                             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                             


Chain AS0_IN_PRE (2 references)
 pkts bytes target     prot opt in     out     source               destination                                                                                           
    0     0 AS0_IN     all  --  *      *       0.0.0.0/0            5.5.0.0/20                                                                                            
    0     0 AS0_IN     all  --  *      *       0.0.0.0/0            192.168.0.0/                                                                                          16
    0     0 AS0_IN     all  --  *      *       0.0.0.0/0            172.16.0.0/1                                                                                          2
    0     0 AS0_IN     all  --  *      *       0.0.0.0/0            10.0.0.0/8                                                                                            
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                             


Chain AS0_OUT (2 references)
 pkts bytes target     prot opt in     out     source               destination                                                                                           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                             


Chain AS0_OUT_LOCAL (1 references)
 pkts bytes target     prot opt in     out     source               destination                                                                                           
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                      icmptype 5
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                             


Chain AS0_OUT_S2C (1 references)
 pkts bytes target     prot opt in     out     source               destination                                                                                           
    0     0 AS0_OUT    all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                             


Chain AS0_WEBACCEPT (2 references)
 pkts bytes target     prot opt in     out     source               destination                                                                                           
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                             


Chain LOG_AND_DROP (1 references)
 pkts bytes target     prot opt in     out     source               destination                                                                                           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0                                                                                                      LOG flags 0 level 7 prefix "iptables deny: "
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0    

```

---

### Post by darkod on 2013-05-06
OK, you have no firewall on the server itself.

I went little bit through the OpenVPN AS guide and it seem to use the standard port 443 for client connections. Don't understand it exactly, it might be using connection through browser, right? I was assuming the 914-917 ports going from the netstat results, but they could have designed the program to work how they want.

Have you downloaded the guide and went through it? It seems to have sufficient info in there. In the menu on the left you have a link for Admin Guide, that's the PDF document:
[http://openvpn.net/index.php/access-server/overview.html](http://openvpn.net/index.php/access-server/overview.html)

Also, it looked to me like there is no free version of this product. If you paid for it, can their support help you little to set it up? You should be able to contact support for anything you paid for.

---

### Post by japtar on 2013-05-07
> **darkod said:**
> OK, you have no firewall on the server itself.

I went little bit through the OpenVPN AS guide and it seem to use the standard port 443 for client connections. Don't understand it exactly, it might be using connection through browser, right? I was assuming the 914-917 ports going from the netstat results, but they could have designed the program to work how they want.

Have you downloaded the guide and went through it? It seems to have sufficient info in there. In the menu on the left you have a link for Admin Guide, that's the PDF document:
[http://openvpn.net/index.php/access-server/overview.html](http://openvpn.net/index.php/access-server/overview.html)

Also, it looked to me like there is no free version of this product. If you paid for it, can their support help you little to set it up? You should be able to contact support for anything you paid for.

Good catch with the manual.  I haven't paid anything for AS.  I think the first 2 users are free (I'm just 1).  I couldn't get the nearest wifi hotspot last time to test, but hopefully I can tonight!

---

