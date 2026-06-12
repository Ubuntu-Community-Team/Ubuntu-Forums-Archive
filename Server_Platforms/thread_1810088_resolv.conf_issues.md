---
title: "resolv.conf issues"
date: 2011-07-22
forum: Server Platforms
---

### Post by NetDoc on 2011-07-22
I am having difficulty with my new server being able to ping an FQD. 

[COLOR="Blue"][B]pjmu@epsilon:~$ ping google.com
ping: unknown host google.com[/B][/COLOR]

Here is my resolv.conf (I am using Google's nameservers)
File: /etc/resolv.conf

[COLOR="Blue"][B]nameserver 8.8.8.8
nameserver 8.8.4.4[/B][/COLOR]

I am expecting something like 74.125.45.99, but it can't find it. Is there something I need to do to restart resolv.conf after I edit it? 

Here is my interfaces file: 

File: /etc/network/interfaces

[COLOR="blue"][B]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0 eth0:1 eth1
iface eth0 inet static
        address 192.168.2.120
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 8.8.8.8
        dns-search scubaboard.com
iface eth0:1 inet static
        address 209.208.24.242
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
        gateway 209.208.24.241
iface eth1 inet static
        address 209.208.24.243
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
        gateway 209.208.24.241[/B][/COLOR]

---

### Post by papibe on 2011-07-22
Could you repost your /etc/network/interfaces (or edit the previous one), but using the code tags? It is easier to read that way.

Also, could you post the result of this command 2 commands:
```
$ ifconfig

$ nslookup google.com
```
And finally post this file: /etc/nsswitch.conf

Regards.

---

### Post by Lloyd_mcse on 2011-07-22
You have 3x gateway statements, remove the [COLOR=blue]**[COLOR=Black]209.208.24.241 [/COLOR]**[COLOR=Black]entries[/COLOR][COLOR=Black] so you just have 192.168.2.1 on eth0
Thanks how I got mine working anyway.
[/COLOR][/COLOR]

---

### Post by NetDoc on 2011-07-22
> **Lloyd_mcse said:**
> You have 3x gateway statements, remove the [COLOR=blue]**[COLOR=Black]209.208.24.241 [/COLOR]**[COLOR=Black]entries[/COLOR][COLOR=Black] so you just have 192.168.2.1 on eth0
Thanks how I got mine working anyway.
[/COLOR][/COLOR]That didn't seem to work. Thanks for the suggestion anyway.

My new interfaces file reads:

```
[COLOR="Blue"][B]File: /etc/network/interfaces                                                        

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0 eth0:1 eth1
iface eth0 inet static
        address 192.168.2.120
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 8.8.8.8
        dns-search scubaboard.com
iface eth0:1 inet static
        address 209.208.24.242
        netmask 255.255.255.240
iface eth1 inet static
        address 209.208.24.243
        netmask 255.255.255.240[/B][/COLOR]
```

---

### Post by NetDoc on 2011-07-22
> **papibe said:**
>  Could you repost your /etc/network/interfaces (or edit the previous one), but using the code tags? It is easier to read that way.  I have no idea how to do this. Please explain. 

> **papibe said:**
> Also, could you post the result of this command 2 commands:
```
$ ifconfig root@epsilon:[COLOR="blue"][B]~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:48:35:2a:32  
          inet addr:192.168.2.120  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe35:2a32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:244423 (244.4 KB)  TX bytes:22265 (22.2 KB)
          Memory:da000000-da020000 

eth0:1    Link encap:Ethernet  HWaddr 00:30:48:35:2a:32  
          inet addr:209.208.24.242  Bcast:209.208.24.255  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Memory:da000000-da020000 

eth1      Link encap:Ethernet  HWaddr 00:30:48:35:2a:33  
          inet addr:209.208.24.243  Bcast:209.208.24.255  Mask:255.255.255.240
          inet6 addr: fe80::230:48ff:fe35:2a33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1017 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:227989 (227.9 KB)  TX bytes:468 (468.0 B)
          Memory:da020000-da040000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88 (88.0 B)  TX bytes:88 (88.0 B)[/B][/COLOR]
```


> **papibe said:**
> $ nslookup google.com root@epsilon:[COLOR="blue"][B]```
~# nslookup google.com
;; connection timed out; no servers could be reached[/B][/COLOR]
```

> **papibe said:**
> And finally post this file: /etc/nsswitch.conf [COLOR="Blue"][B]```
 # /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis[/B][/COLOR]
```

---

### Post by papibe on 2011-07-22
If I use the # button when I answering a thread, it would appear like this:
[PHP]```
Text inside code tags
```[/PHP]
When posted it'll look like this:
```
Text inside code tags
```
Which respects indentation, then making easy to read.

You can edit your post and re-paste the files and wrapping manually into the code tags.

Regards.

---

### Post by papibe on 2011-07-22
For what I can understand, you have 2 NICs, but I'm seeing 3 setups for interfaces. Why? Did you edit your /etc/networks/interfaces yourself?

Regards.

---

### Post by NetDoc on 2011-07-22
> **papibe said:**
> For what I can understand, you have 2 NICs, but I'm seeing 3 setups for interfaces. Why? Did you edit your /etc/networks/interfaces yourself? 

This is a LAMP server and will be utilizing multiple IPs per NIC. It also lives amidst 10 other sister servers in my dedicated rack at Atlantic.net. They aren't having this issue.

---

### Post by NetDoc on 2011-07-22
> **papibe said:**
> Which respects indentation, then making easy to read.  Most excellent! Thanks!

---

### Post by doas777 on 2011-07-22
my first piece of advice is to strip the Network and Broadcast entries from each interface **Except eth0:1** , leaving it only with lines for auto, iface, address, netmask, and gateway. 

the network and broadcast are useless since you are using classful configuration for your address scheme (a class-c address block with a 24bit mask).

Its been some years since my ccna lapsed, but are you sure the subnetting is correct here:
[B][COLOR=blue][B]inet addr:209.208.24.242  Bcast:209.208.24.255  Mask:255.255.255.240
[/B][/COLOR][/B]

---

### Post by papibe on 2011-07-22
> **NetDoc said:**
> This is a LAMP server and will be utilizing multiple IPs per NIC...
I'm afraid that goes beyond my level of expertise. However, a few guesses: if your are not hitting the nameserver could be because:
[LIST]
[*]Maybe you're using ufw (firewall) and it is set too restricted.
[*]There's no clear route or gateway to it.
[/LIST]
To see the route table:
```
$ route -n
```
You may also try to use 'dig' to get more information on your name resolving process:
```
$ dig google.com
```
Regards.

---

### Post by NetDoc on 2011-07-23
Resolution: 

The first IP listed for a server in /etc/network/interfaces **MUST BE** a public IP and must have a public gateway. I switched the eth0 and eth0:1 and everything started to work. Notice that I have only one gateway (on the primary) but defined the network and broadcast for each additional interface. Here is my final file with all the IPs I wanted bound to this server: 

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0 eth0:1 eth0:2 eth0:3 eth0:4 eth0:5 eth0:6 eth0:7 eth1 eth1:1 eth1:2 eth1:3 eth1:4 eth1:5
iface eth0 inet static
        address 209.208.24.242
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
        gateway 209.208.24.241

iface eth0:1 inet static
        address 192.168.2.120
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255

iface eth0:2 inet static
        address 209.208.24.244
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255

iface eth0:3 inet static
        address 209.208.24.246
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
iface eth0:4 inet static
        address 209.208.24.248
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255

iface eth0:5 inet static
        address 209.208.24.250
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255

iface eth0:6 inet static
        address 209.208.24.252
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255

iface eth0:7 inet static
        address 209.208.24.254
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255

iface eth1 inet static
        address 209.208.24.243
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255

iface eth1:1 inet static
        address 209.208.24.245
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255

iface eth1:2 inet static
        address 209.208.24.247
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255

iface eth1:3 inet static
        address 209.208.24.249
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255

iface eth1:4 inet static
        address 209.208.24.251
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255

iface eth1:5 inet static
        address 209.208.24.253
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255 
```

The clue was when I pinged 8.8.8.8 (Google's nameserver) and saw that it went through 192.168.2.1, which is the private IP for sblb1. I sshed into that server and when I pinged 8.8.8.8 it actually went through 8.8.8.8! That's when I noticed that the private IP was second and had no gateway bound to it. I switched eth0 and eth0:1 and it worked. I had already saved the l-o-n-g file as oldinterfaces, so I just rm'ed interfaces and cp'ed old into interfaces repeating the process of switching eth0 and et0:1. 

Yay!!! What a great start for a Saturday!

---

### Post by papibe on 2011-07-23
Thanks for sharing the solution.
Regards.

---

### Post by NetDoc on 2011-07-23
> **papibe said:**
> Thanks for sharing the solution.
Regards.The community is only as strong as we make it. When we are having an issue and resolve it, it only helps us all understand what we are working with. My business is a large forum that runs on a number of Linux servers, but they have all been set up by others. I am always at a loss if/when I can't get them on the phone to resolve an issue. This is an effort for me to truly be in command of my domain by working through these issues one at a time. Thanks for your insights and encouragement: its what makes forums great!

---

### Post by vannia_p on 2011-07-23
> **NetDoc said:**
> The community is only as strong as we make it. When we are having an issue and resolve it, it only helps us all understand what we are working with. My business is a large forum that runs on a number of Linux servers, but they have all been set up by others. I am always at a loss if/when I can't get them on the phone to resolve an issue. This is an effort for me to truly be in command of my domain by working through these issues one at a time. Thanks for your insights and encouragement: its what makes forums great!
Very nice.. congrats

---

### Post by UltraTiga on 2011-08-08
HI. I wish there was a reply for this. I am interested in the same type of issue.  I have a similar issue,but, more complex.  I have 2 servers.  1 has the proper gateway and 2nd DNS Server is pointing to my primary DNS server and seems to work fine.  The primary on the other hand points to itself in the resolv.conf and in the interfaces files as well, but, my forwarders is to 8.8.8.8 as an example. 

My secondary server points to the primary and it seems to work ok.  Also, I have recursion turned off on the primary and not the secondary. 

If anyone can help, I'm sure we would appreciated it much. 

Thanks

Ultratiga

---

