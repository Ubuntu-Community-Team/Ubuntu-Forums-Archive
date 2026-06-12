---
title: "[Router Help] I have a lot of devices in my home..."
date: 2012-03-15
forum: The Cafe
---

### Post by Lucradia on 2012-03-15
I have a lot of devices that cause interference in my home, including, but not limited to:
[LIST]
[*]A Microwave
[*]A Weather Radio
[*]An Android Smartphone
[*]My PlayStation 3
[*]My PlayStation 3's Controller
[*]My 5 huge fans on my desktop computer (and other case aspects of the HAF-X)
[*]My Electric Stove and Fridge
[*]Probably More too.
[/LIST]
But that doesn't even count the plethora of interference from outside too, like the building antenna for the apartment complex I live in, as well as the 10+ Wireless networks around the block I live on.

So, I was wondering what a good router, but has the ability to avoid all of this interference. I've had luck so far with a recent iteration of a D-Link Wireless N router, but recently, it decided to fry itself (Dropping DNS Resolvers, Ethernet ports being bent, etc.) I'm also a gamer as well, so I need gigabit Ethernet ports for my computer or other devices to connect to. However, in about 5 years or so, I plan to look for a suitable upgrade from my desktop to a more compact gaming system (IE: Laptop) so I will need a good router that performs excellent in Wireless capabilities (Such as the Linksys E4200v2, which I am considering.) I don't really need DD-WRT though. However, as a note, I do have systems that don't have Wireless-N Capabilities, such as my PlayStation 3, so I also obviously need good speeds for the wireless G/B.

So although the Linksys E4200v2 seems to be basically the only real choice, I just wanted to post this thread to see what others have to say. I've had good results with an old Linksys WRT54G way back for years, but I decided to upgrade, and, honestly, none of the wireless routers of today--well, a couple years ago--(even new linksys ones) could beat it. I've seen people complain about all wireless routers all across the board, and it's quite frustrating to find what brand, and what specific model does what I want.

As a note, I have no wireless router at all, thanks to the D-Link frying on me. So I have to be without printing and have to manually connect my PlayStation 3 to my cable modem (and turn on/off the cable modem each time I connect before turning on the PlayStation 3, then repeat for my computer when I want to switch back.)

---

### Post by 2F4U on 2012-03-15
I really can't help with wireless LAN, but have you ever thought about using home plug / power line communication?

[http://en.wikipedia.org/wiki/HomePlug](http://en.wikipedia.org/wiki/HomePlug)

I use it at home and I am very satisfied with it. Great, stable speed and very flexible (plug one of the adapters in a free wall outlet and you have access to the network).

---

### Post by Derek Karpinski on 2012-03-15
I have an ASUS rt-n16 that I'm real happy with. I was not happy with my D-Link dir-615. But, I bought the ASUS because it has tons of memory to flash the mega version of DD-WRT, it has usb ports, it has enough memory to run a bit torrent client and save to an external HD without running my PC.
 
It is not dual band though, so you'll get some slow down on your n-band stuff if you connect b/g.
 
I daisy chained an old b/g router to the asus to serve my b/g band devices, and set the asus to only serve the n band stuff.
 
I think the asus is a great deal at only $80 if you can live without dual band, and you want something that has enough memory to do stuff like dd-wrt in the future.

---

### Post by Lucradia on 2012-03-15
> **2F4U said:**
> I really can't help with wireless LAN, but have you ever thought about using home plug / power line communication?

[http://en.wikipedia.org/wiki/HomePlug](http://en.wikipedia.org/wiki/HomePlug)

I use it at home and I am very satisfied with it. Great, stable speed and very flexible (plug one of the adapters in a free wall outlet and you have access to the network).

Apartment complex might have more users of that device, so I'd rather not.

> **Derek Karpinski said:**
> and you want something that has enough memory to do stuff like dd-wrt in the future.

I won't be doing DD-WRT in the future unless the router comes with DD-WRT. I've heard that some ASUS Routers already do come with DD-WRT (I think I may have even made a thread about it?) But so far, I believe they aren't for sale in the USA.

---

### Post by 2F4U on 2012-03-15
This is not necessarily an issue since the devices use encryption, which should prevent outsiders from listening to your network traffic.

---

### Post by sandyd on 2012-03-15
have you used a channel scanner/plotter to check if there are any unused channels?

---

### Post by Lucradia on 2012-03-15
How would I use a channel scanner / plotter? Also, I decided on going with a Belkin 750 DB, since I've never tried a belkin device before. Thanks for the information so far however.

---

### Post by MisterGaribaldi on 2012-03-15
Personally, I'd also recommend you check out [DD-WRT.com: Supported Devices](http://www.dd-wrt.com/wiki/index.php/Supported_Devices) because they give a full breakdown on specs. At least you'll know what features you're paying for.

Also, I would recommend flashing a compatible router (obviously) to DD-WRT because their firmware is generally far better than the regular firmware you get from the manufacturer. They offer all kinds of features, like VPN and VOIP servers, etc.

---

### Post by seenthelite on 2012-03-15
Like most homes today, I have had to deal with this or a similar situation and what I have now is ethernet and wireless N set to 5Ghz. Devices not capable of using the 5Ghz N wireless now have an ethernet outlet to use. I am able to do this myself so it was an easy solution for me. I had to change two Laptop wireless cards to dual band but thats not hard to do and is quite cheap. I only use Dlink devices. 
Another method I use for devices with out 5Ghz N is using a wireless access point configured as a wireless bridge and set to only 5Ghz. D-Link's DAP-1522 is good for this as it has 4 ethernet outlets and can be positioned where you need it.

---

### Post by Old_Grey_Wolf on 2012-03-16
> **Lucradia said:**
> How would I use a channel scanner / plotter? Also, I decided on going with a Belkin 750 DB, since I've never tried a belkin device before. Thanks for the information so far however.

Although I have never had a problem with interference, I use "Wifi Radar" to scan for access points, channel number, signal strength, g/n signal, encryption, and MAC address. Wifi Radar is in the repository.

---

### Post by Lucradia on 2012-03-17
> **Old_Gray_Wolf said:**
> Although I have never had a problem with interference, I use "Wifi Radar" to scan for access points, channel number, signal strength, g/n signal, encryption, and MAC address. Wifi Radar is in the repository.

For windows though :V

---

