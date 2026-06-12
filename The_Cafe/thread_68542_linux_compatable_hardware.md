---
title: "linux compatable hardware"
date: 2005-09-23
forum: The Cafe
---

### Post by ssam on 2005-09-23
hello

while searching for linux wifi information i noticed [network ned](http://networkned.co.uk/) who sell network cards and adsl modems that are guaranteed to work with linux with open source drivers.

does any one know any of any other gpl friendly hardware sellers, as i feel we should be promoting and supporting them.

sam

---

### Post by GeneralZod on 2005-09-23
Ralinktech deserve a lot of respect for their Wireless devices (and our very own jdong posts on the forums :)) :

[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

Incidentally, here is a superb link for WiFi under Linux:

[http://linux_wless.passys.nl/](http://linux_wless.passys.nl/)

---

### Post by NetworkNed on 2005-09-23
Hi Sam,

Your order will be going to the post office tomorrow & thanks for mentioning me here - I was actually already a member of the forums here because Ubuntu was the first distro I installed on the laptop I bought to test PCMCIA cards.

I think Ralink are brilliant for GPLing their drivers, and it's principally Ralink cards that I sell. If you're unlucky then getting wireless cards running under Linux can be a nightmare (cue copious replies of "I installed NDISwrapper and it just worked for me!":wink: ) but the I liked the Ralink because all I had to do was `make && make install` then `modprobe` the drivers. I know there are a couple of other wireless chipsets that have open-source drivers, but as far as I'm concerned (and considering the number of manufacturers that offer no Linux support) they can't be much easier than that!!

For desktop PCs I actually prefer cards using the prism54 chipset - although I thought they'd gone out of production I'm pleased to say I received stock again this week. I know some distros (Mandrake, I think) are shipping the Ralink driver already but the prism54 driver has been in the main Linux kernel tree for some time and it also does "master mode" so you can build your own Linux router using this card. I don't think it'll be long until the rt2500 team catch up, tho', so if you don't have an immediate need for master mode then it's great to be able to reward Ralink for their GPL-support.

If you're a GPL-advocate then it's also worth mentioning the ADSL modems by Sangoma & BeWAN - Sangoma have had drivers in the main kernel tree for years & BeWAN post a Linux driver for their USB & PCI modems as GPL source on their website. If decent Linux support is a criteria then I'd say that it's harder to find an ADSL modem (a PCI one, at least) than any other kind of hardware, so I'm really glad to now have the BeWAN model - it'll also be half the price of the Sangomas I stock!!

I hope there are no objections to me posting this or [link to my website](http://networkned.co.uk/hardware.php) here - because of advertising costs I don't really make very much out of this & so I'm really pleased to be mentioned in the community. Linux hardware is just a sideline business for me - most of the work I get is actually fixing br0ken Windows PCs but this means that I'm able to buy batches of 10 or 20 wireless cards without much risk - if the manufacturer changes the chipset or otherwise breaks Linux compatibility then I can sell them to my Windows customers. From every batch of hardware that I buy, I test one or two cards to be sure they're still Linux-compatible.

If you're having any problems with any of the hardware I mention here, please feel  to [EMAIL=ubuntu-user@networkned.co.uk]drop me an email[/EMAIL] - if your symptoms aren't related to an existing posting then it's probably best if you start a new thread in the appropriate forum before sending me the link.

Ned.

---

