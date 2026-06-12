---
title: "I am thinking about getting a Pangolin Value"
date: 2007-08-27
forum: System76 Support
---

### Post by -SpaZ on 2007-08-27
I was wondering what your opinions about the Pangolin were (if it's a good buy, if it runs well, etc...).

These are the stats:

Ubuntu 7.04 (Feisty Fawn) Linux
Core 2 Duo T7300 2.0 GHz 800 MHz FSB 4 MB L2
2 GB - 2 x 1 GB DDR2 667 MHZ
160 GB 5400 RPM SATA
CD-RW / DVD-RW  
802.11 abg  
no Bluetooth  
no flash drive  
no extra battery
no extra AC adapter
no bag  
1 Yr. Ltd. Warranty and Technical Support  

Price: $1,062.00

Thoughts, comments, and suggestions?

---

### Post by kperkins on 2007-08-27
I love mine.

---

### Post by -SpaZ on 2007-08-27
> **kperkins said:**
> I love mine.

What are the specs on yours?

---

### Post by octathlon on 2007-08-27
I got one with those specs a week and a half ago.  It's really nice - very fast, nice display, the fan and dvd drive are much quieter than my other laptop.  Suspend/resume has been working perfectly which is impressive (I have not tried hibernate yet).  The only thing I'm having problems with so far is getting the wireless under Network Manager to reconnect after a disconnect; have not determined what is causing the problem yet.

---

### Post by -SpaZ on 2007-08-28
> **octathlon said:**
> I got one with those specs a week and a half ago.  It's really nice - very fast, nice display, the fan and dvd drive are much quieter than my other laptop.  Suspend/resume has been working perfectly which is impressive (I have not tried hibernate yet).  The only thing I'm having problems with so far is getting the wireless under Network Manager to reconnect after a disconnect; have not determined what is causing the problem yet.

Thanks, that sounds great.  I assume that you are running Ubuntu Feisty Fawn on it?

---

### Post by octathlon on 2007-08-28
Yes indeedy :)

---

### Post by -SpaZ on 2007-08-28
Awesome.  Sounds like I will be getting the Pangolin, thanks guys.

---

### Post by NaturalScience on 2007-08-29
That's pretty much the exact one I have, although I have a smaller hard drive.  Lucky for you they've dropped the price considerably - I paid about $400 more for mine.  Absolutely no complaints, I love the laptop.  In particular wireless rocks - blows away any previous experience I've had with wireless on Linux.  Go ahead and pick one up, you won't be disappointed.

P.S.  I even re-installed to 64-bit Feisty and it was virtually pain-free.

---

### Post by -SpaZ on 2007-08-29
> **NaturalScience said:**
> That's pretty much the exact one I have, although I have a smaller hard drive.  Lucky for you they've dropped the price considerably - I paid about $400 more for mine.  Absolutely no complaints, I love the laptop.  In particular wireless rocks - blows away any previous experience I've had with wireless on Linux.  Go ahead and pick one up, you won't be disappointed.

P.S.  I even re-installed to 64-bit Feisty and it was virtually pain-free.

So does the Pangolin come with the 64-bit or 32-bit version of Feisty?

---

### Post by wooddragon on 2007-08-29
Yes, the Pangolin Value comes installed with the 32 bit version of Fiesty. I've had one for about 3 weeks now and I'm very pleased with it. I did experience the same wireless problem of not being able to connect after a disconnect though. The problem went away after I removed network manager, set the wireless up for WPA instead of WEP, and assigned it a static IP address to my Linksys wireless router. There's a HOWTO in these forums about how to do the WPA part of it. The eth1 part of my /etc/network/interfaces file now looks like this (you would need to put your own values for ssid and wpa-psk in the brackets):

auto eth1
iface eth1 inet static
address 192.168.1.101
gateway 192.168.1.1
dns-nameservers 192.168.1.1
netmask 255.255.255.0
wpa-driver wext
wpa-ssid [your ssid here]
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk [your password key here]

The wireless now works every time I restart the laptop. I don't really miss having the network manager. Got mine with the bluetooth as well, and that took a little fix to get going, but it wasn't nearly as troublesome to find a fix for that (a quick and easy one) as the wireless problem was.

---

### Post by -SpaZ on 2007-08-29
> **wooddragon said:**
> Yes, the Pangolin Value comes installed with the 32 bit version of Fiesty. I've had one for about 3 weeks now and I'm very pleased with it. I did experience the same wireless problem of not being able to connect after a disconnect though. The problem went away after I removed network manager, set the wireless up for WPA instead of WEP, and assigned it a static IP address to my Linksys wireless router. There's a HOWTO in these forums about how to do the WPA part of it. The eth1 part of my /etc/network/interfaces file now looks like this (you would need to put your own values for ssid and wpa-psk in the brackets):

auto eth1
iface eth1 inet static
address 192.168.1.101
gateway 192.168.1.1
dns-nameservers 192.168.1.1
netmask 255.255.255.0
wpa-driver wext
wpa-ssid [your ssid here]
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk [your password key here]

The wireless now works every time I restart the laptop. I don't really miss having the network manager. Got mine with the bluetooth as well, and that took a little fix to get going, but it wasn't nearly as troublesome to find a fix for that (a quick and easy one) as the wireless problem was.

Thank you.  Wireless is always a big problem in Ubuntu, hopefully Gutsy will have all of that fixed.

---

### Post by octathlon on 2007-08-29
Wooddragon,

Thanks for posting that info.  I have been thinking about not using Network Manager since I don't usually roam around wanting to connect to various wireless networks, though I would like to keep the ability to do that.  I also think I will want to set static IPs for my home network, which I guess is also known to cause problems for NM.

So, by "removed Network Manager", did you mean from the startup services or actually uninstalling it?

---

### Post by wooddragon on 2007-08-29
I uninstalled network manager entirely. i might not have had to go as far as to uninstall it to get around this problem, but that's the way I went about it, and it works for me. :)

---

