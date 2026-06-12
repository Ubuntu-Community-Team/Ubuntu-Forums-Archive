---
title: "Server Wireless RaLink RA61"
date: 2009-06-17
forum: Server Platforms
---

### Post by Muchacho_Gasolino on 2009-06-17
I'm having an odd problem with a fresh install of ubuntu jaunty server.

I can connect fine by ethernet, and my wireless looks fine by all appearances, but won't ping anything.

an ```
iwlist wlan0 scan
``` usually gives me no results, but if i ```
sudo iwconfig essid myssid
``` first, i see my network. I took security off my network temporarily to try and make this easier.

After that, I can just ```
sudo dhclient wlan0
```, and it seems to pick up an IP fine. ifconfig says 
```
wlan0     Link encap:Ethernet  HWaddr ##:##:##:##:##:##
          inet addr:192.168.1.134  Bcast:192.168.1.255  Mask:255.255.255.0
```

If I go to my router's status page, it shows the server's MAC address connected to it. However, if I try ```
ping www.google.com
```, I get unknown host. If I try to ping the router, I get a screen full of Destination Host Unreachable.

Anyone have any thoughts?

---

### Post by Muchacho_Gasolino on 2009-06-17
One more thing: I had this wireless card working perfectly in this computer with kubuntu intrepid right before i reformatted and switched to jaunty server. I don't think I even had to open up a terminal to get the card working in kubuntu.

---

### Post by Muchacho_Gasolino on 2009-06-18
OK, I figured out that the problem has something to do with Shorewall. I uninstalled shorewall, and it works!

I'd like to have a working firewall on this thing, though. Does anyone know how to configure Shorewall to let wireless through?

---

### Post by cariboo on 2009-06-19
It's not a matter of letting the wireless through. It is the interface that your wirelss device using, usually it is wlan0, but it could be something else.

---

### Post by Muchacho_Gasolino on 2009-06-19
Yeah, it's wlan0. 

Is there a certain port I have to unblock? It doesn't seem like it, because if I try to SSH in while the server is connected to eth0, it lets me in on port 22. If I try to SSH in while the server is connected through wlan0, it says connection refused on port 22.

---

### Post by Muchacho_Gasolino on 2009-06-19
Got it!

I should have read the shorewall quickstart before doing this...

[http://www.shorewall.net/shorewall_quickstart_guide.htm](http://www.shorewall.net/shorewall_quickstart_guide.htm)

Anyway, it may be different for someone who has eth0 set as their default interface. I set mine as wlan0 on install. You can check what it is with

```
ip route ls
```

Whatever the last interface mentioned is is the default. If it's wlan0, edit /etc/shorewall/interfaces and change the eth0 you should find there to wlan0. If wlan0 is not your default, I think the firewall perceives all connections as going through the default, so you will have to add wlan0 in as a subinterface of the default somehow.

---

