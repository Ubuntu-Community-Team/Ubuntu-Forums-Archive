---
title: "tap interface doesn't work in intrepid with virtualbox"
date: 2008-11-21
forum: Virtualisation
---

### Post by lime4x4 on 2008-11-21
trying to create the tap interface for virtualbox.I've followed the mega thread and it's not working here is a copy of my interfaces file and ifconfig


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

# Add a tap
auto tap0
iface tap0 inet manual
tunctl_user john

# Add a second tap
auto tap1
iface tap1 inet manual
tunctl_user john

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off


br0       Link encap:Ethernet  HWaddr 00:1a:92:7d:53:e7  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe7d:53e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:931 errors:0 dropped:0 overruns:0 frame:0
          TX packets:693 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:803995 (803.9 KB)  TX bytes:127041 (127.0 KB)

eth0      Link encap:Ethernet  HWaddr 00:1a:92:7d:53:e7  
          inet6 addr: fe80::21a:92ff:fe7d:53e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3036 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3013647 (3.0 MB)  TX bytes:485567 (485.5 KB)
          Interrupt:214 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:7d:6b:99  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:213 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11346 (11.3 KB)  TX bytes:11346 (11.3 KB)

tap0      Link encap:Ethernet  HWaddr 7e:a1:f7:24:c5:c5  
          inet6 addr: fe80::7ca1:f7ff:fe24:c5c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:21411 (21.4 KB)  TX bytes:0 (0.0 B)

tap1      Link encap:Ethernet  HWaddr 3a:83:77:f5:f4:9b  
          inet6 addr: fe80::3883:77ff:fef5:f49b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

john@john-desktop:~$

---

### Post by bodhi.zazen on 2008-11-21
What is not working ? I see both tap :)

Output of :

```
ls -l /dev/net

groups
```

---

### Post by lime4x4 on 2008-11-21
my guest os have no network connection

john@john-desktop:~$ ls -l /dev/net
total 0
crw-rw---- 1 root uml-net 10, 200 2008-11-10 12:41 tun

john@john-desktop:~$ groups
john adm dialout cdrom audio plugdev scanner fuse lpadmin netdev admin sambashare vboxusers uml-net usbuser
john@john-desktop:~$

---

### Post by bodhi.zazen on 2008-11-21
If you have not done so, log of an back in.

Shut down your virtualbox guest.

In the VBox interface, under the network card, use host networking and in the interface put "tap0" without quotes.

Boot the guest.

[img]http://www.savvyadmin.com/wp-content/uploads/2008/07/vbox-network-settings.png[/img]

---

### Post by lime4x4 on 2008-11-21
tried that even rebooted the computer the guest os still has no network connection

---

### Post by bodhi.zazen on 2008-11-21
> **lime4x4 said:**
> tried that even rebooted the computer the guest os still has no network connection

What guest OS ? Hard to tell from your description but the issue may be with the guest as what you have posted on the host seems to be in working order.

---

### Post by lime4x4 on 2008-11-21
1 guest is xp the other is jaunty and neither have a network connection

---

### Post by cprofitt on 2008-11-21
here is a good link I found:

[http://spinczyk.net/blog/2008/03/05/setting-up-a-bridged-network-for-virtualbox-on-ubuntu-linux/](http://spinczyk.net/blog/2008/03/05/setting-up-a-bridged-network-for-virtualbox-on-ubuntu-linux/)

---

### Post by bodhi.zazen on 2008-11-21
Some network cards must be set in promiscuous mode. I added some information to the mega thread, please let me know if it helps.

---

### Post by lime4x4 on 2008-11-21
nope that didn't work either.I never had a problem in hardy. I did just notice now that i no longer have a network applet in the upper right hand corner anymore

---

### Post by lime4x4 on 2008-11-22
any other ideas?

---

### Post by lime4x4 on 2008-11-22
i also have vmware server installed and that creates a bridge automatically and that works

---

### Post by bodhi.zazen on 2008-11-22
> **lime4x4 said:**
> i also have vmware server installed and that creates a bridge automatically and that works

Yes that is a  potential advantage of VMWare, networking is automagically configured.

Can you post a screen shot from VirtualBox with your host interface / tap ?

---

### Post by lime4x4 on 2008-11-22
is this what u mean?

---

### Post by jrobbo on 2008-12-16
Hi,

Did you ever find the solution to this? My setup is almost exactly the same (Ununtu 8.10 host and Windows XP Guest), and i'm having exactly the same problem. I've tried every solution I can find on the net over the past few days, and the result is always the same: My guest VM can't connect to the network. Everything works fine when I use NAT networking, it's just that I have some problems with Host Interfaces. Unfortunately, I have a couple of small but critical apps that won't work with NAT networking so I really need to get Host Interface networking going. 

Thanks in advance for any help

Regards

John

---

### Post by lime4x4 on 2008-12-16
i changed the tap0 interface name to vbox0 and that works. Never could get tap0 to work

---

