---
title: "help, cant get my bridged network running with karmic"
date: 2009-11-02
forum: Virtualisation
---

### Post by sdowney717 on 2009-11-02
following these but no go
trying variations, it used to work but i dont know why not,
 anymore ideas to try?

[http://foxgulch.com/WordPress/?p=459](http://foxgulch.com/WordPress/?p=459)
[https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)
[https://help.ubuntu.com/community/KVM/FAQ](https://help.ubuntu.com/community/KVM/FAQ)

interfaces file
> #auto lo
#iface lo inet loopback

auto lo
iface lo inet loopback

auto eth2
iface eth2 inet manual

auto br0
iface br0 inet dhcp
        bridge_ports eth2
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

> scott@scott-desktop:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:22:15:54:fa:a6  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe54:faa6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16635 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2668 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2768234 (2.7 MB)  TX bytes:551578 (551.5 KB)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12179507 (12.1 MB)  TX bytes:12179507 (12.1 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.43.1  Bcast:172.16.43.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.201.1  Bcast:192.168.201.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

scott@scott-desktop:~$ 


---

### Post by sdowney717 on 2009-11-02
scott@scott-desktop:~$ sudo /etc/init.d/networking force-reload
 * Reconfiguring network interfaces...                                          WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.
     

got it, i had to switch from true to false

---

