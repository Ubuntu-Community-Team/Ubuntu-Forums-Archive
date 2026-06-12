---
title: "Server got sluggish"
date: 2009-06-25
forum: Server Platforms
---

### Post by zagabar on 2009-06-25
Hi.

I have a pretty old (700 MHz) server computer with ubuntu server edition (gutsy) installed on it. I had it below an ISP that gave dynamic IP's automatically and all worked fine. Then I moved and the horror started... In the new place, I had a static IP for the server and so I changed the network settings to static and put in the DNS, IP and such. The settings worked. It is not behind any router, just a switch.

First when I booted it, I got "kernel panic - bla bla not syncing" or something when GRUB loaded. I tried rebooting but it didn't work. I got sad. Then I tried to unplug and replug all the IDE and Molex cords in it, and suddenly it booted up normally.

The problem I have now and have been having ever since I moved is that it is slow/sluggish in a weird way. The website I host from /var/www is not slow. Neither is the homepages any users hosts in home/username/public_html. But the SMF forum is really slow (not for me though from my computer in the LAN). It is like 40 seconds for just opening a page for most people. The connection speed on both places I lived is 100/100 mbit and I have no speed issues otherwise on that front. When I ping my server locally I get >1 ms, and other people who pings it gets normal fast responses. The FTP is also slow (for me too) but not while downloading, only on listing directories and connecting. It can take ~30 sec. The dl itself goes up to huge speeds for most people (like 1-3 mb/s). Connecting with ssh is also terribly slow for everyone (me too). To just get to type your password takes like 30 seconds. But when connected, most commands goes in an instant. 

I have rebooted the server many times. I have checked the DMA settings for the hdds and they are both on udma4 in both BIOS and ubuntu. What more can I try?

Help is really appreciated. =) I am kinda stuck and cannot use my server in this state...

Thanks.

---

### Post by wojox on 2009-06-25
Try selecting "Disable hostname lookups?" in SMF Admin > Features and Options > Layout and Options tab.

---

### Post by windependence on 2009-06-25
Please post the contents of your /etc/resolv.conf and your /etc/network/interfaces file.

-Tim

---

### Post by zagabar on 2009-06-25
> **wojox said:**
> Try selecting "Disable hostname lookups?" in SMF Admin > Features and Options > Layout and Options tab.

Cool, it worked! Thanks! =D Now the forum is fast. However the SSH and FTP is still as slow.

---

### Post by zagabar on 2009-06-25
> **windependence said:**
> Please post the contents of your /etc/resolv.conf and your /etc/network/interfaces file.

-Tim

---------------------------------resolv:  

search .
nameserver 192.168.0.1


-----------------------------interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
 iface eth0 inet static
        address 83.219.220.244
        netmask 255.255.255.0
        network 83.219.220.0
        broadcast 83.219.220.255
        gateway 83.219.220.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 213.79.168.2
        dns-search umea.cust.skycom.se

---

### Post by windependence on 2009-06-25
Edit your /etc/resolv.conf like this:

```
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 4.2.2.2
```
Restart the network and try it again.

-Tim

---

### Post by windependence on 2009-06-25
> **zagabar said:**
> Cool, it worked! Thanks! =D Now the forum is fast. However the SSH and FTP is still as slow.

The reason this worked is because your forum was using the 192.168.0.1 address to try to look up DNS. Your server is configured with an external IP address so this is not going to work and it times out, and finally does it's lookup through the external gateway. This is affecting everything on the machine. If you follow my suggestion above, you will most likely be able to turn your hostname lookups back on.

-Tim

---

### Post by zagabar on 2009-06-25
Yay, it worked!! Completely awesome! Thanks! =)

And now some theory for me to learn. Why did it work and what does that resolv file do?

---

### Post by windependence on 2009-06-27
The /etc/resolv.conf file is where your DNS servers are stored. This tells your server which servers to query to look up domain names. As you may know, when you type in [www.somesite.com](www.somesite.com), your machine doesn't understand somesite.com, it must be translated to an IP address. Your server goes to the DNS servers listed in resolv.conf to find out what the IP address of somesite.com is. The longer this query takes, the slower the page will load so fast DNS is very important as to your perceived speed. If you point it at your router, most times that's fine because the router has DNS servers it also uses which can either be set by you, or found by DHCP from your ISP. If this is not configured properly as in your case, then the DNS query will take longer. Furthermore, you only had one nameserver configured so if that did not work, the query will time out like it did for you. If you had a second and third DNS server configured, the machine would have tried the other ones when the first one did not respond. Resolv.conf will only use the first three nameservers you have listed. You can list as many as you want but only the first three will be used.

-Tim

---

