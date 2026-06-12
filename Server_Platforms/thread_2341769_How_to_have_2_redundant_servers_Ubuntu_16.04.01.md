---
title: "How to have 2 redundant servers Ubuntu 16.04.01 ???"
date: 2016-10-31
forum: Server Platforms
---

### Post by rhandy2 on 2016-10-31
Hello


I use ubuntu 16.04.01 and virtual/webmin.


I know virtualmin/webmin can add and manage clusters.


But I never try it.


PLEASE GIVE SOME GUIDE LINES TO:


SCENARIO


2 SERVERS RUNNING UBUNTU 16.04.01 AND VIRTUALMIN
1 Master and 1 StandBy (2nd Server)
I would like second 2nd server is one sincronized copy of the master and in case of it fails, 2nd assume its position.


Questions.


Virtualmin sincronized 2 server by rpc, or I need other software?


I see one article about Heartbeat, But I think HeartBeat only make monitor of servers.


Is possible have this configuration at home with only one external IP?


How 2nd Server assume Internal Ip Adrress of the Master?


Thank You

---

### Post by TheFu on 2016-10-31
You can do anything you want with the skills, hardware and time.  Whether it is a useful solution or not is a different question - for true HA, if there is just a single WAN provider, then no. But if you just want to learn how to set up HA for yourself, then it can be useful.

HA is usually redundant networking, power, storage, CPUs.  All of those are needed to guarantee 5 9's of uptime. This is non-trivial and usually impossible in a home environment.  OTOH, to learn about these things with hands on experience **is** something we can do at home with minimal (or some people's idea of minimal) costs. 

There are lots of ways to get greater availability for servers.  Have never used webmin (and never plan to), so cannot help with that specifically, but there are standard ways to accomplish higher availability - there are methods of application availability and there are methods for platform availability.  

Each of these overall methods have specific techniques based on the toolset used.  

For example, my blog webapp runs on multiple VMs on different servers, but there is only 1 DB server (because it is a blog and it doesn't matter THAT much). Also, I have only 1 load balancer/reverse proxy to direct inbound traffic to one of the webapp servers and keep track of which client sessions need to be sent back to which app-server.  Of course, RAID10 storage is used for everything and redundant networking with separate switch infrastructure is used for the storage network and the front-end network and the management networks - that's 6 NICs for every server. This is common practice.

OTOH, it might be easier to use whole machine failover if your infrastructure is using virtual machines. Each VM technology provides a way to do this - ESXi, Proxmox, oVirt, and qemu-kvm all do.  This way you failover the entire VM, not just an application running inside.  Redundant storage is needed and you'll still have to handle any load balancing and database replication in a smart way, if that is required for your "cluster."

OTOH, if you are still using webmin, are you ready to handle clustering? It can be complicated.
[https://sheepdog.github.io/sheepdog/](https://sheepdog.github.io/sheepdog/) is a method that might work for you. I haven't tried it on 16.04 - that release is too new for us to use. It has stack requirements that might not fit your setup.

Anyway, lots to learn and this is definitely a project for someone at home.  If you just want the shortest distance to a solution, install a proxmox cluster.

---

### Post by rhandy2 on 2016-11-01
Hello

TheFu. Before I try to work on 2 real servers I try starting use only Heartbeat for test at home using virtualbox and 2 virtual machines running ubuntu 14.04.

I´m a beginner and i´m trying to learn more and more.

I read this tutorial [https://www.digitalocean.com/community/tutorials/how-to-create-a-high-availability-setup-with-heartbeat-and-floating-ips-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-create-a-high-availability-setup-with-heartbeat-and-floating-ips-on-ubuntu-14-04)

But my ip is not floating.

But I think I have to change /etc/network/interfaces on both machines.>  auto eht0
[COLOR=#666666][FONT=Consolas]iface eth0 inet dhcp[/FONT][/COLOR] but I think I have to change for > iface eht0 inet static
address:
netmask:
gateway
.

---

### Post by TheFu on 2016-11-01
You need 3 IPs.  2 static and 1 floating.  Won't work otherwise.
Also, eht0 is wrong - 99.9999% certain that is a typo.

Looks like you want to do application-level HA.  I don't do that anymore. Too much effort. IMHO, there are easier, better, ways - spelled out above.

BTW, if you are serious about this - dump virtualbox. NOBODY uses vbox in data centers.

BTW, there are many, many, youtube videos that show how to do clustering for HA.
For example: [https://www.youtube.com/watch?v=zlORo0TETgU](https://www.youtube.com/watch?v=zlORo0TETgU)

---

### Post by rhandy2 on 2016-11-01
TheFu.

1st - I have 2 servers Like this  >>> [one]("http://www.ebay.com/itm/HP-ProLiant-SE316M1-Server-2x-Xeon-L5520-QC-2-27-GHz-16-GB-RAM-292-GB-SAS-/151905292635?hash=item235e42d15b:g:zLsAAOSwcBhWYcDq") with 4 drives each in RAID 10

But before I try working on real servers. I´m testing using virtualbox.

Network Config one server 1:

/etc/network/interfaces
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static


address 192.168.10.3
netmask 255.255.255.0
network 192.168.10.0
broadcast 192.168.10.255
gateway 192.168.10.254


auto eth1
iface eth1 inet static


address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255




Netwok Config one server 2:

/etc/network/interfaces
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static


address 192.168.10.4
netmask 255.255.255.0
network 192.168.10.0
broadcast 192.168.10.255
gateway 192.168.10.254


auto eth1
iface eth1 inet static


address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255




On both servers

/etc/heartbeat/authkeys


> auth 1
1 sha1 MySecretPassPhrase



/etc/heartbeat/haresources


> master 192.168.10.2


On 1st server (master)


/etc/heartbeat/ha.cf


> logfacility daemon
keepalive 2
deadtime 15
warntime 5
initdead 120
udpport 694
ucast eth1 192.168.10.4 # Slave ip server.
auto_failback on
node master #  hostname of Master.
node slave #  hostname of Slave.
respawn hacluster /usr/lib/heartbeat/ipfail
use_logd yes
On 2nd server (slave)

/etc/heartbeat/ha.cf


> logfacility daemon
keepalive 2
deadtime 15
warntime 5
initdead 120
udpport 694
ucast eth1 192.168.10.3 # Master ip server.
auto_failback on
node master # hostname of Master.
node slave # hostname of servidor Slave.
respawn hacluster /usr/lib/heartbeat/ipfail
use_logd yes


add this line to [COLOR=#000000][FONT=tahoma]/etc/sysctl.conf

[/FONT][/COLOR]> [COLOR=#555555][FONT=tahoma]*net.ipv4.ip_nonlocal_bind=1*[/FONT][/COLOR]

/etc/hosts on both
> 192.168.1.2 slave
192.168.1.1 master


Ok. heart beat is working, but I have one issue.

When i shutdown master, slave takes ip and run on floating ip. but when I start master again, ip still with slave until I shut it down.

---

### Post by rhandy2 on 2016-11-01
No is time to try sheepdog. But I only have 2 real servers. Is possible use it ?

---

