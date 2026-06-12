---
title: "Can't ping server"
date: 2013-05-21
forum: Server Platforms
---

### Post by AmbiguousOutlier on 2013-05-21
Hello, what are some obvious reasons why I can't ping my server, yet I can still access all my NFS shares on it and the server can ping my other machines just fine?

```
rhys@orange:~$ ping tomato
PING tomato.default (192.168.1.72) 56(84) bytes of data.
^C
--- tomato.default ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2999ms
```

---

### Post by jonedney on 2013-05-21
Hi RhysGM,

Have you placed an exception in IPTABLES/firewall to allow orange to connect to tomato?

---

### Post by AmbiguousOutlier on 2013-05-21
Nothing is in iptables and I disabled ufw. 

orange = laptop wlan
tomato = server lan
mango = xbmc lan

I can't ssh into tomato from orange or ping however I can ssh orange into mango then from mango I can ssh and ping tomato. When I've tunnelled into tomato from orange via mango, I can ping back to orange.

I just can't figure out what I've done to prevent orange from seeing tomato?!

EDIT:

And if it makes a difference, I have to specify the private IP and not the computer name to ssh from mango to tomato.

---

### Post by darkod on 2013-05-21
Is the dns resolving correct? Is tomato IP really .72?

---

### Post by AmbiguousOutlier on 2013-05-21
It looks correct to me, 

```

rhys@Tomato:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:d9:b2:c5  
          inet addr:192.168.1.72  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fed9:b2c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4503012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5944157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3661397857 (3.6 GB)  TX bytes:6665486100 (6.6 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:260429 (260.4 KB)  TX bytes:260429 (260.4 KB)
```

---

### Post by darkod on 2013-05-21
Are you sure there is no firewall active?

Did you try pinging the name, and also pinging the IP .72?

---

### Post by AmbiguousOutlier on 2013-05-21
Yeah, I've double checked all that. 

```
rhys@Tomato:~$ sudo ufw status verbose
Status: inactive
```

```

rhys@orange:~$ ping 192.168.1.72
PING 192.168.1.72 (192.168.1.72) 56(84) bytes of data.
^C
--- 192.168.1.72 ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5038ms
```

```
rhys@orange:~$ ssh 'rhys@mango'
rhys@mango's password: 
Welcome to Ubuntu 12.10 - XBMCbuntu (GNU/Linux 3.5.0-22-generic i686)

 * Documentation:  https://help.ubuntu.com/

Last login: Tue May 21 19:21:58 2013 from tomato.local
rhys@Mango:~$ ping tomato
PING tomato (67.215.65.132) 56(84) bytes of data.
64 bytes from hit-nxdomain.opendns.com (67.215.65.132): icmp_req=1 ttl=51 time=36.0 ms
64 bytes from hit-nxdomain.opendns.com (67.215.65.132): icmp_req=2 ttl=51 time=33.4 ms
64 bytes from hit-nxdomain.opendns.com (67.215.65.132): icmp_req=3 ttl=51 time=30.3 ms
64 bytes from hit-nxdomain.opendns.com (67.215.65.132): icmp_req=4 ttl=51 time=12.3 ms
^C
--- tomato ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 12.325/28.040/36.005/9.292 ms
```

---

### Post by darkod on 2013-05-21
Did you notice that when pinging from orange to tomato it tries it on the private IP and when pinging from mango to tomato it does it on a public IP? So, pinging from mango works but on a public IP, not on private IP.

Also, in some cases having ufw inactive doesn't mean much. Can you post this from tomato:
```
sudo iptables -L -n -v
```

---

### Post by AmbiguousOutlier on 2013-05-21
I did not spot that. If I use the private IP then mango doesn't reslove it. 

```

rhys@Mango:~$ ping 192.168.1.72
PING 192.168.1.72 (192.168.1.72) 56(84) bytes of data.
^C
--- 192.168.1.72 ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 6047ms
```

```
rhys@Tomato:~$ sudo iptables -L -n -v
Chain INPUT (policy ACCEPT 13M packets, 11G bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 fail2ban-ssh  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 22

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 15M packets, 15G bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain fail2ban-ssh (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           
```

EDIT:

sudo nano /etc/network/interfaces

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.72
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

---

### Post by darkod on 2013-05-21
iptables is OK, you have the policies as ACCEPT.

But ping and ssh seems to work only on the public IP. Try ssh-ing with username@192.168.1.72 instead of username@tomato, from both mango and orange. I think it won't work.

---

### Post by AmbiguousOutlier on 2013-05-21
Mango works!

```

rhys@Orange:~$ ssh 'rhys@192.168.1.72'
ssh_exchange_identification: Connection closed by remote host
```

```

rhys@Mango:~$ ssh 'rhys@192.168.1.72'
rhys@192.168.1.72's password: 
Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.5.0-30-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Tue May 21 23:17:39 BST 2013

  System load:    0.5                 Processes:           177
  Usage of /home: 43.9% of 415.83GB   Users logged in:     1
  Memory usage:   45%                 IP address for eth0: 192.168.1.72
  Swap usage:     0%

  Graph this data and manage this system at https://landscape.canonical.com/

1 package can be updated.
0 updates are security updates.

You have new mail.
Last login: Tue May 21 19:27:06 2013 from mango.local
```

---

### Post by darkod on 2013-05-22
Are all three machines on the same 192.168.1.x subnet? They would need to be on the same subnet to communicate with .72.

I noticed tomato has only one network interface, and it has the private IP of .72 configured on it. So I guess the public IP seen earlier is the IP of your internet router.

If all the machines are on your private LAN they should be able to communicate between themselves with the private IPs. Also, you might need to have a dns set up so that they can communicate by name.

Since communication between orange and tomato doesn't work with the private IPs I assume you might have a configuration issue (not in the same subnet) or connectivity issue (not connected in the same LAN).

---

### Post by AmbiguousOutlier on 2013-05-22
Yes indeed they are; 
Mango 192.168.1.158
Tomato 192.168.1.72
Orange 192.168.1.14

They are all connected via a router not a switch Orange is on the wifi and Mango and Tomato are on the Ethernet. 

I'm not at home to check what my routers IP is but that makes sense. 

What configuration files should I be checking; I've double checked the /etc/network/interfaces /etc/ssh/sshd_config /etc/ssh/ssh_config 
These all look the same on all 3 computers. 

I might try changing them all back to static and forwarding the MAC address on my router to the machines, to see if that will work, is one method better than the other?

---

### Post by darkod on 2013-05-22
The IP setup should be static for servers, in /etc/network/interfaces. For desktop (client) machines it's not really important whether the IP is static or dynamic.

In the LAN the machines should be able to communicate without problems between themselves. It's really weird the ping is not working between some machines, as there doesn't seem to be firewall involved.

---

### Post by LHammonds on 2013-05-22
If your configuration is assumed to be correct, you need to look at the hardware.  The network cable or port that the cable is plugged into (either on the server or the network hub)

You need to ping [www.google.com](www.google.com) from each machine to make sure each machine is resolving an external friendly name and then has the ability to communicate with it.

If that fails on any machine, that machine's config or access to the Internet/network is hampered in some way.

When pinging internal devices, only use the IP address to avoid bringing in DNS issues as well (for example, when you pinged "tomato" one time, it resolved an external IP...most-likely a web site)

If the Internet test failed, you then need to ping your gateway/router (192.168.1.1 in this case).

LHammonds

---

### Post by CharlesA on 2013-05-22
I usually use this order when troubleshooting connectivity issues:

1. ping different host on same subnet (internal only)
2. ping gateway (router)
3. ping external site (google)

Depending on which test fails, it gives you a place to start.

---

### Post by AmbiguousOutlier on 2013-05-23
Orange - 192.168.1.14

Ping OK on 192.168.1.158 (Mango), 192.168.1.1, [www.google.co.uk](www.google.co.uk)
Ping unsuccessful on 192.168.1.72 (Tomato)
 
```

rhys@Orange:~$ ping 192.168.1.72
PING 192.168.1.72 (192.168.1.72) 56(84) bytes of data.
^C
--- 192.168.1.72 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3024ms

rhys@Orange:~$ ping 192.168.1.158
PING 192.168.1.158 (192.168.1.158) 56(84) bytes of data.
64 bytes from 192.168.1.158: icmp_req=1 ttl=64 time=3.85 ms
64 bytes from 192.168.1.158: icmp_req=2 ttl=64 time=1.88 ms
64 bytes from 192.168.1.158: icmp_req=3 ttl=64 time=2.10 ms
^C
--- 192.168.1.158 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 1.884/2.611/3.850/0.882 ms
rhys@Orange:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=2.37 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=1.78 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=1.88 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=10.8 ms
^C
--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 1.787/4.227/10.869/3.841 ms
rhys@Orange:~$ ping www.google.co.uk
PING www.google.co.uk (173.194.67.94) 56(84) bytes of data.
64 bytes from wi-in-f94.1e100.net (173.194.67.94): icmp_req=1 ttl=45 time=18.7 ms
64 bytes from wi-in-f94.1e100.net (173.194.67.94): icmp_req=2 ttl=45 time=18.4 ms
64 bytes from wi-in-f94.1e100.net (173.194.67.94): icmp_req=3 ttl=45 time=18.2 ms
^C
--- www.google.co.uk ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 18.218/18.477/18.769/0.251 ms

```


Mango - 192.168.1.158

Ping OK on 192.168.1.14 (Orange), 192.168.1.1, [www.google.co.uk](www.google.co.uk)
Ping unsuccessful on 192.168.1.72 (Tomato)

```

rhys@Mango:~$ ping 192.168.1.14
PING 192.168.1.14 (192.168.1.14) 56(84) bytes of data.
64 bytes from 192.168.1.14: icmp_req=1 ttl=64 time=1.62 ms
64 bytes from 192.168.1.14: icmp_req=2 ttl=64 time=2.13 ms
64 bytes from 192.168.1.14: icmp_req=3 ttl=64 time=1.82 ms
^C
--- 192.168.1.14 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 1.623/1.862/2.139/0.215 ms
rhys@Mango:~$ ping 192.168.1.72
PING 192.168.1.72 (192.168.1.72) 56(84) bytes of data.
^C
--- 192.168.1.72 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015ms

rhys@Mango:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=0.499 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=0.433 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=0.418 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=0.431 ms
64 bytes from 192.168.1.1: icmp_req=5 ttl=64 time=0.423 ms
^C
--- 192.168.1.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 0.418/0.440/0.499/0.039 ms
rhys@Mango:~$ ping www.google.co.uk
PING www.google.co.uk (173.194.41.95) 56(84) bytes of data.
64 bytes from lhr08s01-in-f31.1e100.net (173.194.41.95): icmp_req=1 ttl=53 time=11.3 ms
64 bytes from lhr08s01-in-f31.1e100.net (173.194.41.95): icmp_req=2 ttl=53 time=11.3 ms
64 bytes from lhr08s01-in-f31.1e100.net (173.194.41.95): icmp_req=3 ttl=53 time=11.2 ms
64 bytes from lhr08s01-in-f31.1e100.net (173.194.41.95): icmp_req=4 ttl=53 time=11.3 ms
^C
--- www.google.co.uk ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 11.280/11.332/11.376/0.040 ms
```


Tomato - 192.168.1.72

Ping OK on 192.168.1.14 (Orange) 192.168.1.158 (Mango), 192.168.1.1,  173.194.41.95 ([www.google.co.uk](www.google.co.uk))
Ping unsuccessful on 192.168.1.72 (Tomato), [www.google.co.uk](www.google.co.uk)

```

rhys@Tomato:~$ ping 192.168.1.14
PING 192.168.1.14 (192.168.1.14) 56(84) bytes of data.
64 bytes from 192.168.1.14: icmp_req=1 ttl=64 time=1.31 ms
64 bytes from 192.168.1.14: icmp_req=2 ttl=64 time=1.47 ms
64 bytes from 192.168.1.14: icmp_req=3 ttl=64 time=1.93 ms
^C
--- 192.168.1.14 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 1.313/1.571/1.932/0.266 ms
rhys@Tomato:~$ ping 192.168.1.158
PING 192.168.1.158 (192.168.1.158) 56(84) bytes of data.
64 bytes from 192.168.1.158: icmp_req=1 ttl=64 time=0.181 ms
64 bytes from 192.168.1.158: icmp_req=2 ttl=64 time=0.191 ms
64 bytes from 192.168.1.158: icmp_req=3 ttl=64 time=0.187 ms
^C
--- 192.168.1.158 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.181/0.186/0.191/0.011 ms
rhys@Tomato:~$ ping 192.168.1.72
PING 192.168.1.72 (192.168.1.72) 56(84) bytes of data.
^C
--- 192.168.1.72 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1006ms

rhys@Tomato:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=0.496 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=0.443 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=0.439 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=0.450 ms
^C
--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 0.439/0.457/0.496/0.022 ms
rhys@Tomato:~$ ping www.google.co.uk
ping: unknown host www.google.co.uk
rhys@Tomato:~$ ping 173.194.41.95
PING 173.194.41.95 (173.194.41.95) 56(84) bytes of data.
64 bytes from 173.194.41.95: icmp_req=1 ttl=53 time=11.3 ms
64 bytes from 173.194.41.95: icmp_req=2 ttl=53 time=11.1 ms
64 bytes from 173.194.41.95: icmp_req=3 ttl=53 time=11.1 ms
64 bytes from 173.194.41.95: icmp_req=4 ttl=53 time=11.4 ms
^C
--- 173.194.41.95 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 11.161/11.273/11.435/0.174 ms
```

I'm curious to know why there's a DNS issue on Tomato for external domains, would this be a good place to start?

EDIT:
Just as a side note, I have restarted my router and disconnected all cables and blown out any dust (just incase) and reconnected everything.

---

### Post by CharlesA on 2013-05-23
Compare the network configuration of the working machines to the broken one and see what the difference is.

Pay particular attention to the contents of /etc/resolv.conf

---

### Post by AmbiguousOutlier on 2013-05-23
Outputs of;
/etc/resolv.conf
/etc/network/interfaces
/etc/hosts

respectively

Mango - not sure what these addresses are, I can ping them, google suggests they are something to do with openvpn which I do use but not on mango, only tomato and orange.
 
```

# domain dummy.net
nameserver 208.67.222.222
nameserver 208.67.220.220
```

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

```

127.0.0.1       localhost
127.0.1.1       Mango

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```


Orange 

```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search default
```
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

```

127.0.0.1       localhost
127.0.1.1       orange

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```


Tomato
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
```

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.72
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

```

127.0.0.1       localhost
127.0.1.1       Tomato

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

What do you suggest? :confused:

---

### Post by CharlesA on 2013-05-23
Yeah, no DNS servers. You could add this to /etc/network/interfaces under the gateway.

```
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 208.67.222.222

```

Restart networking or reboot and it should be fine.

---

### Post by AmbiguousOutlier on 2013-05-23
All the above tests produce the same results. I used the below methods of restart;

/etc/init.d/networking restart
service networking restart

Plus I rebooted. 

Just to confirm I added this to /etc/network/interfaces
```

  GNU nano 2.2.6                            File: /etc/network/interfaces                                                               

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.72
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

# dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 208.67.222.222
```

---

### Post by darkod on 2013-05-23
Just to revert to something you said, those 208.... IPs are the open dns nameservers. It has nothing to do with openvpn. You also said you are using openvpn on tomato and orange. How exactly?

Are both machines serving as vpn server and clients connect to it, or they are connected between themselves with vpn. In that case one would be server and the other client. I am mentioning this since a client machine can change the gateway and route it uses, depending on the vpn server configuration and the commands pushed to the client.
This could mess up orange networking setup and caue these unexpected issues.

---

### Post by AmbiguousOutlier on 2013-05-23
Oh I've switched off the openvpn's until I can sort this out. The only way the openvpn will effect this is if it's altered some other config files somewhere, currently no machine is acting as a server or client. They were being used as clients with an external vpn server, but openvpn is not running. 

I'm having lots of intermittent nfs connection issues now. I think I might just give in a do a fresh install. :(

---

### Post by jdthood on 2013-05-26
Enter the configuration system of your accesspointmodemrouter and look for a feature which restricts Wi-Fi traffic to HTTP or "web" traffic. Disable it.

---

