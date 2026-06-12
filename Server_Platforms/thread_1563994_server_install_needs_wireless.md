---
title: "server install needs wireless"
date: 2010-08-30
forum: Server Platforms
---

### Post by cli168 on 2010-08-30
I got ubuntu 10 server on livecd.  I have installed it on my pc, however I dont seem to have all the networking installed (mainly wireless).  Is the networking on the livecd, can I install it off the livecd again, as I have already done the install.

thanks

---

### Post by silbak04 on 2010-08-30
did you install your driver for your wireless card already? usually when you have a network adapter, you are going to have to install ndiswrapper to get your wireless working

---

### Post by dtoronto on 2010-08-30
I think 10.04 has a much more robust set of open source wifi drivers.  You should be able to get it up and running.  On your server check your  /etc/udev/rules.d/70-persistent-net.rules to make sure that you have wlan0 set up and then vi or nano into your /etc/network/interfaces and add

```

auto wlan0
iface wlan0 inet dhcp

```

if you still have problems then you'll probably have to run ndiswrapper to get it to work.

---

### Post by cli168 on 2010-08-30
I think I got a error of iface not found.
Is iface installed by default?

---

### Post by silbak04 on 2010-09-01
> **dtoronto said:**
> I think 10.04 has a much more robust set of open source wifi drivers.  You should be able to get it up and running.  On your server check your  /etc/udev/rules.d/70-persistent-net.rules to make sure that you have wlan0 set up and then vi or nano into your /etc/network/interfaces and add

```

auto wlan0
iface wlan0 inet dhcp

```

if you still have problems then you'll probably have to run ndiswrapper to get it to work.

if you nano into your /etc/network/interfaces for wireless you actually want this: 

```

auto wlan0
iface wlan0 inet static 
wireless-essid XXXXXXXXXXX
wireless-key XXXXXXXXXXX
address 192.168.X.X
netmask 255.255.255.0
gateway 192.168.X.XXX

```

then run
```

service network restart

```
usually you want your ip to be static rather than dhcp...dhcp renews your ip after some time (dynamic), so it would be a hassle to connect to your computer through ssh or something, but like I have mentioned before, if this doesn't work, then you're going to have to work with ndiswrapper.

---

### Post by BkkBonanza on 2010-09-01
Umm. No interface. Start with **sudo ifconfig -a** and make sure the wlan0 or other wireless adapter is in the list. If not, then you need to determine your wireless make/model# and get and install the suitable driver. There is a list of wireless adapters in the Laptop forum here and how they are supported.

Sometimes a wireless adapter will show as eth1. Post your output here for help deciding.

---

