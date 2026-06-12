---
title: "Ubuntu Server, No Internet Connection"
date: 2011-05-29
forum: Server Platforms
---

### Post by Dragon6 on 2011-05-29
Hello,
I installed Ubuntu server 11.04 on an old PC of mine successfully, but no internet connection at all, I checked with "ifconfig -a" and the result shows nothing but the loopback interface 

I also tried to edit the "/etc/network/interfaces" file, only the loopback interface is shown

The LAN card attached to my PC is "D-Link DGE-530T V.B1 Gigabit Ethernet Adapter" 

Please help with that
Thank You,

---

### Post by ruffEdgz on 2011-05-30
So when you do the following command in your terminal, you see "D-Link DGE-530T V.B1 Gigabit Ethernet Adapter"?
```

lspci | grep -i Ethernet

```

I wouldn't worry about the /etc/network/interfaces only having lo. I am using DHCP as we speak and my interfaces file only shows lo configurations and I am writing you now. Checkout your /etc/dhcp3/dhclient.conf to see your dhcp configuration or read up on the conf file by doing:
```

man dhclient.conf

```

Hope this helps.

---

### Post by spynappels on 2011-05-30
> **ruffEdgz said:**
> So when you do the following command in your terminal, you see "D-Link DGE-530T V.B1 Gigabit Ethernet Adapter"?
```

lspci | grep -i Ethernet

```

I wouldn't worry about the /etc/network/interfaces only having lo. I am using DHCP as we speak and my interfaces file only shows lo configurations and I am writing you now. Checkout your /etc/dhcp3/dhclient.conf to see your dhcp configuration or read up on the conf file by doing:
```

man dhclient.conf

```

Hope this helps.

The reason you see only the lo interface in /etc/network/interfaces is because your active (eth0 or wlan0) interface is being managed by Network Manager. In the Server Edition, all interfaces are normally controlled by /etc/network/interfaces


To the OP: If the lspci command above finds the card, you could add the following lines to your /etc/network/interfaces file:
```
auto eth0
iface eth0 inet dhcp
```
and restarting networking
```
sudo /etc/init.d/networking restart
```
to see if it works, and if it does, you can edit the /etc/network/interfaces file to set the IP address to static if you want.

---

### Post by brettg on 2011-06-01
Another thing that can go wrong is if you swapped LAN cards somewhere along the line which causes the udev security precautions to disable the interface.

In such a case you need to remove the udev reference to the old adapter and reboot the server.

[Details here ]("http://tuxnetworks.blogspot.com/2009/03/disappearing-network-interfaces-in.html")

---

