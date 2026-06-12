---
title: "KVM, Qemu: no networking with host wireless net"
date: 2008-10-16
forum: Virtualisation
---

### Post by vikofle on 2008-10-16
Hi ,

Seem to be unable to get a working wireless bridged guest network with ubuntu kvm 

None of my kvm guest-boxes running 32bit ubuntu server/winxp on a 64 bit AMD X2 Ubuntu Hardy Host system can access the net / or LAN the host is hooked up to via wireless. 

Has anybody been able to access at least the net from a guest system on a hostsystem connected via wireless ? Funny enough, vmware, virtualbox etc all failed when being connected to wireless. 

My Host config looks like:  

```
[15:54:51]memyselfandi@maximus:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

#auto br0
#iface br0 inet static
#        address 192.168.1.10
# #       network 192.168.1.0
#        netmask 255.255.255.0
#  #      broadcast 192.168.1.255
#        gateway 192.168.1.1
#        bridge_ports eth1
#        bridge_fd 9
#        bridge_hello 2
#        bridge_maxage 12
#        bridge_stp off
[17:38:00]memyselfandi@maximus:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:16:17:8f:66:fc  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Basisadresse:0xd800 

eth1      Link encap:Ethernet  Hardware Adresse 00:11:f6:7f:c2:a2  
          inet Adresse:192.168.1.104  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::211:f6ff:fe7f:c2a2/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:79888 errors:55645 dropped:325 overruns:0 frame:55594
          TX packets:70369 errors:11229 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:102417787 (97.6 MB)  TX bytes:4611042600 (4.2 GB)

eth2      Link encap:Ethernet  Hardware Adresse 80:00:60:0f:e8:00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:15 errors:11 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:920 (920.0 B)  TX bytes:134 (134.0 B)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:2197 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2197 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:110133 (107.5 KB)  TX bytes:110133 (107.5 KB)

vnet0     Link encap:Ethernet  Hardware Adresse ee:bf:65:a7:ff:f5  
          inet Adresse:192.168.122.1  Bcast:192.168.122.255  Maske:255.255.255.0
          inet6-Adresse: fe80::ecbf:65ff:fea7:fff5/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:707 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 B)  TX bytes:97666 (95.3 KB)

```

The guest-configuration is untouched.

Any comments and hints , even solutions, are greatly appreciated ...

V

---

### Post by redbrain on 2008-10-17
What i think you need to do is setup bridged networking with kvm

This involves:

apt-get install bridge utils

vi /etc/network/interfaces
//add your bridge but bridge_ports eth0 from eth0 to your wireless interface

auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

then restart network 
/etc/init.d/networking restart

Next you need the qemu-ifup script:
```

#!/bin/sh
switch=$(ip route ls | awk '/^default / { for(i=0;i<NF;i++) { if ($(i) == "dev") print $(i+1) }}')
/sbin/ifconfig $1 0.0.0.0 up /usr/sbin/brctl addif br0 $1 exit 0

```

place this in 
/etc/qemu-ifup
you may have to create it
then chmod +x /etc/qemu-ifup

Now when you start a vm do:

qemu-system-x86_64 -m <> -cdrom <> -boot c <> -net
nic -net tap

you may need this if it doesnt work:
-net nic,vlan=0 -net tap

Should hopefully work the networking side of kvm is pretty dam messy atm but you can do alot like this is what you would add for virtio network:
-net nic,vlan=0,macaddr=00:0C:29:B6:63:B9 model=virtio -net tap

I hope this helps if not tell me what kvm version you running

And check my website for kvm tutorials i need to put up the networking part more but meh there is alot in kvm now

[http://redbrain.co.uk](http://redbrain.co.uk)

---

