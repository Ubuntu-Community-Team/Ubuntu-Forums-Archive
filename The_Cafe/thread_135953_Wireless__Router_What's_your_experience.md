---
title: "Wireless  Router? What's your experience?"
date: 2006-02-24
forum: The Cafe
---

### Post by carl13 on 2006-02-24
What has  your experience been with wireless routers and what do you recommend? I wired my current house with cat 5 cable so I have been using a regular router. I am moving and will not have the option to wire my new house. I have used connections via wireless routers at friends' houses but they have always seemed to have some lag. I was not sure if this is true of all wireless routers or was just a problem with their setup.

---

### Post by andrewsawyer on 2006-02-24
I'm using a Dlink DI-624 AP and I've had no problems with it.  I have got a Dlink PCI wifi card in my machine that both Dapper and Breezy picked up without problem.  My Acer latop wifi card worked fine, however my girlfriends Compaq needed some 'tweaking'.

---

### Post by polo_step on 2006-02-24
[FONT="Fixedsys"]You might want to run this by the "Networking" forum in Hardware, but I think the biggest hassle you'll have is getting the wireless cards working right under Linux if they are typical new stuff.  I've never gotten any of my wireless PCI or USB devices to work under Linux.

Routers either have the features you want or they don't.  I'm running a Zyxel P-330W, which is not a terribly distinguished router, but it works perfectly for what I want.  It has all the current security options (something to be aware of, as a lot of bargain routers don't) and after the latest firmware update yesterday, it's 100% reliable with all the different "g" devices I have here.  

I don't game or anything, so I don't know if it has any problems for that kind of use, but the DSL throughput tests identically to hardwired ethernet direct to the modem.

Can't complain for $19.99![/FONT]

---

### Post by futz on 2006-02-24
[QUOTE=andrewsawyer]I'm using a Dlink DI-624 AP and I've had no problems with it.  I have got a Dlink PCI wifi card in my machine that both Dapper and Breezy picked up without problem.[/QUOTE]
I use the same DI-624 [http://www.dlink.com/products/?pid=6](http://www.dlink.com/products/?pid=6) router and it works great. Cheap and reliable. My Ubuntu box has a giveaway Gigabyte wireless card that came with a mainboard I bought a while ago for another computer. Ubuntu did drivers for it automagically - it just works. 

Wireless is a tad slower than wired, but it isn't a big deal. Fast enough.

---

### Post by polo_step on 2006-02-24
[QUOTE=futz] My Ubuntu box has a giveaway Gigabyte wireless card that came with a mainboard I bought a while ago for another computer. Ubuntu did drivers for it automagically - it just works. [/QUOTE]
[FONT="Fixedsys"]Do you know what chip it runs?  Can you do WPA2/AES w/no AP SSID in Ubuntu as auto-installed?[/FONT]

---

### Post by futz on 2006-02-24
[QUOTE=polo_step][FONT="Fixedsys"]Do you know what chip it runs?[/quote]
Ralink RT2500

>  Can you do WPA2/AES w/no AP SSID in Ubuntu as auto-installed?[/FONT]
WPA2... I'm not sure. I just use WEP. Secure enough for me.

---

### Post by nickle on 2006-02-24
Just bought a D-link DWL-G520 pci card last week with an artheros chip. Popped it in a, fired up ubuntu and hey presto it was recognised immediately. All I had to do then was use the desktop wifi tools to set it up to (almost) get it working. I had to do *sudo dhclient ath0 *to assign the IP assigned and there I had it all working. There are some good howto's on in this forum. I would avoid getting a card that is only supported by ndiswrapper if possible. I have only had trouble with that implementation.

---

### Post by futz on 2006-02-25
[QUOTE=nickle]Just bought a D-link DWL-G520 pci card last week with an artheros chip. Popped it in a, fired up ubuntu and hey presto it was recognised immediately. All I had to do then was use the desktop wifi tools to set it up to (almost) get it working. I had to do *sudo dhclient ath0 *to assign the IP assigned and there I had it all working. There are some good howto's on in this forum. I would avoid getting a card that is only supported by ndiswrapper if possible. I have only had trouble with that implementation.[/QUOTE]
Excellent! I have one of those too, in my Fedora4/SUSE/Mandriva box. Was wondering if Ubuntu would pick it up without a fight. Fedora doesn't, but SUSE and Mandriva do.

Maybe I'll buy another for my other Ubuntu box.

---

### Post by polo_step on 2006-02-25
[FONT="Fixedsys"]WEP is grossly obsolete.  It can be cracked in ten minutes by some kid with [ commonly available programs. ]("http://video.google.com/videoplay?docid=-1021256519470427962&q=hacking")

Ubuntu does not transparently support the Ralink 2500's native security features.  It is possible that with enough doinking around you can get them to work, but they don't work on install.

Not good enough. [/FONT]:(

---

### Post by futz on 2006-02-25
[QUOTE=polo_step]WEP is grossly obsolete.  It can be cracked in ten minutes [/QUOTE]
Yes, WEP is very weak. But it's much better than nothing. I've wardrived around town here and there are MANY wide open networks. The general public is woefully uninformed about wireless security. They just buy em and plug em in and they work.

Crackers might crack mine just for the "challenge", but there's not much reason to bother otherwise.

I was going to crack my neighbor's WEP just for fun, but I got lazy and had other things to do. Never got around to it.

---

