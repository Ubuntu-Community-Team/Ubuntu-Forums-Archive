---
title: "eth0 not automatically set up on boot"
date: 2011-09-17
forum: Server Platforms
---

### Post by tckotb on 2011-09-17
Every time i boot up my 10.04 server i have to run the command "ifup eth0". I have set up a static IP if that makes a difference.

Is there some easy one-command fix for this problem? (the server has no monitor, so every time there's a reboot, i have to drag a monitor down into my basement).

Thanks in advanced!

---

### Post by papibe on 2011-09-17
Could you post this file:
```
/etc/network/interfaces
```
Regards.

---

### Post by volkswagner on 2011-09-17
What does your /etc/network/interface file look like?

It may be best to setup static ip using your router.  If your router can reserve an ip based on mac address this will allow you to set eth0 to auto dhcp.

---

### Post by tckotb on 2011-09-17
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet static
  address 192.168.1.7
  netmask 255.255.255.0
  gateway 192.168.1.1
```

---

### Post by papibe on 2011-09-17
Looks fine, although I would also add:
```
broadcast 192.168.1.255
network 192.168.1.0

```
Could you post the result of this commands right after a boot, and eth0 is not working?
```
$ lspci -nn | grep -i eth

$ sudo lshw -C network

$ ifconfig -a

$ route -n

$ nslookup ubuntu.com

$ dig ubuntu.com
```
Regards.

---

### Post by tckotb on 2011-09-17
lspci -nn | grep -i eth:
```

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Et$

```

lshw -C network:
```

eth0      Link encap:Ethernet  HWaddr 00:30:67:c2:a5:0f
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:25 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

ifconfig -a: was not outputted

route -n:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

nslookup ubuntu.com:
```

;; connection timed out; no servers could be reached


```

dig ubuntu.com:
```


; <<>> DiG 9.7.0-P1 <<>> ubuntu.com
;; global options: +cmd
;; connection timed out; no servers could be reached

```

---

### Post by papibe on 2011-09-17
I'm missing the output of 'sudo lshw -C network' (important to see what is the driver/module being used).

Could you also post the same commands after the ifup eth0?

Regards.

---

### Post by tckotb on 2011-09-17
after ifup eth0
```


ssh stop/waiting
ssh start/running, process 1582


```

---

### Post by tckotb on 2011-09-17
```


  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 00:30:67:c2:a5:0f
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.7 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:25 ioport:e800(size=256) memory:fdffb000-fdffbfff(prefetchable) memory:fdffc000-fdffffff(prefetchable) memory:febe0000-febfffff(prefetchable)

```

---

### Post by papibe on 2011-09-17
Sorry, I meant to say the same commands of post #5

(Still missing the 'sudo lshw -C network' right after boot).

Regards.

---

### Post by bab1 on 2011-09-17
> **tckotb said:**
> ```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet static
  address 192.168.1.7
  netmask 255.255.255.0
  gateway 192.168.1.1
```

You need to add ```
auto eth0
```

This is the parameter that brings the interface up automatically.  It should look like this 
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
[COLOR="Red"]**auto eth0**[/COLOR]
iface eth0 inet static
  address 192.168.1.7
  netmask 255.255.255.0
  gateway 192.168.1.1
```

---

### Post by tckotb on 2011-09-17
thanks bab1!

---

### Post by bab1 on 2011-09-17
> **tckotb said:**
> thanks bab1!

I assume this means it worked.  Please mark the thread solved. :-)

---

