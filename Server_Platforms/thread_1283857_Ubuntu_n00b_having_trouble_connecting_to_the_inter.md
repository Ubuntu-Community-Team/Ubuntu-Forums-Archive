---
title: "Ubuntu n00b having trouble connecting to the internet"
date: 2009-10-06
forum: Server Platforms
---

### Post by rewsay on 2009-10-06
Hello Ubuntu Forums! I'm pretty much a n00b setting up a personal server on a Dell PowerEdge 300 which I installed Ubuntu Server Jaunty Jackalope.

 I've followed numerous guides on setting up /etc/network/interfaces and resolv.conf files to establish a connection between the server and the internet and have failed, troubleshooting for numerous days and getting to a point when I really can't find what's wrong with it. :confused:

The server is connected through ethernet directly to the cable modem, and can be seen through the network by the Apple computers networking wirelessly around the house.

When I ```
ping www.google.com
``` it returns "unknown host". And when I ```
sudo apt-get update
``` it returns that it can't fetch a bunch of URLs and I should try "sudo apt-get update" to correct this. ¬¬

I've verified all of the IPs for /etc/network/interfaces and changed them numerous times and restarted the network with different combinations of possible IPs and nameservers, none have worked. Also used OpenDNS' nameservers for resolv.conf and the one's which I found through inspecting the nameservers of my cable modem. None have worked either.\

If anyone can diagnose my problem I'd be forever in debt with you. I would enjoy to get more involved in the Ubuntu community and practices of Linux/Debian distributions. :guitar:

---

### Post by slakkie on 2009-10-06
Please see one of the following pages:

[https://help.ubuntu.com/community/NetworkConfigurationCommandLine](https://help.ubuntu.com/community/NetworkConfigurationCommandLine)
[https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic)

---

### Post by Iowan on 2009-10-06
Perhaps you could post your */etc/network/interfaces* file.

---

### Post by rewsay on 2009-10-06
EDIT:

It was the router :/
Problem solved, thanks for the links :P


------


This is /etc/network/interfaces

```
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static[INDENT]address 192.168.0.10
netmask 255.255.255.0
network 192.168.0.1
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers *the ones through which my cable modem connects to the ISP*
dns-search *my ISPs URL, also taken from the modem*
[/INDENT]
```I can access the server through other computers in the network at 192.168.0.10, which returns this "It works!". The only thing I can't get going on is the internet connection, so for every single apt-get install *anything* I try it returns E: Couldn't find package *anything*

---

