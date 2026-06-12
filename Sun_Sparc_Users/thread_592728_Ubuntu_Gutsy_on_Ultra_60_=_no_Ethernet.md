---
title: "Ubuntu Gutsy on Ultra 60 = no Ethernet"
date: 2007-10-26
forum: Sun Sparc Users
---

### Post by jcastill on 2007-10-26
I updated my Feisty installation to Gutsy and after the restart I had no networking, I tried googling around and found that the mod that enables ethernet is "sunhme" yet I can't find it on gutsy. So I decided to reinstall the machine directly on Gutsy to see if it would fix it (after all I keep a local apt-proxy for testing) install worked great, yet when I restarted I was with no ehternet and no mod for "sunhme"

Anybody has the same issue? What mod do you use to have ethernet?

Thanks

---

### Post by zanderred on 2007-10-26
Hi I'll tak-it you mave booted in ok, whut do'es system/preference/hardware info say?

---

### Post by jcastill on 2007-10-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/158323](https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/158323) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I did "lspci | grep Eth"

0000:00:01.1 Ethernet controller: Sun Microsystems Computer Corp. Happy Meal 10/100 Ethernet [hme] (rev 01)

doing "dmesg | grep eth" shows:

[ 92.800838] eth0: HAPPY MEAL (PCI/CheerIO) 10/100BaseT Ethernet 08:00:....... (the rest of the MAC address)

ifconfig does not show it, so I decided to run "sudo ifconfig eth0 up"

which does make it appear, yet it seems like it's IPv6 only (not showing any IPv4 address)

doing "dmesg | grep eth" after that shows:

[ 513.824500] eth0: Link is up using internal transceiver at 100Mb/s, Full Duplex.
[ 520.556981] eth0: no IPv6 roiuters present

Plus it seems "Network Manager" keeps using 100% CPU before I even move any setting.

---

### Post by netztier on 2007-10-29
> **jcastill said:**
> 
Plus it seems "Network Manager" keeps using 100% CPU before I even move any setting.

NetworkManager left my Ultra5 with Gutsy completely unusable, hogging all of it's scarce CPU ressources.  With synaptic,  I removed packages **network-manager** and **network-manager-gnome**.

Removing Network-Manager like this is probably only a quick&dirty fix; I imagine that the proper solution to this problem has to do with reconfiguring/rearranging some udev or dbus/hal related scripts - but I  wanted the network back on my U5 (as in: I want it now!) and that was a way to do it.

In the end, I had to edit **/etc/network/interfaces** to have a simple config for eth0 like this:

```
auto eth0
iface eth0 inet dhcp
```

Of course, If you need static IP addressing or some advanced configuration, adapt etc/network/interfaces to your needs. My U5 now runs smoothly with Ubuntu 7.10.  We now even have usplash during boot and shutdown! 8-)

regards

Marc

---

### Post by jcastill on 2007-10-29
It worked! Thanks Mark.

I hope this bug gets fixed.

---

### Post by gavinj44 on 2007-11-05
Hi There, 

I had Feisty running really well on a headless Ultra 10, i followed the instructions on the following link: [https://help.ubuntu.com/community/GutsyUpgrades#head-f2435a45758bb5836f8e5b87e90045463f8c6ec7](https://help.ubuntu.com/community/GutsyUpgrades#head-f2435a45758bb5836f8e5b87e90045463f8c6ec7)  to upgrade to Gutsy and went well until the reboot ...

After the reboot, I appear to have no Ethernet connection as described here now unfortunately the only access I have to the server is via a serial console would anyone be able to shed some light as to how I can reactivate the Ethernet connectivity ?

Regards,
Gavin

---

### Post by gavinj44 on 2007-11-06
Fixed it .... for some reason eth0 has become eth0_rena e.g. 

```

eth1      Link encap:Ethernet  HWaddr 08:00:20:C2:91:36
          inet addr:172.16.100.20  Bcast:172.16.100.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:20ff:fec1:9046/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1075 errors:0 dropped:0 overruns:0 frame:0
          TX packets:556 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:310687 (303.4 KB)  TX bytes:79999 (78.1 KB)
          Interrupt:16 Base address:0x9000

eth0_rena Link encap:Ethernet  HWaddr 08:00:20:C2:91:36
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:12 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

so /etc/network/interfaces needed a few changes e.g. 

```
cp /etc/network/interfaces /etc/network/interfaces.old
cat /etc/network/interfaces.old | sed s/eth0/eth1/g > /etc/network/interfaces  
```

That seems to have fixed it ... I noticed that both interfaces show the same MAC address also ... any ideas what happened as part of the upgrade to Gutsy with the network interfaces ?

Regards,
Gavin

---

### Post by tahirdar on 2007-11-15
What is your local-mac-address? set to in OBP. It should be local-mac-address?=true to get unique mac address assigned to each card.

 ok > setenv local-mac-address? true
 ok> reset

Should do the job.

---

