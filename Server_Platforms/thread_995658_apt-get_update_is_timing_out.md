---
title: "apt-get update is timing out"
date: 2008-11-28
forum: Server Platforms
---

### Post by jfernand on 2008-11-28
First, I want to apologize if this question has already been answered but i could not find the solution.

I just installed 8.04 Server and I want to update all of the packages that are installed. When I run ```
sudo apt-get update
``` the connection just hangs and times out.  This is a fresh install and I am assuming the sources.list file is correct.

I know that it would be bad to update a live production machine without testing it but my server is not critical.

Are there default server settings that I must change to enable updating and upgrading?

Thanks.

---

### Post by jfernand on 2008-11-28
Well i figured out my update/upgrade problem. One of the first things I did was give my server a static IP address. When I changed this to DHCP the upgrade worked. 

So now I have a new question. Is there a reason why a static IP is not allowed to upgrade?  

This is what my interfaces file looks like:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
```

---

### Post by cariboo on 2008-11-28
If you are setting a static ip address, you should set it beyond the range of the dhcp addresses supplied by your router. In my case the dhcp range is from 192.168.1.100 to 192.168.1.110, I set the server static ip address to 192.168.1.200 and 192.168.1.202

Jim

---

### Post by andguent on 2008-11-29
I completely agree with cariboo907 above. I often set my servers to the 192.168.1.10-19 range, but it really doesn't matter as long they don't overlap with other computers.

Your /etc/network/interfaces looks fine. Did you do a 'ifup -a' once done adding info to it? The command ON ONE LINE of:
**ifdown -a;ifup -a**
should reset much of your network settings and force it to use what you gave.

When setting a server to a static IP address, it is very easy to forget about /etc/resolv.conf which should have the IP of your preffered DNS server(s). Apt-get definitely can work using a static address, but make sure you can ping websites (like google.com, cnn.com, etc) if you go back to static. If pinging websites fail, apt-get will probably fail too.

---

