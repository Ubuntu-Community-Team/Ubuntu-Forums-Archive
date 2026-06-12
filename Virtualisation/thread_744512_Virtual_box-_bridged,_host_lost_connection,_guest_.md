---
title: "Virtual box- bridged, host lost connection, guest works fine"
date: 2008-04-03
forum: Virtualisation
---

### Post by bmwman on 2008-04-03
Hello guys, I'm new to the forum so i apologize if i'm posting in the worng place. I set up my Ubuntu 7.10 and have the latest Virtual box 1.5.6. Installed XP guest. I work in corporate environment so i couldn't use NAT for network and had to set up a bridge to access all the severs. I read the help in Virtual box and managed to set it up, everything worked great. Until i rebooted. The weird thing is that my network is up and i am connected. My virtual XP works fine and can go to the internet, but when i open Firefox in Ubunru - no go. My Host doesn't have connection and the XP works fine. So weird.

Any thoughts??

Thanks in advance.

---

### Post by karyonix on 2008-04-04
Assign an IP address to network bridge.  Don't assign IP address to eth0.  

Please post your /etc/network/interfaces, script or commands you use, so other people can try to figure out what is wrong.

---

### Post by bmwman on 2008-04-04
First when I reboot, the network is down period. Then I disable/enable it from the icon on the task bar and it goes online but i am still unable to access internet from Ubuntu. When i boot the Vbox XP everything works fine on the Guest, except is really slow, cpu 100%. 
I show the following IPs:

Host - eth0  IP  15x.80.64.165
Guest IP  15x.80.64.123

Both assigned from DHCP and thats the way it worked perfect the first time. What kind of IP i need to give to the bridge so I still get the same IPs on the Host and the Guest.

Here is the /etc/Networks/Interfaces 
.......................................................................................
auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
    bridge_ports eth0
........................................................................................

Also my whole system is working really slow, cpu is at 100% when i use the Guest. I'm not sure if it's a coincidence but I thin it happened after i did the network changes.

Thanks for all your help guys. ;)

---

### Post by bmwman on 2008-04-04
Here is my whole info:

br0       Link encap:Ethernet  HWaddr 00:16:41:34:CD:20  
          inet addr:156.80.64.165  Bcast:156.80.64.255  Mask:255.255.255.0
          inet6 addr: fe80::216:41ff:fe34:cd20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2044429 (1.9 MB)  TX bytes:4862 (4.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:16:41:34:CD:20  
          inet addr:156.80.64.165  Bcast:156.80.64.255  Mask:255.255.255.0
          inet6 addr: fe80::216:41ff:fe34:cd20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1187790 errors:254397 dropped:0 overruns:0 frame:0
          TX packets:3835 errors:0 dropped:0 overruns:0 carrier:0
          collisions:161 txqueuelen:1000 
          RX bytes:968477295 (923.6 MB)  TX bytes:634385 (619.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15523 (15.1 KB)  TX bytes:15523 (15.1 KB)

vbox0     Link encap:Ethernet  HWaddr 00:FF:DA:DA:D9:F3  
          inet6 addr: fe80::2ff:daff:feda:d9f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3515 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31346 errors:0 dropped:534 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:596366 (582.3 KB)  TX bytes:4537287 (4.3 MB)

So if I want to keep the same IP range on both eth0 and vbox0 what kind of IP i need to put on the bridge? Does it need to be on the same subnet? Also how to set up the IP on the bridge? The main thing I want is the Guest IP to be in 156.80.64.1xx range.

Thanks.

---

### Post by karyonix on 2008-04-04
It's strange. Where does this IP address come from ?
> eth0 Link encap:Ethernet HWaddr 00:16:41:34:CD:20
inet addr:156.80.64.165 Bcast:156.80.64.255 Mask:255.255.255.0
Do you manually run "ifconfig eth0 156.80.64.165 netmask 255.255.255.0" ? 
Or maybe because you use Network Manager applet to disable/enable network.  Maybe Network Manager applet in ubuntu 7.10 does not support network bridge very well.  I cannot test it now because I'm using ubuntu 8.04 alpha.  

eth0 and vbox0 are part of br0 interface. They don't need IP addresses. 
Assign IP address to br0 only. 

The guest virtual machine connected to vbox0 which is part of br0 works like another machine connected to network switch on the same LAN. 
You can configure the guest OS to use DHCP, or use a static IP address.

---

### Post by bmwman on 2008-04-04
I just reloaded my whole system and put Ubuntu 8.04 as well. Now i tried a different method to setup the bridge. I followed each step and everything seemed to work fine, now errors. You can see here.

[http://samiux.wordpress.com/2007/07/11/bridge-network-interface-on-virtualbox/](http://samiux.wordpress.com/2007/07/11/bridge-network-interface-on-virtualbox/)

Now I get this error when i try to start the Guest system using tap1

Failed to open '/dev/net/tun' for read/write access. Please check the permissions of that node. Either do 'chmod 0666 /dev/net/tun' or change the group of that node and get member of that group. Make sure that these changes are permanently in particular if you are using udev.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).

Was having problem with permissions at first but seemed to fixed that one.

---

### Post by bmwman on 2008-04-04
I type  sudo chmod 0666 /dev/net/tun and then get this


Failed to initialize Host Interface Networking.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).
Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 Next time i try to use it i have to type chmod....... again.

---

### Post by karyonix on 2008-04-05
This post is about creating TUN interfaces with uml-utilities in ubuntu 7.10 and bridging it with eth0 => _[http://ubuntuforums.org/showthread.php?p=4191629](http://ubuntuforums.org/showthread.php?p=4191629)_


You can also create TUN interface + bridge without uml-utilities by using virtualbox instead. 
1. Install bridge-utils package
2. Modify **/etc/network/interfaces** something like this
```
auto lo
iface lo inet loopback

iface eth0 inet manual

auto br0
iface br0 inet dhcp
  bridge-ports eth0
  bridge-maxwait 0
```
Apply settings. 
```
sudo /etc/init.d/networking restart
```
3. Create TUN interface vbox0 and add it to network bridge br0
```
sudo VBoxAddIF vbox1 *username* br0
```
Note : I have not test these steps in a fresh system.  It may require some more configuration.

---

