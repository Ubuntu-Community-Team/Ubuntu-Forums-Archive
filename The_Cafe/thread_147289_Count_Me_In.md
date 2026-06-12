---
title: "Count Me In"
date: 2006-03-19
forum: The Cafe
---

### Post by bradlis7 on 2006-03-19
I've gotten a computer up and running with Ubuntu now. I've had previous experience with Fedora, but that was a year or so ago.

I need a wireless card though... anyone have any suggestions for a cheap one on ebay that will work well? I compared the online list of working cards to ones on ebay, but couldn't find one I was pleased with. I can do configuring, but would rather not if possible. If I could get a cheap router that would connect me to a wireless network, that would work too (I have wired network cards that work I think). Any suggestions would be great!

---

### Post by Zelut on 2006-03-19
I would suggest a broadcom chipset if you look for a wireless card to buy.  They seem to be pretty common & are fairly well supported.  Also, Dapper will be including firmware for broadcom chipsets so it should be very limited configuration.

I've also bought a netgear WG311 pci card and it works fine (using ndiswrapper)..  I guess its just what you can find on the supported page vs. what you can find locally/eBay to purchase.

---

### Post by cilynx on 2006-03-19
Most Linksys and Netgear stuff works.  Quite a bit of 3com as well.  Avoid Broadcom like the plague.

If you're looking for 802.11b, look into the Prism chipset
If you're looking for 802.11g, look into Prism54

They seem to be the best supported of all.  As for a router, I prefer the Linksys stuff as they're basically rebadged Cisco equip.  Also, some of the open-source firmwares are nice.

---

### Post by LinuxKid on 2006-03-19
[QUOTE=kuyaedz]I would suggest a broadcom chipset if you look for a wireless card to buy.  They seem to be pretty common & are fairly well supported.  Also, Dapper will be including firmware for broadcom chipsets so it should be very limited configuration.

I've also bought a netgear WG311 pci card and it works fine (using ndiswrapper)..  I guess its just what you can find on the supported page vs. what you can find locally/eBay to purchase.[/QUOTE]
yes, broadcom should **_START_** working with dapper (which I'm downloading now, come on 35% ;))

and yes, broadcom is very common

but it is absolutely **_NOT_** supported by any linux distro at all (other than dapper, come on 36% ;)), you could use ndiswrapper but I have been having so much trouble with it that I don't think it's worth it

sorry for the harshness, but I don't want anyone getting into what I got into (just look at the sig :()

---

### Post by bradlis7 on 2006-03-19
Thanks for the replies. I've bid on a Linksys WUSB54G. That should work good enough.

---

### Post by Zelut on 2006-03-19
I hear a lot of people don't like ndiswrapper but its supported 7 wireless cards for me.. 

Where are you getting stuck with ndiswrapper?

---

### Post by LinuxKid on 2006-03-19
well, I can't tell you outright, because as my sig says; I'm in windows

but if I remember it was:

**ndiswrapper -i bcmwl5.inf**
output: installed already, use -e to remove

when I tried to remove and install again it didn't work

so I went on:
**ndiswrapper -m**
output: .... is a read only file (I got this once, hmm...)

**depmod -a**
output: fatal:... (can't remember)

**modprobe ndiswrapper**
output: nothing probably because of the other steps

btw, don't think I did this myself no!!!, I'm a noob, I got it from instructions ^_^

if you want, after dapper finishes downloading (come on 47% ;)), I'll go back in and write down everything I get (that is as long as dapper doesn't configure it the other way ;))

---

### Post by briancurtin on 2006-03-20
[QUOTE=kuyaedz]I would suggest a broadcom chipset if you look for a wireless card to buy.[/QUOTE]
[QUOTE=cilynx]Avoid Broadcom like the plague.[/QUOTE]

so, which one should this guy be listening to?

---

### Post by matthinckley on 2006-03-20
I love Linksys.. have all Linksys networking equipment at home with wireless G router and 1 wireless G card and 1 wireless B card.. never a problem with Linux.. both wireless cards worked right out of the box.. no hunting for drivers at all.

Linksys made by Cisco..

---

### Post by John.Michael.Kane on 2006-03-20
[http://cgi.ebay.com/Belkin-F5D7010-Wireless-G-Notebook-Card-PCMCIA-54g-NIB_W0QQitemZ5677822073QQcategoryZ45000QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/Belkin-F5D7010-Wireless-G-Notebook-Card-PCMCIA-54g-NIB_W0QQitemZ5677822073QQcategoryZ45000QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)
[http://cgi.ebay.com/D-Link-DWL-G630-802-11G-PCMCIA-Wireless-Card_W0QQitemZ9700126399QQcategoryZ45000QQrdZ1QQcmdZViewItem](http://cgi.ebay.com/D-Link-DWL-G630-802-11G-PCMCIA-Wireless-Card_W0QQitemZ9700126399QQcategoryZ45000QQrdZ1QQcmdZViewItem)

---

### Post by BoyOfDestiny on 2006-03-20
Which guy to listen to... Not a hard call. A well supported wireless card will not require ndiswrapper and should work out of the box.

I've heard from a friend who works at broadcom... That they will eventually support linux (i.e. provide native linux drivers)...

If you want out of the box support... I dunno, only my laptop has out of the box wireless (intel internal wireless)

Reasons for disliking ndiswrapper vary... I'll mention a few, dunno how will it would work on other architectures ( since you are using the windows driver...) and supposedly not as efficient. I consider it a 'last resort'.

---

### Post by GeneralZod on 2006-03-20
[QUOTE=briancurtin]so, which one should this guy be listening to?[/QUOTE]

Let's just say that this thread has contained the only positive recommendation for a Broadcomm wireless card that I have ever seen in my entire life ;)

---

### Post by bradlis7 on 2006-03-20
I'm using a desktop PC, so pcmcia cards will not do. I'm still winning the bid on the linksys, hopefully I'll be able to get that one.

Off topic, FYI: I'm also replacing the motherboard, because for some reason, after my computer shuts down, the fans continue to run. But I've got one that's coming. I hope it's the motherboard that's the problem, and I'm pretty sure it is, because when I used another power supply, it did the same thing.

It'll be nice when I get this box working well. :)

---

### Post by shaunm666 on 2006-03-21
I would avoid the WUSB54G if possible m8, Ive had a ton of problems with it and never been able to get it working. If you (or any1) can get it working it would be gr8 if u could post your solutions! Ive heard that linux doesnt support USB WNICS well at all....

---

### Post by mostwanted on 2006-03-21
Maybe off-topic: Does Intel wireless chips come with open source drivers like their graphics cards?

---

### Post by bradlis7 on 2006-03-21
I found a really good deal on a D-Link DWL-G510. It was listed on the supported hardware page as working, or at least a revision of this item.

---

### Post by Teroedni on 2006-03-21
[QUOTE=shaunm666]I would avoid the WUSB54G if possible m8, Ive had a ton of problems with it and never been able to get it working. If you (or any1) can get it working it would be gr8 if u could post your solutions! Ive heard that linux doesnt support USB WNICS well at all....[/QUOTE]

Its works

But you need to upgrade to Dapper
I hav the card myself and use it daily. Only problem is that it disconnects itself after a while:/
It uses the rt2570 alpha driver;)

---

### Post by Brunellus on 2006-03-21
hang on.  dapper has rt2570 in the kernel ????

---

### Post by Teroedni on 2006-03-22
Yes 

Here a screenshot as proof:)
[http://www.ubuntuforums.org/gallery/showimage.php?i=2287&original=1&c=2](http://www.ubuntuforums.org/gallery/showimage.php?i=2287&original=1&c=2)


BUT, The driver is very unstable, since its still alpha:(

---

### Post by Titus A Duxass on 2006-03-23
I have the following:

Edimax EW-7126 - rtl8180 chipset
Deutsche Telekom T154PCI - PrismGT
Linksys ??? V4 pcmcia - rtl8180 chipset.

All three of them work with NDISWRAPPER, all three of them are recognised during the install process but never work correctly.

The Edimax EW-7126 has linux drivers, but I have never got them to work.  Way too complicated installation process!

The Edimax EW-7126 also has an annoying habit, if you disconnect from the mains (i.e pull the plug) you must boot the pc without the card, shutdown replace card and then reboot.

Otherwise it will not pick up an IP address and backgrounds the process.

The problem I have with eBay (this may only apply to Germany) is that the vendor hardly ever puts the chipset details in the offer.

My 0.2€ worth!

---

### Post by celloandy on 2006-03-23
Yeah, I'd get a card that's supported by native drivers, if at all possible (prism54, etc., are good).  Ndiswrapper provides marginal support (it's how I'm connected and typing this message, actually), but you don't want to be stuck with a hack to make proprietary drivers work if you can avoid it.  Aside from the potential ethical/legal questionability of it (whether or not you really can legally load closed-source code into a GPL kernel, etc.), ndiswrapper also has other disadvantages, mainly because the NDIS standard on which it depends is just pretty narrow, so lots of more interesting features of cards don't work with it.  You can't tell the link quality to a network, for example, nor can you use the card in any mode other than "ad-hoc" and "managed" (in other words, say goodbye to kismet, etc.).

Don't get me wrong.  I applaud the ndiswrapper folks for their work in getting these cards to work, and I recognize that there are some situations where it's the only think that works, but even they would agree that it's a less-than-ideal solution.  Go with something native, since you have a choice, anyway.

Andrew

---

### Post by bradlis7 on 2006-03-24
I've got the DWL-G510, and it worked without a problem. I'm using it right now :D. Thanks for all the comments.

---

