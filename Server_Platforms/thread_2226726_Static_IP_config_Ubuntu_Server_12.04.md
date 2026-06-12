---
title: "Static IP config Ubuntu Server 12.04"
date: 2014-05-28
forum: Server Platforms
---

### Post by max48 on 2014-05-28
Hello guys, I am loving learning all I can about Linux and more specifically Ubuntu. Here is probably a rookie question but its the first time I have been stumped by Ubuntu. This is also my first experience with VirtualBox.

I just thought I would play with Ubuntu Server in VirtualBox and I was trying to set my server to use a static IP. I followed steps as best I could but I lost my internet connection. Here are some pics. Let me know if I need to get more info.

[[IMG]http://s7.postimg.org/6rwbfhbbb/static_IP.jpg[/IMG]]("http://postimg.org/image/6rwbfhbbb/") 
**I did see that I accidentally left broadcast as 192.168.*1*.255 when it should have been 192.168.0.255 I think. **Even after changing it I still cannot type [www.google.com](www.google.com) or use sudo apt-get update

I hope this is the right section for this. Thanks in advance.

Max

---

### Post by papibe on 2014-05-28
Hi max48. Welcome to the forum ):P

You need to restart your network after you correct the change:
```
sudo service networking restart
```
I believe you're trying to get your VM open to the host's network?  If so, you need to set the VM's virtual network card as 'bridge'.

For the most cases, you don't want to do that (security reasons). I'd recommend staying behind NAT, check the range VB is serving DHCP, and setting the static IP on that range.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by max48 on 2014-05-28
papibe, Thank you! Yes I was aware of the need to restart the network adapter but bridging the Host to the VM was the problem. I will take your warnings seriously as far as the bridging goes. Just playing around right now. One other quick question...

I am aware that in order to keep the /etc/resolv.conf from being overwritten you must remove the DHCP client. However when I use sudo apt-get remove dhcp-client I see this:

[[img]http://s1.postimg.org/hmz217pbv/dhcpremove.jpg[/img]](http://postimg.org/image/hmz217pbv/)

---

### Post by steeldriver on 2014-05-28
You probably don't need to stop /etc/resolv.conf getting overwritten - you just need to make sure it gets overwritten with the right values, by adding a

```
dns-nameservers 8.8.8.8 8.8.4.4
```

or whatever to the interface definition in /etc/network/interfaces file. You may need to remove any holdover definitions from /etc/resolvconf/resolv.conf.d/base if they interfere with those settings.

---

