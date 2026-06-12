---
title: "Eth0 Not Launch?"
date: 2009-10-03
forum: Server Platforms
---

### Post by huangyingw on 2009-10-03
Hello, 
    After moving my virtual Ubuntu server 9.4 32bit to my current host machine, the eth0 seems not work.
   For I only got following info after running "ifconfig"
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```
    How could I launch up my desired ethnet adapter?

---

### Post by Vegan on 2009-10-03
How many do you have on the machine?

---

### Post by cariboo on 2009-10-03
Could you paste the output of:

```
sudo lshw -C network
```

in your next post, it looks like your nic is not being detected.

---

### Post by ian dobson on 2009-10-04
Hi,

I've copied my "server configuration" several times and each time the eth interface changes (eth0 -> eth1). It looks as if hotplug "remembers" the mac address of the network card and when it sees a new network card (ie a new mac address) it creates a new eth device.

Just try editing your /etc/network/interfaces and create entries for eth1.

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth inet static
address ......
netmask .....
broadcast ...
gateway ...
```

Hope this helps
Regards
Ian Dobson

---

### Post by huangyingw on 2009-10-04
> **Vegan said:**
> How many do you have on the machine?
I have only one ethnet adapter. And seen from the output of ifconfig, the OS only find the lo...

---

### Post by huangyingw on 2009-10-04
> **cariboo907 said:**
> Could you paste the output of:

```
sudo lshw -C network
```

in your next post, it looks like your nic is not being detected.
The output of ```
sudo lshw -C network
```
```
  *-network DISABLED
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth1
       version: 10
       serial: 00:0c:29:b8:88:d3
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical logical tp 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=vmxnet driverversion=2.0.1.1 duplex=full firmware=N/A latency=64 link=yes maxlatency=255 mingnt=6 module=vmxnet multicast=yes port=twisted pair speed=1GB/s

```

---

### Post by huangyingw on 2009-10-04
> **ian dobson said:**
> Hi,

I've copied my "server configuration" several times and each time the eth interface changes (eth0 -> eth1). It looks as if hotplug "remembers" the mac address of the network card and when it sees a new network card (ie a new mac address) it creates a new eth device.

Just try editing your /etc/network/interfaces and create entries for eth1.

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth inet static
address ......
netmask .....
broadcast ...
gateway ...
```

Hope this helps
Regards
Ian Dobson
No, this might not help. For I used to share the same situation of "server configuration" changed, and the network adapter alias change from eth0 to eth1, and all others etc.
Even if the network adapter alias change, it could still be shown from the output of "ifconfig"...While, this time, no one shown in my "ifconfig" command.

---

### Post by brettg on 2009-10-04
You have a problem with the extra security for udev that comes with Ubuntu server.

Edit /etc/udev/rules.d/70-persistent-net.rules 

There will be a line like this;

```
# PCI device 0x14e4:0x1659 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1a:64:6e:65:fc", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```


You can either remove these lines and restart, or change the mac address to suit the new interface.

[http://tuxnetworks.blogspot.com/2009/03/disappearing-network-interfaces-in.html]("http://tuxnetworks.blogspot.com/2009/03/disappearing-network-interfaces-in.html")

---

### Post by huangyingw on 2009-10-04
> **brettg said:**
> You have a problem with the extra security for udev that comes with Ubuntu server.

Edit /etc/udev/rules.d/70-persistent-net.rules 

There will be a line like this;

```
# PCI device 0x14e4:0x1659 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1a:64:6e:65:fc", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```


You can either remove these lines and restart, or change the mac address to suit the new interface.

[http://tuxnetworks.blogspot.com/2009/03/disappearing-network-interfaces-in.html]("http://tuxnetworks.blogspot.com/2009/03/disappearing-network-interfaces-in.html")
Yes, really thank you. Your suggestion point out the root cause, and learn a lot from your guidance.

---

### Post by cariboo on 2009-10-04
It looks like you are running your server in a vm, which virtualization program are you using, and how do you have the network interface setup?

---

### Post by huangyingw on 2009-10-05
> **cariboo907 said:**
> It looks like you are running your server in a vm, which virtualization program are you using, and how do you have the network interface setup?
Yes, I am running this on vmware. It works previously, but not work, after moving from the original host to current host.
After the switch of host, the virtual ethernet has changed, so, that is my problem.
And this problem has been solved now.

---

