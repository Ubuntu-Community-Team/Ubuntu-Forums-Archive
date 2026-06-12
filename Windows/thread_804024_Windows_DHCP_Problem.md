---
title: "Windows DHCP Problem"
date: 2008-05-22
forum: Windows
---

### Post by DGortze380 on 2008-05-22
Frankly, I'm so tired of windows it pains me to even post this, but I'm setting up a Windows 98SE Desktop for a friend (he insists, so I'm giving it a shot)...

... Everything works fine, except wireless.  I've installed a linksys Wireless G PCI card, it's installed correctly, connects to my network correctly, can't connect to the internet.

The card says it's connected to the network, the cards mac address shows up in my routers log, but no IP gets assigned, no subnet, and no gateway. 

There are three other computers working correctly via DHCP on the network. I tried assigning a static IP on the windows box, still nothing.

Anyone have any ideas on why this machine wouldnt be getting an IP?

---

### Post by hellion0 on 2008-05-23
Sounds like the card isn't asking for a DHCP lease from the router. Do you have another machine you could try the card in? If so, hook the card in question up to that machine, install what's needed, and see if it has the same problems.

If it doesn't, then it's something 98SE-related.

---

### Post by smoker on 2008-05-23
just a suggestion, sometimes you have to adjust a setting in the modem/router for it to relate to different protocols, ie, wireless b, wireless g, whatever. maybe worth a check

---

### Post by DGortze380 on 2008-05-23
Thanks for the suggestions. No other machine to check the card in, but I tried a different card in the same machine (this one USB), same problem. Leads me to believe it's a 98SE thing... I'm going to try forcing 802.11b and see if it helps at all. Any other ideas?

---

### Post by jrusso2 on 2008-05-24
run winipcfg

Release and renew the wireless card.

If you can't get an IP address are you using WPA?  I don't think W98 does WPA, at least mine won't.

---

### Post by DGortze380 on 2008-05-24
tried winipcfg ... cant release and renew. click it, nothing happens. still no ip assigned when checking in ipconfig afterwards.

havent had time yet to force a spec standard. I'll try that next.

---

### Post by sdowney717 on 2008-05-25
you likely have a dns issue
goto properties TCP/IP for the card and advanced DNS server and give it the DNS server ip address. Plus you may have to type in the computer host name, I just did this on a 98 setup and anyname worked.

you can run ipconfig and ipconfig/all to view info about the connections.
It should also work fine with obtaining an IP automatically, IF the card is properly installed. If the card is not installed right it wont work. How does it look under device manager?

---

### Post by DGortze380 on 2008-05-27
still having issues. Forced 802.11b , same problem.

Changed the DNS server to my routers IP address, made sure everything was enabled correctly on the router. DNS host name shows up in ipconfig, but not the server. still no IP or gateway information.

Device is installed correctly, shows correctly in Device Manager with no errors.

I'm not sure where to go from here. A DNS issue makes sense, maybe I'm probably setting something up wrong... god I hate windows... lol

---

### Post by rickyjones on 2008-05-27
> **DGortze380 said:**
> still having issues. Forced 802.11b , same problem.

Changed the DNS server to my routers IP address, made sure everything was enabled correctly on the router. DNS host name shows up in ipconfig, but not the server. still no IP or gateway information.

Device is installed correctly, shows correctly in Device Manager with no errors.

I'm not sure where to go from here. A DNS issue makes sense, maybe I'm probably setting something up wrong... god I hate windows... lol

Are you positive that you have the correct drivers for that version of the card? I know especially with DLINK wireless cards you need to match the driver with the version of the card. It will install, but if there is a mismatch then it will not fully connect to the network, even if it says it has.

-Richard

---

### Post by jrusso2 on 2008-05-27
Your not using WPA encryption or something?  I have W98SE on an old laptop with a netgear wireless card and it works fine with DHCP.  But it won't work with WPA.

---

### Post by DGortze380 on 2008-05-28
I'm positive it was installed correctly, and no, no encryption... no matter, I've convinced him to ditch windows for ubuntu. Everything is set-up, runs fast, wireless supported by default, hes up and running...

... yet another reason to not even bother with windows... always go with unix.

---

