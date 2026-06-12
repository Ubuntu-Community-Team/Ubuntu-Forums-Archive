---
title: "Ubuntu Networking Issue"
date: 2015-08-12
forum: Server Platforms
---

### Post by Bashed on 2015-08-12
Trying to bind a /28 to my Ubuntu 14.04 dedicated server. Everything looks good, but no ping on any IP except the main .82. I'm baffled.

My resolv.conf is set to Google's DNS (I even had the primary IP first, both don't work).

/etc/network/interfaces

    ```
# This file describes the network interfaces available on your system
    # and how to activate them. For more information, see interfaces(5).
    
    # The loopback network interface
    auto lo
    iface lo inet loopback
    
    # The primary network interface
    auto eth0
    iface eth0 inet static
            address xxx.xxx.42.82
            netmask 255.255.255.240
            network xxx.xxx.42.80
            broadcast xxx.xxx.42.95
            gateway xxx.xxx.42.81
            # dns-* options are implemented by the resolvconf package, if installed
            dns-nameservers xxx.xxx.42.82
    
    user@ubuntu:~$ ip addr show eth0 
    2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
        link/ether 00:25:90:3a:c2:36 brd ff:ff:ff:ff:ff:ff
        inet xxx.xxx.42.82/28 brd xxx.xxx.42.95 scope global eth0
           valid_lft forever preferred_lft forever
        inet6 fe80::225:90ff:fe3a:c236/64 scope link 
           valid_lft forever preferred_lft forever
    
           user@ubuntu:~$ ifconfig -a
    eth0      Link encap:Ethernet  HWaddr 00:25:90:3a:c2:36  
              inet addr:xxx.xxx.42.82  Bcast:xxx.xxx.42.95  Mask:255.255.255.240
              inet6 addr: fe80::225:90ff:fe3a:c236/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:1988597 errors:0 dropped:1277940 overruns:0 frame:0
              TX packets:562121 errors:198 dropped:0 overruns:0 carrier:198
              collisions:16020 txqueuelen:1000 
              RX bytes:281303904 (281.3 MB)  TX bytes:121464307 (121.4 MB)
              Interrupt:16 Memory:fb5e0000-fb600000 

```
          

          
Also ran  /etc/init.d/networking restart

---

### Post by TheFu on 2015-08-12
Remove the *network* and *broadcast* lines - those are deprecated.

For the other IPs, you need to make similar stanzas - either with other network devices (which must exist) or virtual devices.
[https://askubuntu.com/questions/313877/how-do-i-add-an-additional-ip-address-to-etc-network-interfaces](https://askubuntu.com/questions/313877/how-do-i-add-an-additional-ip-address-to-etc-network-interfaces)

---

### Post by Bashed on 2015-08-12
Hi, thanks.

So to add the remainder of the /28, what would I add to the file?

For example in that link, it shows this:

```
auto eth0:0
iface eth0:0 inet static
  address fff.fff.fff.fff
  netmask 255.255.254.0
```

I have to do this literally for each single IP? Isn't there an easier, cleaner way?

---

### Post by Bashed on 2015-08-12
I tried the 2nd variation in that link.

/etc/network/interfaces

Added this line to the end

up ip addr add xxx.xxx.42.80/28 dev eth0

Then I ran

sudo ip addr add xxx.xxx.42.80/28 dev eth0
/etc/init.d/networking restart

Still can't ping the rest of the IPs in the /28.

---

### Post by Bashed on 2015-08-12
Would appreciate help on this. Thanks.

---

### Post by nerdtron on 2015-08-13
This is correct. But why is the dns server the same as the IP of the server?
```
    # The loopback network interface
    auto lo
    iface lo inet loopback
    
    # The primary network interface
    auto eth0
    iface eth0 inet static
            address xxx.xxx.42.82
            netmask 255.255.255.240
            network xxx.xxx.42.80
            broadcast xxx.xxx.42.95
            gateway xxx.xxx.42.81
            # dns-* options are implemented by the resolvconf package, if installed
            dns-nameservers xxx.xxx.42.82
```
Are you sure this is a server and you don't have any GUI installed?(some conflicts on GUI tools)

 Did you tried to reboot? because if the server can't assign it's ip address you will see something like "waiting for network" while the server is booting.

And the commands to restart the eth interface is the following.
```
sudo ifdown eth0
sudo ifup eth0
```

Post here any errors that you encountered on those commands. 
Another advice is to delete the net-persistent file if it exists. (maybe move it somewhere else) Then try to reboot and see if changes take effect on your interface.
```
sudo mv /etc/udev/rules.d/70-persistent-net.rules /home/username/
```

---

### Post by Bashed on 2015-08-13
Can't get this working 

Updated too

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address xxx.xxx.42.82
        netmask 255.255.255.240
        gateway xxx.xxx.42.81
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 174.128.33.61 174.128.33.62
        up ip addr add xxx.xxx.42.80/28 dev eth0
```

---

### Post by Bashed on 2015-08-13
I also changed it to this, and ran /etc/init.d/networking restart

Still no ping

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
auto eth0:0
auto eth0:1

iface eth0 inet static
        address xxx.xxx.42.82
        netmask 255.255.255.240
        gateway xxx.xxx.42.81

iface eth0:0 inet static
        address xxx.xxx.42.83
        netmask 255.255.255.240
        gateway xxx.xxx.42.81

iface eth0:1 inet static
        address xxx.xxx.42.84
        netmask 255.255.255.240
        gateway xxx.xxx.42.81
```

---

### Post by Bashed on 2015-08-13
Tried below, can't ping anything but primary .82

Not sure why packets are dropping?


    ```
# The primary network interface
    auto eth0
    iface eth0 inet static
            address xxx.xxx.42.82
            netmask 255.255.255.240
            gateway xxx.xxx.42.81
            # dns-* options are implemented by the resolvconf package, if installed
            dns-nameservers 8.8.8.8

    eth0      Link encap:Ethernet  HWaddr 00:25:90:3a:c2:36  
              inet addr:xxx.xxx.42.82  Bcast:xxx.xxx.42.95  Mask:255.255.255.240
              inet6 addr: fe80::225:90ff:fe3a:c236/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:14425 errors:0 dropped:12092 overruns:0 frame:0
              TX packets:911 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:1118063 (1.1 MB)  TX bytes:212166 (212.1 KB)
              Interrupt:16 Memory:fb5e0000-fb600000 

    lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:65536  Metric:1
              RX packets:1210 errors:0 dropped:0 overruns:0 frame:0
              TX packets:1210 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:66658 (66.6 KB)  TX bytes:66658 (66.6 KB)
```

---

### Post by SeijiSensei on 2015-08-13
So, as I understand it, you want this machine to answer for all available IPs in your subnet?  Here's a script I wrote for a client to do that:
```

#!/bin/bash
NET=192.168.42
MASK=255.255.255.240
BC=192.168.42.95

#!/bin/sh
INTS="83 84 85 86 87 88 89 90 91 92 93 94"

for i in $INTS
do
     ifconfig eth0:$i down
     ifconfig eth0:$i "$NET.$i" netmask $MASK broadcast $BC
done

```
That assumes the primary interface, eth0, has 192.168.42.82 as its address, and .81 is owned by the router.  This script will create virtual interfaces like eth0:83 with 192.168.97.83 as its IP address.

Are you running a firewall?  Make sure there are rules like these near the top of the iptables ruleset:
```

/sbin/iptables -I INPUT   -s 192.168.97.80/28 -d 192.168.97.80/28 -j ACCEPT
/sbin/iptables -I FORWARD -s 192.168.97.80/28 -d 192.168.97.80/28 -j ACCEPT

```

---

### Post by Bashed on 2015-08-13
> **SeijiSensei said:**
> So, as I understand it, you want this machine to answer for all available IPs in your subnet?  Here's a script I wrote for a client to do that:
```

#!/bin/bash
NET=192.168.42
MASK=255.255.255.240
BC=192.168.42.95

#!/bin/sh
INTS="83 84 85 86 87 88 89 90 91 92 93 94"

for i in $INTS
do
     ifconfig eth0:$i down
     ifconfig eth0:$i "$NET.$i" netmask $MASK broadcast $BC
done

```
That assumes the primary interface, eth0, has 192.168.42.82 as its address, and .81 is owned by the router.  This script will create virtual interfaces like eth0:83 with 192.168.97.83 as its IP address.

Are you running a firewall?  Make sure there are rules like these near the top of the iptables ruleset:
```

/sbin/iptables -I INPUT   -s 192.168.97.80/28 -d 192.168.97.80/28 -j ACCEPT
/sbin/iptables -I FORWARD -s 192.168.97.80/28 -d 192.168.97.80/28 -j ACCEPT

```


Thanks. I created that script, but getting errors.

```
#!/bin/bash
NET=xxx.xxx.42.80
MASK=255.255.255.240
BC=xxx.xxx.42.95

#!/bin/sh
INTS="83 84 85 86 87 88 89 90 91 92 93 94"

for i in $INTS
do
     ifconfig eth0:$i down
     ifconfig eth0:$i "$NET.$i" netmask $MASK broadcast $BC
done

user@ubuntu:~$ sudo sh /etc/iplist
SIOCSIFFLAGS: Cannot assign requested address
xxx.xxx.42.80.83: Unknown host
ifconfig: `--help' gives usage information.
SIOCSIFFLAGS: Cannot assign requested address
xxx.xxx.42.80.84: Unknown host
ifconfig: `--help' gives usage information.
SIOCSIFFLAGS: Cannot assign requested address
xxx.xxx.42.80.85: Unknown host
ifconfig: `--help' gives usage information.
SIOCSIFFLAGS: Cannot assign requested address
xxx.xxx.42.80.86: Unknown host
ifconfig: `--help' gives usage information.
SIOCSIFFLAGS: Cannot assign requested address
xxx.xxx.42.80.87: Unknown host
ifconfig: `--help' gives usage information.
SIOCSIFFLAGS: Cannot assign requested address
xxx.xxx.42.80.88: Unknown host
ifconfig: `--help' gives usage information.
SIOCSIFFLAGS: Cannot assign requested address
xxx.xxx.42.80.89: Unknown host
ifconfig: `--help' gives usage information.
SIOCSIFFLAGS: Cannot assign requested address
xxx.xxx.42.80.90: Unknown host
ifconfig: `--help' gives usage information.
SIOCSIFFLAGS: Cannot assign requested address
xxx.xxx.42.80.91: Unknown host
ifconfig: `--help' gives usage information.
SIOCSIFFLAGS: Cannot assign requested address
xxx.xxx.42.80.92: Unknown host
ifconfig: `--help' gives usage information.
SIOCSIFFLAGS: Cannot assign requested address
xxx.xxx.42.80.93: Unknown host
ifconfig: `--help' gives usage information.
SIOCSIFFLAGS: Cannot assign requested address
xxx.xxx.42.80.94: Unknown host
ifconfig: `--help' gives usage information.
```

---

### Post by Bashed on 2015-08-13
```
user@ubuntu:~$ dmesg | grep eth0
[    5.317464] e1000e 0000:02:00.0 eth0: registered PHC clock
[    5.317465] e1000e 0000:02:00.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:25:90:3a:c2:36
[    5.317467] e1000e 0000:02:00.0 eth0: Intel(R) PRO/1000 Network Connection
[    5.317546] e1000e 0000:02:00.0 eth0: MAC: 3, PHY: 8, PBA No: 0101FF-0FF
[   13.718720] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.893141] e1000e: eth0 NIC Link is Up 100 Mbps Half Duplex, Flow Control: None
[   15.893316] e1000e 0000:02:00.0 eth0: Autonegotiated half duplex but link partner cannot autoneg.  Try forcing full duplex if link gets many collisions.
[   15.893317] e1000e 0000:02:00.0 eth0: 10/100 speed: disabling TSO
[   15.893567] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

@ubuntu:~$ uname -r
3.16.0-30-generic

---

### Post by Bashed on 2015-08-13
I'm sorry to bump this, really need to get this sorted out. This is really strange. I've never had such difficulty binding IPs with Windows server or Centos / Debian. I'm not sure why Ubuntu is giving me a headache on this one.

---

### Post by Bashed on 2015-08-14
Edit: I just fixed the subnetting to .64/28  correctly, and only this method finally worked

```
auto eth0
auto eth0:0
auto eth0:1
iface eth0 inet static
        address xxx.xxx.42.66
        netmask 255.255.255.240
        gateway xxx.xxx.42.65
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 8.8.8.8
iface eth0:0 inet static
        address xxx.xxx.42.67
        netmask 255.255.255.240
        gateway xxx.xxx.42.65
```

---

### Post by SeijiSensei on 2015-08-14
> **Bashed said:**
> Thanks. I created that script, but getting errors.

```
#!/bin/bash
**NET=xxx.xxx.42.80**
MASK=255.255.255.240
BC=xxx.xxx.42.95

```

The NET environment variable in my script only includes the first three octets, xxx.xxx.42 in your case.

---

