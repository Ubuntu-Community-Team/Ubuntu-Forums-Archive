---
title: "Eth1 isnt picking up a IP"
date: 2009-06-04
forum: Server Platforms
---

### Post by jmclein on 2009-06-04
Hello all

Please be patient with me as I am not a "linux person".  My expirence is pretty limited.  I am working on setting up a captive wireless portal on Ubuntu server 8.4  I am running this virtually on vmware server.  I have 2 ethernet adapters setup in vmware and both are showing up in Ubuntu when I do a /ifconfig however only 1 of them is picking up a IP address.  Both of the virtual adapters on the windows side are picking a IP up fine.  Can anyone give me some advice on a few things that I should be looking at/trying to get the other adapter to pick up a IP?

Thank you very much

---

### Post by UBSec on 2009-06-04
Hi,

What do u mean by pick up an address (is it static or DHCP ?) . In Ubuntu you can configure your interfaces using ifconfig but when the server reboots you'll loose your changes.

To make it permanently you should edit the file : /etc/network/interfaces

sudo vi /etc/network/interfaces

For more informations ( see man interfaces(5))

Notice that for wireless cards you may use iwconfig instead of ifconfig

UBSec

---

### Post by jmclein on 2009-06-04
> **UBSec said:**
> Hi,

What do u mean by pick up an address (is it static or DHCP ?) . In Ubuntu you can configure your interfaces using ifconfig but when the server reboots you'll loose your changes.

To make it permanently you should edit the file : /etc/network/interfaces

sudo vi /etc/network/interfaces

For more informations ( see man interfaces(5))

Notice that for wireless cards you may use iwconfig instead of ifconfig

UBSec

It is set to DHCP but doesnt get an address.  The other one picks a IP up fine.

---

### Post by cariboo on 2009-06-04
Normally you have to set up one nic with a static ip address and the other using dhcp. Having a server that uses dhcp makes it hard for the other systems on the network to find the server. Edit /etc/network/interfaces to look something like this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
  address    192.168.1.100
  netmask    255.255.255.0
  broadcast  192.168.1.254
  gateway    192.168.1.1

```

substitute your router ip address for the one in the example above.

---

### Post by jmclein on 2009-06-05
> **cariboo907 said:**
> Normally you have to set up one nic with a static ip address and the other using dhcp. Having a server that uses dhcp makes it hard for the other systems on the network to find the server. Edit /etc/network/interfaces to look something like this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
  address    192.168.1.100
  netmask    255.255.255.0
  broadcast  192.168.1.254
  gateway    192.168.1.1

```

substitute your router ip address for the one in the example above.

Ok, so I copied this over and changed the information over to match my network settings.  After doing a ifconfig I till don't have a IP or anything showing up on eth1.  Here is the output of a ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0c:29:a7:32:ea
          inet addr:10.232.75.24  Bcast:10.232.79.255  Mask:255.255.240.0
          inet6 addr: fe80::20c:29ff:fea7:32ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50096 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4642278 (4.4 MB)  TX bytes:145301 (141.8 KB)
          Interrupt:17 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:0c:29:a7:32:f4
          inet6 addr: fe80::20c:29ff:fea7:32f4/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:45984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4213552 (4.0 MB)  TX bytes:11950 (11.6 KB)
          Interrupt:18 Base address:0x2080

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5380 (5.2 KB)  TX bytes:5380 (5.2 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.1.0.1  P-t-P:10.1.0.1  Mask:255.255.255.0
          UP POINTOPOINT RUNNING  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Serangan on 2009-06-05
You might have to restart the networking component. 

```
sudo /etc/init.d/networking restart
```

---

### Post by UBSec on 2009-06-05
Do you have a DHCP server for your LAN ?
If yes can you show us the section where you declare the eth1 mac address ? 

For testing u can try to force the IP to static by :

ifconfig eth1 my_ip_address netmask my_netmask 

can u post ur ifconfig -a ? 

UBSec

---

