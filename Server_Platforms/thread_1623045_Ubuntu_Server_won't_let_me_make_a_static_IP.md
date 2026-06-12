---
title: "Ubuntu Server won't let me make a static IP"
date: 2010-11-16
forum: Server Platforms
---

### Post by andrewcow on 2010-11-16
Hi
So I followed the guide like the one [here]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html") to try and get my server to have a static IP. When I reset the network settings using 


$ sudo /etc/init.d/networking restart


it gets an error saying 

*Reconfiguring network interfaces...
SIOCADDRT: No such process
Failed to bring up eth0.


HELP!!
AndrewCow

---

### Post by pricetech on 2010-11-16
Workaround;  Does your router let you reserve IP addresses ??  I've quit doing static IPs at home since I started using the feature.  It just works better for me.

---

### Post by andrewcow on 2010-11-16
good idea i'll try that. Soo do i just set the server back to DHCP

---

### Post by wongo888 on 2010-11-16
Ensure that your entries are valid for your network. Pay particular attention to the network, netmask and gateway IPs. Are they valid?

[https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html#static-ip-addressing](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html#static-ip-addressing)

Also, consider posting your /etc/network/interfaces file.

---

### Post by pricetech on 2010-11-16
> **andrewcow said:**
> good idea i'll try that. Soo do i just set the server back to DHCP

Yes.

---

### Post by arrrghhh on 2010-11-16
I've seen this error before, and it's due to a bad static IP configuration.  Please post your /etc/network/interfaces file as previously requested.

---

### Post by chideock on 2010-11-16
Try the instructions on this How-To regarding static IP.
Page down a distance to get to them.

[http://woodel.com/](http://woodel.com/)

---

### Post by geoffmcc on 2010-11-16
> **andrewcow said:**
> Hi
So I followed the guide like the one [here]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html") to try and get my server to have a static IP. When I reset the network settings using 


$ sudo /etc/init.d/networking restart


it gets an error saying 

*Reconfiguring network interfaces...
SIOCADDRT: No such process
Failed to bring up eth0.


HELP!!
AndrewCow

check /var/log/messages. Search for eth and go threw log to see what was originally brought up. I suspect it was not eth0 for whatever reason

also /etc/network/interfaces should look something like this


> 
# The primary network interface
auto eth0

 iface eth0 inet static
     address 192.168.0.100
     network 192.168.0.0
     netmask 255.255.255.0
     broadcast 192.168.0.255
     gateway 192.168.0.1
     dns-nameservers 192.168.0.1


---

### Post by i.r.id10t on 2010-11-16
All wrong above... not due to bad info (well, it could be but usually it will complain about a duplicate entry or malformed entry).

Due to the crazy way Ubuntu handles network config and dhcp.  Instead of using the same as Debian w/ the /etc/network/interfaces file

```

auto lo
iface lo inet loopback

#for dhcp
auto eth0
iface eth0 inet dhcp

# for static
#auto eth0
#iface eth0 inet static
#  address 10.10.10.100
#  netmask 255.255.255.0
#  gateway 10.10.10.1

```

Ubuntu only has an entry for the lo device (local loopback).  So the usual ifup and ifdown don't work.

Set your file to be Debian style, reboot, and you'll be fine.

And please don't get me started with changing ethX references based on what MAC address a card has .... plays heck in my labs w/ Ubuntu on usb drives...

---

### Post by cbarron on 2010-11-16
I just set an address reservation in my router based on Mac address, works well and I dont have to worry about DHCP....makes using putty alot easier too

---

### Post by geoffmcc on 2010-11-16
> **i.r.id10t said:**
> All wrong above... not due to bad info (well, it could be but usually it will complain about a duplicate entry or malformed entry).

Due to the crazy way Ubuntu handles network config and dhcp.  Instead of using the same as Debian w/ the /etc/network/interfaces file

```

auto lo
iface lo inet loopback

#for dhcp
auto eth0
iface eth0 inet dhcp

# for static
#auto eth0
#iface eth0 inet static
#  address 10.10.10.100
#  netmask 255.255.255.0
#  gateway 10.10.10.1

```

Ubuntu only has an entry for the lo device (local loopback).  So the usual ifup and ifdown don't work.

Set your file to be Debian style, reboot, and you'll be fine.

And please don't get me started with changing ethX references based on what MAC address a card has .... plays heck in my labs w/ Ubuntu on usb drives...

I guess I wasn't clear when i said it should look like this. I was referring to the part of the file that would be edited during assigning a static ip, not the whole file. Your answer is the same as mine except in a different range and you referenced the whole file.

As far as ethX based on MAC addresses, if that was also in reference to my post i guess i wasn't clear there either. I suggested to go into /var/log/messages and search for eth within the file and see what was previously loaded, not by MAC but by ethX in plain text.

---

### Post by andrewcow on 2010-11-17
thanks lol:) I just ended up doing in on the router
AndrewCow

---

