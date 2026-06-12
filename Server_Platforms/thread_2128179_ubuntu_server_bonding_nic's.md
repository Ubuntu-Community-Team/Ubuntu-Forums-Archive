---
title: "ubuntu server bonding nic's"
date: 2013-03-22
forum: Server Platforms
---

### Post by brianmills on 2013-03-22
Hi, I'm trying to setup bonding using 802.3ad.

I have a FreeNas server with bonded NIC's setup and they seem to be working. 
I have 2 ubuntu 12.04 servers, I've just installed new Intel dual I350 NIC's in them. 
I then used this guide [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding) to try and bond the nic's together. 
They are both connected to a HP ProCurve 1810G 24 port switch, and I've setup trunk ports on the connections. 
One server, is working, and the other is not. 
I have installed ifenslave-2.6 package. 
I've added 'bonding' to /etc/modules file
I've restarted networking, added bonding with 'sudo modprobe bonding'

On the server that doesn't work:
- /proc/net/bonding/bond0 doesn't exist
- the eth0 and eth1 interfaces don't come up when viewing ifconfig
- sudo ifenslave bond0 eth0 eth1 command gives this error: 
Master 'bond0': Error: handshake with driver failed. Aborting
- the bond0 interface does exist in ifconfig, and you can ping the static IP given to it, but nothing else. 

Any Idea's why it doesn't come up on this server?

---

### Post by albandy on 2013-03-22
> **brianmills said:**
> Hi, I'm trying to setup bonding using 802.3ad.

I have a FreeNas server with bonded NIC's setup and they seem to be working. 
I have 2 ubuntu 12.04 servers, I've just installed new Intel dual I350 NIC's in them. 
I then used this guide [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding) to try and bond the nic's together. 
They are both connected to a HP ProCurve 1810G 24 port switch, and I've setup trunk ports on the connections. 
One server, is working, and the other is not. 
I have installed ifenslave-2.6 package. 
I've added 'bonding' to /etc/modules file
I've restarted networking, added bonding with 'sudo modprobe bonding'

On the server that doesn't work:
- /proc/net/bonding/bond0 doesn't exist
- the eth0 and eth1 interfaces don't come up when viewing ifconfig
- sudo ifenslave bond0 eth0 eth1 command gives this error: 
Master 'bond0': Error: handshake with driver failed. Aborting
- the bond0 interface does exist in ifconfig, and you can ping the static IP given to it, but nothing else. 

Any Idea's why it doesn't come up on this server?

Can you post your /etc/network/interfaces file ?

---

### Post by hash4all on 2013-03-22
Please see the below link, might be it help you
[http://bertrand.gotpike.org/space/start/2007-12-11/1?PSESSIONID=43c8256bb2399fba211b](http://bertrand.gotpike.org/space/start/2007-12-11/1?PSESSIONID=43c8256bb2399fba211b)

Thanks

---

### Post by brianmills on 2013-03-22
That would have been useful of me. Here it is. 

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth2
iface eth2 inet static
  address 10.1.2.40
  netmask 255.255.255.0
  network 10.1.2.0
  gateway 10.1.2.1
  broadcast 10.1.2.255
  dns-search millsit.net ad.millsit.net
  dns-nameservers 10.1.2.1


auto eth0
iface eth0 inet manual
  bond-master bond1


auto eth1
iface eth1 inet manual
  bond-master bond1


auto bond1
iface bond1 inet static
  address 10.1.5.40
  netmask 255.255.255.0
  network 10.1.5.0
  broadcast 10.1.5.255
  bond-mode 802.3ad
  mond-slaves none
  bond-miimon 100
  bond-lacp-rate 1

---

### Post by brianmills on 2013-03-22
I've had a look at that link, the symptoms match, however after adding these lines in /etc/modprobe.d/aliases

alias bond0 bonding
options bonding mode=1 miimon=100 downdelay=200 updelay=200 max_bonds=1

and rebooting, no luck. On running 
sudo ifup bond0

I get:
ifup: interface bond0 already configured

however, eth0 and eth1 are not listed on ifconfig
there is now a file/status in /proc/net/bonding/bond0

$ cat /proc/net/bonding/bond0
Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)


Bonding Mode: fault-tolerance (active-backup)
Primary Slave: None
Currently Active Slave: None
MII Status: down
MII Polling Interval (ms): 100
Up Delay (ms): 200
Down Delay (ms): 200

---

