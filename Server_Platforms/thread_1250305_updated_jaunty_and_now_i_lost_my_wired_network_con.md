---
title: "updated jaunty and now i lost my wired network connection"
date: 2009-08-26
forum: Server Platforms
---

### Post by Foeburner on 2009-08-26
I recently updated jaunty about 2 days ago and when I restarted, I couldnt get the network connections to work. Its configured correctly but I get a "network cable is unplugged" message which is not. I checked all connections and I even get link light. 

can I uninstall the recent updates? is there a way around it? I have it set to a static address and most posts I've found that are similar to this issue require that I set it to grab from the dhcp server which I cant have it to that because its a vpn server. 

Any help is appreciated!  =*D

---

### Post by cdenley on 2009-08-26
Edit the file /etc/network/interfaces.
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.0.2
        gateway 192.168.0.1
        netmask 255.255.255.0

```

then edit /etc/resolv.conf
```

nameserver 208.67.222.222
nameserver 208.67.220.220

```
This will disable the management of your network configuration with the NetworkManager applet, but might fix your problem.

---

### Post by FeTTo on 2009-08-26
gonna depend what kind of computer you have. i have a dell laptop and had the same problem...google it and you'll find the answers, i really dont remember step by step how i fixed it. ndiswrapper or something

---

### Post by Foeburner on 2009-08-26
Yes!! That worked!

The only change was adding the auto eth0 between the iface's.

Thank you!!!  XD

---

