---
title: "ps3 no wifi"
date: 2009-12-04
forum: Server Platforms
---

### Post by zoggnoff on 2009-12-04
Does not work out of the box on 9.10 server ppc ps3 edition
 
Can someone please help?

---

### Post by munky99999 on 2009-12-04
[http://psubuntu.com/forums/viewtopic.php?f=4&t=458](http://psubuntu.com/forums/viewtopic.php?f=4&t=458)

---

### Post by zoggnoff on 2009-12-04
me and amrit on #linux freenode got it to associate but now i need to know how to set it up so that it connects on boot up...
 
any help there?

---

### Post by zoggnoff on 2009-12-05
ummm im having a problem
this is what i did
 
sudo nano /etc/network/interfaces
 
Rebooted and No Wifi connection....
 
doesn't make sense because when I run the command
sudo  /etc/init.d/networking restart
wifi loads every time
 
Why would it not associate access point on boot up
I did every step right
doesn't the restart networking command get all it's Wep key and SSid info from my interfaces file??
 
whats going on

---

### Post by zoggnoff on 2009-12-05
okay heres what happened
I got it to work
I added some stuff to the /etc/network/interfaces to force it to work on boot up
 
auto wlan0
iface wlan0 inet static
                 address 192.168.1.149
                 netmask 255.255.255.0
                 network 192.168.1.0
                 broadcast 192.168.1.255
                 gateway 192.168.1.1
                 pre-up /sbin/ifconfig wlan0 down
                 pre-up /sbin/ifconfig wlan0 up
                 pre-up /sbin/iwlist wlan0 scanning
                 wireless-key1 F543D56G45
                 wireless-essid Startrek
 
 
its ugly but it got the job done
pretty sure iwlist scanning isnt neccasssary but ehh
interestingly it forms a connection on 102 even thou i forward the ports to 149 and somehow it still manages to function,,, hosting a domain on it right now.
pinging my host puts lamp.domain.com at 192.168.1.102 and lamp.local at 192.168.1.149
of course thats just local stuff
 
tested from outside too and all ports forwarding perfectly

---

### Post by zoggnoff on 2009-12-11
just an update to this

I BELIEVE that the run level of the system might have something to do with this problem and the need of this solution.

It is set in run level 2 at start up and I BELIEVE that it needs to be in run level 3
at this time I do not know how to set that but will post again once I have figured this out.

---

