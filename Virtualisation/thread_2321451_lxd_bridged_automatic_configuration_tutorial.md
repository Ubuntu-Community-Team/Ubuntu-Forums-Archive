---
title: "lxd: bridged automatic configuration tutorial?"
date: 2016-04-22
forum: Virtualisation
---

### Post by ivo-welch on 2016-04-22
dear experts:

I have used two virtual instances of vmware player, all on 14.04 (host + 2 guests), because it made it easy to move virtual machines to different hardware and because it gives some extra security isolation to different web hosts.  hardware is exceedingly simple, with one network adapter,
```
   Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 04)

```on the motherboard.

with ubuntu 16.04 out now, I am thinking of moving away from my old vmware setup.  lxc/lxd look appealing.  this would be easy, except that my organization firmly requires bridged networking (not NAT or host-only), and I am not a network expert.  the one nice thing about vmplayer is that it is one click in the network settings and everything rolls.  (I fought with kvm in the distant past, but then gave up.  it was not possible for me to follow along to get the bridged networking to go.  the instructions were spread out over too many different pages, with needs to become experts on networking first.)

so, I need a good tutorial for a new install of a gui-16.04 as host with (two) new installs of server-16.04 with bridged networking.  just out of the box.  nothing modified.  I hope this is easy.  does anyone know of such a tutorial?

/iaw

---

### Post by hondaman on 2016-04-22
I'm not an expert by any means, but I figured out last night how to do static ip's for the guests and they appear on my network side by side with everything else.  Is that what you would like to do?

---

### Post by MAFoElffen on 2016-04-23
Questions before I answer this (because you said you only have one network card).

Do you really require Linux containers with the same NID as your host network? Or is that you need to make services available to the outside?

If you need it to be on the same NID, then yes, bridge... But you say you only have one NIC, so you can't. bridge the way most set up a bridge ... That would take a NIC to do the bridge.. If your host needs access to the world, (at least that way) it cannot use that same NIC. 

This basic reference uses that: [LXC Networking Guide]("https://www.flockport.com/lxc-networking-guide/")

NAT goes through the same NIC as the host's connection. You could forward your services through the NAT with routing rules and port forwarding...

Now, there is a newer/different way to do it following this guide that only uses one NIC to do [Simple Bridge]("https://wiki.debian.org/LXC/SimpleBridge"). It takes a lot more manual configuration of files (under the covers) to do this...
> 
**Host device as bridge**

Features:
 - persisted in host's /etc/network/interfaces
 - the container's veth virtual ethernet interface can share the network link on the physical interface of the host (eth0). So the container resides on the same ethernet segment and talks to the same dhcp server as the host does.
<Requires bridge-utils package.>


---

### Post by ivo-welch on 2016-04-23
I am not really sure what I am doing, which is part of the problem here.  essentially, I want to run a few webservers (funnydomain1.info, odddomain2.info, ...) on ipv4 for the internet, each in its linux guest container.  each guest container has its own IP address.  somehow, VM is smart enough to make this all transparent.  they all share the host ethernet card.  (how vm bridges eth automatically is beyond me.  ifconfig on the host does show a vmnet1 and vmnet8.)

for installation, I am looking at  [https://linuxcontainers.org/lxd/getting-started-cli/](https://linuxcontainers.org/lxd/getting-started-cli/) .  I have done

> host# apt install lxd
host# lxc launch ubuntu:16.04 first
Creating first
host# du -h -d0 /var/lib/lxd1.5G	lxd
host# lxc launch ubuntu:16.04 second
Creating second
host#  lxc list
+--------+---------+------+------+------------+-----------+
|  NAME  |  STATE  | IPV4 | IPV6 |    TYPE    | SNAPSHOTS |
+--------+---------+------+------+------------+-----------+
| first  | RUNNING |      |      | PERSISTENT | 0         |
+--------+---------+------+------+------------+-----------+
| second | RUNNING |      |      | PERSISTENT | 0         |
+--------+---------+------+------+------------+-----------+



now I need to start following the networking guide, [https://www.flockport.com/lxc-networking-guide/](https://www.flockport.com/lxc-networking-guide/) .  I decided I may as well try both solution and see if one works.  I changed /etc/network/interfaces on the host according to the instructions and rebooted.  now I seem a vethPGBH5C and vethV3F3LO (slightly randomized) in my ifconfig, too.  however, unlike the vmnet* entries, there are no inet addr, only inet6 addr on the two veth* entries.  (I am also still running vmplayer on the host for a few guests, at least until I figure out how to get lxd to work.)

reading on in the networking guide, the instructions refer to /var/lib/lxc/... , but this is probably outdated.  instead, I see /var/lib/lxd and /var/lib/lxd-bridge .  there is also no /etc/default/lxc file on my machine.  there is an /etc/default/lxd-bridge file, however.  I know this is new stuff, so docs are not always updated, and 16.04 may have changed stuff.  maybe my fingering around in the darkness can help the docs improve...apologies, everyone.  I hope to post at the end a simple step-by-step set of instructions to get this done.

/iaw

---

### Post by MAFoElffen on 2016-04-24
I'll look at my config later this morning. And confirm my directory structure and what "mine" looks like, as compared to that guide.

EDIT-- I just looked through your post #4 in detail...

You installed LXD instead of LXC. So yes, you would have /var/lib/lsd instead of /var/lib/lxc... Basically, think of [LXD]("http://www.ubuntu.com/cloud/lxd") as the next generation of LXC. I'm thinking LX**[COLOR=#ff8c00]C[/COLOR]**+1 = LXD ... When you are following guides, if you just interchange "lxd" for lxc, you will be okay... For instance in the networking, LXC uses a default NAT bridge called bvrlxc, whereas LXD uses an default NAT bridge called brlxd...

You are fine. In fact LXD is an Ubuntu Server Edition 16.04 LTS default package, and is installed/works on it out of the box. One thing I notice in the new install, is that a fresh install of the new SE installs brlxd as brlxc, but gives instructions in that install on how to convert it to brlxd (with one command). 

On my new fresh install, I'll copy and post that for reference. I sometimes do from 5-10 installs a day, and while in the mix, take that for granted).

---

### Post by ivo-welch on 2016-04-25
thanks, MAFOElffen (spell right? ;-) ).  there are is a lot of novice-confusing lxc/lxd there.  I understand that lxd is newer and simplified and better, but I never knew the old lxc, so I am indifferent.  except, that many guides for lxd seem to use the lxc command linux utility. my problem is, I hope, the sort of thing that someone with experience will hopefully spot immediately, but I would never figure it out. 

I definitely need a Host Bridge, not a NAT Bridge.  (Our networking guy is around on Mondays!)

I started with the guide and added

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_stp off
bridge_fd 0
bridge_maxwait 0
```

and then rebooted.  (I assume it is a matter of indifference that vmplayer is also running, and using vmnet1 and vmnet8 automatically, too.)

Following on in the instructions suggested files like /var/lib/lx*/<containername>/config , and the directory structure seems to have changed to /var/lib/lxd/containers/<containername>, but there are no config files in these containers, nor are there any files in /var/lib/lxd/* anywhere that contain the word lxc.network.type .  so, this is probably a dead end.  the /etc/default/lxd-bridge file is not supposed to be updated.  so I did not touch it.

another install guide recommended (note the desperation in my following random install guides):

```

lxc profile device set default eth0 parent br0

```

reboot, and I see on the host

```
br0       Link encap:Ethernet  HWaddr fe:87:f2:d5:b4:c4
          inet6 addr: fe80::deleted-for-post/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10584 (10.5 KB)  TX bytes:6453 (6.4 KB)


eno1      Link encap:Ethernet  HWaddr deleted-for-post
          inet addr:164.deleted-for-post  Bcast:164...191  Mask:255.255.255.192
          inet6 addr: fe80::deleted-for-post/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5771944 (5.7 MB)  TX bytes:2813282 (2.8 MB)
          Interrupt:20 Memory:f7c00000-f7c20000


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:47900 (47.9 KB)  TX bytes:47900 (47.9 KB)


lxdbr0    Link encap:Ethernet  HWaddr 52:c3:49:f9:1b:56
          inet6 addr: fe80::50c3:49ff:fef9:1b56/64 Scope:Link
          inet6 addr: fe80::1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:3791 (3.7 KB)


vethC6HRA0 Link encap:Ethernet  HWaddr fe:87:f2:d5:b4:c4
          inet6 addr: fe80::fc87:f2ff:fed5:b4c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9540 (9.5 KB)  TX bytes:5565 (5.5 KB)



```

when one container is running.  when it stops, the veth* goes away. both br0 and lxdbr0 stay.  so, my bridge seems to be doing something.  yeah...

not so yeah---there seems to be no ipv4 associated with it:

```

host# lxc exec first -- /bin/bash
root@first:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:3e:1f:5b:8f
          inet6 addr: fe80::216:3eff:fe1f:5b8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5755 (5.7 KB)  TX bytes:9540 (9.5 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:2068 (2.0 KB)  TX bytes:2068 (2.0 KB)

```

---

