---
title: "Networking needs to be restarted frequently (revisited)"
date: 2007-06-16
forum: Server Platforms
---

### Post by juantao on 2007-06-16
Last week I wrote that my new LAMP server needed to have its networking restarted every morning or I couldn't ssh in or see my webpages from home.

traceroute shows maybe there's a problem with my ISPs routing (?)

Home IP 69.9.151.x (dynamic)
69.9.146.28 (FreeBSD box that never goes down)
69.9.146.90 (Ubuntu LAMP server frequently unreachable)
(both the 69.9.146.x addresses come from the same DSL modem > out to a switch > out to the two boxes).

Here's a letter I wrote to my ISP, but maybe you can help me sooner.

...
I thought changing the OS, or the NIC, or the cables, or the switch, or the motherboard, or the moon-phase would solve my problem (where I sometimes can't connect to one of my static IPs) but nothing has fixed it so far.

I did a traceroute test and maybe it's something you can fix at your end (?) Or, maybe you have come across this before and know what I can do (?). 

I can trace 69.9.146.28 in about 2 seconds. When I first try 69.9.146.90 it will finally go through in about 120 seconds. If I wait it out, and let it succeed, my webpages pop right up and if I run that traceroute again I can reach the destination in about 2 seconds.

===================

jondowd@homesara:~$ traceroute 69.9.146.28
traceroute to 69.9.146.28 (69.9.146.28), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  0.597 ms  0.609 ms  0.485 ms
 2  core0-medford.mind.net (69.9.150.1)  62.663 ms  164.949 ms  158.950 ms
 3  69-9-146-28.dsl.mind.net (69.9.146.28)  94.463 ms  94.275 ms  93.802 ms

jondowd@homesara:~$ traceroute 69.9.146.90
traceroute to 69.9.146.90 (69.9.146.90), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  0.584 ms  0.581 ms  0.476 ms
 2  core0-medford.mind.net (69.9.150.1)  51.339 ms  46.822 ms  47.011 ms
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * 69-9-146-90.dsl.mind.net (69.9.146.90)  144.117 ms  95.080 ms

jondowd@homesara:~$ traceroute 69.9.146.90
traceroute to 69.9.146.90 (69.9.146.90), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  0.569 ms  0.627 ms  0.497 ms
 2  core0-medford.mind.net (69.9.150.1)  51.863 ms  47.461 ms  47.003 ms
 3  69-9-146-90.dsl.mind.net (69.9.146.90)  95.558 ms  96.321 ms  95.281 ms

====================

Thanks for looking : - )

---

### Post by Mr. C. on 2007-06-18
I asked in your previous post about why you are connected at 10Mbit, half-duplex, but you didn't respond.  You claim you are connected via a switch, but the data implies a hub.  Can you clarify ?

It is highly unlikely that routing problems are the issue here.

It is possible this is your issue:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=401435](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=401435)
[http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/](http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/)
[http://marc.info/?l=postfix-users&m=115739945701551](http://marc.info/?l=postfix-users&m=115739945701551) 

MrC

---

### Post by juantao on 2007-06-19
Mr. C., Thanks for your patience (boy - HS graduation, wife - Masters degree - busy June) The 'switch' was 10Mbs. I've replaced it with a newer 10/100 - but the problem persists. I'm not knowledgeable enough to implement any of the remedies for the tcp_window_scaling issue (without some hand-holding), but still confused how I can't ssh to the box from home, but can ssh to a different box in the same room and from that box ssh to the box I couldn't reach from 5 miles away... Once I get in, and restart the network all is well for a few hours.

---

### Post by Mr. C. on 2007-06-19
No problem.  That's one very old switch!

The issue with the window scaling is a router problem in conjunction with recent changes made to the linux kernel.  Being able to connect to another box, and then connect to your linux box via that path is in alignment with how the issue manifests itself.

The remedy is a simple pari of cat commands:

```
echo "4096 16384 131072" > /proc/sys/net/ipv4/tcp_wmem
echo "4096 87380 174760" > /proc/sys/net/ipv4/tcp_rmem
```

and/or

```
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
```

These values revert after reboot, so no harm done in trying.
MrC

---

### Post by juantao on 2007-06-19
Cool. Thank you. I've run all three commands, we'll see what the morning brings.

---

### Post by juantao on 2007-06-19
Even though I did
echo "4096 16384 131072" > /proc/sys/net/ipv4/tcp_wmem
echo "4096 87380 174760" > /proc/sys/net/ipv4/tcp_rmem

and

echo 0 > /proc/sys/net/ipv4/tcp_window_scaling 

I had to restart the networking yet again.

1. Can't ssh to the Ubuntu box at my shop from home or reach any domains hosted there.
2. Am able to ssh to a FreeBSD box at my shop from home.
3. From the FreeBSD box I can ssh to the Ubuntu box (two feet away)
4. Once I'm logged into the Ubuntu box I can do /etc/init.d/networking restart and
5. Once the networking has restarted, the problems described in 1. disappear.

I haven't been able to pinpoint the time it take for the failure, but it seems to happen over night.
Thanks for helping.

---

### Post by Mr. C. on 2007-06-19
Have you checked your router for settings on packet fragementation ?

MrC

---

### Post by turinglabs on 2007-06-19
> **juantao said:**
> 
1. Can't ssh to the Ubuntu box at my shop from home or reach any domains hosted there.
2. Am able to ssh to a FreeBSD box at my shop from home.
3. From the FreeBSD box I can ssh to the Ubuntu box (two feet away)
4. Once I'm logged into the Ubuntu box I can do /etc/init.d/networking restart and
5. Once the networking has restarted, the problems described in 1. disappear.


Since the problem is fixed by the network restart, something must be different with your networking config before step 4 and after, when access is restored. With that in mind, get a snapshot of your networking setup 1) when all is working and 2) when internet access to your ubuntu box has failed, but before you restart networking.  Ideally you would want to see

- ifconfig -a
- netstat -rn
- arp -vn
- cat /etc/iftab

It might be worth trying to find the smallest change that restores your access, so rather than doing a full network restart, try just bouncing an interface 'ifdown eth1 && ifup eth1', for example. 

Another thought - perhaps you are a victim of the asynchronous network interface naming of the newer Linux kernels. How often is this box rebooted, if at all ('last' will show you prior reboots, perhaps an overnight power failure)? Does your ubuntu box have any other network interfaces that are not being used? Are there frequent link-state changes to any of your interfaces (e.g., 'egrep 'eth[0|1]' /var/log/kern.log')?

---

### Post by juantao on 2007-06-20
Here's the output of some of your suggestions. I'll check these again in the morning. Now that my wife's domain is back on my FreeBSD box, I can leave this ubuntu box in a 'network down' state long enough to come to the shop and run these commands locally.

Thanks for all your assistance : - )

root@CDOserver:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:60:08:11:F0:A9
          inet addr:69.9.146.90  Bcast:69.9.146.255  Mask:255.255.255.0
          inet6 addr: fe80::260:8ff:fe11:f0a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:437 errors:0 dropped:0 overruns:0 frame:0
          TX packets:205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:270907 (264.5 KiB)  TX bytes:18309 (17.8 KiB)
          Interrupt:18 Base address:0xd000

eth1      Link encap:Ethernet  HWaddr 00:48:54:84:54:C8
          inet addr:192.168.4.2  Bcast:192.168.4.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1088 (1.0 KiB)  TX bytes:1088 (1.0 KiB)


root@CDOserver:~# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
69.9.146.0      0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.4.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         192.168.4.1     0.0.0.0         UG        0 0          0 eth1
0.0.0.0         69.9.146.1      0.0.0.0         UG        0 0          0 eth0

root@CDOserver:~# arp -vn
Address                  HWtype  HWaddress           Flags Mask            Iface
69.9.146.1               ether   00:D0:97:9C:90:A0   C                     eth0
69.9.146.28              ether   00:E0:4C:82:48:45   C                     eth0
Entries: 2      Skipped: 0      Found: 2

root@CDOserver:~# cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:60:08:11:f0:a9 arp 1
eth1 mac 00:48:54:84:54:c8 arp 1

root@CDOserver:~# egrep 'eth[0|1]' /var/log/kern.log
Jun 19 21:20:24 CDOserver kernel: [   28.904111] eth1: RealTek RTL8139 at 0xf8862000, 00:48:54:84:54:c8, IRQ 19
Jun 19 21:20:24 CDOserver kernel: [   28.904114] eth1:  Identified 8139 chip type 'RTL-8139B'
Jun 19 21:20:24 CDOserver kernel: [   35.083111] eth0:  setting half-duplex.
Jun 19 21:20:32 CDOserver kernel: [   46.394589] eth0: no IPv6 routers present
Jun 19 21:23:24 CDOserver kernel: [  217.890609] eth0:  setting half-duplex.
Jun 19 21:23:24 CDOserver kernel: [  217.924730] eth1: link down
Jun 19 21:23:24 CDOserver kernel: [  217.924765] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 19 21:23:34 CDOserver kernel: [  228.395238] eth0: no IPv6 routers present

root@CDOserver:~# last
jondowd  pts/0        69-9-146-28.dsl. Tue Jun 19 21:25   still logged in
jondowd  tty1                          Tue Jun 19 21:21    gone - no logout
reboot   system boot  2.6.20-15-server Tue Jun 19 21:20 - 21:31  (00:11)

wtmp begins Tue Jun 19 21:20:24 2007

---

### Post by Mr. C. on 2007-06-20
Why do you have two default routes?  This is a misconfiguration.  Remove the extraneous default route.

MrC

---

### Post by juantao on 2007-06-20
How do I remove one and which one?

Here I've commented out the last line in my interfaces file:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 69.9.146.90
        netmask 255.255.255.0
        gateway 69.9.146.1

# The LAN network interface
auto eth1
iface eth1 inet static
        address 192.168.4.2
        netmask 255.255.255.0
#       gateway 192.168.4.1

Now netstat shows this:
root@CDOserver:~# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
69.9.146.0      0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.4.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         69.9.146.1      0.0.0.0         UG        0 0          0 eth0

Is this correct?

---

### Post by Mr. C. on 2007-06-20
Its correct if you have all the network access you desire (I don't recall which interface led to your internet gateway, or if you mentioned that).

The two default routes nonsense is a network manager bug.  There should be only 1 default route, which by definition is the route used when no specific host or network route matches.

MrC

---

### Post by juantao on 2007-06-20
eth0 faces my DSL modem and uses a static IP address of 69.9.146.90

eth1 is not in use yet, but I hope to use it to provide NAT to a small LAN. based on this info, is my 'interfaces' file correct now?

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 69.9.146.90
netmask 255.255.255.0
gateway 69.9.146.1

# The LAN network interface
auto eth1
iface eth1 inet static
address 192.168.4.2
netmask 255.255.255.0
# gateway 192.168.4.1

---

### Post by Mr. C. on 2007-06-20
Got it.  Yup, looks ok.

MrC

---

### Post by juantao on 2007-06-20
8 hours later... IT'S RUNNING !!!

Thank you MrC ! 

My little error of having two gateways in my interfaces file has caused me trouble for more than a month! 

Next question. The sample dhcpd.conf files sometimes show a 'option routers' with an IP address of 192.168.x.x - What should I have there, the gateway for my DSL connection?

Here's my /etc/network/interfaces followed by a potential /etc/dhcp3/dhcpd.conf file. What should I declare in the place of 'option broadcast-address' & 'option routers' ? Do you see any other problems?

=======================
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 69.9.146.90
        netmask 255.255.255.0
        gateway 69.9.146.1

# The LAN network interface
auto eth1
iface eth1 inet static
        address 192.168.4.2
        netmask 255.255.255.0
#       gateway 192.168.4.1 
=======================
# Sample /etc/dhcpd.conf
# (add your comments here)
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
# ?? option broadcast-address 192.168.1.255;
# ?? option routers 192.168.1.254;
option domain-name-servers 69.9.146.28, 69.9.129.9;
option domain-name "CDOserver";

subnet 192.168.4.0 netmask 255.255.255.0 {
range 192.168.4.10 192.168.4.50;
}

---

### Post by Mr. C. on 2007-06-20
Good to hear.

man dhcp-options yields :
>        option routers ip-address [, ip-address...  ];

          The routers option specifies a list of IP addresses for  routers  on
          the  client's  subnet.  Routers should be listed in order of prefer-
          ence.

A router's job is to switch packets from one network to another.  The routers option here allows you to specify which routers you want clients to know about when your DHCP server replies to DHCP requests.  In your case, you have only one router; it is at the other end of the cable connected to your Ubuntu system.  Another way to look at this option is to ask: "where should my systems send packets that go to another network?".  Answer: your router (i.e. its IP).

MrC

---

