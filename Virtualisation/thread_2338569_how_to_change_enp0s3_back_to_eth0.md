---
title: "how to change enp0s3 back to eth0"
date: 2016-09-29
forum: Virtualisation
---

### Post by satimis on 2016-09-29
Hi all,

Host	ubuntu 16.04
VM	ubuntu 16.04
Oracle VirtualBox

I clone VM1 creating VM2
Reinitialize the MAC address of all network cards
Full clone

Start VM2
$ ifconfig```

....
enp0s3    Link encap:Ethernet  HWaddr 08:00:27:3a:4a:33  
          inet addr:192.168.8.2  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::8233:e300:c42f:18f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9654 (9.6 KB)  TX bytes:6988 (6.9 KB)
....

```

eth0 changed to enp0s3 and unable to connect Internet.

I encountered this problem before but forgot how to fix it.  Please help.

TIA

satimis

---

### Post by Tadaen_Sylvermane on 2016-09-29
post contents of /etc/network/interfaces pls.

---

### Post by oldfred on 2016-09-29
I do not think name is issue.
[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)
> Starting with v197 systemd/udev will automatically assign  predictable, stable network interface names for all local Ethernet, WLAN  and WWAN interfaces. This is a departure from the traditional interface  naming scheme ("eth0", "eth1", "wlan0", ...), but should fix real  problems. 



**[SIZE=1][FONT=arial][B][https://help.ubuntu.com/stable/ubuntu-help/net-wireless-connect.html](https://help.ubuntu.com/stable/ubuntu-help/net-wireless-connect.html)**[/FONT][/SIZE][/B]

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
Wireless script if wired working :
wget -N -t 5 -T 10 [https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script) && chmod +x wireless_script && ./wireless_script
[http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222](http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222)

---

### Post by satimis on 2016-09-29
Hi all,

&#10219; cat /etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
dns-nameservers xxx.xxx.xxx.xxx xxx.xx.xx.xx

# The primary network interface
auto eth0
iface eth0 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.xx.xx
        network         192.168.xx.xx
        netmask         255.255.255.0
        broadcast       192.168.xx.xx
        gateway         192.168.xx.x
        bridge_ports    eth0
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```

If [uncheck] "Reinitialize the MAC address of all network cards" before cloning, there is no problem.  eth0 won't be changed to enp0s3

I came across this problem about before.  Unfortunately I already forgot how to fix it.  It is the problem in the name of the device.  However it won't happen on 14.04 even [check] "Reinitialize the MAC address of all network cards"

Regards
satimis

---

### Post by satimis on 2016-09-30
Hi all,

The solution is quite simple.  Just edit /etc/network/interfaces
Change all "eth0" to "enp0s3"
Reboot VM

Then it works able to connect Internet.

But above solution doesn't work on "ubuntu-16.04.1-desktop-amd64.iso"

Just install "ubuntu-16.04.1-desktop-amd64" on a VM.

Solution: on terminal run;```

sudo ifconfig enp0s3 192.168.x.x netmask 255.255.255.0

```
"192.168.x.x" is the fixed IP

Reboot VM, then Internet can be connected.

It is very strange to me.

satimis

---

### Post by satimis on 2016-10-03
Hi all,

**PROBLEM SOLVED**

My problem encountered on the newly installed "ubuntu-16.04.1-desktop-amd64.iso" is that I forgot installing bridge-utils on the VM.  After installing bridge-utils and on /etc/network/interfaces renaming all eth0 to enp0s3 now VM works without problem connecting Internet and with fixed IP assigned permanently.

satimis

---

