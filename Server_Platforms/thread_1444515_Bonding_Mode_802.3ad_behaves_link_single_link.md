---
title: "Bonding Mode 802.3ad behaves link single link"
date: 2010-04-01
forum: Server Platforms
---

### Post by kofi2 on 2010-04-01
Hi
 
I'm struggling with a test setup trying to learn Bonding with 802.3ad LACP.
I have a quad Port 100Mbit card that uses the 'sundance' module.
 
First I was lucky with a elderly Managed 3Com SuperStack 4400 the ubuntu Server was spitting out roughly 40MB/s over the 4 aggregated links when I was downloading a single file via Aapache.
 
Unfortunately I had to switch harddisk and my collegue flashed - so a complete re-do was necessary. I followed Ubuntu's and Debian's bonding advises (e.g [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding) - I have exactly this config at the end) which are basically exactly the same when using newer Versions.
 
Failover between the links seems working but 'bmon' reports only 1 Port being thus hitting 100Mbit/s link speed limit. Sometimes speed goesway down very instable between 2-6 MB/s
 
The Switch is a 3Com SuperStack 4400, RSTP and LACP enabled on concerned ports.
My Test-Client is connected directly to the single Gbit Port of the switch.
 
Any idea what is going wrong? - I'm confused because last time I was impressioned by the speed I was able to get with 802.3ad bonding aka mode 4.

---

### Post by xianthax on 2010-04-01
Make sure you don't have exactly the configuration in that tutorial.  For instance it tells you to put:

 alias bond0 bonding
 options bonding mode=0 miimon=100

into:

/etc/modprobe.d/bonding.conf

then later sets a different mode in /etc/network/interfaces (it sets mode=4 in this file)

make sure that the mode setting in /etc/modprobe.d/bonding.conf is mode=4 and the setting in /etc/network/interfaces is also mode=4. 

What version of ubuntu are you using?  i've had bonded setups on 8.04 -> 9.10 and haven't noticed any bugs.  However, make sure you remove network-manager if its installed, it will mess with things.  I found it would cause the system to connect via one of the individual interfaces rather than the bond0 interface.

If none of this works, i've found reseting and reconfiguring the switch tends to solve many network problems.

---

### Post by kofi2 on 2010-04-03
Hi
 
I'm using Ubuntu Server 9.04, having also tried Debian lenny (minimal, without desktop). Thus network-manager is not installed, at least aptitude tells so. :-)
 
I did only configure in /etc/network/interfaces as following:
```
 
# Disabled other eth0 interfaces leaving loopback as is.
 
auto bond0
 iface bond0 inet static
 slaves all (tried also with 'eth0 eth1 et2 eth3' veryfying udev rules)
 address <myIP>
 gateway <myGate>
 netmask 255.255.255.0
 bond-mode 4 (tried also with '802.3ad' instead)
 bond-miimon 100

```
 
Ubuntu and Debian recommend for newer releases to only enter bonding settings directly into /etc/networking/interfaces - Seems that there has been a shift in the way you have to configure bonding.
 
See also: [http://wiki.debian.org/Bonding](http://wiki.debian.org/Bonding)
 
Hmm, what I see, if I hit 100Mbit, that all traffic goes through eth0. And dmesg tells me with each interface:
```
 
 
bonding: bond0 setting mode to 802.3ad (4)
...
bondng: bond0 enslaving eth<X> as backup interface wiah an uplink
... finaly saying:
,,, bond0: link becomes ready.

```
 
I've tried to add the /etc/modprobe.d/bonding.conf without success after reboot.
Will do another factory reset of the switch - which already has latest Firmware...

---

