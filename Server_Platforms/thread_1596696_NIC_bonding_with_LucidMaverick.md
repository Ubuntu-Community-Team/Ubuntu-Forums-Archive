---
title: "NIC bonding with Lucid/Maverick"
date: 2010-10-14
forum: Server Platforms
---

### Post by Solignis on 2010-10-14
Hi there,

I am pulling my hair out over this issue, I cannot figure out for the life of me how to bond NICs in Ubuntu server 10.04/10.10 correctly.

I installed ifenslave-2.6 on a fresh install. Then I tried going into the /etc/network/interfaces file and adding a new entry for bond0 to the file and adding bond-mode 6, bond-miimon 100 and slaves eth1 eth2 to the end of the bond0 config.

That did not work, it keep telling me it cannot bring up the interface even after a reboot it still does not work.

I also followed some tutorial I found online about editing /etc/modprobe.d/aliases

That did not work really well either, the interface came up but had no slaves.

Can anyone give a clue or a current method to bond interfaces in the 10.04/10.10

Thanks,
Solignis

---

### Post by tstave on 2010-10-14
For 10.04 I use something similar to this.  This is bond mode 1 but the concept is the same

To use bonding you will first need the ifenslave package.

apt-get install ifenslave

For an example lets say we have two nics and are bonding eth0 and eth1 together to a single IP 192.168.0.50. Lets assume the same network as above where the network gateway is 192.168.0.1. The changes to the /etc/network/interfaces file would look as follows:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto bond0
iface bond0 inet static
        address 192.168.0.50
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bond-slaves none
        bond-mode 1
        bond-miimon 100

auto eth0
iface eth0 inet manual
        bond-master bond0
        bond-primary eth0 eth1

auto eth1
iface eth1 inet manual
        bond-master bond0
        bond-primary eth0 eth1

Restart the Network:

/etc/init.d/networking restart

NOTE: I have noticed when working with bonding it may not be enough to restart the network. You may need to restart the computer.

Check the Network configuration:

ifconfig

The output should be similar to the following:

bond0     Link encap:Ethernet  HWaddr 00:25:64:fe:39:25  
          inet addr:192.168.0.50  Bcast:192.168.0.254  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fefe:3925/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33089 (33.0 KB)  TX bytes:7470 (7.4 KB)

eth0      Link encap:Ethernet  HWaddr 00:25:64:fe:39:25  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33089 (33.0 KB)  TX bytes:7470 (7.4 KB)
          Interrupt:24 Memory:e4000000-e4012800 

eth1      Link encap:Ethernet  HWaddr 00:25:64:fe:39:25  
          UP BROADCAST SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:25 Memory:e6000000-e6012800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2800 (2.8 KB)  TX bytes:2800 (2.8 KB)

---

### Post by Solignis on 2010-10-14
No luck

I tried it and wont bring up the interface :(

Tried service restart and system reboot. Both did no good at fixing it.

---

### Post by tstave on 2010-10-14
Could you post your /etc/network/interfaces file as well as the output from ifconfig after the network has been restarted.

---

### Post by Solignis on 2010-10-14
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 10.0.0.254
netmask 255.255.255.0
gateway 10.0.0.1

auto bond0
iface bond0 inet static
address 10.0.0.3
netmask 255.255.255.0
gateway 10.0.0.1
bond-slaves none
bond-mode 0
bond-miimon 100

auto eth1
iface eth1 inet manual
bond-master bond0
bond-primary eth1 eth2

auto eth2
iface eth2 inet manual
bond-master bond0
bond-primary eth1 eth2

```

```
san01@san01:/etc/network$ sudo /etc/init.d/networking restart
[sudo] password for san01:
 * Reconfiguring network interfaces...                                                                                                                        ssh stop/waiting
ssh start/running, process 921
SIOCSIFADDR: No such device
bond0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
bond0: ERROR while getting interface flags: No such device
Failed to bring up bond0.
ssh stop/waiting
ssh start/running, process 958
ssh stop/waiting
ssh start/running, process 981

```

I don't know why it is complaining about my netmask and address I have used the same all of the time without problem. Anyhow, enjoy.

---

### Post by ElllisD on 2010-10-14
How you're doing it is not at all how I was able to make mine work- on 10.10.

You weren't calling ifenslave to do anything.
I edited the /etc/network/interfaces file you posted, try this- it's how mine's up.

1. Make your /etc/network/interfaces look like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 10.0.0.254
        netmask 255.255.255.0
        gateway 10.0.0.1

auto bond0
iface bond0 inet static
	bond_miimon  100
	bond_mode balance-rr
	address  10.0.0.3
	netmask  255.255.255.0
	gateway  10.0.0.1
	up /sbin/ifenslave bond0 eth1 eth2
	down /sbin/ifenslave -d bond0 eth1 eth2

```

2. Create or edit your /etc/modprobe.d/aliases.conf to look like this:

```

alias bond0 bonding
options mode=0 miimon=100 downdelay=200 updelay=200

```

3. Restart your network:

```
# /etc/init.d/networking restart
```

---

### Post by ElllisD on 2010-10-14
How you're doing it is not at all how I was able to make mine work- on 10.10.

You weren't calling ifenslave to do anything.
I edited the /etc/network/interfaces file you posted, try this- it's how mine's up.

1. Make your /etc/network/interfaces look like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 10.0.0.254
        netmask 255.255.255.0
        gateway 10.0.0.1

iface eth1 inet manual

iface eth2 inet manual

auto bond0
iface bond0 inet static
	bond_miimon  100
	bond_mode balance-rr
	address  10.0.0.3
	netmask  255.255.255.0
	gateway  10.0.0.1
	up /sbin/ifenslave bond0 eth1 eth2
	down /sbin/ifenslave -d bond0 eth1 eth2

```

2. Create or edit your /etc/modprobe.d/aliases.conf to look like this:

```

alias bond0 bonding
options mode=0 miimon=100 downdelay=200 updelay=200

```

3. Restart your network:

```
# /etc/init.d/networking restart
```

---

### Post by Solignis on 2010-10-14
Woo Hoo, it works!!

Thanks, ElllisD

---

### Post by salvo84 on 2010-11-16
found this guide very useful for setting up bonding in 10.10. Thanks ElllisD!! :P

I only had two nics so I just commented out the eth0 and changed eth1 and eth2 to eth0 and eth1.

make sure you match the mode in your aliases.conf with the one you put in /etc/networking/interfaces.

You can find a list of the different modes [here]("https://help.ubuntu.com/community/UbuntuBonding").

---

### Post by liam_p on 2010-11-19
Hello,

This is just another thanks.  Bonding was working for me in 10.04 and when I upgraded to 10.10 it stopped.  Going to try with that config now.

fingers crossed!
:D

---

### Post by xentity on 2010-12-13
Hello,

this workaround worked for me for a short time, but I was still in mode=0, although mode=1 was configured. After one weekend the system failed to create the bond. I don't know why it doesn't work anymore. 

Nevertheless I find out, that this isn't the right way. As you can see here ([https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Bonded%20network%20interfaces%20must%20use%20hotplug-style%20configuration]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Bonded%20network%20interfaces%20must%20use%20hotplug-style%20configuration")), the way to create the /etc/modprobe.d/(aliases|bonding|somethingelse).conf is deprecated.

I can confirm, that NIC bonding doesn't work, does someone find a reason, why it isn't possible to use the examples from /usr/share/doc/ifenslave-2.6/README.Debian?

---

### Post by santhony on 2010-12-20
I've tried this config, and I don't see eth1 participating, in that the packets in ifconfig are not increasing for eth1.

Am I missing something?


/etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet manual

iface eth1 inet manual

auto bond0
iface bond0 inet static
	bond_miimon  100
	bond_mode balance-rr
	address  192.168.1.4
	netmask  255.255.255.0
	gateway  192.168.1.253
	up /sbin/ifenslave bond0 eth0 eth1
	down /sbin/ifenslave -d bond0 eth0 eth1


/etc/modprobe.d/alias.conf

alias bond0 bonding
options mode=0 miimon=100 downdelay=200 updelay=200

---

### Post by ion-ral on 2010-12-22
> **ElllisD said:**
> How you're doing it is not at all how I was able to make mine work- on 10.10.
 
You weren't calling ifenslave to do anything.
I edited the /etc/network/interfaces file you posted, try this- it's how mine's up.
 
1. Make your /etc/network/interfaces look like this:
 
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
 
# The loopback network interface
auto lo
iface lo inet loopback
 
# The primary network interface
auto eth0
iface eth0 inet static
        address 10.0.0.254
        netmask 255.255.255.0
        gateway 10.0.0.1
 
iface eth1 inet manual
 
iface eth2 inet manual
 
auto bond0
iface bond0 inet static
    bond_miimon  100
    bond_mode balance-rr
    address  10.0.0.3
    netmask  255.255.255.0
    gateway  10.0.0.1
    up /sbin/ifenslave bond0 eth1 eth2
    down /sbin/ifenslave -d bond0 eth1 eth2

```
 
2. Create or edit your /etc/modprobe.d/aliases.conf to look like this:
 
```

alias bond0 bonding
options mode=0 miimon=100 downdelay=200 updelay=200

```
 
3. Restart your network:
 
```
# /etc/init.d/networking restart
```
 
ok, so it only works if you activate a bond only if you add another alias (bond1)when the system reboots erorre the bond1 there...
 
alias bond0 bonding
options mode=0 miimon=100 downdelay=200 updelay=200
 
**alias bond1 bonding**
**options mode=0 miimon=100 downdelay=200 updelay=200**
 
 
 
I'm going crazy, but it is possible that ubuntu has these problems !!!!????

---

### Post by santhony on 2011-02-12
Does anyone have a good link or instructions for NIC Bonding in Ubuntu Maverick 10.10 ??

---

### Post by FanOfTuxs on 2011-02-28
There is a bug in Maverick 10.10 (at least in the amd64 version) which breaks bonding. See: [URL="https://bugs.launchpad.net/ubuntu/+source/ifenslave-2.6/+bug/714904"]https://bugs.launchpad.net/ubuntu/+source/ifenslave-2.6/+bug/714904
[/URL]

---

### Post by salvo84 on 2011-06-04
I revisited my bonding setup when I was about to create a bridge and install openVPN.

Turns out I thought it was setup correctly when it wasn't.

I have since fixed it, but apparently it's still a bug since it's not working the way it is supposed to (hotplug module or something).

I added "bonding" in /etc/modules

and made a bonding.conf in /etc/modprobe.d/

```
alias bond0 bonding
options bonding mode=2 miimon=100 downdelay=200 updelay=100
```

here is my /etc/network/interfaces
notice how I didn't have to list "bond-mode" or any other options since it is defined in my bonding.conf. When I tried to list the options in /etc/network/interfaces it wouldn't work.
```

auto lo
iface lo inet loopback

auto bond0
iface bond0 inet static
	address  192.168.1.4
	netmask  255.255.255.0
	gateway  192.168.1.1

up /sbin/ifenslave bond0 eth0 eth1
down /sbin/ifenslave -d bond0 eth0 eth1

auto eth0
iface eth0 inet manual
	bond-master bond0

auto eth1
iface eth1 inet manual
	bond-master bond0
```

sudo cat /proc/net/bonding/bond0

```
Ethernet Channel Bonding Driver: v3.6.0 (September 26, 2009)

Bonding Mode: load balancing (xor)
Transmit Hash Policy: layer2 (0)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 100
Down Delay (ms): 200

Slave Interface: eth0
MII Status: up
Link Failure Count: 0
Permanent HW addr: XX:XX:XX:XX:2d:d4

Slave Interface: eth1
MII Status: up
Link Failure Count: 0
Permanent HW addr: XX:XX:XX:XX:2d:d3
```

dmesg
```
[   18.188362] bonding: Ethernet Channel Bonding Driver: v3.6.0 (September 26, 2009)
[   18.188375] bonding: MII link monitoring set to 100 ms
[   18.711091] ADDRCONF(NETDEV_UP): bond0: link is not ready
[   18.894000] bonding: bond0: enslaving eth0 as an active interface with an up link.
[   19.008296] bonding: bond0: enslaving eth1 as an active interface with an up link.
[   19.020599] bonding: bond0: link status definitely up for interface eth0.
[   19.020609] bonding: bond0: link status definitely up for interface eth1.
[   19.021194] ADDRCONF(NETDEV_CHANGE): bond0: link becomes ready
[   29.350016] bond0: no IPv6 routers present
```

---

### Post by hamedhmd on 2012-01-29
Hi
I just wanted to know is it possible to add bond from shell? for example using ip command or ifconfig command.
I am in such a situation that I need to add bond without making changes to interfaces or aliases.conf.

thanks

---

