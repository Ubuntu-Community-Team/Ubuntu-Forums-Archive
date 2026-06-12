---
title: "Monochrome Printer Recommendation"
date: 2017-04-08
forum: The Cafe
---

### Post by pqwoerituytrueiwoq on 2017-04-08
Does anyone know of a affordable linux friendly monochrome printer i can plug up to my network switch
I am tried if buying ink and it going bad or running out it feels like i only get about 20 pages over 6 months or so, i know ink jets are not efficient but really
I live in the US, i prefer to use newegg, but i can get it from amazon, office max, walmart, staples, etc.
If it does not come with toner please tell me, thanks

---

### Post by Bucky Ball on 2017-04-08
[Something like this]("https://www.brother.com.au/monochrome-laser-printers/hl-l2340dw-detail") would do. Monochrome, duplex, toner is cheap and DIY (I'm in Australia and use a place called [TonerStop]("http://www.tonerstop.com.au/") which sells the ink kits, and cartridges, real cheap). 

I had the Brother HL-2270DW and just recently bought the HL-2365DW which is only available at Officeworks, which I think only exists in Australia. It is pretty much exactly the same as the HL-2340DW in the link above. 

Brother is very Linux friendly and have drivers/installer which makes the process easy.

Hope that helps and good luck.

---

### Post by SeijiSensei on 2017-04-08
Here are [HP and Brother monochrome lasers with an Ethernet port]("https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100006550%2050001816%2040000630%208000%2050001186%20600046504%20600046837%20600471085&IsNodeId=1&bop=And&ActiveSearchResult=True&Order=PRICE&PageSize=60").  They're all remarkably expensive for a monochrome device.  I have a Brother [HL-3170CDW]("https://www.newegg.com/Product/Product.aspx?Item=N82E16828113832&ignorebbr=1") color laser, and it cost not a whole lot more than any of those monochrome ones.  I paid $199 for this printer at Amazon a couple years back, while NewEgg wants $234 for it today. [Staples]("http://www.staples.com/Brother-HL-3170CDW-Color-Laser-Printer-Refurbished/product_1821375?cid=PS:GooglePLAs:1821375&ci_src=17588969&ci_sku=1821375&KPID=1821375&cvosrc=PLA.google-SALES.Printers%20%26%20Scanners&cvo_crid=39357180942&cvo_campaign=173956062&gclid=CjwKEAjwlKLHBRDztKr6wMnRthMSJAALcT-s58AATac3B2YndX7lj8kpY4FjlZjEfpjfKiJrZhiRFhoCOLHw_wcB") has refurbished ones for $150, and [Amazon]("https://www.amazon.com/Brother-HL-3170CDW-Wireless-Networking-Replenishment/dp/B00BQU141C/ref=sr_1_1?ie=UTF8&qid=1491666989&sr=8-1&keywords=brother+hl-3170cdw") currently sells it for $217.  There's a similar model, the HL-3170CW that's cheaper, but it has no Ethernet port, only wifi.

One little quirk I'll mention about this printer.  If you want to print envelopes, you need to put the printer into Postscript mode.

---

### Post by pqwoerituytrueiwoq on 2017-04-08
I consider wireless to be a hassle and prone to issues (asking for trouble), I'd rather just go USB via my raspberry pi, bt i do have a high limit for the printer if that is the case (29 cm / 11.5 in) by which i mean it that includes space to use the printer for example put had in it to get paper out

---

### Post by Bucky Ball on 2017-04-08
The Brother HL-2340DW I linked to is wireless, ethernet cable or USB, take your pick. :)

---

### Post by pqwoerituytrueiwoq on 2017-04-08
> **Bucky Ball said:**
> The Brother HL-2340DW I linked to is wireless, ethernet cable or USB, take your pick. :)
The product line comparison on amazon shows otherwise
[url=http://i.imgur.com/kA8r6Ha.png]
  [img]http://imgur.com/kA8r6Hal.png[/img]
[/url]

---

### Post by pqwoerituytrueiwoq on 2017-04-08
The lowest cost one i was able to find on there website that advertises a Ethernet port is a HL-L2360DW ($100+tax at office max; local retail store)
How good is brother when it comes to keeping there drivers updated and compatible with current distribution releases

Do monochrome printer come with a drum and toner?

---

### Post by Bucky Ball on 2017-04-08
> **pqwoerituytrueiwoq said:**
> The product line comparison on amazon shows otherwise
[url=http://i.imgur.com/kA8r6Ha.png]
  [img]http://imgur.com/kA8r6Hal.png[/img]
[/url]

You're right, my mistake, so it's the HL-2380DW. Has it all, and that is quite clearly shown on the list. You missed?

---

### Post by SeijiSensei on 2017-04-09
Brother offers a "Driver Install Tool" on its site that automatically downloads and installs the proper drivers for your device.  You can use CUPS, of course, but the Tool also handles a scanner if you buy an all-in-one device.

I don't use the wireless feature in my printer either.  Mine is hard-wired directly into the network with Ethernet.  I can still print to it from my phone using the Brother Android app by specifying its IP address.  (Of course, any device like a printer should have a static address.  I had to configure that using the command window on the machine itself.)

I'm not sure why you're asking about a drum and toner.  Of course they are included.  People need to open the box, install the printer, and start printing.  How would they do that without a drum and toner?

---

### Post by pqwoerituytrueiwoq on 2017-04-09
> **Bucky Ball said:**
> You're right, my mistake, so it's the  HL-2380DW. Has it all, and that is quite clearly shown on the list. You  missed?
i saw it and the price tag
> **SeijiSensei said:**
> Brother offers a "Driver Install Tool" on  its site that automatically downloads and installs the proper drivers  for your device.  You can use CUPS, of course, but the Tool also handles  a scanner if you buy an all-in-one device.
I do not care about a scanner on it (i am actually looking at the HL-L2360DW), but anyway you are saying that for solely printing, CUPS has native support built thus no need for special drivers? so i can print from hardware that is not i386/AMD64 architecture (raspberry pi A/A+/B/B+/Zero)

> **SeijiSensei said:**
> I don't use the wireless feature in my printer either.  Mine is  hard-wired directly into the network with Ethernet.  I can still print  to it from my phone using the Brother Android app by specifying its IP  address.  (Of course, any device like a printer should have a static  address.  I had to configure that using the command window on the  machine itself.)
I did see l lot of reviews that complained about the deep sleep feature messing up the wireless feature and there was a FW update for it, but did you have any issues with that having it wired to the network?

> **SeijiSensei said:**
> I'm not sure why you're asking about a drum and toner.  Of course they  are included.  People need to open the box, install the printer, and  start printing.  How would they do that without a drum and  toner?On amazon it shows bundles so you get the printer and a toner cartridge, so i figured maybe it is sold separately just like they used to include usb cables with printers, so i figured if it does not have a cartage maybe it has no drum.

---

### Post by Bucky Ball on 2017-04-09
> **pqwoerituytrueiwoq said:**
> I did see l lot of reviews that complained about the deep sleep feature messing up the wireless feature and there was a FW update for it, but did you have any issues with that having it wired to the network?

No, not with mine. Works faultlessly with ethernet cable, no deep sleep issue. Hit print, it prints.

---

### Post by SeijiSensei on 2017-04-09
> **pqwoerituytrueiwoq said:**
> I do not care about a scanner on it (i am actually looking at the HL-L2360DW), but anyway you are saying that for solely printing, CUPS has native support built thus no need for special drivers? so i can print from hardware that is not i386/AMD64 architecture (raspberry pi A/A+/B/B+/Zero)
There is not currently a specific driver in the "foomatic" set for the 2360DW.  There wasn't one for my 3170CDW either.  I'm using the one for the 3070CDW.  Brother supplies [this driver](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2360dw_us&os=128) for the 2360DW.  You'll notice the CUPS driver for that printer is about two years old now, suggesting it is pretty stable.  My printer also includes Postscript emulation, so you can print with a generic Postscript driver, too.

---

### Post by pqwoerituytrueiwoq on 2017-04-09
I was looking on best buy and i noticed a HP that has the features i want at the same price
[very long product comparison link (LaserJet Pro MFP M130nw Wireless Black-and-White All-In-One Printer VS. HL-L2360DW Wireless Mono Laser Printer)]("http://www.bestbuy.com/site/compare?skus=5623291,6130209&productString=00000*00000&url=%2Fsite%2Fsearchpage.jsp%3Fcp%3D1%26searchType%3Dsearch%26_dyncharset%3DUTF-8%26ks%3D960%26sc%3DGlobal%26list%3Dy%26usc%3DAll%2520Categories%26type%3Dpage%26id%3Dpcat17071%26iht%3Dn%26seeAll%3D%26browsedCategory%3Dpcmcat223500050006%26st%3Dcategoryid%2524pcmcat223500050006%26qp%3Dbrand_facet%253DBrand~Brother%255Ebrand_facet%253DBrand~HP%255Econnectivitymv_facet%253DConnectivity~Ethernet%26sp%3D%252Bcurrentprice%2520skuidsaas")
i was looking at the cost of toner and the larger toner claims 12k pages it is expensive but the standard size only claims 1.6k
it claims to work with hplip 3.13.11 and later

the copy feature is convent but not necessary (i have scanners i can use to scan then print via computers)
not sure if it offers duplex printing

Would i be making a mistake not getting this HP model?

I want Ethernet connectivity; low price (100$ feels pricey to me, but that looks as low as i am gonna get); duplex is preferred; linux comparability is a must have.
i can afford it but i am budget conscious (don't like spending $$$)

---

