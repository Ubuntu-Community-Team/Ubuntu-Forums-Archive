---
title: "Static routing: ready to give up the ship!"
date: 2009-09-08
forum: Server Platforms
---

### Post by mrcoulson on 2009-09-08
I have zero Linux experience.  I needed to explore the option of a Linux web server for work, so I downloaded Ubuntu Server.  It's been a real nightmare.  After a WEEK of not being able to get updates or apt-get anything that's not on my disk, I FINALLY realized that this thing is just not getting out past the firewall.  Well, after a few more days of struggle, I realized I couldn't fix that.  So, I got the network guy at work to give my server an external address.  He told me I'd have to figure out how to do do static routing on it.  I don't even know what static routing is!  Every doc I find online seems to be written for people with networking experience, so I'm actually getting more confused as I read more stuff.  

Basically, my server with example internal IP address 10.17.10.157 needs to be accessible from the web when someone types in the example address 200.100.200.100.  The network guy told me I need to add static routing for an example gateway 10.17.10.100 and an example subnet mask of 255.0.0.0.  The device is eth1 because the card on eth0 is broken.  It's a hand-me-down server.

Part of the problem surely is that I don't even understand the concept of what it is I'm trying to do.  At this point, I don't know if I have time to understand the concept.  I'm just a dumb web designer who needs to make a server work.  Understanding why is something I can do in my spare time when I'm relaxing because I got to keep my job!

I'm stressed!  I'm ready to throw in the towel and go back to my Windows server that's already just working.  

Jeremy

---

### Post by Cardale on 2009-09-08
If your using a router or something along those lines you can forward the ports that you need to the server that is static.

but on to making your server static.
Try sudo nano /etc/network/interfaces

Normally you see the dhcp setting
```
auto eth0
iface eth0 inet dhcp
```change it to 

```
auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```if you need more help send me a pm.

then reboot your system.

Just a side note you will probably have to use different IP addresses

---

### Post by Bachstelze on 2009-09-09
> **Cardale said:**
> 
then reboot your system.


Not needed. A simple [font=monospace]sudo /etc/init.d/networking restart[/font] will do.

---

### Post by mrcoulson on 2009-09-09
> **Cardale said:**
>  Try sudo nano /etc/network/interfaces

Hey, that's all I needed to do!  After all this stressing I was going through, I just needed to edit this file.  Whew!  Thanks for pointing me in the right direction!

Jeremy

---

### Post by pricetech on 2009-09-09
I hope your firewall is up to the task.  I'm a little concerned that your admin forwarded an external IP to your machine and left the rest to you.  Makes me wonder what his motivation was.

Just my thoughts on the subject.

---

### Post by Bachstelze on 2009-09-09
> **pricetech said:**
> I hope your firewall is up to the task.  I'm a little concerned that your admin forwarded an external IP to your machine and left the rest to you.  Makes me wonder what his motivation was.

Just my thoughts on the subject.

OP asked for an external IP, and the admin gave him one. What is there to wonder about?

---

### Post by Cardale on 2009-09-09
Ya I had the same problem not to long ago.  If you stick with it I think Ubuntu has a short learning curve.

---

### Post by mrcoulson on 2009-09-09
> **pricetech said:**
> I hope your firewall is up to the task.  I'm a little concerned that your admin forwarded an external IP to your machine and left the rest to you.  Makes me wonder what his motivation was.

Just my thoughts on the subject.

His motivation was probably: "Hey, I'm pretty busy and Jeremy's smart enough to figure this out on his own."  There are three of us: a network analyst, a webmaster, and a PC tech servicing the needs of 15 servers, an Exchange mail system, a big website, a few remote offices, and 200+ internal users.  I'm sure his motivation was just to give me the bare minimum of what he thought I needed and then to move on to the next issue.

Jeremy

---

### Post by wieman01 on 2009-09-09
Problem solved? Then let's move on.

---

