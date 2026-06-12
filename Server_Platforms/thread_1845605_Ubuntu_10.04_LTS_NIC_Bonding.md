---
title: "Ubuntu 10.04 LTS NIC Bonding"
date: 2011-09-17
forum: Server Platforms
---

### Post by rampager5000 on 2011-09-17
I have googled the crap outta this and I have found 50 different ways to  do this. I am trying to get a HA (High Availability) iSCSI setup going,  but am stuck at the NIC bonding part. I need help trying to get this  working. Can anyone shed some light?

---

### Post by Entilza on 2011-09-17
Try these instructions:

[http://ubuntuforums.org/showthread.php?t=1840543&highlight=nic+bond0](http://ubuntuforums.org/showthread.php?t=1840543&highlight=nic+bond0)

---

### Post by rampager5000 on 2011-09-17
I'lll have to build another server up to try that as I don't have access ATM. I will post a reply and let you know how it works out.

---

### Post by rampager5000 on 2011-09-19
I have done those steps that you wanted me to in the other forum link, but still it isn't working correctly. Any other ideas?

---

### Post by Entilza on 2011-09-19
You're gonna have to help out by posting your:

/etc/network/interfaces
ifconfig
dmesg | grep bond

---

### Post by rampager5000 on 2011-09-19
As per your request here are the commands you asked me to use.

/etc/networking/interfaces

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.20
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
auto bond0
iface bond0 inet static
        address 192.168.1.25
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
        slaves eth1 eth2

```ifconfig
```

bond0     Link encap:Ethernet  HWaddr 00:e0:81:31:97:70
          inet addr:192.168.1.25  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:e0:81:31:97:47
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:fe31:9747/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:247535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21969326 (21.9 MB)  TX bytes:136156 (136.1 KB)

eth1      Link encap:Ethernet  HWaddr 00:e0:81:31:97:70
          UP BROADCAST SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth2      Link encap:Ethernet  HWaddr 00:e0:81:31:97:70
          UP BROADCAST SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:352 (352.0 B)  TX bytes:352 (352.0 B)

```dmesg | grep bond
```

[    7.185897] bonding: MII link monitoring set to 100 ms
[    7.217243] bonding: bond0: doing slave updates when interface is down.
[    7.217253] bonding: bond0: Adding slave eth1.
[    7.217257] bonding bond0: master_dev is not up in bond_enslave
[    7.233745] bonding: bond0: enslaving eth1 as an active interface with a down link.
[    7.240880] bonding: bond0: doing slave updates when interface is down.
[    7.240889] bonding: bond0: Adding slave eth2.
[    7.240893] bonding bond0: master_dev is not up in bond_enslave
[    7.252894] bonding: bond0: enslaving eth2 as an active interface with a down link.
[    7.272226] ADDRCONF(NETDEV_UP): bond0: link is not ready
[ 3717.319820] bonding: bond0: doing slave updates when interface is down.
[ 3717.319828] bonding: bond0: Removing slave eth1
[ 3717.319835] bonding: bond0: Warning: the permanent HWaddr of eth1 - 00:e0:81:31:97:70 - is still in use by bond0. Set the HWaddr of eth1 to a different address to avoid conflicts.
[ 3717.319839] bonding: bond0: releasing active interface eth1
[ 3717.395877] bonding: bond0: doing slave updates when interface is down.
[ 3717.395885] bonding: bond0: Removing slave eth2
[ 3717.395889] bonding: bond0: releasing active interface eth2
[ 3722.803833] bonding: bond0: doing slave updates when interface is down.
[ 3722.803842] bonding: bond0: Adding slave eth1.
[ 3722.803847] bonding bond0: master_dev is not up in bond_enslave
[ 3722.820713] bonding: bond0: enslaving eth1 as an active interface with a down link.
[ 3722.826439] bonding: bond0: doing slave updates when interface is down.
[ 3722.826447] bonding: bond0: Adding slave eth2.
[ 3722.826451] bonding bond0: master_dev is not up in bond_enslave
[ 3722.841681] bonding: bond0: enslaving eth2 as an active interface with a down link.
[ 3722.855492] ADDRCONF(NETDEV_UP): bond0: link is not ready
[ 3745.203507] bonding: bond0: doing slave updates when interface is down.
[ 3745.203517] bonding: bond0: Removing slave eth1
[ 3745.203522] bonding: bond0: Warning: the permanent HWaddr of eth1 - 00:e0:81:31:97:70 - is still in use by bond0. Set the HWaddr of eth1 to a different address to avoid conflicts.
[ 3745.203527] bonding: bond0: releasing active interface eth1
[ 3745.271874] bonding: bond0: doing slave updates when interface is down.
[ 3745.271883] bonding: bond0: Removing slave eth2
[ 3745.271887] bonding: bond0: releasing active interface eth2
[ 3745.484196] bonding: bond0: doing slave updates when interface is down.
[ 3745.484206] bonding: bond0: Adding slave eth1.
[ 3745.484210] bonding bond0: master_dev is not up in bond_enslave
[ 3745.500738] bonding: bond0: enslaving eth1 as an active interface with a down link.
[ 3745.506357] bonding: bond0: doing slave updates when interface is down.
[ 3745.506366] bonding: bond0: Adding slave eth2.
[ 3745.506370] bonding bond0: master_dev is not up in bond_enslave
[ 3745.521677] bonding: bond0: enslaving eth2 as an active interface with a down link.
[ 3745.534929] ADDRCONF(NETDEV_UP): bond0: link is not ready

```

One other point of clarification, I have 3 NIC's in this server 1 x 10/100 and 2 x Gb's (eth1 and eth2). Those 2 are the ones I am trying to bond.

---

### Post by Entilza on 2011-09-19
Hmm seems like you are close.

Can you do:
#ethtool -i bond0

Mine shows:

driver: bonding
version: 3.7.0
firmware-version: 2
bus-info:

The first line in my dmesg is:

[    6.455024] bonding: Ethernet Channel Bonding Driver: v3.7.0 (June 2, 2010)

But I see yours is missing so maybe something there.

Did you reboot of course.. and restart /etc/init.d/networking restart

as well as in: /etc/modprobe.d/aliases.conf:

alias bond0 bonding
options bonding mode=0 miimon=100

Try bonding mode=1 maybe theres something incompatible

Good luck

---

### Post by rampager5000 on 2011-09-19
I will try that tomorrow and report back to what I find out.

---

### Post by rampager5000 on 2011-09-20
I checked the
```
ethtool -i
``` command with the following results.
```
driver: bonding
version: 3.5.0
firmware-version: 2
bus-info:

```

My aliases.conf is identical to yours except I have mode set to 1.

---

### Post by Entilza on 2011-09-20
I think the version is different just because I am using a different kernel version, but that's fine.

Note this error in your log:

[ 3717.319835] bonding: bond0: Warning: the permanent HWaddr of eth1 - 00:e0:81:31:97:70 - is still in use by bond0. Set the HWaddr of eth1 to a different address to avoid conflicts.

Did you try rebooting?

---

### Post by rampager5000 on 2011-09-20
I tried using macchanger to change the HWAddress. 

```
macchanger -a eth1
```bond0 keeps grabbing that address as its own MAC as well. 
```
bond0     Link encap:Ethernet  HWaddr [COLOR=Red]00:05:b3:26:f6:a3[/COLOR]
          inet addr:192.168.1.25  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:e0:81:31:97:47
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:fe31:9747/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25860 errors:0 dropped:0 overruns:0 frame:0
          TX packets:750 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2336077 (2.3 MB)  TX bytes:87612 (87.6 KB)

eth1      Link encap:Ethernet  HWaddr [COLOR=Red]00:05:b3:26:f6:a3[/COLOR]
          UP BROADCAST SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth2      Link encap:Ethernet  HWaddr 00:05:b3:26:f6:a3
          UP BROADCAST SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```I'm not sure man...

Yes, I have tried rebooting almost after every step with no results.

---

### Post by Entilza on 2011-09-20
The HWaddr of my bond0 is the same as my eth0 and eth1

Just I don't get that warning in the log.

I'm not sure what to do either at this point if it's a kernel thing or driver or hardware.

I am using Intel 82574L nic cards with the e1000e module driver.

Maybe you need to update your network card drivers

check ethtool -i eth1

Here's my dmesg log just for example.

```

[    6.455024] bonding: Ethernet Channel Bonding Driver: v3.7.0 (June 2, 2010)
[    6.455027] bonding: MII link monitoring set to 100 ms
[    6.480967] bonding: bond0: Adding slave eth0.
[    6.559816] bonding: bond0: enslaving eth0 as an active interface with a down link.
[    6.561436] bonding: bond0: Adding slave eth1.
[    6.639643] bonding: bond0: enslaving eth1 as an active interface with a down link.
[    6.668192] ADDRCONF(NETDEV_UP): bond0: link is not ready
[    9.652001] bonding: bond0: link status definitely up for interface eth1, 1000 Mbps full duplex.
[    9.652358] ADDRCONF(NETDEV_CHANGE): bond0: link becomes ready
[    9.741909] bond0: IPv6 duplicate address fe80::225:90ff:fe27:5cc8 detected!
[    9.751754] bonding: bond0: link status definitely up for interface eth0, 1000 Mbps full duplex.


```

---

### Post by rampager5000 on 2011-09-20
ethtool -i eth1

```
driver: e1000
version: 7.3.21-k5-NAPI
firmware-version: N/A
bus-info: 0000:04:01.0

```

This is the model of my cards that I got from 
```

lspci -tv

 Intel Corporation 82546EB Gigabit Ethernet Controller

```

---

### Post by Entilza on 2011-09-20
Unless anyone else has any more suggestions, you can try upgrading these drives:

[Click Here -> Intel 82546EB Drivers (e1000)]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProdId=991&DwnldID=9180&ProductFamily=Ethernet+Components&ProductLine=Ethernet+Controllers&ProductProduct=Intel%C2%AE+82546EB+Gigabit+Ethernet+Controllereng")

After you do the insmod you should see some new messages.  With the default readme.txt instructions I don't think it will save it on a reboot without doing: sudo update-initramfs -c -k <Your kernel version> 

Did you try eth1 and eth2 without bonding?

If anyone else has some ideas please offer.

---

### Post by rampager5000 on 2011-09-20
I have got it working thank god. I had made a typo in going over my files while I was trying to get it cleaned up... I will post my relevant configurations below as well as all commands I performed while getting this working.

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
        address 192.168.1.20
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
auto bond0
iface bond0 inet static
        address 192.168.1.25
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
        slaves eth1 eth2

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

```/etc/modprobe.d/aliases.conf

```

alias bond0 bonding
options bonding mode=6 miimon=100

```cat /proc/net/bonding/bond0

```

Ethernet Channel Bonding Driver: v3.5.0 (November 4, 2008)

Bonding Mode: adaptive load balancing
Primary Slave: None
Currently Active Slave: eth1
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0

Slave Interface: eth1
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:e0:81:31:97:70

Slave Interface: eth2
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:e0:81:31:97:71

```I also downloaded and installed the drivers for the NIC's using the link you gave me and the following commands

```

 wget http://downloadmirror.intel.com/9180/eng/e1000-8.0.30.tar.gz -o /usr/src/e1000-8.0.30.tar.gz
 cd /usr/src/
 tar -xvzf e1000-8.0.30.tar.gz
 cd /e1000/src/
 apt-get install build-essential
 make install
 rmmod e1000
 insmod /lib/modules/2.6.32-33-generic-pae/kernel/drivers/net/e1000/e1000.ko

```[Entilza]("http://ubuntuforums.org/member.php?u=1322711") please let me know if I left anything out of this as I want to be as complete as possible to avoid any issues like this in the future and also to help others overcome this obstacle.

Also I don't know where to thank you at if there is such a thing here. In lieu of that I thank you here.

---

### Post by Entilza on 2011-09-20
Grats I'm glad you got it!  Now you can actually use your new server :)

What made you choose mode 6? I read about the different methods but can only really make heads or tails regarding 0 and 1.  I chose 0 for what I thought was the best of both worlds.

Be sure to set this one as solved.

---

### Post by rampager5000 on 2011-09-20
[https://help.ubuntu.com/community/UbuntuBonding#Ethernet_Bonding_modes](https://help.ubuntu.com/community/UbuntuBonding#Ethernet_Bonding_modes)

Basically as I read this, it randomly distributes traffic out of any sub interface and puts more of the work on the bonding driver as traffic is sent and received. Also it doesn't require any special configurations on the switch thus allowing even old commodity hardware to be used as it uses the ARP replies independently of any kind of setup.

---

