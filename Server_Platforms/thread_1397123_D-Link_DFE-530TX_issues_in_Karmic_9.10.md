---
title: "D-Link DFE-530TX issues in Karmic 9.10"
date: 2010-02-02
forum: Server Platforms
---

### Post by m3rc on 2010-02-02
(Disclosure: I posted this in the other forums yesterday and realized this is the better place for it. I'll get rid of the other one.)

I'm trying to add a second NIC to my Karmic 9.10 (Server Edition) as  eth1. The new NIC is a D-Link DFE-530TX+ [http://www.dlink.com/products/?pid=122](http://www.dlink.com/products/?pid=122).  It seems like everything should be working fine because it showed up in  ifconfig with no configuration after I put it in my machine and it's  even is able to get an IP address from the DHCP server in the router. 

The problem is that it's not transmitting anything. I can't SSH into it  from my other computers on the LAN, and when I ran a sniffer on the  interface it was directly connected to there were no packets.

Here's lspci:
```

00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9500 Pro] (Secondary)
02:01.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:01.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:01.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
02:02.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:02.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:02.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
02:07.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 86)
02:0c.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 10)

```Here's dmesg:
```

[ 3556.000292] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 3556.000551] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3563.384099] eth1: link down
[ 3563.384295] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3566.956016] eth0: no IPv6 routers present
[ 3719.826151] e100 0000:02:0c.0: firmware: requesting e100/d102e_ucode.bin
[ 3719.848746] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3721.988261] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 3721.988534] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3723.377569] eth1: link down
[ 3723.377763] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3732.788010] eth0: no IPv6 routers present
[ 5570.678151] e100 0000:02:0c.0: firmware: requesting e100/d102e_ucode.bin
[ 5570.700746] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5572.988262] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 5572.988540] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 5577.373253] eth1: link down
[ 5577.373447] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 5583.460028] eth0: no IPv6 routers present
[ 5899.350152] e100 0000:02:0c.0: firmware: requesting e100/d102e_ucode.bin
[ 5899.372754] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5901.988291] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 5901.988566] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 5905.374955] eth1: link down
[ 5905.375148] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 5912.204009] eth0: no IPv6 routers present
[29271.489652] e100 0000:02:0c.0: firmware: requesting e100/d102e_ucode.bin
[29271.512251] ADDRCONF(NETDEV_UP): eth0: link is not ready
[29274.000265] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[29274.000521] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[29278.370782] eth1: link down
[29278.370977] ADDRCONF(NETDEV_UP): eth1: link is not ready
[29284.004008] eth0: no IPv6 routers present
[31708.153652] e100 0000:02:0c.0: firmware: requesting e100/d102e_ucode.bin
[31708.217650] e100 0000:02:0c.0: firmware: requesting e100/d102e_ucode.bin
[31708.273649] e100 0000:02:0c.0: firmware: requesting e100/d102e_ucode.bin
[31711.000263] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[32213.017653] e100 0000:02:0c.0: firmware: requesting e100/d102e_ucode.bin
[32213.040246] ADDRCONF(NETDEV_UP): eth0: link is not ready
[32215.000265] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[32215.000521] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[32218.716171] eth1: link down
[32218.716366] ADDRCONF(NETDEV_UP): eth1: link is not ready
[32225.320167] eth0: no IPv6 routers present

```I was on freenode's #networking IRC channel earlier and someone  suggested adding d102e_ucode.bin to the /lib/firmware/e100 directory.  After looking around the net for awhile I found the file in the  /lib/`uname -r`/e100 folder on my computer and copied it to  /lib/firmware/e100. The dmesg above reflects that. 

I hope I've provided enough info and I'd really appreciate any  suggestions!

---

### Post by kiranmurari on 2010-02-03
Hi,

Can you confirm if you are using DFE-530TX or DFE-530TX+?
Because your subject says DFE-530TX, whereas the link points to DFE-530TX+.

For your clarification, DFE-530TX uses Via Rhine chipset and DFE-530TX+ uses Realtek 8139 chipset. 
See: [Ubuntu Supported Wired Network Cards - Dlink]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsDlink")
   Can you post the output of following commands:
```
$ lsmod
$ sudo mii-tool eth1
$ ifconfig
```  If RTL8139 module is not loaded, you might have to load it manually
```
$ sudo modprobe rtl8139too
```See: [D-Link DFE-530TX]("http://www.linuxquestions.org/hcl/showproduct.php?product=136&cat=133")

Also, checking on the physical aspects would sometimes help to narrow down the issue.
       
[LIST]
[*]Changing the Ethernet cable.
[*]If possible, check on other desktop (to eliminate having a bad PCI slot)
[/LIST]

---

### Post by m3rc on 2010-02-03
Thanks Kiranmurari. The link was right; I'm using the D-Link DFE-530TX+ and driver-wise it sounds like an important distinction. 

```

# lsmod
Module                  Size  Used by
nfsd                  241104  0 
exportfs                4412  1 nfsd
nfs                   271912  0 
lockd                  67724  2 nfsd,nfs
nfs_acl                 2844  2 nfsd,nfs
auth_rpcgss            36576  2 nfsd,nfs
vfat                   10716  0 
fat                    51452  1 vfat
sunrpc                191712  6 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
radeon                636576  0 
ttm                    36308  1 radeon
drm                   160224  2 radeon,ttm
i2c_algo_bit            5760  1 radeon
intel_agp              27748  1 
iptable_filter          3100  0 
intel_rng               4444  0 
agpgart                35020  3 ttm,drm,intel_agp
ppdev                   6688  0 
ip_tables              11692  1 iptable_filter
shpchp                 32336  0 
parport_pc             32228  1 
psmouse                56500  0 
serio_raw               5280  0 
x_tables               16544  1 ip_tables
dell_wmi                2564  0 
dcdbas                  7332  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
via_rhine              22532  0 
e100                   32772  0 
mii                     5212  2 via_rhine,e100

```

```

# mii-tool eth1
eth1: no link

```

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:e9:ee:5b:8c  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:feee:5b8c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17624 (17.6 KB)  TX bytes:17866 (17.8 KB)

eth1      Link encap:Ethernet  HWaddr 00:1b:11:b4:36:d5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x400 

eth1:0    Link encap:Ethernet  HWaddr 00:1b:11:b4:36:d5  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3308 (3.3 KB)  TX bytes:3308 (3.3 KB)

```

```

# modprobe rtl8139too
FATAL: Module rtl8139too not found.

# modprobe rtl8139
FATAL: Module rtl8139 not found.

```

I'll get those drivers set up and double-check the ethernet cable and PCI card and post my results. Thanks again for responding so quickly.

---

### Post by m3rc on 2010-02-03
I tested the ethernet cable on another box on my LAN and the PCI card as well so that rules those out. I'm not very familiar with loading modules and such because most everything has worked out of the box thus far. I tried 

```

# modprobe 8139too
# rmmod via_rhine
# lsmod
Module                  Size  Used by
8139too                22716  0 
nfsd                  241104  0 
exportfs                4412  1 nfsd
nfs                   271912  0 
lockd                  67724  2 nfsd,nfs
nfs_acl                 2844  2 nfsd,nfs
auth_rpcgss            36576  2 nfsd,nfs
vfat                   10716  0 
fat                    51452  1 vfat
sunrpc                191712  6 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
radeon                636576  0 
ttm                    36308  1 radeon
drm                   160224  2 radeon,ttm
i2c_algo_bit            5760  1 radeon
intel_agp              27748  1 
iptable_filter          3100  0 
intel_rng               4444  0 
agpgart                35020  3 ttm,drm,intel_agp
ppdev                   6688  0 
ip_tables              11692  1 iptable_filter
shpchp                 32336  0 
parport_pc             32228  1 
psmouse                56500  0 
serio_raw               5280  0 
x_tables               16544  1 ip_tables
dell_wmi                2564  0 
dcdbas                  7332  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
e100                   32772  0 
mii                     5212  2 8139too,e100

```

When I restart the network with 
```

$ sudo /etc/init.d/networking restart

```

eth1 doesn't work at all.
```

SIOCSIFADDR: No such device
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

```

What am I missing here? Do I need to get eth1 to use the 8139too driver?

---

### Post by m3rc on 2010-02-05
Bump. I downgraded my server to 8.04 and am still having the exact same issues. Does anyone have a suggestion?

---

### Post by kiranmurari on 2010-02-05
Hi,

> mii                     5212  2 8139too,e100As far as module loading is concerned, the correct module for DFE-530TX+ would be rtl8139too, which has been loaded and is using the MII module (MII is the standard interface used to connect fast ethernet). Since your Intel NIC card also uses the mii module, the used by count is 2.
> eth1:0 Link encap:Ethernet HWaddr 00:1b:11:b4:36:d5
inet addr:192.168.0.10 Bcast:192.168.0.255 Mask:255.255.255.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:16 Base address:0x400From your ifconfig output, I see an alias is set for eth1 interface. Have you done this manually or was it appearing by default?

So to get the interface names correct i.e., eth0 and eth1, can you take a backup of the file /etc/udev/rules.d/70-persistent-net.rules and reboot the machine.

After reboot, at first glance you might get the names as something like... eth2, eth3... You can change the names back to eth0 and eth1 in /etc/udev/rules.d/70-persistent-net.rules (NAME="ethX")

Also on Ubuntu server, new NIC's, although automatically recognized, don't activate by default. See if you have a valid entry for the second card (eth1) in /etc/network/interfaces, something like:
> # eth1 configured for dynamic ip
auto eth1
iface eth1 inet dhcpor
> # eth1 configured for static ip
auto eth1
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1Please change the ip addresses above as per your need.
On desktop versions, the activation is taken care through the Network Manager.

Hope this helps.

---

