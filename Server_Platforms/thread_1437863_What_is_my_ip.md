---
title: "What is my ip ?"
date: 2010-03-24
forum: Server Platforms
---

### Post by alket on 2010-03-24
I have two computers one with Ubuntu Server (just for fun) and another with Ubuntu Desktop. I connected them with one LAN cable so there is no internet and what I want is to open firefox in Ubuntu Desktop and view the apache test page (somethink like [http://192.168.1.2](http://192.168.1.2)) but I can't find IP address, ifconfig just displays the ipv6 one ?

---

### Post by terazen on 2010-03-24
If ifconfig doesn't show an ip then you don't have one.  First, does ubuntu see the link as up for your network interface?  You may need a crossover cable if not.

If you want to manually set an ip then in your /etc/network/interfaces file on the server set something like this:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
```

Then on the desktop go into your network manager and set the same thing, but change ip address to 192.168.1.3.

Easy way to avoid all this is to plug both into a router. ;)

---

### Post by KB1JWQ on 2010-03-24
I'd check with ethtool for a link as well; if at least one of those network cards doesn't support MDI/MDIX autosense, you're going to need to use a crossover cable, or a switch.

---

### Post by Ikith on 2010-03-24
Do ifconfig in terminal it should be eth0 or wlan0 depending but it should be the inet ip on there :).

If you are looking for your external IP (assuming you are behind a router that does NAT) then go to this site [http://www.whatismyip.com/](http://www.whatismyip.com/)

---

### Post by TwiceOver on 2010-03-24
If you connected the cable between the two and the link lights don't come on, then you need what is called a cross-over cable (not that easy to just find), or a plain old network switch (very easy to find).

You'll then also need to manually configure static IP addresses for each device (do a google search, very easy).

---

### Post by Iowan on 2010-03-24
Whilst you're having server fun, you could configure it as a DHCP server. If the Desktop is "Out-of-the-box" configuration, it will probably already be set to get a DHCP address. Of course, configuring a DHCP server is more complicated than configuring a couple of static addresses, but no pain - no gain... ;)

(You'll still need MDI/MDIX autosense NIC, or switch, or crossover cable)

---

