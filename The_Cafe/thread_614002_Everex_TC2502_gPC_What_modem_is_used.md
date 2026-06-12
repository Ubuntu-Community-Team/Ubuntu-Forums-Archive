---
title: "Everex TC2502 gPC: What modem is used?"
date: 2007-11-15
forum: The Cafe
---

### Post by wie6Ein0 on 2007-11-15
What PCI modem is being used in the new [Everex TC2502 gPC]("http://www.walmart.com/catalog/product.do?product_id=7754614") computer being sold at WAL-MART Stores?

A close family member recently bought the computer for her child's birthday because of it's cheap price, but found out that it has an Ubuntu-based operating system. The person was more familiar with Windows XP, so I was drafted to install it for her. So far I have been able to find and download the necessary Windows hardware drivers, except for one -- the PCI modem.

If anyone knows which modem is being used, please let me know so I can download the appropriate driver... The family needs it most of all since they will be using AOL's Internet service.

Please excuse them for shopping at Wal-Mart and using AOL... They simply do not know better :-)

[http://www.walmart.com/catalog/product.do?product_id=7754614](http://www.walmart.com/catalog/product.do?product_id=7754614)

---

### Post by n3gbz on 2007-11-16
I don't believe there is a modem on the gPC.  It is designed for broadband connection.  Here is the reponse to the question > Dialing in with gOS (dial-up) which was asked on the gPC support faq at [http://www.faqly.com/faq/view/id/34]("http://www.faqly.com/faq/view/id/34")

> madjr

2007-11-09 11:18:11
first off you need a compatible external modem

get one at amazon

external serial modem (the actiontec one works great)

then install gnome-ppp and/or kppp

look for them in ADD/REMOVE.. (be sure to select show all applications while browsing add/remove)

configure, plug, add your isp username/pass and all done


---

### Post by n3gbz on 2007-11-16
Oops!  My bad! 

According to [http://money.aol.com/news/articles/_a/wal-mart-sells-199-linux-computer/n20071031143009990074]("http://money.aol.com/news/articles/_a/wal-mart-sells-199-linux-computer/n20071031143009990074")  the gPC does come with a modem but it is not supported in gOS.  

Sorry for giving the wrong info!

---

### Post by Dale61 on 2007-11-17
I found an article of that very pc, but no mention of modem support.

[Linux PCs selling for only $200 in US]("http://www.tech.co.uk/computing/computer-hardware/desktop-systems/news/linux-pcs-selling-for-only-200-in-us?articleid=1404395826")

> While the TC2502 gPC comes with Linux, you can install Windows on the PC should you want to. Just don't expect the VIA chip to cope very well.

I PMSL when I read this review:
> This is a great computer. Even without the monitor it works great because of the text to speech program. Sometimes I hook this up to my TV and work from there but other times I just use the text to speech because it tells me exactly what I'm viewing and where to click for other pages on the internet.
My favorite features of this computer are the following:
Myspace
Youtube
Google
Facebook
I've had this computer for 6 months now and used it in every environment such as dust and heat. I even spilled some water on it but it continues to work great! I love this computer! 

Apologies if this has gone off-topic, but I couldn't find anything else posted about this PC.

---

### Post by saulgoode on 2007-11-17
> While the TC2502 gPC comes with Linux, you can install Windows on the PC should you want to. Just don't expect the VIA chip to cope very well.

This is not completely true. The computer is capable of running Windows XP but it can not run Vista. This is [according to the motherboard manufacturer, VIA,](http://www.via.com.tw/en/initiatives/empowered/pc2500_mainboard/index.jsp?) and not just owing to performance issues.

Also, I see no mention of a modem in the [manufacturer's specifications](http://www.everex.com/products/gpc/gpc.htm).

---

### Post by Bartender on 2007-11-17
The WalMart gPC is sort of a paradoxical machine.  It's a very cheap PC intended for people who can afford broadband.  I read on the internet that it has a modem but the modem doesn't work.

Betcha there's going to be a lot of clueless WalMart shoppers who will be quite angry when they're unable to sign into their AOL accounts.

---

### Post by az on 2007-11-17
> **saulgoode said:**
> This is not completely true. The computer is capable of running Windows XP but it can not run Vista. This is [according to the motherboard manufacturer, VIA,](http://www.via.com.tw/en/initiatives/empowered/pc2500_mainboard/index.jsp?) and not just owing to performance issues.

Also, I see no mention of a modem in the [manufacturer's specifications](http://www.everex.com/products/gpc/gpc.htm).

There is a modem mentioned in the description:
[http://www.walmart.com/catalog/product.do?product_id=7754614](http://www.walmart.com/catalog/product.do?product_id=7754614)
[http://www.walmart.com/catalog/product.do?product_id=7754613](http://www.walmart.com/catalog/product.do?product_id=7754613)
[http://www.walmart.com/catalog/product.do?product_id=5673669](http://www.walmart.com/catalog/product.do?product_id=5673669)

And the two non-linux versions sold at wal-mart (none of which are sold out like the linux one) are sold with Vista, so it looks like the hardware does indeed work with Vista.

As for the modem, just post

lspci

and you should see the modem there along with the rest of the hardware.

---

### Post by saulgoode on 2007-11-17
> **az said:**
> And the two non-linux versions sold at wal-mart (none of which are sold out like the linux one) are sold with Vista, so it looks like the hardware does indeed work with Vista.

The two Windows versions are not TC2502s. They use a different motherboard (probably the [VIA PC3500](http://www.via.com.tw/en/initiatives/empowered/pc3500_mainboard/index.jsp?)).

---

### Post by sanitycheck on 2007-11-17
The modem is an Agere Pinball P40.  It's sitting on my desk because I have much better uses for the PCI slot it previously occupied.

---

### Post by Bartender on 2007-11-18
sanity -
Thanks for partially dismantling your new PC and sharing the results!

---

### Post by djdarrin91 on 2008-02-18
Agere Systems PCI-SV92PP Soft Modem.

---

