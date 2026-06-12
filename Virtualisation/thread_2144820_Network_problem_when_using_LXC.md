---
title: "Network problem when using LXC"
date: 2013-05-13
forum: Virtualisation
---

### Post by thnewguy on 2013-05-13
I have created a new LXC container on my Ubuntu machine. Since I would like outside clients to be able to connect to this container I have triedto set up the container to use the same network settings as the rest of my LAN. I've run into a snag where programs in the LXC container cannot connect to (or ping) other machines on the network and other machines cannot see the container. Any attempt to connect to the LXC container from another machine indicates there is no route to host. Trying to ping from the LXC container to another machine results in a network error.

Here are are my network settings on the host, output provided by ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:40:ca:b1:64:11  
          inet addr:192.168.2.25  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:feb1:6411/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:396165 (396.1 KB)  TX bytes:503131 (503.1 KB)
          Interrupt:20 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19242 (19.2 KB)  TX bytes:19242 (19.2 KB)

lxcbr0    Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:192.168.2.200  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::c485:a4ff:feb6:5ff6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19584 (19.5 KB)  TX bytes:468 (468.0 B)

```

And here are my settings inside the container, output provided by ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:16:3e:7e:78:e4  
          inet addr:192.168.2.202  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:3eff:fe7e:78e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:600 (600.0 B)  TX bytes:1004 (1.0 KB)

```


And here is the contents of my container's /etc/network/interfaces file
```

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
# iface eth0 inet dhcp
iface eth0 inet static
address 192.168.2.102
netmask 255.255.255.0
broadcast 192.168.2.255
gateway 192.168.2.1

```

I must be missing something obvious. When i created containers with the default 10.0.3.x addresses the containers were able to see and connect to machines in the outside world, but I was unable to connect to the LXC container from another machine. Any suggestions on how I can remedy this so the container can connect to other machines and clients can connect to my container?

---

### Post by thnewguy on 2013-05-14
I think I found the problem. My host operating system is running a firewall. With the firewall enabled no traffic can get into (or out from) the LXC container. Once the firewall has been disabled on the host OS traffic is able to flow freely from the guest to the outside world. My container can now see outside, though I still haven't figured out how to allow remote clients to connect to the container....

Anyone have a suggestion for allowing remote machines to see my container?

---

### Post by heiko_s on 2013-05-16
I'm not that familiar with LXC containers, but under Xen, VMware, and kvm (i believe) the host and the guests would typically be connected via a virtual bridge. LXC uses the same concept - have a look here under lxcbr0: [lxc-hostsetup]("https://help.ubuntu.com/12.04/serverguide/lxc.html#lxc-hostsetup") and [http://www.thomas-krenn.com/en/wiki/Event-News:_LinuxCon_Europe_2012]("http://www.thomas-krenn.com/en/wiki/Event-News:_LinuxCon_Europe_2012"), specifically slide 17.

The network configuration of the host is actually a bridge configuration. For a **good example** look here: [http://srdandukic.blogspot.co.nz/2012/04/lxc-on-ubuntu.html]("http://srdandukic.blogspot.co.nz/2012/04/lxc-on-ubuntu.html").

See [http://srdandukic.blogspot.co.il/2012/04/internal-lan-on-lxc.html]("http://srdandukic.blogspot.co.il/2012/04/internal-lan-on-lxc.html") for more on that.

In essence, you create a virtual bridge in the host that is connected to the eth0 port (bridge_ports eth0) on your PC, which is a real network adapter. The LXC container connects to a virtual bridge port (veth in the config file) on this bridge, which is seen by the container as eth0 (or eth1... as defined by the LXC config file).

Hope it works.

---

