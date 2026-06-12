---
title: "wireless Cards"
date: 2007-04-11
forum: The Cafe
---

### Post by gunthermeyer on 2007-04-11
Is there any certain pcmcia wireless cards that Ubuntu prefers? At current my system doesn't have access to the internet and I'm wanting to buy one for it but don't want to buy something that Ubuntu is going to choke on or just doesn't like to work with. I also don't want to spend a whole lot of money in a pcmcia card. Thanks for any info.

---

### Post by ahaslam on 2007-04-11
It tends to be pot luck, but I had good experiences with a Linksys WPC54G v.7.1 which had an Atheros chipset. This worked otb using WEP. For WPA, configurations had to be made but it was simple enough.

You may find these useful:

[http://www.linuxquestions.org/hcl/index.php/cat/10](http://www.linuxquestions.org/hcl/index.php/cat/10)
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by yatt on 2007-04-11
> **gunthermeyer said:**
> Is there any certain pcmcia wireless cards that Ubuntu prefers? At current my system doesn't have access to the internet and I'm wanting to buy one for it but don't want to buy something that Ubuntu is going to choke on or just doesn't like to work with. I also don't want to spend a whole lot of money in a pcmcia card. Thanks for any info.
I've heard prism based cards work well. I use an atheros based card, which is a pain on non-ubuntu based distros.

---

### Post by ahaslam on 2007-04-11
> **yatt said:**
> which is a pain on non-ubuntu based distros.
Not true, if you want WPA it's the same process.

---

### Post by Skidpad on 2007-04-11
Ralink RT2500 series chipset (in an ASUS WL107g, about $30 from NewEgg) for me.

Here's a couple of links for you:
[https://www.fsf.org/resources/hw/net/wireless/cards.html](https://www.fsf.org/resources/hw/net/wireless/cards.html)

[http://ralink.rapla.net/](http://ralink.rapla.net/)


The second link breaks it down into card format, manufacturer, etc for easy review.  :)

---

### Post by PatrickMay16 on 2007-04-12
My experience with wireless in linux is, the thing you expect should work will not work or work like ****, and the thing which should not work works alright, and most of the rest will not do anything even with ndiswrapper.

Buy whatever pcmcia wireless card you can find on ebay and then sell on it if it doesn't work.

---

### Post by Co.Sinecure on 2007-04-12
I found a list of cards supported by the linug-wlan-ng drivers, and from that hunted around the local computer fair till I found one that was on the list -  a D-Link DWL-G650. 
It worked as soon as I installed restricted modules kernel on edgy.

If I can find it again I'll post it, but I did find one for the madwifi drivers (which I think are in the restricted drivers too) 
[http://madwifi.org/wiki/Compatibility]("http://madwifi.org/wiki/Compatibility")

---

