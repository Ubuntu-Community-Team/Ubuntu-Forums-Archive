---
title: "Why I won't be getting a System 76 any time soon..."
date: 2006-11-19
forum: The Cafe
---

### Post by aysiu on 2006-11-19
I'm a strong believer in preloading Linux. To me, that's the only way that Linux will make it on the desktop (and I mean *make it*, not *dominate*--I don't even want it to dominate... just 5-10% of the market is great).

I've been wanting to get a [System 76](http://www.system76.com) for a while. The Gazelle Value makes me drool (figuratively, of course).

But Ubuntu has brought something to me Windows never could--the ability to use old hardware. In my old Windows-using days, a computer getting old meant getting a new computer. There's no way Windows XP could work well on my old 128 MB RAM/ 766 MHz processor computer, but even Edgy with IceWM flies on it.

Right now, my wife is a student, so we're a bit short on cash, and I've been thinking about getting a laptop, but my wife suggested we just take back the laptop we lent my sister-in-law (that she doesn't really need any more). That seemed reasonable, since we don't really have $1000 to spend.

It's an old Dell with only 256 MB of RAM and no wireless card (yes, we got it back in the days when wireless cards were a luxury and didn't come standard with laptops). I figure with IceWM and a good Ubuntu-friendly wireless card, it could be useful again.

But it also means no System 76 for a while... probably not for a couple of years.

Not sure what the point of this thread is...

---

### Post by nalmeth on 2006-11-19
Yeah, why go for new hardware when you can make existing hardware work? Unless you need it specifically, it's not worth it for a well versed linux user. 

I have two old machines that are quite useful thanks to GNU/linux. A laptop I use daily (same ballpark as the dell you refer to), and an older PC with the same amount of RAM.

Both are running Xubuntu, and both perform extremely well. I'm going to give away the PC, and keep the laptop for a few more years.

It's funny, I used to think all my hardware was poor and needed to be upgraded, but as time goes on, I find myself needing new hardware less and less. 

Oh, and those Koala's kind of make *me* drool, but its not in my budget right now. 

Not totally sure why I replied..

---

### Post by mips on 2006-11-19
> **aysiu said:**
> 
It's an old Dell with only 256 MB of RAM and no wireless card (yes, we got it back in the days when wireless cards were a luxury and didn't come standard with laptops). I figure with IceWM and a good Ubuntu-friendly wireless card, it could be useful again.

But it also means no System 76 for a while... probably not for a couple of years.

Not sure what the point of this thread is...

I'm sure that Dell will do the job well with ubuntu & a lite WM. Wireless cards are cheap so that should not be a problem. Maybe a Cisco Aironet 350 from ebay ?

What model Dell is it ?

I myself would never buy system76 but my reasons are different.

---

### Post by aysiu on 2006-11-19
Yeah, I know your reasons for not buying a System76.

In any case, it's a Dell Inspiron 500m.

There's only [one HowTo on it for Linux (Red Hat 9)](http://projects.nudieman.com/500m/), and it's extremely old. I remember using a patch to get the screen resolution working for Blag on it in June 2004. I'm not sure if Ubuntu Edgy might just detect it automatically. We'll see.

As for the wireless card, I have heard good things about Cisco Aironet 350 (I did a little Google searching for Ubuntu-compatible cards in the forums and also checking out [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)).

Have you used it? Is it hard to set up? Frankly, I'm a bit scared of setting up wireless in Ubuntu. Everything has worked smoothly for me up till now. No twiddling with the wired connection or sound or even my media card reader. The only hardware tweak I had to do was adding two lines to my /etc/X11/xorg.conf for optimal screen resolution.

*ndiswrapper* scares me. Does Cisco Aironet 350 work "out of the box"?

---

### Post by shining on 2006-11-19
About wireless cards, I've a netgear wg511, which has a prism54 chipset, and support directly in the linux kernel. Only a firmware is needed (isl3890) which you can get from there: [http://prism54.org/fullmac.html](http://prism54.org/fullmac.html)
But Ubuntu already provides it. The only problem is that WPA isn't supported, while it is with netgear windows driver.
I also have netgear wg511T, atheros chipset. It's supported by the madwifi project, which is an external driver, but it's also included by Ubuntu. The only problem maybe is that the card seems to be less powerful, I got a lower signal compared to the other card.

Though, I believe both cards come in several flavors, and IIRC some of these may have different chipsets. That's very annoying, it seems you can never know for sure which chipset you'll get.
It would be much easier if hardware vendors used a different name for different chipset, and also said which chipset a particular card had.

Edit: Oops, I totally forgot about a very important point
There are the older 16 bit PCMCIA cards, and the newer 32 bit CardBus cards.
The two cards above must be CardBus cards. What does this laptop support?

---

### Post by mips on 2006-11-19
> **aysiu said:**
> 

As for the wireless card, I have heard good things about Cisco Aironet 350 (I did a little Google searching for Ubuntu-compatible cards in the forums and also checking out [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported%29").

Have you used it? Is it hard to set up? Frankly, I'm a bit scared of setting up wireless in Ubuntu. Everything has worked smoothly for me up till now. No twiddling with the wired connection or sound or even my media card reader. The only hardware tweak I had to do was adding two lines to my /etc/X11/xorg.conf for optimal screen resolution.

*ndiswrapper* scares me. Does Cisco Aironet 350 work "out of the box"?

I honestly do not know. I know that they are good cards though and come in PCMCIA which you will probably need with an older laptop. they worked great on Win when I used them at work.

Take your time and get the right card. I will look into the Cisco 350 for you.

---

### Post by aysiu on 2006-11-19
shining, I'm assuming PCMCIA (based on [this link](http://www.linux.ie/articles/tutorials/inspiron500m.php) (I don't have it physically in front of me yet)... I honestly don't know all this wireless terminology. The world of wireless is new to me. I haven't ever really used it (in Windows or Ubuntu). We did set up my wife's wireless in OS X, and even that was a pain to set up properly despite Apple's claims to "just work."


mips, thanks for volunteering to look into Cisco 350. I thought you might just know, but if you're going to do research on it, I might as well do the research myself. Thanks for the offer, but you don't have to go out of your way to do that.

---

### Post by mips on 2006-11-19
aysiu,

I have some good news for you, no need for pcmcia or usb wireless. If I'm looking at the correct product then your notebook has a mini-PCI slot and there should be an antenna connector as well. you will have to open the little cover where the card goes in.
Look here:
[http://support.dell.com/support/edocs/systems/ins500m/en/sm/upgrades.htm#1019173](http://support.dell.com/support/edocs/systems/ins500m/en/sm/upgrades.htm#1019173)
Might as well just get an Genuine Intel card as they are dirt cheap. Will find a source soon.


While you are looking at that you might as well check how many memory stick you have installed. upgrading the memory will be cheap, another 256MB and your flying.
[http://accessories.us.dell.com/sna/category.aspx?c=us&l=en&s=dhs&cs=19&category_id=6348&mfgpid=160107&rpu=1&p=1](http://accessories.us.dell.com/sna/category.aspx?c=us&l=en&s=dhs&cs=19&category_id=6348&mfgpid=160107&rpu=1&p=1)
[http://www.ec.kingston.com/ecom/configurator_new/modelsinfo.asp?SysID=14739&mfr=Dell&model=Inspiron+500m&root=us&LinkBack=&Sys=14739-Dell-Inspiron+500m&distributor=0&submit1=Search](http://www.ec.kingston.com/ecom/configurator_new/modelsinfo.asp?SysID=14739&mfr=Dell&model=Inspiron+500m&root=us&LinkBack=&Sys=14739-Dell-Inspiron+500m&distributor=0&submit1=Search)
[http://www.newegg.com/ProductSort/SubCategory.asp?SubCategory=381](http://www.newegg.com/ProductSort/SubCategory.asp?SubCategory=381)

> **aysiu said:**
> shining, I'm assuming PCMCIA (based on [this link]("http://www.linux.ie/articles/tutorials/inspiron500m.php") (I don't have it physically in front of me yet)... I honestly don't know all this wireless terminology. The world of wireless is new to me. I haven't ever really used it (in Windows or Ubuntu). We did set up my wife's wireless in OS X, and even that was a pain to set up properly despite Apple's claims to "just work."


mips, thanks for volunteering to look into Cisco 350. I thought you might just know, but if you're going to do research on it, I might as well do the research myself. Thanks for the offer, but you don't have to go out of your way to do that.

---

### Post by aysiu on 2006-11-19
Talk to me as you would a four-year-old. I know virtually nothing about hardware terminology. A mini-PCI slot allows me to... install an internal wireless card? Is that the idea? But would... whatever I put inside be Ubuntu-compatible?

As for the extra memory, I think I'd be fine with 256 MB of RAM. I don't do anything terribly memory-intensive, and I happen to like IceWM a lot.

Thanks for researching, though. I appreciate the effort.

---

### Post by shining on 2006-11-19
> **aysiu said:**
> shining, I'm assuming PCMCIA (based on [this link](http://www.linux.ie/articles/tutorials/inspiron500m.php) (I don't have it physically in front of me yet)... I honestly don't know all this wireless terminology. The world of wireless is new to me. I haven't ever really used it (in Windows or Ubuntu). We did set up my wife's wireless in OS X, and even that was a pain to set up properly despite Apple's claims to "just work."


Hmm, I'm confused. This laptop doesn't seem that old. It's a Centrino, which is generally intel mobo (i855 here), intel pentium-m, and intel wireless (ipw2100). ipw2100 are in the linux kernel, so it'll work out of the box in every linux distrib (or after manually installing the firmware image with some, but Ubuntu already does it).
And since it isn't very old, it certainly has PCMCIA 32bit (CardBus) for adding extension cards, like wireless, or additional usb or firewire ports.

Edit: Oh ok, I understand now. Like mips pointed out, this intel wireless support may be optional, which could explain why on the link you gave, the laptop has ipw2100 wireless, but your laptop doesn't have it.

---

### Post by aysiu on 2006-11-19
> **shining said:**
> Hmm, I'm confused. This laptop doesn't seem that old. It's a Centrino, which is generally intel mobo (i855 here), intel pentium-m, and intel wireless (ipw2100). ipw2100 are in the linux kernel, so it'll work out of the box in every linux distrib (or after manually installing the firmware image with some, but Ubuntu already does it).
And since it isn't very old, it certainly has PCMCIA 32bit (CardBus) for adding extension cards, like wireless, or additional usb or firewire ports.

Edit: Oh ok, I understand now. Like mips pointed out, this intel wireless support may be optional, which could explain why on the link you gave, the laptop has ipw2100 wireless, but your laptop doesn't have it.
Maybe the 500m later became Centrino, but I had not even heard the word *Centrino* when we bought that... I think back in 2003 is when we bought it.

---

### Post by John.Michael.Kane on 2006-11-19
aysiu If your machine is centrino based it should have a slot for a mini pci wifi card which looks like this [http://i21.ebayimg.com/01/i/04/6d/1c/f9_2.JPG](http://i21.ebayimg.com/01/i/04/6d/1c/f9_2.JPG) 

You could try to find an intel or an ralink based one.

---

### Post by shining on 2006-11-19
> **aysiu said:**
> Maybe the 500m later became Centrino, but I had not even heard the word *Centrino* when we bought that... I think back in 2003 is when we bought it.

According to wikipedia: [http://en.wikipedia.org/wiki/Centrino](http://en.wikipedia.org/wiki/Centrino)
It was launched in March 2003 :)

---

### Post by aysiu on 2006-11-19
Cool. So does that mean I should be looking at [this part of the "supported wireless cards" page](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-751ff8f98030df97347576e45ed468055b1e3fe3) to find one?

---

### Post by Kannisto on 2006-11-19
> **aysiu said:**
> Talk to me as you would a four-year-old. I know virtually nothing about hardware terminology. A mini-PCI slot allows me to... install an internal wireless card? Is that the idea? But would... whatever I put inside be Ubuntu-compatible?

Yes there should be mini-pci slot for internal wireless cards, I installed ipw2200 (intel card) in my dell and the antenna connectors (you migth want to google which is aux and which is antenna, I don't remember anymore) were there and everything worked out of the box. Intel cards are also the only mini-pci wlan cards available in almost every computer store. 
Dell has pretty good instructions for opening the computer. Learn also the right technique for installing the mini-pci card, stick it in and push it down (I tried the other way first and didn't succeed :p  )

---

### Post by shining on 2006-11-19
> **aysiu said:**
> Cool. So does that mean I should be looking at [this part of the "supported wireless cards" page](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-751ff8f98030df97347576e45ed468055b1e3fe3) to find one?

Yes, but since you have a mini-pci slot, and can add an Intel card, just take that. Either the 2100 or 2200 chipset.
I'm not sure about the difference between both chipsets, but both work well in Linux. Maybe the main one is that 2100 only supports 802.11b, while 2200 also supports 802.11g

---

### Post by mips on 2006-11-19
> **aysiu said:**
> Talk to me as you would a four-year-old. I know virtually nothing about hardware terminology. A mini-PCI slot allows me to... install an internal wireless card? Is that the idea? But would... whatever I put inside be Ubuntu-compatible?


mini-PCI is similair to a PCI slot on a normal PC, just mini-turised for laptops. When you buy a new laptop this slot is usually already occupied with a wireless card. In your case it was left blank but be thank full they at least provided the slot.

Yes, you can install a wireless card into the slot amongst other things. BUT you have to make sure the antenna connector is there. A little cable with small plug on the end that you connect to the wireless card. This cable usually runs all the way to the sides of your display in order to provide better signal quality. It's internal so you don't see it.

Compatibility depends on the card type or vendor chipset. If you use something like a Intel 220BG (I have one in my HP, not tested) it will work. The Intel cards are the ones that ship with all "Centrino" notebooks and they generally work in linux without hassles. I dunno what encryption types they support though, WEP, WPA etc. There is also a newer 2915abg model available. They are cheap and can be had for about $25
[http://www.pricegrabber.com/p__Intel_Intel_Pro_Wireless_2200_Mini_PCI_Adapter_Type_3B_54_Mbps_at_2_4_GHz_802_11,__12871988/](http://www.pricegrabber.com/p__Intel_Intel_Pro_Wireless_2200_Mini_PCI_Adapter_Type_3B_54_Mbps_at_2_4_GHz_802_11,__12871988/)


Attached is a picture of the card in the slot, with the two antenna connectors (black & white with copper ends) at the top middle to right near the big Intel logo.

---

### Post by John.Michael.Kane on 2006-11-19
Heres what i found [http://support.dell.com/support/edocs/systems/ins500m/en/sm/upgrades.htm#1019173](http://support.dell.com/support/edocs/systems/ins500m/en/sm/upgrades.htm#1019173)

---

### Post by mips on 2006-11-19
> **aysiu said:**
> Cool. So does that mean I should be looking at [this part of the "supported wireless cards" page]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-751ff8f98030df97347576e45ed468055b1e3fe3") to find one?

I would actually ignore that list, majority of cards listed are not mini-PCI and a lot of the ones that are use Broadcom chipset which you don't want to touch with a ten foot pole.

I'll go with SD-Plissken here and say just get an Intel ipw2200 or ipw2945, if you look at the list you mention above you will see they work. The other nice thing is Intel, they at least support open source drivers, I'm not a big Intel fan but I'll give credit where it is due.

---

### Post by aysiu on 2006-11-19
Thanks for all your help. When I actually get the laptop in my physical possession, I'll double-check to make sure that slot actually exists, get an Intel Pro Wireless, and then have my wife install it for me (she's a bit more dextrous with things like this--I can do software installations till kingdom come, but hardware is not my bag). If any further questions come up, I'll post back here in this thread.

Thanks again for all your help. This community is great!

---

### Post by shining on 2006-11-19
> **mips said:**
> 
Compatibility depends on the card type or vendor chipset. If you use something like a Intel 220BG (I have one in my HP, not tested) it will work. The Intel cards are the ones that ship with all "Centrino" notebooks and they generally work in linux without hassles. I dunno what encryption types they support though, WEP, WPA etc. There is also a newer 2915abg model available. They are cheap and can be had for about $25
[http://www.pricegrabber.com/p__Intel_Intel_Pro_Wireless_2200_Mini_PCI_Adapter_Type_3B_54_Mbps_at_2_4_GHz_802_11,__12871988/](http://www.pricegrabber.com/p__Intel_Intel_Pro_Wireless_2200_Mini_PCI_Adapter_Type_3B_54_Mbps_at_2_4_GHz_802_11,__12871988/)


2100, 2200bg and 2915abg should all work flawlessly in Linux, and support WEP and WPA.

---

### Post by mips on 2006-11-19
> **SD-Plissken said:**
> Heres what i found [http://support.dell.com/support/edocs/systems/ins500m/en/sm/upgrades.htm#1019173](http://support.dell.com/support/edocs/systems/ins500m/en/sm/upgrades.htm#1019173)

See post #8 above ;)

---

### Post by John.Michael.Kane on 2006-11-19
Well I can say that when i had an acer travelmate it had an intel 2100 80211 b mini card,and it work.

Also tested an Ralink mini pci card which ubuntu detected,and allowed to be setup.

---

### Post by prizrak on 2006-11-19
Aysiu,
That is precisely one of the reasons that OEM's are not willing to preload Linux on their machines for anyone but business customers who buy in huge quantities. With Windows you NEED faster hardware, 2K ran just fine on a P2 333 w/ about 300MB or RAM. XP doesn't run all that well below 512 and a Gig CPU, despite not having any really usefull improvements over 2K. Vista will require hardware that is actually beyond even the newest machine I own (though all I would need is another 512MB stick to meet the rqs). They basically force people to buy new machines when they have no need for them. 

Ubuntu Edgy (with Beryl and AIGLX) works beautifully on my old laptop (2.2P4-m 512MB, intel video) and actually faster than Breezy or Dapper. Under such conditions now OEM will want to preload it as people will not upgrade until their hardware breaks and lets face it, electronics are very reliable in general.

---

### Post by jimrz on 2006-11-19
> **aysiu said:**
> Thanks for all your help. When I actually get the laptop in my physical possession, I'll double-check to make sure that slot actually exists, get an Intel Pro Wireless, and then have my wife install it for me (she's a bit more dextrous with things like this--I can do software installations till kingdom come, but hardware is not my bag). If any further questions come up, I'll post back here in this thread.

Thanks again for all your help. This community is great!

I still have my TP 600x (even older than your Dell). If for some reason, you cannot go the mini-pci route, the Netgear 511T (Atheros chipset) works out of box running Xubuntu Dapper and right now I am on it trying the Ubuntu Edgy "live cd" which also worked otb. On both, I am getting the same signal strenght in the same location that I used to get when it was still running Win2k. The card supports 802.11 b/g/super g  (108 Mb/sec)  WEP and WPA (with updated firmware) and has been an excellent performer under every OS that I have tried it on.

Don't be too concerned about wireless under Ubuntu. Just make sure to get a card that is known to be supported and it is all good. I have been fortunate in that mine have always worked OTB (dumb luck not research, since the cards were here before Ubuntu), except that the Intell a/b/g mini-pci card in my primary laptop (also Atheros) is only partially supported in Edgy. Which works for internet/ftp but not my home LAN nor even to log in to my router ( this is not true for the 511T). In fact I have not put Edgy on that box for this very reason, even though all else runs beautifully.

---

### Post by aysiu on 2006-11-19
Once again, thanks to all for your input. If anyone else has anything to add, please do. I may not respond, but I'm reading.

---

### Post by compuguy1088 on 2006-11-19
> **mips said:**
> mini-PCI is similair to a PCI slot on a normal PC, just mini-turised for laptops. When you buy a new laptop this slot is usually already occupied with a wireless card. In your case it was left blank but be thank full they at least provided the slot.

Yes, you can install a wireless card into the slot amongst other things. BUT you have to make sure the antenna connector is there. A little cable with small plug on the end that you connect to the wireless card. This cable usually runs all the way to the sides of your display in order to provide better signal quality. It's internal so you don't see it.

Compatibility depends on the card type or vendor chipset. If you use something like a Intel 220BG (I have one in my HP, not tested) it will work. The Intel cards are the ones that ship with all "Centrino" notebooks and they generally work in linux without hassles. I dunno what encryption types they support though, WEP, WPA etc. There is also a newer 2915abg model available. They are cheap and can be had for about $25
[http://www.pricegrabber.com/p__Intel_Intel_Pro_Wireless_2200_Mini_PCI_Adapter_Type_3B_54_Mbps_at_2_4_GHz_802_11,__12871988/](http://www.pricegrabber.com/p__Intel_Intel_Pro_Wireless_2200_Mini_PCI_Adapter_Type_3B_54_Mbps_at_2_4_GHz_802_11,__12871988/)


Attached is a picture of the card in the slot, with the two antenna connectors (black & white with copper ends) at the top middle to right near the big Intel logo.
I actually did a similar thing to my Acer Aspire 3003LCi, it originally had a Brodcom 4318 G card, but from all the issues i had with it with the native bcm43xx drivers, and not wanting to use ndiswrapper, I got a Intel 2200bg card to replace it, and it works pretty well, except for the occasionall disconnects from high transfer...

---

### Post by jdong on 2006-11-19
> **aysiu said:**
> Once again, thanks to all for your input. If anyone else has anything to add, please do. I may not respond, but I'm reading.

All I have to say, is that I totally understand what you're saying. At first, I was like "oh no, not another non-free firmware debate" ;-) but anyway...

I can relate to your situation. right now, I have my beloved Core Duo laptop as my primary system, a 733MHz Celeron as my router / mini-server, and two Pentium 4 1.xGHZ class systems that are just unused. Once in a while I'll dig out one system as a temporary Ubuntu test box or build server, but most of the time they stay tucked away in my basement collecting dust.

I will say that they run very competently for desktop usage and if I needed more desktops around my house, they'd do just fine.

So, like you, there will be no System76's in my near future, nor will there be any $200 Black Friday desktop purchases.... The most I'm looking for is a nice-sized hard drive to stick in my server, as it only has 20GB right now and I'd like to offload some storage onto the server.

---

### Post by blueturtl on 2006-11-20
This thread reminds me of why I turned to Linux in the first place.

After my current rig turned into an expensive paperweight with Windows XP I made the decision to stick with my hardware and change the software when the system would start slowing down. That's way better and more nature friendly than buying a new system.

Don't you find it funny how a system that was perfectly good for many things when you bought it is suddenly incapable of those same things? This is essentially what is happening everywhere around us. To me it sounds just absurd. If I bought a system that was capable of word processing, email and web browsing it's not just going to turn incapable of those things unless there's something wrong with the software (aka if the software becomes bloated). The typical office computer of today would have the old multimedia masters *** in terms of performance, but all the potential is wasted on bloat!

I remember doing a presentation at school of a foney software piece for the future (the goal was to practise the use of Adobe PageMaker). The alleged software had incredible system requirements of 500 MHz CPU clock, 256 megs of RAM, and 8 gigs of hard-disk space. Now that was a joke when I made it, but obviously it's not so anymore. I'm not even that old!

The process of perpetual upgrades is a vicious cycle and will never end.
/rant

p.s. These threads get me every time.

---

### Post by gn2 on 2006-11-20
If it was me, I'd go for the PCMCIA option rather than the built-in, because that way it's easier to swap it between laptops.

Rather than buy a new Laptop, have you considered a re-furb or a second user one from eBay?

I have two Toshibas which I got on eBayUK, both are P3 500, one (mine) is 192 other (wife's) is 256mb. Both can run Ubuntu  perfectly well.

Total cost of the pair was £50 less than the cheapest new laptop on the UK market at the time. That was two years ago. They both still work flawlessly. :)

---

### Post by mips on 2006-11-20
> **gn2 said:**
> If it was me, I'd go for the PCMCIA option rather than the built-in, because that way it's easier to swap it between laptops.

Rather than buy a new Laptop, have you considered a re-furb or a second user one from eBay?


Why would you want to swap the card out ?

If you look at the spec of his Dell Inspiron 500m you will see it is pretty powerfull, Pentium 4 M 1.5GHz. It's not that old and will run fine. Hell, I have 18mnth old HP nx6110 1.5GHz Celeron and that works fine, although I do have 512MB ram. Currently has is standard XP & PCBSD on it, PCBSD I find very fast. I actually think I'm going to try Edgy server + X + Fluxbox on it with all my favorite apps.

---

### Post by gn2 on 2006-11-20
> **mips said:**
> Why would you want to swap the card out ?



To facilitate the connection of different laptops.

As an example: recently I removed W98SE from a friend's laptop and installed another OS for him. This was made much easier by using my DWL-650+ PCMCIA card to connect for updates, as the laptop didn't have a LAN port.

In a word- Flexibility.

---

### Post by shining on 2006-11-20
> **gn2 said:**
> To facilitate the connection of different laptops.

As an example: recently I removed W98SE from a friend's laptop and installed another OS for him. This was made much easier by using my DWL-650+ PCMCIA card to connect for updates, as the laptop didn't have a LAN port.

In a word- Flexibility.

Yes, there is indeed a flexibility advantage. But well, all laptops nowadays have a built-in wireless, and all Centrino laptops have working wireless in Linux afaik. So I think this flexibility advantage will only be really useful in a few specific cases, like yours. 
One disadvantage I see is that it isn't integrated in the laptop, so it takes more space, and you generally need to remove/insert the card each time you move/travel with the laptop.
Another inconvenient is that it'll use one pcmcia slot, which could be used for another extension card instead.

---

### Post by kerry_s on 2006-11-20
Has any one bought from retrobox? ( [http://www.retrobox.com/rbwww/home/search_results_pc_laptops.asp?bin_id=world](http://www.retrobox.com/rbwww/home/search_results_pc_laptops.asp?bin_id=world) )
I've been looking for a replacement laptop locally(HI) but haven't had much luck. I was thinking of grabbing a older used laptop from retrobox. 
If any one has dealt with them i would like to hear your experience & if you were satisfied with the purchase. Thank you.

---

### Post by anaconda on 2006-11-20
> **aysiu said:**
> I've been wanting to get a [System 76](http://www.system76.com) for a while. The Gazelle Value makes me drool (figuratively, of course).

But it also means no System 76 for a while... probably not for a couple of years.


Back to the orginal topic.

I was also interested in buying a laptop from system76, but the 100$ shipping to europe and the 29% VAT (or is it 22%?) and any additional customs fees would have maked it quite expensive.
Why dont they have a shop in EU?

I bought a laptop with winXP :C  
But when I told that I dont need/want the winXP, the seller gave me 50€ extra discount. I like to think that it was "refund" from winXP.. but of cource I now also have a legal windows for the very first time in my life.

---

### Post by gn2 on 2006-11-20
> **shining said:**
> Yes, there is indeed a flexibility advantage. But well, all laptops nowadays have a built-in wireless, and all Centrino laptops have working wireless in Linux afaik. So I think this flexibility advantage will only be really useful in a few specific cases, like yours. 
One disadvantage I see is that it isn't integrated in the laptop, so it takes more space, and you generally need to remove/insert the card each time you move/travel with the laptop.
Another inconvenient is that it'll use one pcmcia slot, which could be used for another extension card instead.

Not everyone has a new-ish laptop, my newest one is six years old, it does everything I need. Lots of people I know have older laptops, and I would always advise anyone to buy a second-hand laptop rather than a new one if they already have a desktop which they intend to keep.

---

### Post by mips on 2006-11-20
> **anaconda said:**
> 
I was also interested in buying a laptop from system76, but the 100$ shipping to europe and the 29% VAT (or is it 22%?) and any additional customs fees would have maked it quite expensive.
Why dont they have a shop in EU?
.

Well you can buy a System76 laptop in most countries around the world. the only thing is that it does not have the System76 sticker on it and no Linux preloaded or Windows for that matter(barebones). Just buy the same ASUS model System76 uses as they basically just rebrand certain ASUS models. The ASUS will also be much cheaper and you will have local warranty/harware support, just an idea.

---

### Post by mips on 2006-11-20
> **kerry_s said:**
> Has any one bought from retrobox? ( [http://www.retrobox.com/rbwww/home/search_results_pc_laptops.asp?bin_id=world](http://www.retrobox.com/rbwww/home/search_results_pc_laptops.asp?bin_id=world) )
I've been looking for a replacement laptop locally(HI) but haven't had much luck. I was thinking of grabbing a older used laptop from retrobox. 
If any one has dealt with them i would like to hear your experience & if you were satisfied with the purchase. Thank you.

[http://www.resellerratings.com/seller3928.html](http://www.resellerratings.com/seller3928.html)

IF you do buy from them get a IBM Thinkpad, good support, lots of spares, [www.thinkwiki.org](www.thinkwiki.org) and they are pretty bulletproof.

---

### Post by jimrz on 2006-11-30
> **mips said:**
> [http://www.resellerratings.com/seller3928.html](http://www.resellerratings.com/seller3928.html)

IF you do buy from them get a IBM Thinkpad, good support, lots of spares, [www.thinkwiki.org](www.thinkwiki.org) and they are pretty bulletproof.

definitely second that ... have 2 of them (T42 + 600x) and wouldn't trade either one for the world (couldn't even stand to part with the old 600x when I got the T42)

---

### Post by aysiu on 2007-01-02
Well, got the Inspiron 500m from my sister-in-law, installed both Windows and Ubuntu on it. So far, Windows is doing pretty well, Ubuntu... not so well. I'm new to this whole laptop thing and all the headaches that come along with it. Ubuntu on the desktop--I'm all over that.

Right now, I'm trying to work through (trial and error + Google searches) resuming from suspend and WPA working with the Intel Pro 2200 my wife helped me install. Network manager recognizes all my neighbors' connections but not my own.

Windows took a little fiddling around, but I got WPA working eventually (my network also was not detected). Suspend resume works, though, so I'm sticking with Windows until I get this figured out. BBLean is helping to make my Windows experience more bearable.

---

### Post by mips on 2007-01-02
Maybe first try switching WPA off and getting a connection, next add the encryption.MegaDemoI-2.adf.gz

---

### Post by aysiu on 2007-01-02
I'll play around with it and post back any questions I have in a support thread. I'm also doing some extensive searching of HowTos.

Thanks for all your help so far.

If I get too lazy, I may just keep using Windows with BBLean until Feisty comes out. There are some interesting specs on Feisty for laptops:
[https://blueprints.launchpad.net/distros/ubuntu/+spec/network-roaming](https://blueprints.launchpad.net/distros/ubuntu/+spec/network-roaming)
[https://blueprints.launchpad.net/distros/ubuntu/+spec/kubuntu-feisty-laptop](https://blueprints.launchpad.net/distros/ubuntu/+spec/kubuntu-feisty-laptop)

---

### Post by prizrak on 2007-01-03
Best way of doing WPA in my experience is with Network-Manager. I got the same card as you and it works pretty well, perhaps the router settings prevent your system from seeing it. Check your MAC filtering list, you might not have the other machine allowed on (happens to me all the time I try to add a new client)

---

### Post by Mateo on 2007-01-03
i won't be getting one because of the odd cases.

---

### Post by stalker145 on 2007-01-03
> **aysiu said:**
> But Ubuntu has brought something to me Windows never could--the ability to use old hardware. In my old Windows-using days, a computer getting old meant getting a new computer. There's no way Windows XP could work well on my old 128 MB RAM/ 766 MHz processor computer, but even Edgy with IceWM flies on it.
...
It's an old Dell with only 256 MB of RAM and no wireless card (yes, we got it back in the days when wireless cards were a luxury and didn't come standard with laptops). I figure with IceWM and a good Ubuntu-friendly wireless card, it could be useful again.
...

aysui and all others, 
I fully agree here about bringing new life to old hardware; it's incredible!

I was home on leave from overseas in late '05 and went to the Navy and Marine Corps Intranet (NMCI) warehouse here on base and found that they sell their old computers for a pittance. I picked up a Micron Transport GX2, 1GHz processor, 512MB RAM, 40GB HDD, and combo drive for USD$350. It was a blank HDD and I had to provide my own OS... nooo problem. When I came back from my overseas assignment in early '06 I picked up a Dell Latitude C640, 2GHz, 256MB RAM, 40GB HDD, combo drive for the same price. 

I originally bought the Micron to learn Linux, but when I returned overseas my wife had a Windows crash on her desktop at home and I had to wipe Linux from the Micron, load XP (since it's what she knows) and send it back to her. XP ran like a pig on that old thing. 2K runs acceptably, but even a full load of Ubuntu with Gnome runs like a dream.

When I got her the Dell, we loaded XP on it and it ran pretty well. We fell victim of WGA (yes, it was a legal copy) and ended up regressing(?) to 2K, which runs very well. There is no Linux in the near future for that machine as my wife has no desire to learn a new OS.

I've recently started checking out the other WM's for my Micron and have really started to see the advantages of Linux on older hardware. Enlightenment, IceWM, XFCE; they all run fantastically once you get the hang of them. I don't think I'll *ever* buy a new computer. 

I'm sorry if this is turning into a thread hi-jack. It's definitely not meant to be that. I just wanted to put my two cents in on the topic.

By the way, I do NOT work for NMCI (thank God!), but I heartily suggest that if you have one of their warehouses near you or a similar type of business, that you check them out. Nothing like picking up used equipment that has been guaranteed to be in good working order without the W1nd0w$ virus on it ;)

---

### Post by PanzerMKZ on 2007-01-03
I just got a used laptop.  Once I get a power brick to test then I will also be running ubuntu or xubuntu on it.  P3 1g with 256 and 20gig.  Might see about a upgrade to 384.  Heck I got a desktop right now that is dual 500's.  Runs sweet where even 2k is alittle slow.


Panzer

---

### Post by Gargamella on 2007-01-03
I know what you're talking about I always wanted another pc in my house (I have a laptop and my father's server), my dad bring me a win98 64MBram to use it or to trash it (don't know exactly) now it's xubuntu and we're all right

---

### Post by aysiu on 2007-03-25
**Update**: I just upgraded my Dell Inspiron 500m to Feisty Beta today, and resume from suspend worked! I closed the laptop lid, it suspended, I opened the lid, it asked for my password, and resumed... perfectly.

Let's see if that turns out to have been a fluke, or if it's actually going to always work.

Very exciting, though. Up until this point, I've been using Windows on this laptop, and it hasn't been fun.

---

### Post by prizrak on 2007-03-25
> **aysiu said:**
> **Update**: I just upgraded my Dell Inspiron 500m to Feisty Beta today, and resume from suspend worked! I closed the laptop lid, it suspended, I opened the lid, it asked for my password, and resumed... perfectly.

Let's see if that turns out to have been a fluke, or if it's actually going to always work.

Very exciting, though. Up until this point, I've been using Windows on this laptop, and it hasn't been fun.

If it has an Intel gfx card it should work very well. Feisty has the updated drivers and in general I have found suspend to be working perfectly with those cards. If it's either ATI or nVidia the minute you put binary driver on it suspend will break.

---

### Post by aysiu on 2007-03-25
> **prizrak said:**
> If it has an Intel gfx card it should work very well. Feisty has the updated drivers and in general I have found suspend to be working perfectly with those cards. If it's either ATI or nVidia the minute you put binary driver on it suspend will break.
Well, resume from suspend hadn't been working well with Dapper or Edgy, so something new must have happened. I'm very excited about it.

---

### Post by prizrak on 2007-03-25
> **aysiu said:**
> Well, resume from suspend hadn't been working well with Dapper or Edgy, so something new must have happened. I'm very excited about it.

Yeah from what I have seen, Feisty is shapping up to be quite good. While it doesn't have all the features that were supposed to make into it and the last update made my touchpad scroll way too slow it's extremely stable and everything seems to work out of the box.

---

### Post by dbbolton on 2007-03-25
i hope to get a gazelle as a graduation present.

---

