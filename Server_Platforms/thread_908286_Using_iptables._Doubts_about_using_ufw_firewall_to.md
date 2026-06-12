---
title: "Using iptables. Doubts about using ufw firewall too"
date: 2008-09-02
forum: Server Platforms
---

### Post by zazuzimbo on 2008-09-02
Hi, :)

   I am running an Ubuntu Server 8.04.1 with 2 network interfaces. One of them is connected to the internet. The other I use to serve the internal network. I use IP_FORWARDING from one interface to another so the internal network has internet access too. I also have Squid and SquidGuard up for filtering their content.

   Now I need to block all access to server ports, except for internet(http/https). Then I will open other ports on demand.

   1. If I enable ufw, will it clear the iptables' rules I have now? Or will simply add restricions to it?

   2. When I do commands like:
      - ufw allow proto tcp from any to any port 22
      - ufw default deny
      Do I need to put them on source /etc/init.d/ script to get them up when the server reboots? That was not clear to me from the documents I have read.

   Thank you in advance.

Zazuzimbo

References:
[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)
[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)
and these forums.

---

### Post by jamesrfla on 2008-09-02
iptables blocks all the ports except the ones that programs need to use I believe.

---

### Post by zazuzimbo on 2008-09-03
> iptables blocks all the ports except the ones that programs need to use I believe.

And from which file it knows what ports to allow. /etc/services?

If I can deny most of them easily I can achieve the same thing I will do with ufw. But without having to put to ufw the rules I use now directly with iptables.

I am unfamiliar with all this, any comment you say would be very helpfull.

Kindly,

Zazu

---

### Post by heebus on 2008-09-03
Here is some documentation for iptables.

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by zazuzimbo on 2008-09-04
Ok, that howto gave me a doubt about how to save and restore iptables.

Piece from the howto:

[FONT="Courier New"]
auto eth0
iface eth0 inet dhcp
  pre-up iptables-restore < /etc/iptables.rules
  post-down iptables-save -c > /etc/iptables.rules
[/FONT]

I have 2 interfaces, eth0 and eth1. I am also using a PPP interface, and eth0 will be "replaced" by ppp0. Do I have to put pre-up and predown on each interface configuration? Or in just one of them is enough? Does it matter wich do I choose?

My /etc/networks/interfaces file is:

[FONT="Courier New"]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

mapping hotplug
        script grep
        map eth0

auto eth0
iface eth0 inet static
        address  192.168.4.100
        netmask 255.255.255.0
        network 192.168.4.0
        gateway 10.10.0.100
        broadcast 192.168.4.255

auto eth1
iface eth1 inet static
        address 10.10.0.200
        netmask 255.255.255.0
        network 10.10.0.0
        broadcast 10.10.0.255
        gateway 10.10.0.100

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
[/FONT]

---

### Post by lmno149 on 2008-09-04
[mesos](http://games.groups.yahoo.com/group/mesos_01/)[potbs gold](http://games.groups.yahoo.com/group/potbs_gold_01/)[rf gold](http://games.groups.yahoo.com/group/rf_gold/)[rohan gold](http://games.groups.yahoo.com/group/rohan_gold_01/)[silkroad gold](http://games.groups.yahoo.com/group/silkroad_gold/)

---

### Post by zazuzimbo on 2008-09-04
Maybe I weren´t clear from were I took that ideia. It was from the howto heebus suggested. I edited my previous answer to make this clear.

---

