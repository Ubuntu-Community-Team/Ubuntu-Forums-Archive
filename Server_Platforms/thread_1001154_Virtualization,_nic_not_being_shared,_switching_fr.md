---
title: "Virtualization, nic not being shared, switching from sbs2003"
date: 2008-12-03
forum: Server Platforms
---

### Post by turbozmike on 2008-12-03
Hey folks,
I feel the need to tell you im a linux newb right off.

Im trying to replace a 2003 sbs server with ubuntu 8.04 server.
I ran into the problem one of the server applications requires MSDE
(server 2000 desktop sql).  Wine cant run it so I turned to running an instance of windows in linux.

I got it all working fine except when I set up the br0 nic Linux no longer has access to the network.  The VM works fine.

Both should be able to have access to the network at the same time correct?
I cant figure out how to get this to work.

Im using the build in kvm and vir-manager to configure my VM's.  Yah I put gnome on a server, sorry but Im really used to windows servers so it helps me.  I just use it when configuring things.

If you can point me in the right direction I would really appreciate it.

Thanks

Mike

---

### Post by linux_tech on 2008-12-03
re: an instance of windows in linux.
to clarify 
Are you running windoze on the vm that runs on linux?

what is the output of:
```
ifconfig
```

---

### Post by turbozmike on 2008-12-03
yes im running ubunto 8.04 then running an instance of a windows vm


I remove the #'s so br0 works and I loose connectivity.
putting the #'s back and restarting the network doesnt give me connectivity back.  I had to reboot to get you this info.

/etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto br0
#iface br0 inet dhcp
#     	bridge_ports eth0
#       bridge_fd 9
#       bridge_hello 2
#       bridge_maxage 12
#       bridge_stp off


ifconfig

br0       Link encap:Ethernet  HWaddr 00:16:e6:5d:5e:30  
          inet addr:192.168.16.16  Bcast:192.168.16.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e6ff:fe5d:5e30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:892 (892.0 B)  TX bytes:5422 (5.2 KB)

eth0      Link encap:Ethernet  HWaddr 00:16:e6:5d:5e:30  
          inet6 addr: fe80::216:e6ff:fe5d:5e30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:823870 (804.5 KB)  TX bytes:223119 (217.8 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55800 (54.4 KB)  TX bytes:55800 (54.4 KB)

vnet0     Link encap:Ethernet  HWaddr 2a:1f:ac:ca:4f:81  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::281f:acff:feca:4f81/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:13150 (12.8 KB)

---

### Post by linux_tech on 2008-12-03
Try editing vmware-config.pl, and reverse the settings for network link 0 
ie. from eth1 to eth0.
```
/usr/bin/vmware-config.pl
```

---

### Post by turbozmike on 2008-12-04
i dont have a vmware-config

I am not using vmware.

Im using ubuntu's KVM with virt-manager

---

