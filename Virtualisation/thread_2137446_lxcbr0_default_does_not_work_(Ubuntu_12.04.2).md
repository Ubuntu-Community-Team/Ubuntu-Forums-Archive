---
title: "lxcbr0 default does not work (Ubuntu 12.04.2)"
date: 2013-04-20
forum: Virtualisation
---

### Post by qzjul on 2013-04-20
Hi; I decided to try LXC last week on Ubuntu 12.04, and at first everything was great, creating starting &etc, until I realized I had no network connectivity whatsoever inside the container.

I have the default /etc/lxc/lxc.conf
```
lxc.network.type=veth
lxc.network.link=lxcbr0
lxc.network.flags=up

```

and the default /etc/default/lxc

```
# MIRROR to be used by ubuntu template at container creation:
# Leaving it undefined is fine
#MIRROR="http://archive.ubuntu.com/ubuntu"
# or
#MIRROR="http://<host-ip-addr>:3142/archive.ubuntu.com/ubuntu"

# LXC_AUTO - whether or not to start containers symlinked under
# /etc/lxc/auto
LXC_AUTO="true"

# Leave USE_LXC_BRIDGE as "true" if you want to use lxcbr0 for your
# containers.  Set to "false" if you'll use virbr0 or another existing
# bridge, or mavlan to your host's NIC.
USE_LXC_BRIDGE="true"

# If you change the LXC_BRIDGE to something other than lxcbr0, then
# you will also need to update your /etc/lxc/lxc.conf as well as the
# configuration (/var/lib/lxc/<container>/config) for any containers
# already created using the default config to reflect the new bridge
# name.
# If you have the dnsmasq daemon installed, you'll also have to update
# /etc/dnsmasq.d/lxc and restart the system wide dnsmasq daemon.
LXC_BRIDGE="lxcbr0"
LXC_ADDR="10.0.3.1"
LXC_NETMASK="255.255.255.0"
LXC_NETWORK="10.0.3.0/24"
LXC_DHCP_RANGE="10.0.3.2,10.0.3.254"
LXC_DHCP_MAX="253"

LXC_SHUTDOWN_TIMEOUT=120

```



The host has the following lxcbr0 and veth (when the container is started):

```
lxcbr0    Link encap:Ethernet  HWaddr 42:a8:41:cd:ea:eb  
          inet addr:10.0.3.1  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: fe80::20f6:f4ff:fef6:d026/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:58592 (58.5 KB)  TX bytes:26849 (26.8 KB)

vethFpoYlq Link encap:Ethernet  HWaddr 42:a8:41:cd:ea:eb  
          inet6 addr: fe80::40a8:41ff:fecd:eaeb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22968 (22.9 KB)  TX bytes:19737 (19.7 KB)

```

By default i got no IP address in the container, so I read that i should give one to it manually; I did so in the config file for the container, named boxcar (/var/lib/lxc/boxcar/config)

```
lxc.network.type=veth
lxc.network.link=lxcbr0
lxc.network.flags=up
lxc.network.ipv4 = 10.0.3.3/24
lxc.network.hwaddr = 00:16:3e:47:5e:41
lxc.utsname = boxcar

lxc.devttydir = lxc
lxc.tty = 4
lxc.pts = 1024
lxc.rootfs = /var/lib/lxc/boxcar/rootfs
lxc.mount  = /var/lib/lxc/boxcar/fstab
lxc.arch = amd64
lxc.cap.drop = sys_module mac_admin
lxc.pivotdir = lxc_putold

# uncomment the next line to run the container unconfined:
#lxc.aa_profile = unconfined

lxc.cgroup.devices.deny = a
# Allow any mknod (but not using the node)
lxc.cgroup.devices.allow = c *:* m
lxc.cgroup.devices.allow = b *:* m
# /dev/null and zero
lxc.cgroup.devices.allow = c 1:3 rwm
lxc.cgroup.devices.allow = c 1:5 rwm
# consoles
lxc.cgroup.devices.allow = c 5:1 rwm
lxc.cgroup.devices.allow = c 5:0 rwm
#lxc.cgroup.devices.allow = c 4:0 rwm
#lxc.cgroup.devices.allow = c 4:1 rwm
# /dev/{,u}random
lxc.cgroup.devices.allow = c 1:9 rwm
lxc.cgroup.devices.allow = c 1:8 rwm
lxc.cgroup.devices.allow = c 136:* rwm
lxc.cgroup.devices.allow = c 5:2 rwm
# rtc
lxc.cgroup.devices.allow = c 254:0 rwm
#fuse
lxc.cgroup.devices.allow = c 10:229 rwm
#tun
lxc.cgroup.devices.allow = c 10:200 rwm
#full
lxc.cgroup.devices.allow = c 1:7 rwm
#hpet
lxc.cgroup.devices.allow = c 10:228 rwm
#kvm
lxc.cgroup.devices.allow = c 10:232 rwm

```

ifconfig inside the container then shows:

```
eth0      Link encap:Ethernet  HWaddr 00:16:3e:47:5e:41  
          inet addr:10.0.3.3  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: fe80::216:3eff:fe47:5e41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19737 (19.7 KB)  TX bytes:25362 (25.3 KB)

```

I read in a number of older posts about specifying br0 or similar in /etc/network/interfaces, but copying those items (and changing the name to lxcbr0) did nothing at all.

The routing table for the host is thus:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         96.52.96.1      0.0.0.0         UG    0      0        0 eth0
10.0.3.0        *               255.255.255.0   U     0      0        0 lxcbr0
96.52.96.0      *               255.255.252.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
192.168.1.0     *               255.255.255.0   U     1      0        0 eth1

```

I feel like I've been missing something really simple or obvious, since nobody else appears to have this difficulty on a default install of LXC, as far as I've read.

I do have shorewall set up on this box, if that's at all a consideration; but other than that I have no idea why it's not "just working".

Does anybody have any ideas or thoughts?

Thanks!

---

### Post by heiko_s on 2013-05-16
You don't have a eth0 interface configured in your host. Edit your host's /etc/network/interfaces file. It should look like this (for static IP, else it has the dhcp option):
```
auto lo
iface lo inet loopback

auto lxcbr0

iface lxcbr0 inet static
address 10.0.3.1
broadcast 10.0.3.255
netmask 255.255.255.0
gateway your.gateway.ip.addr
dns-nameservers 8.8.8.8
bridge_ports eth0
```

Note the **bridge_ports eth0** line. See [http://wiki.debian.org/LXC/SimpleBridge]("http://wiki.debian.org/LXC/SimpleBridge") for examples (perhaps change br0 to lxcbr0).

Hope it helps.

---

### Post by qzjul on 2013-06-01
Well, for anybody who runs into this, I eventually solved it thusly:

in order for the host to see/ssh to the container, I had to add this to my /etc/shorewall/masq

$ETH_NET            $ETH_LXC

(so it looks like this):

```
#INTERFACE      SUBNET          ADDRESS
$ETH_NET            192.168.1.0/24
$ETH_NET            $ETH_LXC

```

where my /etc/shorewall/params file looks like this:

```
ETH_NET=eth0
ETH_LOC=eth1
ETH_LXC=lxcbr0

```


-----

Then in order to make LXC see out, I had to add this to /etc/lxc/lxc.conf

```
lxc.network.ipv4.gateway=auto

```


Then everything worked :D

Though I have to say that last one was way too difficult to find for something that is probably required nearly universally...

---

