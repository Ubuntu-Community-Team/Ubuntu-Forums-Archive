---
title: "2nd NIC in box is not working..."
date: 2008-11-12
forum: Server Platforms
---

### Post by Zuhaib on 2008-11-12
So i am having a weird issue with a headless Ubuntu Server install.
I installed a 2nd NIC after having issues with the onboard being flaky.  The 2nd a PCI, D-Link System Inc RTL8139 Ethernet, and was able to boot up and having it show up on lspci.

I go ahead and add this to my interface

iface eth1 inet static
        address 192.168.10.25
        netmask 255.255.255.0
        gateway 192.168.10.2

and restart the network and then the weirdness starts.  First the Router will report the old IP for eth0 and eth1 have the same MAC.  I can ping the new IP and even SSH in.  If i take down eth0, the old IP is still pingable.  Now if I go and physically disconnect eth0 then eth1 goes down and I cant connect.

Now if i restart with eth0 physically disconnected, i see eth1 up on the router with its proper MAC and see it talking to the outside world BUT no connection inside.  I cant ping it, I cant SSH.  Nothing.

Here is the ifconfig with both on right now

eth0      Link encap:Ethernet  HWaddr 00:50:2c:00:eb:a5  
          inet addr:192.168.10.10  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::250:2cff:fe00:eba5/64 Scope:Link
          UP BROADCAST RUNNING ALLMULTI MULTICAST  MTU:1500  Metric:1
          RX packets:17959 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2259787 (2.2 MB)  TX bytes:1879845 (1.8 MB)
          Interrupt:11 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:40:05:8a:93:99  
          inet addr:192.168.10.103  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::240:5ff:fe8a:9399/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:916592 (916.5 KB)  TX bytes:913446 (913.4 KB)
          Interrupt:12 Base address:0xc000 

any ideas?

---

### Post by devonps on 2008-11-12
> **Zuhaib said:**
> I go ahead and add this to my interface

[B]iface eth1 inet static
        address 192.168.10.25[/B]
        netmask 255.255.255.0
        gateway 192.168.10.2


Here is the ifconfig with both on right now


eth1      Link encap:Ethernet  HWaddr 00:40:05:8a:93:99  
          **inet addr:192.168.10.103  **Bcast:192.168.10.255  Mask:255.255.255.0


Not sure if I've missed something but the IP address for eth1 is different between your /etc/network/interfaces file and the output of IFCONFIG eth1.

Did you change anything between updating the ../interfaces file and running the IFCONFIG command?

Steve.

---

