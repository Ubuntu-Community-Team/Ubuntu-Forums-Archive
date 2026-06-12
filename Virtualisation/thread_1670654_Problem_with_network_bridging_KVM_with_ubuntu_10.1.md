---
title: "Problem with network bridging KVM with ubuntu 10.10 host and fedora 8 client"
date: 2011-01-19
forum: Virtualisation
---

### Post by Bradderz on 2011-01-19
I've read many guides, forum posts and wikis over the last few days  but I've hit a brick wall on this so hoping someone may be able to shed some light on my problem!! Basically I'm running Ubuntu 10.10 as the host OS running KVM and trying to setup full network bridging on a second NIC to my fedora 8 client.

I'll try best to describe my config, I've followed the guide in [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking) (and others!) for setting up the host. My xml config file under /etc/libvirt/qemu contains the following setup:


    <interface type='bridge'>
      <mac address='52:54:00:34:16:04'/>
      <source bridge='br1'/>
      <model type='ne2k_pci'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>


My interfaces file contains the following:


# The primary network interface
auto eth0
iface eth0 inet dhcp
        metric 0
###############################

auto eth1
iface eth1 inet manual

auto br1
iface br1 inet static
        address 135.86.195.46
        network 135.86.195.0
        netmask 255.255.255.192
        broadcast 135.86.195.63
        gateway 135.86.195.62
        bridge_ports eth1
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
        metric 1
###############################


And if I do an ifconfig I get the following:


br1       Link encap:Ethernet  HWaddr 20:cf:30:06:88:ce
          inet addr:135.86.195.46  Bcast:135.86.195.63  Mask:255.255.255.192
          inet6 addr: fe80::22cf:30ff:fe06:88ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:130499 (130.4 KB)  TX bytes:45527 (45.5 KB)

eth0      Link encap:Ethernet  HWaddr 20:cf:30:06:88:9f
          inet addr:135.86.202.239  Bcast:135.86.202.255  Mask:255.255.255.0
          inet6 addr: fe80::22cf:30ff:fe06:889f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30827 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37771 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2754270 (2.7 MB)  TX bytes:36262176 (36.2 MB)
          Interrupt:18 Memory:fbce0000-fbd00000


eth1      Link encap:Ethernet  HWaddr 20:cf:30:06:88:ce
          inet6 addr: fe80::22cf:30ff:fe06:88ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4951 errors:0 dropped:0 overruns:0 frame:0
          TX packets:537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:415200 (415.2 KB)  TX bytes:77633 (77.6 KB)
          Interrupt:19 Memory:fbde0000-fbe00000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:136386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:201037363 (201.0 MB)  TX bytes:201037363 (201.0 MB)

virbr0    Link encap:Ethernet  HWaddr fe:0a:d1:f7:b8:b4
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::fc0a:d1ff:fef7:b8b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:14062 (14.0 KB)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:34:16:04
          inet6 addr: fe80::fc54:ff:fe34:1604/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2075 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:528 (528.0 B)  TX bytes:173114 (173.1 KB)


So this does all appear to look good!!

The problem is (before booting up the VM machine), if I attempt an ssh connection from another machine on the network to 135.86.195.46 (the static IP address of the VM), I get a connection to the host, is this right?

If I then start up my guest, with static ip setting for eth0 using the 135.86.195.46 address, I get an error saying that the ip address is already in use, which I guess is correct as the host seems to be hogging it but I just can't see what I'm doing wrong here.

I'm hoping someone can push me in the right direction, thanks!!

---

