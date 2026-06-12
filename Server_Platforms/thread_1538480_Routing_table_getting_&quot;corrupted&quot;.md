---
title: "Routing table getting &quot;corrupted&quot;"
date: 2010-07-25
forum: Server Platforms
---

### Post by TrondK on 2010-07-25
Hi,

I have an Ubuntu 9.10 server installation which have been working flawlessly for some months.

The server runs bridged networking, because of some VMs that runs on it.

But, a couple of weeks ago the network connectivity have started to disappear now and then (usually once a day or so).

Running "sudo /etc/init.d/networking restart" always kicks it back to life.

After a bit of debugging I noticed that when OK the routing table looked like this:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 br0
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
default         192.168.1.1     0.0.0.0         UG    100    0        0 br0


While when in the non-working state it looked like this:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 br0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 br0


Deleting the two routes to eth0 restores the networking again.

Does anybody have any idea about why these "erronous" routes gets added, and what adds them?

Or, any idea on how to further debug this?



/Trond

---

### Post by YesWeCan on 2010-07-25
It looks like bridge interface br0 is being assigned the same IP routing as eth0, which is probably not right. How do you define the br0 interface? What's the output of 'ifconfig'?

---

### Post by TrondK on 2010-07-25
Hm, i did not notice that.

Both are defined to get the IP address via DHCP:

trond@gax58:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0



They (br0 and eth0) also have the same MAC address, which probably explains why the DHCP server gives out the same IP.

Maybe I should configure br0 to have another MAC address?


/Trond

---

### Post by TrondK on 2010-07-25
Come to think of it, this section should not really be there at all, should it?

# The primary network interface
auto eth0
iface eth0 inet dhcp

When using a bridge, eth0 should not have an IP address, or should it?

/Trond

---

### Post by TrondK on 2010-07-25
I tried removing the section on eth0 from the /etc/network/interfaces file, and restarted networking.

I still got network connectivity, but now ifconfig shows this:

trond@gax58:/etc/network$ ifconfig                         
br0       Link encap:Ethernet  HWaddr 6c:f0:49:5e:bc:6d    
          inet addr:192.168.1.51  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:fe5e:bc6d/64 Scope:Link            
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1             
          RX packets:535 errors:0 dropped:0 overruns:0 frame:0           
          TX packets:207 errors:0 dropped:0 overruns:0 carrier:0         
          collisions:0 txqueuelen:0                                      
          RX bytes:59113 (59.1 KB)  TX bytes:35209 (35.2 KB)             

eth0      Link encap:Ethernet  HWaddr 6c:f0:49:5e:bc:6d  
          inet6 addr: fe80::6ef0:49ff:fe5e:bc6d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:542835 errors:0 dropped:0 overruns:0 frame:0
          TX packets:357182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:89406517 (89.4 MB)  TX bytes:444918675 (444.9 MB)
          Interrupt:36 Base address:0x6000

I.e. the eth0 interface got no IP address, which is probably more correct.

I'll try running with this config, and see if the problem disappears.

---

### Post by YesWeCan on 2010-07-25
This may help: [https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)

I think the basic idea is that the component interfaces of the bridge need to be brought up in manual configuration mode with a 0.0.0.0 address. Then the bridge needs to add them and then the bridge is given an IP address. I don't think the component interfaces of the bridge should appear at all in the kernel routing table.

---

### Post by TrondK on 2010-07-25
Seems like removing eth0 from /etc/network/interfaces did the trick, as expected.

Thanks for pointing me in the right direction.


/Trond

---

