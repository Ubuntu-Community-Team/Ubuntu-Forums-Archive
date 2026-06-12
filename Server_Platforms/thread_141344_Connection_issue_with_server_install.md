---
title: "Connection issue with server install"
date: 2006-03-08
forum: Server Platforms
---

### Post by Tux_Phoenix on 2006-03-08
Ok I set up my server a while back and then got bussy with work and haven't had time to mess with it in a few months but now Im back and hope to get this nocked out quick.  Ok I have everything installed and working and I can see my site on my lan.  But then I type my static ip fomr my isp I get a time out error.  I then checked to make sure my server could talk to the outside world and it can't.  So I think the problem is in my /etc/network/interfaces but Im not really sure what I should be looking for.  So here is my layout

Modem Zoom 5551a: 10.0.0.2
Router Linksys BEFSR41v4: (static set to) 10.0.0.5
Server:  (Static set to) 192.168.1.30


Here is my current interfaces: 

```
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address 192.168.1.30
        netmask 255.255.255.0
        gateway 192.168.1.1

auto eth0
```

I am going to keep looking for answers but if anyone has an idea of what I am doing wrong feel free to point me in the right direction.  Thanks :-k :-k :-k :-k

---

### Post by Iowan on 2006-03-08
I'm probably spewing more smoke than fact (again), but it would seem that your server would need to be in the same subnet as whatever it's connected to.

---

### Post by VinceDee on 2006-03-08
I'm not the expert but it looks to me as though your network card is set up properly. Maybe it's your router, try this:

[http://www.ubuntuwebservers.com/?q=node/46](http://www.ubuntuwebservers.com/?q=node/46)


Vince

---

### Post by Tux_Phoenix on 2006-03-08
[QUOTE=VinceDee]I'm not the expert but it looks to me as though your network card is set up properly. Maybe it's your router, try this:

[http://www.ubuntuwebservers.com/?q=node/46](http://www.ubuntuwebservers.com/?q=node/46)


Vince[/QUOTE]


Thanks for the help but it didn't do anything for me.  And the links on his site tell you how to set a static IP useing windows.  

I am fairly sure I am missiong somethign simple I had the connectiong work back when I started this whole thing but have since then changed routers.  Anyone else have an idea of what I should look for?

---

### Post by Tux_Phoenix on 2006-03-08
Fairly sure its a problem with how I have my DNS set up cause I can ping IP addresses but not domain names.   I tryed adding the DNS ips from my isp but no good.  Here is my current interfaces...



```
# The primary network interface
iface eth0 inet static
        address 192.168.1.30
        netmask 255.255.255.0
        gateway 192.168.1.1
        nameserver 192.107.41.34
        nameserver 192.107.41.21

auto eth0

```

---

### Post by Iowan on 2006-03-09
[QUOTE=Tux_Phoenix]I am fairly sure I am missiong somethign simple [COLOR="Red"]I had the connectiong work back when I started this whole thing but have since then changed routers[/COLOR].  Anyone else have an idea of what I should look for?[/QUOTE] Something in the new router different?

---

### Post by kmi on 2006-03-09
Maybe a dumb question but what machine/os/etc. is at 192.168.1.1 ?

Then, if I have understood something, you can ping XX.YY.ZZ.AA but not [www.ohmygod.org](www.ohmygod.org) ?

Could you please give more details about your network ?

---

### Post by Tux_Phoenix on 2006-03-09
The new router is a linksys BEFSR41v4.  My set up is Modem -> Router -> Switch -> Server.  

Modem: Zoom adsl 5551a
Router: Linksys BEFSR41v4
Switch: Tigerstack 12 port
Server: Old Dell poweredge

There are some differnces with this new router cause it is a dif brand.  What they are spacificly I couldn't tell you.

---

### Post by kmi on 2006-03-09
[QUOTE=Tux_Phoenix]

```
# The primary network interface
iface eth0 inet static
        address 192.168.1.30
        netmask 255.255.255.0
        gateway 192.168.1.1
        nameserver 192.107.41.34
        nameserver 192.107.41.21

auto eth0
```[/QUOTE]

In /etc/network/interfaces, I have the equivalent of :

```
# The primary network interface
iface eth0 inet static
        address 192.168.1.30
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        **dns-nameservers** 192.107.41.34 192.107.41.21
auto eth0
```

dns-nameservers instead of nameserver might be worth a try... 

('resolvconf' is installed on my system, I don't know if you'll miss it but I'd say... no ! ;))

---

