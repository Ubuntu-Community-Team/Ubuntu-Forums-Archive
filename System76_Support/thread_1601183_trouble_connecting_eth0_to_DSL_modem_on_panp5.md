---
title: "trouble connecting eth0 to DSL modem on panp5"
date: 2010-10-19
forum: System76 Support
---

### Post by doubletruncation on 2010-10-19
I'm having trouble getting an ethernet connection to a Motorola SB5120 modem via DHCP with my panp5 laptop running ubuntu 10.04. The ISP is Cox. I am able to connect a windows XP machine to this modem and have access to the internet through it. I also have connected the panp5 laptop to several other networks via DHCP without trouble, so I don't think it's a hardware problem. I'm hoping that maybe it's a simple configuration problem that someone more experienced can spot right away.

I have tried the troubleshooting procedure given at [http://knowledge76.com/index.php/Wired_Ethernet_Troubleshooting](http://knowledge76.com/index.php/Wired_Ethernet_Troubleshooting) things fail at the dhclient step.

```
ifconfig eth0
``` gives:

```
eth0    Link encap:Ethernet  HWaddr 00:90:f5:86:2f:3e
              inet6 addr: fe80::290:f5ff:fe86:2f3e/64 Scope:Link
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:16762 errors:0 dropped:0 overruns:0 frame:0
              TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX byets:1022051 (1.0 MB)  TX bytes:27673 (27.6 KB)
              Interrupt:30 Base address:0xc000


```

```
lspci | grep Eth
``` gives:

```
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

```
route -n
``` gives:

```
Kernel IP routine table
Destination     Gateway      Genmask     Flags Metric Ref     Use Iface
169.254.0.0     0.0.0.0      255.255.0.0 U     0      0           0 wlan0
169.254.0.0     0.0.0.0      255.255.0.0 U     0      0           0 eth0

```

when I try to ping 169.254.0.0 I am instructed to use the -b option, it then hangs (no data received).

Running ```
sudo dhclient
``` gives:

```

......

Listening on LPF/eth0/00:90:f5:86:2f:3e
Sending on   LPF/eth0/00:90:f5:86:2f:3e
Listening on LPF/wlan0/00:21:6a:3a:da:14
Sending on   LPF/wlan0/00:21:6a:3a:da:14
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
...
...
...
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

running ```
dmesg | less
``` gives at the end, a line like:

```

eth0: no IPv6 routers present

```

I note that when I talked to the Cox service people, they told me that they use IPv4 and not IPv6, I thought the default ubuntu configuration would automatically adjust for this though...  I have also tried using the Network Connections gui, editing Auto eth0 and manually setting the IPv4 Settings to the IP address, Netmask and Gateway that are assigned by DHCP to the windows computer. When I do this the Network Manager icon shows that there is a connection, but I am unable to ping other ip addresses which I know to be active.

Thanks for any help someone might have, and please let me know if I can provide additional information.

---

### Post by isantop on 2010-10-20
The first thing I'd try would be to unplug your router for a few moments, then plug it back in. I've seen this fix loads of connectivity issues before, and I think it's worth a try.

If that doesn't get it fixed up for you, you might try going to System > Preferences > Network Connections. On the wired tab, click on Auto eth0, then click edit. 

On the IPv4 Settings tab, ensure that the method dropdown is set to Automatic (DHCP) and that under IPv6 Settings, the method is set to ignore.

---

### Post by doubletruncation on 2010-10-20
Thanks for your reply isantop!

I managed to get connected by using a router between the ubuntu laptop and the modem. I still don't understand why the laptop was not able to connect directly to the modem, maybe I didn't wait long enough in recycling the power on the modem or something like that. In any case the laptop is happy talking to the router, and the router is happy talking to the modem, so I am happy.

---

