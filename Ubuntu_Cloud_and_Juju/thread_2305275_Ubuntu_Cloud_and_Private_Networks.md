---
title: "Ubuntu Cloud and Private Networks"
date: 2015-12-04
forum: Ubuntu Cloud and Juju
---

### Post by cr396 on 2015-12-04
I have two Ubuntu Cloud 15.10 images running as VM's in KVM.  They are both in 192.168 space, but different subnets.  I have them connected with switches and routers.  But when I ping host B (192.168.56.100) to host A (192.168.57.100), there is no reply.  Through tcpdump, I know the Ping request is getting to host B's network stack.  But no reply is even attempted.  The weird thing is I can ping host A from host B, and the exact same thing happens ... the request gets to host A, but a reply is never generated.  Oh, and this happens for TCP protocols too, not just ICMP/Ping.  

I have a similar setup with two Ubuntu Desktop images, and the same thing DOES NOT occur.  That makes me think there's something in Ubuntu Cloud that's killing the packet.  I kinda understand this ... you don't normally want private cloud instances to have their own networks and talk to one another.  But is this the case?  And what component filters it out?  (It's not iptables, I have that shut off).

---

### Post by TheFu on 2015-12-04
Welcome to the forums.

If there isn't a router handling the routing between subnets, then packets should be ignored.
From each box, run
* ifconfig
* route

So we get a clear understanding of what you are really doing based on facts.  We'll expect 5 or 6 sets of outputs, please. 1 set from each box.

---

### Post by cr396 on 2015-12-04
With pleasure!  From Host A:


[FONT=courier new]ubuntu@ubuntu:~$ ifconfig | less[/FONT]
[FONT=courier new]eth0      Link encap:Ethernet  HWaddr 00:11:22:ee:ee:ee  [/FONT]
[FONT=courier new]          inet addr:192.168.56.100  Bcast:192.168.56.255  Mask:255.255.255.0[/FONT]
[FONT=courier new]          inet6 addr: fe80::211:22ff:feee:eeee/64 Scope:Link[/FONT]
[FONT=courier new]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=courier new]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:1000 [/FONT]
[FONT=courier new]          RX bytes:0 (0.0 B)  TX bytes:4274 (4.2 KB)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]lo        Link encap:Local Loopback  [/FONT]
[FONT=courier new]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
[FONT=courier new]          inet6 addr: ::1/128 Scope:Host[/FONT]
[FONT=courier new]          UP LOOPBACK RUNNING  MTU:65536  Metric:1[/FONT]
[FONT=courier new]          RX packets:1780 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:1780 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:0 [/FONT]
[FONT=courier new]          RX bytes:131752 (131.7 KB)  TX bytes:131752 (131.7 KB)[/FONT]


[FONT=courier new]lxcbr0    Link encap:Ethernet  HWaddr 22:b8:69:c3:74:0c  [/FONT]
[FONT=courier new]          inet addr:10.0.3.1  Bcast:0.0.0.0  Mask:255.255.255.0[/FONT]
[FONT=courier new]          inet6 addr: fe80::20b8:69ff:fec3:740c/64 Scope:Link[/FONT]
[FONT=courier new]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=courier new]          RX packets:0 errors[/FONT]
[FONT=courier new]         TX packets:7 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:0 [/FONT]
[FONT=courier new]          RX bytes:0 (0.0 B)  TX bytes:570 (570.0 B)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]ubuntu@ubuntu:~$ arp[/FONT]
[FONT=courier new]Address                  HWtype  HWaddress           Flags Mask            Iface[/FONT]
[FONT=courier new]192.168.157.100          ether   00:11:22:cc:cc:c1   CM                    eth0[/FONT]
[FONT=courier new]192.168.56.1             ether   00:11:22:cc:cc:c1   CM                    eth0[/FONT]
[FONT=courier new]192.168.157.1            ether   00:11:22:cc:cc:c1   CM                    eth0[/FONT]
[FONT=courier new]192.168.161.1            ether   00:11:22:cc:cc:c3   CM                    eth0[/FONT]
[FONT=courier new]192.168.159.1            ether   00:11:22:cc:cc:c2   CM                    eth0[/FONT]
[FONT=courier new]192.168.57.100           ether   00:11:22:cc:cc:c1   CM                    eth0[/FONT]
[FONT=courier new]192.168.156.1            ether   00:11:22:cc:cc:c1   CM                    eth0[/FONT]
[FONT=courier new]192.168.160.1            ether   00:11:22:cc:cc:c3   CM                    eth0[/FONT]
[FONT=courier new]192.168.158.1            ether   00:11:22:cc:cc:c2   CM                    eth0[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]ubuntu@ubuntu:~$ ip route[/FONT]
[FONT=courier new]default via 192.168.56.1 dev eth0 [/FONT]
[FONT=courier new]10.0.3.0/24 dev lxcbr0  proto kernel  scope link  src 10.0.3.1 [/FONT]
[FONT=courier new]192.168.56.0/24 dev eth0  proto kernel  scope link  src 192.168.56.100 [/FONT]


------------------------------------------------------
And from Host B:


[FONT=courier new]ubuntu@ubuntu:~$ ifconfig | less[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]eth0      Link encap:Ethernet  HWaddr 00:11:22:dd:dd:dd  [/FONT]
[FONT=courier new]          inet addr:192.168.57.100  Bcast:192.168.57.255  Mask:255.255.255.0[/FONT]
[FONT=courier new]          inet6 addr: fe80::211:22ff:fedd:dddd/64 Scope:Link[/FONT]
[FONT=courier new]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=courier new]          RX packets:9 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:1000 [/FONT]
[FONT=courier new]          RX bytes:891 (891.0 B)  TX bytes:648 (648.0 B)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]lo        Link encap:Local Loopback  [/FONT]
[FONT=courier new]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
[FONT=courier new]          inet6 addr: ::1/128 Scope:Host[/FONT]
[FONT=courier new]          UP LOOPBACK RUNNING  MTU:65536  Metric:1[/FONT]
[FONT=courier new]          RX packets:2604 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:2604 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:0 [/FONT]
[FONT=courier new]          RX bytes:193236 (193.2 KB)  TX bytes:193236 (193.2 KB)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]lxcbr0    Link encap:Ethernet  HWaddr 46:21:19:47:96:72  [/FONT]
[FONT=courier new]          inet addr:10.0.3.1  Bcast:0.0.0.0  Mask:255.255.255.0[/FONT]
[FONT=courier new]          inet6 addr: fe80::4421:19ff:fe47:9672/64 Scope:Link[/FONT]
[FONT=courier new]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=courier new]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:0 [/FONT]
[FONT=courier new]          RX bytes:0 (0.0 B)  TX bytes:570 (570.0 B)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]ubuntu@ubuntu:~$ arp[/FONT]
[FONT=courier new]Address                  HWtype  HWaddress           Flags Mask            Iface[/FONT]
[FONT=courier new]192.168.157.1            ether   00:11:22:cc:cc:c4   CM                    eth0[/FONT]
[FONT=courier new]192.168.156.100          ether   00:11:22:cc:cc:c4   CM                    eth0[/FONT]
[FONT=courier new]192.168.159.1            ether   00:11:22:cc:cc:c5   CM                    eth0[/FONT]
[FONT=courier new]192.168.156.1            ether   00:11:22:cc:cc:c4   CM                    eth0[/FONT]
[FONT=courier new]192.168.57.1             ether   00:11:22:cc:cc:c4   CM                    eth0[/FONT]
[FONT=courier new]192.168.161.1            ether   00:11:22:cc:cc:c6   CM                    eth0[/FONT]
[FONT=courier new]192.168.56.100           ether   00:11:22:cc:cc:c4   CM                    eth0[/FONT]
[FONT=courier new]192.168.158.1            ether   00:11:22:cc:cc:c5   CM                    eth0[/FONT]
[FONT=courier new]192.168.160.1            ether   00:11:22:cc:cc:c6   CM                    eth0[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]ubuntu@ubuntu:~$ ip route[/FONT]
[FONT=courier new]default via 192.168.57.1 dev eth0 [/FONT]
[FONT=courier new]10.0.3.0/24 dev lxcbr0  proto kernel  scope link  src 10.0.3.1 [/FONT]
[FONT=courier new]192.168.57.0/24 dev eth0  proto kernel  scope link  src 192.168.57.100 [/FONT]


------------------------------------------------------
Now on Host A, I do a ping of host B:


[FONT=courier new]ubuntu@ubuntu:~$ ping 196.168.57.100[/FONT]
[FONT=courier new]PING 196.168.57.100 (196.168.57.100) 56(84) bytes of data.[/FONT]
 ... < hangs > ...


And I can see the requests come in on host B, but no replies are generated:


[FONT=courier new]ubuntu@ubuntu:~$ sudo tcpdump -i eth0[/FONT]
[FONT=courier new]sudo: unable to resolve host ubuntu[/FONT]
[FONT=courier new]tcpdump: verbose output suppressed, use -v or -vv for full protocol decode[/FONT]
[FONT=courier new]listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes[/FONT]
[FONT=courier new]16:11:04.893086 IP 192.168.156.100 > 192.168.57.100: ICMP echo request, id 1019, seq 30, length 64[/FONT]
[FONT=courier new]16:11:05.901065 IP 192.168.156.100 > 192.168.57.100: ICMP echo request, id 1019, seq 31, length 64[/FONT]
[FONT=courier new]16:11:06.909101 IP 192.168.156.100 > 192.168.57.100: ICMP echo request, id 1019, seq 32, length 64[/FONT]
[FONT=courier new]16:11:07.917088 IP 192.168.156.100 > 192.168.57.100: ICMP echo request, id 1019, seq 33, length 64[/FONT]
[FONT=courier new]16:11:08.924986 IP 192.168.156.100 > 192.168.57.100: ICMP echo request, id 1019, seq 34, length 64[/FONT]
[FONT=courier new]16:11:09.932857 IP 192.168.156.100 > 192.168.57.100: ICMP echo request, id 1019, seq 35, length 64[/FONT]
[FONT=courier new]16:11:10.941072 IP 192.168.156.100 > 192.168.57.100: ICMP echo request, id 1019, seq 36, length 64[/FONT]
[FONT=courier new]16:11:11.949069 IP 192.168.156.100 > 192.168.57.100: ICMP echo request, id 1019, seq 37, length 64[/FONT]
[FONT=courier new]16:11:12.956532 IP 192.168.156.100 > 192.168.57.100: ICMP echo request, id 1019, seq 38, length 64[/FONT]
[FONT=courier new]^C[/FONT]
[FONT=courier new]9 packets captured[/FONT]
[FONT=courier new]9 packets received by filter[/FONT]
[FONT=courier new]0 packets dropped by kernel[/FONT]


---------------------------
Yep, and it's weird that the ping appears to be coming from 192.168.156.100, but that's a little IP rewriting going on in my switch+router infrastructure.  The important thing is the requests come to the right host.  And if I do a ping to 192.168.156.100, I get the exact same effect (requests get to host A, but A never generates replies).

---

### Post by TheFu on 2015-12-04
a) hostnames should all be different. Can't tell which host is which it will cause issues with some protocols if FQDN aren't unique later.  I'm not calling you a liar, but seeing is believing.
b) I'm old and don't know how to read "ip route" commands. "route" was requested 'cause that's what I've been reading for 20+ yrs and it puts output in a format I understand completely. Someday I might have to learn 'ip' commands.  Someday.
c) we're used to "code" tags so things line up. Thanks for using monospace font. No action needed. Generally, changing fonts here is frowned upon. The mods will change it to the default font so people don't go crazy when it doesn't make sense.

arp just shows that a dumb switch is connecting these things. Not useful for non-ethernet traffic/protocols (local-link).  Routing is mandatory between 2 different subnets. That can be performed either with routers or with static routes added to each machine.  This is often required for 2-system networking when just a cable is used - a manual route must be added for each machine to locate the other machine.

Do you have 2 routers?
* 192.168.56.1
* 192.168.57.1
???? That's what the output seems to say.  And do those routers know how route traffic between each other's networks?

BTW, that was just 2 systems. Where are the desktops and the VM host OSes?

---

### Post by cr396 on 2015-12-04
A couple of people and I finally narrowed down the problem.  It doesn't look like it's a problem with Ubuntu Cloud in particular, or the fact that it was on 192.168 subnets.  If a packet arrives with:

- Correct IP Address
- BUT the Incorrect MAC Address

The packet will be dropped regardless of iptables, etc.  And this is true even though the packet was delivered to the "right" NIC (in this case, by an instance of OpenVSwitch that we had programmed to do exactly what it was doing).   Real switches and routers would NEVER do this, just our crazy SDN ones.  Once we set them straight, everything worked fine.

Thanks for looking at this, and for the tips on proper request formatting, etc.  For the record, yes, there was a router between the two subnets - one and only one - which was working properly.  The host OS was Ubuntu 15.10 Desktop.  All VM's were KVM/QEMU.

---

### Post by iulianpojar on 2016-02-15
your netmask 255.255.255.0 does not allow this connections from one subnet to another.
should be 255.255.0.0 to work

---

