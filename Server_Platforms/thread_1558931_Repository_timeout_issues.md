---
title: "Repository timeout issues?"
date: 2010-08-22
forum: Server Platforms
---

### Post by christiebunny on 2010-08-22
trying to install a few things (and reinstall citadel which is acting weird)  and I'm having trouble both downloading citadel's newest package from the citadel server, and trouble installing a couple other packages too.  I get:

Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main ntp 1:4.2.4p8+dfsg-1ubuntu2
  Connection failed [IP: 91.189.88.31 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ntp/ntp_4.2.4p8+dfsg-1ubuntu2_amd64.deb:](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ntp/ntp_4.2.4p8+dfsg-1ubuntu2_amd64.deb:) Connection failed [IP: 91.189.88.31 80]

and a similar error with the citadel repository too.  Also, Web surfing anything but google.com also hangs, times out, or takes forever to resolve.


Additionally, my 'hostname -a', 'hostname -f' both hang, they return nothing at all and don't exit out to a comamand prompt without ^C. 'hostname' by itself works fine though and returns 'bunny.thewarren.ws' as it should.

I'm guessing they're related somehow -- and probably part of the reason citadel's acted weird since I moved everything over to 10.04 (64-bit, on new hardware, and clean install except for /home and /var/www)

I realize I've got multiple issues going on here, and they're likely not all related- but it seems to me the repository issue is a good first step to fix....   anyone have any ideas?

---

### Post by CharlesA on 2010-08-22
What does this return?

```
route
```

```
ifconfig
```

---

### Post by christiebunny on 2010-08-23
> **CharlesA said:**
> What does this return?

```
route
```

```
ifconfig
```


christie@bunny:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         qwestmodem.doma 0.0.0.0         UG    100    0        0 eth0

------------

christie@bunny:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:08:cb:ed
          inet addr:192.168.0.68  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe08:cbed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:201056 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164943 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20376541 (20.3 MB)  TX bytes:37403943 (37.4 MB)
          Interrupt:20 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48869 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48869 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14623039 (14.6 MB)  TX bytes:14623039 (14.6 MB)


I don't have a clue if those are right or not :confused:

(and is there a way to get monospaced text, like courier, in posts?)

---

### Post by maikel.b on 2010-08-23
> **christiebunny said:**
> christie@bunny:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         qwestmodem.doma 0.0.0.0         UG    100    0        0 eth0

------------

christie@bunny:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:08:cb:ed
          inet addr:192.168.0.68  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe08:cbed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:201056 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164943 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20376541 (20.3 MB)  TX bytes:37403943 (37.4 MB)
          Interrupt:20 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48869 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48869 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14623039 (14.6 MB)  TX bytes:14623039 (14.6 MB)


I don't have a clue if those are right or not :confused:

(and is there a way to get monospaced text, like courier, in posts?)

Do you have a dhcp server for your home connection?

When the dhcp server fails you can edit your own IP-address to your network interface..

 Maybe this will work for you..

# vi /etc/network/interfaces
 when you have a dhcp server and the server is using the default dhcp settings  you see this
 #############################
 # This file describes the network interfaces available on your system
#  and how to activate them. For more information, see interfaces(5).
 # The loopback network interface
auto lo
iface lo inet loopback
 # The primary network interface
auto eth0
iface eth0 inet dhcp
 Change this file in
 




######
 # This file describes the network interfaces available on your system
#  and how to activate them. For more information, see interfaces(5).
 # The loopback network interface
auto lo
iface lo inet loopback
 # The primary network interface
auto eth0
#iface eth0 inet  dhcp
iface eth0 inet static
address 192.168.1.105
netmask  255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway  192.168.1.1
 And edit the file /etc/resolv.conf
 # vi /etc/resolv.conf
domain dns-server-dell
search  dns-server-dell
nameserver 192.168.1.103
 edit your local or isp nameserver or the ipadress from your router this wil  be the gateway
 now restart the network
 # /etc/init.d/networking restart
 this wil load the settings you edit at the /etc/network/interfaces

edit the ip addresses  to your local addresses..


Can you post here cat /etc/resolv.conf 

This is for the dns server... you must have a correctly name server there.

---

### Post by christiebunny on 2010-08-23
> **maikel.b said:**
> Do you have a dhcp server for your home connection?

<clipped>

Can you post here cat /etc/resolv.conf 

This is for the dns server... you must have a correctly name server there.


christie@bunny:~$ cat /etc/resolv.conf
nameserver 192.168.0.1
nameserver 205.171.3.65
domain domain.actdsltmp
search domain.actdsltmp


I've got a dsl modem/router, actiontec pk5000, it assigns addresses to everything, in the 192.168.0.xxx range (this one's .68)

I have no /clue/ what the domain/search entries are in resolv.conf, I'm not on a domain at all. the second nameserver's right, though I'm not sure why the modem's listed as the first.

I'll edit /etc/network/interfaces when I get back home and'll post an update.

---

### Post by wojox on 2010-08-23
You need to try removing the colons off the end of the line

```
http://us.archive.ubuntu.com/ubuntu/...tu2_amd64.deb:
```

---

### Post by christiebunny on 2010-08-23
> **wojox said:**
> You need to try removing the colons off the end of the line

```
http://us.archive.ubuntu.com/ubuntu/...tu2_amd64.deb:
```

I wouldn't know how to without editing the package index - any package from that repository, or from citadel's, does that. both from the command line and through synaptic.  (And I've got other network issues too)

---

### Post by christiebunny on 2010-08-24
I edited interfaces an rebooted - could finally 'aptget update' though it spazzed out on "http://security.ubuntu.com"

Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
  Connection failed [IP: 91.189.88.37 80]

-------------------

I tried installing npt again, but it still won't work:

root@bunny:/etc# apt-get install ntp
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  ntp-doc
The following NEW packages will be installed:
  ntp
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
Need to get 559kB of archives.
After this operation, 1,450kB of additional disk space will be used.
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main ntp 1:4.2.4p8+dfsg-1ubuntu2
  Connection failed [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ntp/ntp_4.2.4p8+dfsg-1ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ntp/ntp_4.2.4p8+dfsg-1ubuntu2_amd64.deb)  Connection failed [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


This was after the interfaces rewrite, and after 'apt-get update' too....  any ideas?

---

