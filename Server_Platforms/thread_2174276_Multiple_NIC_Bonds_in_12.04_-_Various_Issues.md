---
title: "Multiple NIC Bonds in 12.04 - Various Issues"
date: 2013-09-13
forum: Server Platforms
---

### Post by Zach_Wolf on 2013-09-13
Hey all. 

I have installed Ubuntu Server 12.04 x64 on an HP Proliant DL380 G7 (dual CPUs, 24GB RAM, RAID 5 - 300GB). Clean install, nothing else is on the machine. Virtualizing this machine isn't an option or I would already have done that. 

I am trying to bond the network connections of the built in 4-port Broadcom NIC with an HP 331T adapter (Broadcom). Both are gigabit and are recognized by Ubuntu (latest firmware has been applied to everything). 

I am trying to create two bonds (bond0 and bond1), corresponding to the front-end and back-end network. Each bond has a single connection to each NIC. 

I have done an extensive amount of troubleshooting/reading over the past 2 days and have had a little bit of success, but I have run into issues at every step. Most of what I read out there deals with creating a single bond between multiple interfaces. There is virtually no information on creating multiple bonds over multiple interfaces. I am looking for anyone's help/input. It would be greatly appreciated! I figure someone out there has done this in Ubuntu before. 

Some important reads:
[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding) (very lacking in regards to having multiple bonds- I plan to add to this webpage once I have this working) 
[https://www.kernel.org/pub/linux/kernel/people/marcelo/linux-2.4/Documentation/networking/bonding.txt](https://www.kernel.org/pub/linux/kernel/people/marcelo/linux-2.4/Documentation/networking/bonding.txt) (ifenslave howto) 
[http://ubuntuforums.org/archive/index.php/t-1888967.html](http://ubuntuforums.org/archive/index.php/t-1888967.html) (talks about multiple bonds) 

As it stands right now, I have both bonds *mostly* working. If I only wanted a single bond, I would have no problems. The second bond is where the problems start. 

-The server hangs at boot trying to start bond1 (which is the 2nd bond). After around 5 minutes, the server finally boots and everything works fine (including bond1) 
-Restarting the networking service causes bond1 to become unresponsive. I have to restart the entire machine to get bond1 back. Trying "ifup bond1" results in various issues like "bond1 is already configured/is already up". 
I have also tried "sudo networking service stop %% sudo networking service start", same issue.

Config Files: (have tried virtually every combination of parameters- the following is what got me the furthest)

/etc/modprobe.d/bonding.conf

> alias bond0 bonding        options bond0 mode=4 lacp_rate=1 miimon=100 max_bonds=2
alias bond1 bonding options bond1 mode=4 lacp_rate=1 miimon=100 max_bonds=2


/etc/network/interfaces (no gateway needed on bond1 - backend)

> 
auto eth3
iface eth3 inet manual
bond-master bond0


auto eth4
iface eth4 inet manual
bond-master bond0


auto bond0
iface bond0 inet static
        address 10.100.0.60
        netmask 255.255.255.0
        gateway 10.100.0.1
        dns-nameservers 10.100.0.53 10.100.0.54
post-up ifenslave bond0 eth3 eth4
pre-down ifenslave -d bond0 eth3 eth4


auto eth0
iface eth0 inet manual
bond-master bond1


auto eth1
iface eth1 inet manual
bond-master bond1


auto bond1
iface bond1 inet static
        address X.X.X.X
        netmask 255.255.255.0
post-up ifenslave bond1 eth0 eth1
pre-down ifenslave -d bond1 eth0 eth1


/etc/modules
> 
loop
lp
rtc
bonding


---

### Post by hawkmage on 2013-09-13
I have not used the pre-down and post up for bonding since before 12.04 but then again I have not done multiple bonds in a while.

I the systems I have with a single LACP bonds I do the following.

Add the bonding line to the /etc/modules, I do not put anything in /etc/modprobe.d/ for the bonding.

In the interfaces file I have something like this:
```
auto eth0iface eth0 inet manual
bond-master bond0


auto eth1
iface eth1 inet manual
bond-master bond0


auto bond0
iface bond0 inet static
address 192.168.10.85
gateway 192.168.10.1
netmask 255.255.255.0
bond-mode 802.3ad
bond-miimon 100
bond-lacp-rate 1
bond-slaves eth0 eth1
```

Not sure if this is at all helpful.

---

### Post by Zach_Wolf on 2013-09-13
I will try removing the pre-down/post-up lines. I thought I had already tested that, but my mind is pretty jumbled at the moment. Can't hurt to give it try. 

Even if it doesn't resolve the problem, thanks :) 
Anything to get me thinking about this will help.

---

### Post by Zach_Wolf on 2013-09-16
> **Zach_Wolf said:**
> I will try removing the pre-down/post-up lines. I thought I had already tested that, but my mind is pretty jumbled at the moment. Can't hurt to give it try. 

Even if it doesn't resolve the problem, thanks :) 
Anything to get me thinking about this will help.

Trying these changes this morning, will report back.

---

### Post by Entilza on 2013-09-19
I would try the second bond independent of the first one to see if it boots with no delay?

Here is my config for a single bond, slight variances:

/etc/modprobe.d/aliases.conf

alias bond0 bonding
options bonding mode=0 miimon=100


/etc/network/interfaces

# The loopback network interface

auto lo bond0
iface lo inet loopback


# The primary network interface


iface bond0 inet static
        address 10.1.16.2
        netmask 255.255.255.0
        gateway 10.1.16.1
        slaves eth0 eth1

---

