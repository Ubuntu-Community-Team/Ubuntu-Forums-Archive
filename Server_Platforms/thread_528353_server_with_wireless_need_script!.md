---
title: "server with wireless need script!"
date: 2007-08-17
forum: Server Platforms
---

### Post by yage on 2007-08-17
Hi i'm having BIG problems here.... i've been trying for some time now to get my (yes) wireless server to catch the same ip everytime it boots automaticly. 
The networkcard is at netgear and i use ndiswrapper to load the right driver (wg311v3) it's a encrypted net but only with WEP.. 

If i issue the command after boot;
```
sudo iwconfig wlan0 essid <myessid> channel 5 key <somekey>
```
and then;
```
sudo dhclient wlan0
```
it all works as it should! 

I need this to work at boot time since its a LAMP server.
No there is no GUI on this one.

someone please help :confused:

---

### Post by a9k on 2007-08-17
The ip address is assigned to your wifi server by the DHCP server. 

You have two choices:

(1) If you have control of the DHCP server you should associate the MAC address of your WIFI interface with an ip address you want to have your server use.

(2) assuming you are using private IP's like 192.168.x.x, you could give your machine a static ip address outside the range the DHCP server is handing out. The new address should not duplicate any ip address already in use.

Links:
[Ubuntu Network Configuration Doc]("http://doc.ubuntu.com/ubuntu/serverguide/C/network-configuration.html")
[http://en.wikipedia.org/wiki/MAC_address]("http://en.wikipedia.org/wiki/MAC_address")

---

### Post by yage on 2007-08-17
My bad... this is done! it's assigned by MAC but it still don't work! i need a script to run here... the nic will not come up with a ip to route

---

### Post by yage on 2007-08-17
SOLVED!

Just had to make e file that contained 
```
#!/bin/bash
sudo iwconfig wlan0 essid <essid> channel 5 key<my key>
```
save it somewhere and name it wlan, then link it to /etc/rc2.d with the name S15Wlan

My /etc/network/interfaces looks like this
```
auto wlan0
iface wlan0 inet static 
        address 192.168.1.101
        netmask 255.255.255.0
        gateway 192.168.1.1
        dns-nameservers 192.168.1.1
        essid <myessid>
        mode managed
        channel 5
        key <my key>
```

Hope that this helps someone :popcorn:

---

