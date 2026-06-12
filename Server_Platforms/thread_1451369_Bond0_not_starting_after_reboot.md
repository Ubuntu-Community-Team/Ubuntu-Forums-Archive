---
title: "Bond0 not starting after reboot"
date: 2010-04-10
forum: Server Platforms
---

### Post by achaiah on 2010-04-10
E7501

I am having problems with bond0 starting at boot on ubuntu server 9.10. After I do a restart I have to manually start the network with "ifup bond0". I have installed the built package ([ifenslave-2.6_1.1.0-15ubuntu1_i386.deb]("https://edge.launchpad.net/~bhavi/+archive/crickinfo/+build/1472212/+files/ifenslave-2.6_1.1.0-15ubuntu1_i386.deb") (as indicated in [Bug #482419]("https://bugs.launchpad.net/ubuntu/+bug/482419"))).

I have setup bonding for mode=6 with miimon=100 using eth0 and eth1 (both are Intel 10/100/1000 ports using an aic79xx network driver).

The contents of the aliases file are:
  alias bond0 bonding
  options bond-mode=6 miimon=100

The contents of the interfaces file are:
  auto bond0
  iface bond0 inet static
  address 192.168.15.60
  netmask 255.255.255.0
  gateway 192.168.15.1
  slaves eth0 eth1
  bond-mode 6

Any help would be appreciated.

Kevin

---

### Post by fang0654 on 2010-04-11
Do you need bond-mode 6 in the /etc/interfaces file?

Also, is there any mention of eth0/eth1/bond0 in dmesg after bootup?

---

### Post by achaiah on 2010-04-12
From what I have read regarding network interface bonding listing the mode in the interface file should be there (there were a few articles that didn't list it... I will try that later this morning and see if that works).

In the dmesg file the only mention of eth0, eth1 or bonding are the following:  

  e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
  e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
  mode=6: Unknown parameter `bond0'

Thank you,

Kevin

---

### Post by fang0654 on 2010-04-12
That looks like the mode=6 may indeed be the issue.  I have several boxes set up using mode 1, and only have it listed in the aliases, not in the interface file.

---

### Post by achaiah on 2010-04-12
I have commented out the bond-mode 6 from the interfaces file and restarted the system. Once logged in only "lo" was available and I had to start the network with 'ifup bond0'.

---

### Post by achaiah on 2010-04-13
I have tried multiple configurations and so far this is the most promising.

File: /etc/modules
  bonding mode=6 miimon=100

File: /etc/network/interfaces
  Auto bond0
  iface bond0 inet static
        address 192.168.15.60
        netmask 255.255.255.0
        gateway 192.168.15.1
        network 192.168.15.0
        broadcast 192.168.15.255
        slaves eth0 eth1

File: /etc/modprobe.d/bonding
  alias bond0 bonding

Output from dmesg  (/var/log/dmesg)
  [   18.133403] Ethernet Channel Bonding Driver: v3.5.0 (November 4, 2008 )
  [   18.133411] bonding: In ALB mode you might experience client disconnections upon reconnection of a link if the bonding module updelay parameter (0 msec) is incompatible with the forwarding delay time of the switch
  [   18.133417] bonding: MII link monitoring set to 100 ms

 With this configuration I am no longer getting the " mode=6: Unknown parameter `bond0' " error message. 

 Unfortunately I am still having to start 'bond0' manually after a restart.

---

### Post by achaiah on 2010-04-21
Any other suggestions on how to resolve this issue. I realize 10.04 is being released next week, which I just may wait until then and then do the upgrade and see what happens (this server is for my own domain web and email - so no worries if I take it down for a bit).

---

### Post by grufo on 2010-05-02
i have installed a new server with ubuntu 10.04 an tried to get bonding running.

my network config looks like that (/etc/network/interfaces):

auto bond0
iface bond0 inet static
        address 192.168.10.10
        netmask 255.255.255.0
        network 192.168.10.0
        bond-mode 0
        bond-miimon 100
        bond-slaves none

auto eth0
iface eth0 inet manual
        bond-master bond0
        bond-primary eth0 eth1 eth2

auto eth1
iface eth1 inet manual
        bond-master bond0
        bond-primary eth0 eth1 eth2

auto eth2
iface eth2 inet manual
        bond-master bond0
        bond-primary eth0 eth1 eth2

with that configuration the system starts up and ifconfig shows me all interfaces without any errors!

in "dmesg" i get the following:

[    5.115992] bonding: bond0: enslaving eth0 as an active interface with a down link.
[    5.117251] netxen_nic: eth0 NIC Link is up
[    5.611232] bonding: bond0: enslaving eth1 as an active interface with a down link.
[    5.612436] netxen_nic: eth1 NIC Link is up
[    5.707368] bonding: bond0: link status definitely up for interface eth0.
[    5.707371] bonding: bond0: link status definitely up for interface eth1.
[    5.708056] netxen_nic: eth3 NIC Link is up
[    5.882425] bonding: bond0: enslaving eth2 as an active interface with a down link.
[    5.883674] netxen_nic: eth2 NIC Link is up
[    5.907177] bonding: bond0: link status definitely up for interface eth2.

after system startup the bond0 interface does not work! i can't ping any host on the network.
but when i do a "service networking restart" the interface bond0 works great and i can ping every host!!!

i can't find the reason why bonding is only working after a networking restart, maybe there is a bug in 10.04.

the bonding configuration is nearly the same as in /usr/share/doc/ifenslave-2.6/examples/two_hotplug_ethernet documentet.

any help would be great!!!

---

### Post by leslieyiddn3 on 2011-01-08
> **achaiah said:**
> E7501I am having problems with bond0 starting at boot on ubuntu server 9.10. After I do a restart I have to manually start the network with "ifup bond0". I have installed the built package ([ifenslave-2.6_1.1.0-15ubuntu1_i386.deb](https://edge.launchpad.net/~bhavi/+archive/crickinfo/+build/1472212/+files/ifenslave-2.6_1.1.0-15ubuntu1_i386.deb) (as indicated in [Bug #482419](https://bugs.launchpad.net/ubuntu/+bug/482419))).I have [[COLOR=#000000]setup[/COLOR]](http://www.purplers.net/no/software/projectoffice.net-debut-cebit-2008.html) bonding for mode=6 with miimon=100 using eth0 and eth1 (both are Intel 10/100/1000 ports using an aic79xx network driver).The contents of the aliases file are:alias bond0 bondingoptions bond-mode=6 miimon=100The contents of the interfaces file are:auto bond0iface bond0 inet staticaddress 192.168.15.60netmask 255.255.255.0gateway 192.168.15.1slaves eth0 eth1bond-mode 6Any help would be appreciated.KevinThanks for your explanation! I got more deep understanding about this part.

---

### Post by vortmax on 2011-01-09
This is my config working on server 10.10

/etc/modprobe.d/bonding.conf
```

alias bond0 bonding
options bond0 mode=6 miimon=100

```

/etc/network/interfaces
```


# The loopback network interface
auto lo
iface lo inet loopback

#The bonded interface
auto bond0
iface bond0 inet static
  address 192.168.30.140
  gateway 192.168.30.1
  netmask 255.255.255.0
  pre-up modprobe bonding
  up ifenslave bond0 eth0 eth1
  pre-down ifenslave -d bond0 eth0 eth1
  post-down rmmod bonding

```

---

