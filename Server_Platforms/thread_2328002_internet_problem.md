---
title: "internet problem"
date: 2016-06-16
forum: Server Platforms
---

### Post by Flynns82 on 2016-06-16
I installed ubuntu 14.04 x86 servers, but it gives me some problems with the internet, when I type # sudo wget ww.google.com, it tells me: "resolving [www.google.com](www.google.com) .. failed: name of service not know.
wget: unable to resolve host address 'www.google.com' . i try to search this on the web but i didn't resolve, please help me..

---

### Post by steeldriver on 2016-06-16
Hello and welcome to the forum

How are your server's interfaces configured? Please post the contents of your /etc/network/interfaces and /etc/resolv.conf files 

```

cat /etc/network/interfaces

cat /etc/resolv.conf

```

---

### Post by Flynns82 on 2016-06-16
on the first it say:
auto lo
iface lo inet loopback

on the second it say: 

nameserver 192.168.1.1
nameserver 8.8.8.8
nameserver 8.8.4.4

i'm connected on internet with wifi(wlan0)

---

### Post by SeijiSensei on 2016-06-16
Is there really a nameserver running on 192.168.1.1?  (Probably it's your wifi router.)  Try deleting that entry from resolv.conf and see if you can now resolve names.

Since this is a server I'd suggest a different configuration:

1) Plug it directly into the router with an Ethernet cable.

2) Create an entry in /etc/network/interfaces like this:

```

auto eth0
iface eth0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    gateway 192.168.1.1
    dns-nameservers 8.8.8.8 8.8.4.4

```
Now the server will have a fixed IP address (192.168.1.100) and will use the Google nameservers.

Please read: [https://help.ubuntu.com/lts/serverguide/network-configuration.html#name-resolution](https://help.ubuntu.com/lts/serverguide/network-configuration.html#name-resolution)

---

### Post by Flynns82 on 2016-06-16
i delete the string: nameserver 192.168.1.1 from the resolv.conf and on the interfaces now there are write:
#the loopback network interface
auto lo
iface lo inet loopback
#wlan0 interface
auto wlan0
iface wlan0 inet static
address 192.168.1.179(i read it on the router)
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 8.8.4.4
i type wlan0 and not eth0 because now i don't have an ethernet cable, but not work

---

### Post by steeldriver on 2016-06-16
Do you have a desktop (GUI) running on your "server"? in particular, is your wifi connection configured via network-manager?

---

### Post by Flynns82 on 2016-06-16
i dont have GUI and to connect wifi i use wpa_supplicant

---

### Post by Flynns82 on 2016-06-16
what can i do? i try to install the gui but without connection also apt-get don't work

---

### Post by SeijiSensei on 2016-06-16
Can you ping 8.8.8.8?  This sounds more and more like a problem at the router itself.  Have you tried rebooting the router?

---

### Post by Flynns82 on 2016-06-16
it spam: from 192.168.1.179 icmp_seq=xx(1..2..3..4) destination host unreachable

---

