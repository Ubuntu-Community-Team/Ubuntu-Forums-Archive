---
title: "Issues with up &amp; ifdown ifup: couldn't read interfaces file &quot;/etc/network/interfaces&quot;"
date: 2017-05-04
forum: Ubuntu/Debian BASED
---

### Post by alextomko on 2017-05-04
Hello - after removing the network-manager package & removing resolvconf application so I could manage my /etc/network/interfaces with ifup & ifdown along with manually manage my /etc/resolv.conf file I am receiving the following errors when trying to bring up ethernet & my wireless interface.

ethernet interface:

```
root@user-computer:/etc/network# ifup eno1
/etc/network/interfaces:21: unknown or no method and no inherits keyword specified
ifup: couldn't read interfaces file "/etc/network/interfaces"
root@user-computer:/etc/network#
```

wireless interface wlp3s0:

```
root@user-computer:/etc/network# ifup wlp3s0
/etc/network/interfaces:21: unknown or no method and no inherits keyword specified
ifup: couldn't read interfaces file "/etc/network/interfaces"
```

Here are the steps after doing a reboot of my computer - First when I boot back up my primary ethernet interface comes shut down:

Step 1:

```
root@user-computer:/home/user# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
: vibr0 is for my virtualbox.
virbr0    Link encap:Ethernet  HWaddr aa:bb:cc:dd:ee:gg 
          inet addr:xx.xx.xx.xx  Bcast:xx.xx.255.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Step 2:

Then I will try to bring it up:

```
root@user-computer:/home/user# ifup eno1
/etc/network/interfaces:21: unknown or no method and no inherits keyword specified
ifup: couldn't read interfaces file "/etc/network/interfaces"
root@user-computer:/home/user# cat /etc/network/interfaces

```
Step 3:

I read my /etc/network/interfaces file to make sure everything looks good:

```
root@user-computer:/home/user# cat /etc/network/interfaces

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

#eno1
auto eno1
iface eno1 inet static
  address xx.xx.xx.xx
  netmask 255.255.255.0
  gateway xx.xx.xx.xx
  up route add -net xx.xx.0.0 netmask 255.255.0.0 gw xx.xx.xx.xx
  up route add -net xx.xx.0.0 netmask 255.128.0.0 gw xx.xx.xx.xx
  up route add -net xx.xx.0.0 netmask 255.255.0.0 gw xx.xx.xx.xx
  up route add -net xx.xx.0.0 netmask 255.255.0.0 gw xx.xx.xx.xx
  dns-nameservers xx.xx.xx.xx xx.xx.xx.xx xx.xx.xx.xx
  dns-search local1.local local2.local local2.local local3.local local4.local 

# wlp3s0
auto wlp3s0
  iface wlp3s0 inet statc
  address xx.xx.xx.xx
  netmask 255.255.255.0
  gateway xx.xx.xx.xx
  wireless-essid xxxx
  wireless-mode managed

```
Step 4:

I can bring the interface up with ifconfig eno1 up:

```
ifconfig eno1 up
root@user-computer:/home/user# ifconfig
eno1      Link encap:Ethernet  HWaddr aa:bb:cc:dd:ee:ff  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7d00000-f7d20000
```

Step 5:

The only way I can get the interface running is to run dhclient eno1:

```
dhclient eno1
root@user-computer:/home/user# ifconfig
eno1      Link encap:Ethernet  HWaddr aa:bb:cc:dd:ee:ff  
          inet addr:xx.xx.xx.xx  Bcast:xx.xx.xx.xx  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1963415 (1.9 MB)  TX bytes:108139 (108.1 KB)
          Interrupt:20 Memory:f7d00000-f7d20000

```
Other Issues:

Trying to bring up wifi:

```
root@user-computer:/home/user/Downloads# ifup wlp3s0
/etc/network/interfaces:21: unknown or no method and no inherits keyword specified
ifup: couldn't read interfaces file "/etc/network/interfaces"
root@user-computer:/home/user/Downloads# ifconfig wlp3s0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill

```
Final:

I need to have control over my network interfaces with ifup && ifdown with the /etc/network/interfaces file along with control over my /etc/resolv.conf file:

Now my dhclient is overwriting resolv.conf again - and I specifically removed resolvconf package to stop this behavior. 

Is this a bug or what is going on and how do I resolve this issue to get ifup & ifdown working for ethernet & wifi interfaces.

---

### Post by steeldriver on 2017-05-04
Hello and welcome to the forums - please use [CODE] tags to make your posts more readable

First thing to do is correct the typo in your wlp3s0 definition - as I mentioned here:

[https://askubuntu.com/questions/911864/issues-with-up-ifdown-ifup-couldnt-read-interfaces-file-etc-network-interf](https://askubuntu.com/questions/911864/issues-with-up-ifdown-ifup-couldnt-read-interfaces-file-etc-network-interf)

However it shouldn't be necessary to do any of this in order to control name resolution on a desktop machine

---

