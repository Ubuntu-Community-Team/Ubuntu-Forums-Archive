---
title: "No Internet Connection with RJ45 cable"
date: 2007-08-14
forum: Windows
---

### Post by Zdravko on 2007-08-14
Hi there! I am really frustrated by a problem I experience under WinXP. I hope that you can help me resolve it.
At home there is an Internet plug-in RJ-45 and I was assured that I have Internet there.
My laptop is Acer TravelMate 2493NWLMi. It had such a cable and I used it. However I recieve the red X mark below stating: "A network cable is unplugged".
What should I do now?
Help me!

---

### Post by Steve1961 on 2007-08-14
try:

ipconfig /renew

---

### Post by Zdravko on 2007-08-14
> **Zdravko said:**
> Hi there! I am really frustrated by a problem I experience under WinXP. I hope that you can help me resolve it.
At home there is an Internet plug-in RJ-45 and I was assured that I have Internet there.
My laptop is Acer TravelMate 2493NWLMi. It had such a cable and I used it. However I recieve the red X mark below stating: "A network cable is unplugged".
What should I do now?
Help me!
Where do I type that?
Btw, my laptop has 2 plug-ins - both seem to look the same. The first one is behind the laptop - it has 2 golden wires inside it and a square picture near it. That is where I plug in the RJ45 cable.
The second one is on the left side. It is rather rectangular than square and has 8 golden pins. The attached images illustrate the situation.

---

### Post by heimo on 2007-08-14
> **Zdravko said:**
> Where do I type that?
Btw, my laptop has 2 plug-ins - both seem to look the same. The first one is behind the laptop - it has 2 golden wires inside it and a square picture near it. That is where I plug in the RJ45 cable.
The second one is on the left side. It is rather rectangular than square and has 8 golden pins. The attached images illustrate the situation.

The second one is for ethernet. First one is probably for modem. Try the other one.

---

### Post by Zdravko on 2007-08-14
> **heimo said:**
> The second one is for ethernet. First one is probably for modem. Try the other one.
Okay, I will try it, when I come back at home today. But I am pretty sure that my cable fitted perfectly in the hole behind the laptop.

---

### Post by heimo on 2007-08-14
> **Zdravko said:**
> Okay, I will try it, when I come back at home today. But I am pretty sure that my cable fitted perfectly in the hole behind the laptop.

Narrow one (RJ-11) will also fit the 8 pin one (RJ-45), but it won't work. Make sure your cable has 8 wires (is cat 5 or cat 6 cable with RJ-45 connectors) and connect it to ethernet port (at both ends!)

---

### Post by Zdravko on 2007-08-14
> **heimo said:**
> Narrow one (RJ-11) will also fit the 8 pin one (RJ-45), but it won't work. Make sure your cable has 8 wires (is cat 5 or cat 6 cable with RJ-45 connectors) and connect it to ethernet port (at both ends!)
I don't have the cable with me right now. But I strongly believe that it is pure symmetrical on both ends. It looks as if it has 8 wires with different colors inside it. The cables fits into the plugin in the wall perfectly.

---

### Post by heimo on 2007-08-14
> **Zdravko said:**
> I don't have the cable with me right now. But I strongly believe that it is pure symmetrical on both ends. It looks as if it has 8 wires with different colors inside it. The cables fits into the plugin in the wall perfectly.

Ok, good. All I can say is that symbol on this image, line connecting squares symbolizes local area network or ethernet, and I'm 99.99% sure that's the port you should be using.
[http://ubuntuforums.org/attachment.php?attachmentid=40634&d=1187092252](http://ubuntuforums.org/attachment.php?attachmentid=40634&d=1187092252)

---

### Post by Zdravko on 2007-08-14
> **heimo said:**
> Ok, good. All I can say is that symbol on this image, line connecting squares symbolizes local area network or ethernet, and I'm 99.99% sure that's the port you should be using.
[http://ubuntuforums.org/attachment.php?attachmentid=40634&d=1187092252](http://ubuntuforums.org/attachment.php?attachmentid=40634&d=1187092252)
I hope that you're right. Because if this cable does something wrong to my laptop, or even worse, if it interferes with the other computers in the building, I swear to God, you will be spanked!:-&

---

### Post by heimo on 2007-08-14
> **Zdravko said:**
> I hope that you're right. Because if this cable does something wrong to my laptop, or even worse, if it interferes with the other computers in the building, I swear to God, you will be spanked!:-&

Thank you for the offer, but I'm volunteer and require no compensation.

---

### Post by Zdravko on 2007-08-15
Yesterday I tried your advice. But the cable I have does not fit into that "Ethernet" plugin in the laptop. It is just too square to fit in there. Do I have a Fax/Modem cable? Do I need an RJ45 cable for Internet? How much does it cost? Any suggestions?

---

### Post by heimo on 2007-08-15
> **Zdravko said:**
> Yesterday I tried your advice. But the cable I have does not fit into that "Ethernet" plugin in the laptop. It is just too square to fit in there. Do I have a Fax/Modem cable? Do I need an RJ45 cable for Internet? How much does it cost? Any suggestions?

Well, it's possible to get internet connection with dial-up, using modem (RJ-11), but broadband connection is usually established with ADSL/Cable modem through USB or over ethernet (RJ-45 connectors). For ethernet connection, you'll need straight (not crossover) cat 5 or cat 6 cable (8 wires) with RJ-45 connectors on each end. 3-5 meter cables cost couple bucks (under $10). If you have a RJ-45 connection on wall, you may or may not have internet connection - it's possible that somewhere there is a router which shares internet connection via local area network (ethernet). Or it may be just a connector with no other end connected to anything. Best way to find out is to try.

---

### Post by Zdravko on 2007-08-15
I was just given an RJ45 cable. This time it fits perfectly in the second plug-in. I am almost sure that this is the cable I need. When I come home, I will test it. It must work!

---

### Post by heimo on 2007-08-15
> **Zdravko said:**
> I was just given an RJ45 cable. This time it fits perfectly in the second plug-in. I am almost sure that this is the cable I need. When I come home, I will test it. It must work!

I hope it does. It probably uses DHCP (dynamic host configuration protocol) to setup connection automatically (ip address, dns settings etc), which should be default. If you don't get connection, you may try what Steve suggested, run "ipconfig /renew". You do that on command line (start->programs->accessories->command prompt). Good luck.

---

### Post by Zdravko on 2007-08-15
Thanks. I will try it... and eventually report soon.

---

