---
title: "ubuntu server disconnection issue"
date: 2024-06-23
forum: Server Platforms
---

### Post by eraknix on 2024-06-23
Hello,
I set up a web server based on ubuntu a while ago. I had initially set it up under ubuntu desktop, but as the problem persisted I switched to ubuntu server (the latest LTS version, everything is up to date with apt).
The server disconnects randomly from the internet (it's connected via ethernet). I can't even see it on my box's configuration page. I only have ports 80 and 443 open on my box and I have set up a dmz on the server from my box. I am currently with red by sfr (a French operator) with a NB6VAC-FXC-r1 box and a NB6VAC-MAIN-R4.0.45d program version. I have only installed the nextcloud package on the server using snap (I had previously configured owncloud). I've also set up a static local IP address for the server on my box's control panel.
Is this a server configuration problem? Server security? Or the box itself?
Have a nice day.
PS: I'm French, sorry in advance if my English is bad...

---

### Post by TheFu on 2024-06-23
Less discussion. More facts.  Run commands to show what you think the issues are.  Please show the exact, full, command AND the output from it. Wrap both in forum code-tags.

I'm confused about a DMZ for a system hosted at a provider. That doesn't make any sense. Those systems are already on the public internet and don't generally have any firewall rules, unless you added some to the system.  The only firewall rules I've seen in my VPS hosts are that SMTP traffic was blocked, until I asked them to unblock it. Besides that, it was open to the world until I set up some ipset block rules to keep the nastiest parts of the internet away.

Also "latest LTS" isn't clear.  Exactly, which release?  **lsb_release -d** will tell us.  "Latest" is never specific enough, since we don't know what YOU believe.

---

### Post by currentshaft on 2024-06-23
> **eraknix said:**
> server disconnects randomly from the internet 

What does this mean? What objective facts, tools and reasoning did you use to come to this conclusion?

---

### Post by eraknix on 2024-06-23
Hello,
Thank you for your answers. I may have misspoken, but the machine is at my home and I host the server there. The lsb_release -d command gave "Ubuntu 24.04 LTS". I know it's not connected because I can't access it via ssh even on the local network (it's not even connected to the local network any more). On my internet box page, it is not displayed, it is only when I physically restart it that it reconnects.
What commands would you like me to run?
Thanks again.

---

### Post by currentshaft on 2024-06-23
Perhaps another device on the local network shares an IP address? Are you using DHCP or static assignments?

"sudo tcpdump -qni any arp" would reveal such a common problem.

---

### Post by TheFu on 2024-06-23
Please use forum code tags to post the exact commands and output.

I don't care which commands you run. What commands do you believe you should run to prove your statements?  ssh is very high up a software stack.  Perhaps if you started lower and checked for basic connectivity, basic network services, and check bi-directionally (from outside the host and inside the host)?  

These forums are full of posts where people claim they don't have connectivity.  What commands did the helpers ask them to run?  Have you run those? What were the EXACT results?  <---- this is another hint to show your work.

BTW, this question comes up so often that I wrote a blog article about it in 2013 - [https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) . That's one way to go, but there are almost always 50 different solutions to any Unix problem.

I'll be gone for a while, perhaps until Monday.  My LUG is meeting in a few minutes and life does get in the way for all of us.

---

### Post by TheFu on 2024-06-23
> **currentshaft said:**
> Perhaps another device on the local network shares an IP address? Are you using DHCP or static assignments?

"sudo tcpdump -qni any arp" would reveal such a common problem.

Way to jump to step 45 of troubleshooting this type of issue.  There are so many much more likely problems to check first before throwing someone into tcpdump.

---

### Post by eraknix on 2024-06-23
Thanks for your answers, I'm going to follow the advice on the site when the server stops working, the problem is that I don't know when..., just the ```
dmesg |grep eth[0-9]
``` command didn't do anything, even with sudo.
Have a nice day.

---

### Post by TheFu on 2024-06-23
It is important to do things in the correct order and share the results - IN THAT ORDER.

---

### Post by eraknix on 2024-06-23
Ok, for the command ```
ip addr
``` :
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 30:9c:23:ac:99:96 brd ff:ff:ff:ff:ff:ff
    altname enp33s0
    inet 192.168.1.87/24 metric 100 brd 192.168.1.255 scope global dynamic eno1
       valid_lft 70635sec preferred_lft 70635sec
    inet6 fe80::329c:23ff:feac:9996/64 scope link
       valid_lft forever preferred_lft forever

```
for ```
route -n
``` :
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eno1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1
192.168.1.1     0.0.0.0         255.255.255.255 UH    100    0        0 eno1

```
all the pings tests went well. (It's normal because there is no problem now)
For ```
dmesg |grep eth[0-9]
``` :
```
dmesg: read kernel buffer failed: Operation not permitted
```
and with sudo, nothing happens.
For ```
sudo lshw -C network
``` :
```
*-network
       description: Ethernet interface
       product: I211 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:21:00.0
       logical name: eno1
       version: 03
       serial: 30:9c:23:ac:99:96
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=6.8.0-35-generic duplex=full firmware=0. 6-2 ip=192.168.1.87 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:25 memory:fc900000-fc91ffff ioport:f000(size=32) memory:fc920000-fc923fff

```
For ```
ifconfig -a
``` :
```
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.87  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::329c:23ff:feac:9996  prefixlen 64  scopeid 0x20<link>
        ether 30:9c:23:ac:99:96  txqueuelen 1000  (Ethernet)
        RX packets 5094979  bytes 7634868115 (7.6 GB)
        RX errors 0  dropped 9398  overruns 0  frame 0
        TX packets 931656  bytes 63270606 (63.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0xfc900000-fc91ffff


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 19087  bytes 10049009 (10.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 19087  bytes 10049009 (10.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
For ```
more /etc/resolv.conf
``` :
```
# This is /run/systemd/resolve/stub-resolv.conf managed by man:systemd-resolved(8).
# Do not edit.
#
# This file might be symlinked as /etc/resolv.conf. If you're looking at
# /etc/resolv.conf and seeing this text, you have followed the symlink.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "resolvectl status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs should typically not access this file directly, but only
# through the symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a
# different way, replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.


nameserver 127.0.0.53
options edns0 trust-ad
search .

```
and finally for ```
route
``` :
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         box             0.0.0.0         UG    100    0        0 eno1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1
box             0.0.0.0         255.255.255.255 UH    100    0        0 eno1

```

For the pings, it doesn't reach 192.168.1.0, I don't know if it's normal or not.

Thanks again.

---

### Post by TheFu on 2024-06-23
When it doesn't work, run those commands again and see what's different.
I'd start with the pings ... local, the gateway, then a public IP.  If all those work, it isn't a network issue at all. 

Probably just a DNS issue.  Search for forum posts about solving that.  There are many ways to do that.  The way I fixed it forever isn't what most people would do, but you can find those posts in these forums and follow them if you like.  Or wait until someone else comes and explains how to make systemd-resolved work.

---

### Post by currentshaft on 2024-06-23
> **TheFu said:**
> Way to jump to step 45 of troubleshooting this type of issue.  There are so many much more likely problems to check first before throwing someone into tcpdump.

Not really. Packet loss is best diagnosed with a tool to dump packets. Novice users setting static IP assignments and having conflicts on the local network is more common than you think.

---

### Post by currentshaft on 2024-06-23
> **TheFu said:**
> When it doesn't work, run those commands again and see what's different.
I'd start with the pings ... local, the gateway, then a public IP.  If all those work, it isn't a network issue at all. 

Probably just a DNS issue.  Search for forum posts about solving that.  There are many ways to do that.  The way I fixed it forever isn't what most people would do, but you can find those posts in these forums and follow them if you like.  Or wait until someone else comes and explains how to make systemd-resolved work.

It's not a DNS issue, because as OP said, SSH stops working.

ping for networking troubleshooting hasn't been useful since about 1998. Most, if not all, secure networks have blocked ICMP traffic years and years ago.

---

### Post by darkod on 2024-06-24
I don't want to steal the thread but I might be having the same/similar problem. I am busy these days but I was planning to open a thread of my own soon to see if anyone more expert than me can help. As some might know, I can find my way in ubuntu but this problem has puzzled me for years.

I think I first noticed it in Ubuntu Server 18.04, then after an in-place upgrade to 20.04 it continued. At that time I was using HDDs in mdadm raid1 for the OS. After that I moved to SSDs in mdadm raid1 for OS and to see if it will help I did a clean new install of 22.04, which I am running now. But the problem is still here.

What my server does is that it simply stops communicating over the network. All light are still on as normal, fans running, HDD led seems to have ocassional activity, but no network, ping, ssh, nothing. Like you pulled the cable out (but connectivity LED on the NIC and the switch port still shows as normal).

Obviously without ssh at that moment it is difficult to troubleshoot. I have Supermicro board with IPMI but honestly I don't know too much about IPMI to check if maybe there is local console connection available through it. And I don't have my IPMI port plugged in usually (still working on additional wall RJ-45 socket).

After a reset it boots normal, and all looks fine. Until the next time. It might "freeze" again the next day, or three weeks later. No apparent rule. CPU temp seems in "normal" range, never seen it above 52-55º C when I can access the server.

No load of any kind on this server, basically it's for my personal home stuff and ocassional Plex viewing. Really embarassing calling it a server. :)

But this network freeze I really can't figure out. As soon as I can I will follow the linked troubleshooting guide to see if I detect something, and I will open my own thread as I said. Just mentioning my experience here, since initially it sounds similar. Network not working suddenly with no apparent reason.

---

### Post by TheFu on 2024-06-24
Darknod, sometimes integrated NICs fail.  I'd drop in a $25 Intel PRO/1000 NIC.  BTW, certain types of packets going though certain NICs have been known to brick the NIC.  In the 2000s, some Intel Server NICs made in their Mexico plant could be bricked with certain VoIP traffic.  Took too many years to figure that out, but I got lucky with a replacement NIC that was made somewhere else and never had the issue again.  Then a few years later, I came across an Intel blog article discussing the VoIP traffic/NIC issue.  I'd had exactly that model card.

Over the decades, I've seen very few NIC issues on servers, though the company standard was for redundant connections, always, for everything.  When I started running lots of stuff at home, I found that Realtek NICs failed much more often and used more CPU than Intel. Plus the BSDs didn't have good Realtek NIC drivers, so if you use BSD as your way to choose good Linux hardware like I do, then you quickly learn to avoid Realtek and certain other wifi chips (if you use wifi at all).

I'd much rather have a NIC that fails completely than a NIC that causes data corruption.  So having a completely failed NIC is really a good thing, at least in my book.  I have a few spare NICs laying around here to help with troubleshooting these sorts of issues.  They usually aren't Intel - rather they are the NICs that I replaced with Intel after some issue happened.

---

### Post by Doug S on 2024-06-24
> **eraknix said:**
> 
For ```
dmesg |grep eth[0-9]
``` :
```
dmesg: read kernel buffer failed: Operation not permitted
```
and with sudo, nothing happens.


Try using your actual network interface name:

```
sudo dmesg | grep eno1
```

Example, using my NIC name:

```
doug@s19:~/idle/teo/util2$ [COLOR="#FF0000"]sudo dmesg |grep enp3s0[/COLOR]
[    1.293486] igc 0000:03:00.0 enp3s0: renamed from eth0
[    3.475712] br0: port 1(enp3s0) entered blocking state
[    3.475717] br0: port 1(enp3s0) entered disabled state
[    3.475723] igc 0000:03:00.0 enp3s0: entered allmulticast mode
[    3.475745] igc 0000:03:00.0 enp3s0: entered promiscuous mode
[    6.377479] igc 0000:03:00.0 enp3s0: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[    6.481225] br0: port 1(enp3s0) entered blocking state
[    6.481229] br0: port 1(enp3s0) entered forwarding state
```

---

### Post by Doug S on 2024-06-24
> **currentshaft said:**
> It's not a DNS issue, because as OP said, SSH stops working.

ping for networking troubleshooting hasn't been useful since about 1998. Most, if not all, secure networks have blocked ICMP traffic years and years ago.

Was the SSH attempt via IP address or host name?

With respect, I disagree about "ping". I still think it is one of best low level tools for debugging network issues. But, yes one needs to be aware of potential no responding points. Once I get beyond my gateway, I know that Google's 8.8.8.8 address always responds to ping.

From another post, I agree with using tcpdump to help.

---

### Post by eraknix on 2024-06-24
Hello, I tried for SSH with with local IP address so here it's 192.168.1.87.
For ```
sudo dmesg | grep eno1
``` :
The same as before without sudo, I have the same message and with sudo, there's nothing.
I have to wait the next bug to retest all the commands, I have installed the graphics card this morning, so the next time I will be able to test. 
For ```
sudo tcpdump -qni any arp
``` : 
```
tcpdump: data link type LINUX_SLL2
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on any, link-type LINUX_SLL2 (Linux cooked v2), snapshot length 262144 bytes
15:07:35.182020 eno1  B   ARP, Request who-has 192.168.1.1 tell 192.168.1.77, length 46
15:07:40.286167 eno1  B   ARP, Request who-has 192.168.1.1 tell 192.168.1.77, length 46
15:07:45.391190 eno1  B   ARP, Request who-has 192.168.1.1 tell 192.168.1.77, length 46
15:07:50.491959 eno1  B   ARP, Request who-has 192.168.1.1 tell 192.168.1.77, length 46
15:07:51.833359 eno1  In  ARP, Request who-has 192.168.1.87 tell 192.168.1.1, length 46
15:07:51.833381 eno1  Out ARP, Reply 192.168.1.87 is-at 30:9c:23:ac:99:96, length 28
15:07:55.597250 eno1  B   ARP, Request who-has 192.168.1.1 tell 192.168.1.77, length 46
15:08:00.699396 eno1  B   ARP, Request who-has 192.168.1.1 tell 192.168.1.77, length 46
15:08:05.804398 eno1  B   ARP, Request who-has 192.168.1.1 tell 192.168.1.77, length 46
15:08:10.908392 eno1  B   ARP, Request who-has 192.168.1.1 tell 192.168.1.77, length 46
15:08:16.013473 eno1  B   ARP, Request who-has 192.168.1.1 tell 192.168.1.77, length 46
15:08:16.298147 eno1  In  ARP, Request who-has 192.168.1.87 tell 192.168.1.1, length 46
15:08:16.298170 eno1  Out ARP, Reply 192.168.1.87 is-at 30:9c:23:ac:99:96, length 28
15:08:21.117382 eno1  B   ARP, Request who-has 192.168.1.1 tell 192.168.1.77, length 46
15:08:26.222772 eno1  B   ARP, Request who-has 192.168.1.1 tell 192.168.1.77, length 46
15:08:31.326779 eno1  B   ARP, Request who-has 192.168.1.1 tell 192.168.1.77, length 46
15:08:36.431881 eno1  B   ARP, Request who-has 192.168.1.1 tell 192.168.1.77, length 46
15:08:41.536217 eno1  B   ARP, Request who-has 192.168.1.1 tell 192.168.1.77, length 46
15:08:46.641679 eno1  B   ARP, Request who-has 192.168.1.1 tell 192.168.1.77, length 46
15:08:51.747006 eno1  B   ARP, Request who-has 192.168.1.1 tell 192.168.1.77, length 46
15:08:54.139991 eno1  In  ARP, Request who-has 192.168.1.87 tell 192.168.1.1, length 46
15:08:54.140016 eno1  Out ARP, Reply 192.168.1.87 is-at 30:9c:23:ac:99:96, length 28
15:08:56.849744 eno1  B   ARP, Request who-has 192.168.1.1 tell 192.168.1.77, length 46
^C
23 packets captured
24 packets received by filter
0 packets dropped by kernel

```
192.168.1.77 is my netatmo relay (it's my connected thermostat), I don't know why it's here.
Tanks for the responses.

---

### Post by currentshaft on 2024-06-25
If you run "arp -a" does it show an entry in the cache?

---

### Post by darkod on 2024-06-25
FYI in my case dmesg doesn't give any helpful info. Only what I understand to be the initialization of the NIC at OS load:
```
darko@filesrv:~$ sudo dmesg | grep eno1
[sudo] password for darko: 
[    7.872635] igb 0000:03:00.0 eno1: renamed from eth0
[   14.573649] igb 0000:03:00.0 eno1: igb: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
```

PS. What TheFu suggested about getting a new NIC is good idea although I would like to avoid using one of the few PCIE slots that I have for a NIC. After using simple home boards for my "server" for years I finally got a Supermicro X11-SCL server board with double NIC and it would be shame if it turns out I can't use them. :)

I have some USB-to-RJ45 laying around, they might be a way to do some temporary testing acting as new NIC without buying anything yet or populating a PCIE slot.

---

