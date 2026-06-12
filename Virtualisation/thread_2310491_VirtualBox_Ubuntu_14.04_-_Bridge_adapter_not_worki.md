---
title: "VirtualBox Ubuntu 14.04 - Bridge adapter not working"
date: 2016-01-19
forum: Virtualisation
---

### Post by giuliob on 2016-01-19
Hello everyone, I'm having some troubles setting up my network connection using the Bridged Adapter configuration. I'm just starting with Linux and even if I was going through different forum discussions on the web, I'm still not able to make it work. NAT is working perfectly and I'm able to access Internet, while with Bridged Adapter the network result unreachable, altough I need it for the application I have in mind.
My setup is the following:

VirtualBox 5, Host: Windows 10, Guest: Ubuntu 14.04 LTS

Here you could see in details my configuration:
VirtualBox Network Config

Beside the RealTek, I could use also: Qualcomm Atheros AR946x Wireless Network Adapter. However the problem remain the same, since it seems I have no network working.

This if the ifconfig command:

```
giulio@giulio-VirtualBox:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 08:00:27:f5:87:2f 
inet6 addr: fe80::a00:27ff:fef5:872f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:24737 (24.7 KB)

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:161 errors:0 dropped:0 overruns:0 frame:0
TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:11409 (11.4 KB) TX bytes:11409 (11.4 KB)
```

While /etc/network/interface looks like this:

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

Here it is a screenshot of the overall network settings. For the IPv4 settings I'm using AUtomatic (DHCP), while for IPv6 I've set "ignore".
I hope somebody could have a look and help me out, thank you! Giulio

---

### Post by MAFoElffen on 2016-01-20
I'm out the door, but I see your problem... no config for your NIC's in /etc/network/interfaces.

Note: Please post all code and output within [ code ] tags...

See my post [here]("http://ubuntuforums.org/showthread.php?t=2309132&p=13421039#post13421039") to look at my file. Will return laters...

---

### Post by MAFoElffen on 2016-01-20
Back now...
```

giulio@giulio-VirtualBox:~$ ifconfig
[COLOR=#ff8c00]eth0 Link encap:Ethernet HWaddr 08:00:27:f5:87:2f [/COLOR]
[COLOR=#ff0000]inet6 addr: fe80::a00:27ff:fef5:872f/64 Scope:Link[/COLOR]
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:24737 (24.7 KB)


lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:161 errors:0 dropped:0 overruns:0 frame:0
TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:11409 (11.4 KB) TX bytes:11409 (11.4 KB)

```
Between the two colored lines would be an IPv4 IP address, but it was not assigned. The reason for this is next:
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

[COLOR=#ff0000]# this is what your are missing
auto eth0
iface eth0 inet dhcp[/COLOR]

```
Edit to add what you were missing. Restart the VM... Then repost the results of your
```

ifconfig -a

```

---

### Post by giuliob on 2016-01-21
Thank you [COLOR=#000000]MAFoElffen for taking the time to have a look at my issue. 

Here it is the result of the ifconfig -a:

[/COLOR]```

giulio@giulio-VirtualBox:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 08:00:27:f5:87:2f 
          inet6 addr: fe80::a00:27ff:fef5:872f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:26354 (26.3 KB)

eth0:avahi Link encap:Ethernet  HWaddr 08:00:27:f5:87:2f 
          inet addr:169.254.7.53  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6592 (6.5 KB)  TX bytes:6592 (6.5 KB)


```[COLOR=#000000]

Basically what I would like to do is to establish a connection between the guest and host (and the two should be perceived as two different machines with their own ip address etc..) + the possibility to connect via ethernet cable to a third pc and exchange data. Thank you for your help! Best, Giulio[/COLOR]

---

### Post by giuliob on 2016-01-27
Still not able to fix it...is there anyone who can have a look? Thanks!

---

### Post by MAFoElffen on 2016-01-28
Please post the results of 
```

cat /etc/network/interfaces

```
I just want to confirm that the edits were done and that there are no extraneous characters there. Because:
```

eth0:avahi Link encap:Ethernet  HWaddr 08:00:27:f5:87:2f 
          inet addr:[COLOR=#ff0000]169.254.7.53[/COLOR]  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```
a 169.254.0.0/16 address is called an APIPA address, with is link-local. What that means is that there is no route to a DHCP Server so it failsafes to an automatic assigned failsafe address in that range.

Also post a screen shot of the VM's NIC settings in the VM Window > Settings Window > Network Adapter Settings

---

### Post by giuliob on 2016-01-28
This is the result of cat /etc/network/interfaces

```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

[Here ]("http://imgur.com/cRz6Zxa")is the screenshot of the VM network configuration.

Just to clear, I don't want to connect to Internet via ethernet cable, I just want to connect to another computer directly and also being able to communicate with the host OS (Windows 10) on the same machine. I was trying to ping but didn't work. Thanks for your help!

---

### Post by MAFoElffen on 2016-01-30
Okay then, now we hear the missing piece. Connecting directly to another computer can be done without a switch or router, but you need to do a few things to be able to do that.

Since no route is invloved, there is no dchp server, that is why you don't get an IP adress from dhcp. Because of that, instead, you need to set a staic ip address manually, on both side.... Say 192.168.3.2, with a mask of 255.255.255.0  on one side. ...And 192.168.3.3 with a network mask of 255.255.255.0 on the other. That would give a Netwrok ID (NID) of 192.168.3.0 for your 2 hosts. 

Next, if you are connecting a cable from one computer to another, then you need to connect between them with a "cross-over) cable. See the lower half of this picture.
[IMG]http://www.bb-elec.com/Images/EthernetRJ45A-(1).aspx[/IMG]
What that will do is transmit pairs to receive pairs, to complete the circuits between each... You aren't going to find these at any big-box store. You might be able to find them at an electronics supply. I make my own, so I posted the pin out if you need it to have one made.

So on your linux side in interfaces:
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
    address    192.168.3.2
    netmask   255.255.255.0

```
You wouldn't have dns or a gateway, so that would be all you would need.

Now if you were to want to talk with the host... then I would set up another virtual nic, then in the VirtualBox VM setting on that NIC, set it to Host Only. That would point that one to your host... 

Then in VirtualBox  File" -> "Preferences" -> "Network", check Virtualboxes internal dhcp settings , so that it will provide setting to its internal guest networks...

Then go back and start you guest, tomake sure that new Nic comes up as eth1 ... then to interfaces to set that one up as eth1... so then your /etc/network/interface should be edited to look like this:
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
    address    192.168.3.2
    netmask   255.255.255.0

auto eth1
iface eth1 inet dhcp

```

---

