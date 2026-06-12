---
title: "which e-sata expresscard are good with ubuntu?"
date: 2008-10-09
forum: The Cafe
---

### Post by legolas_w on 2008-10-09
Hi
Thank you for reading my post.
Does anyone here know which e-sata express cards are working with ubuntu?
I need to use an external hard drive with esata port but i do not know which e-sata expresscard card works with ubuntu.

Thanks

---

### Post by medic2000 on 2008-10-09
I need too! Maybe most of them. Just a quick search on google:
[http://www.satacard.com/](http://www.satacard.com/)
[http://www.cooldrives.com/2ra01espccal.html](http://www.cooldrives.com/2ra01espccal.html)

---

### Post by legolas_w on 2008-10-16
Hi
Can you please share your experience if you bought that express card or any other model to use with Ubuntu?

Thanks

---

### Post by OZFive on 2008-11-07
Just saw this today...

[http://ubuntuforums.org/showthread.php?t=926093&highlight=expresscard](http://ubuntuforums.org/showthread.php?t=926093&highlight=expresscard)

---

### Post by Npl on 2008-11-07
I dunno whats an "expresscard", do you mean a PCMCIA-Card for Notebooks?

If you need eSata on a desktop and have some unused internal Sata-Connectors then the best choice is to merely pass them to the outside : [Sata to eSata Bracket]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812119021"). Cheapest option aswell

---

### Post by thatguymark on 2010-08-04
dup

---

### Post by thatguymark on 2010-08-04
I'm also looking as I'm migrating to Ubuntu with an SSD upgrade - found this page doing a search where the reviewer indicated it was plug and play with Ubuntu, and elsewhere there are references to other card reviews on Newegg:

[http://www.dealextreme.com/details.dx/sku.28899](http://www.dealextreme.com/details.dx/sku.28899)

---

### Post by gletob on 2010-08-05
I have no idea

> **Npl said:**
> I dunno whats an "expresscard", do you mean a PCMCIA-Card for Notebooks?

If you need eSata on a desktop and have some unused internal Sata-Connectors then the best choice is to merely pass them to the outside : [Sata to eSata Bracket]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812119021"). Cheapest option aswell

No he means an ExpressCard.

[http://en.wikipedia.org/wiki/ExpressCard](http://en.wikipedia.org/wiki/ExpressCard)

---

### Post by locutus42 on 2011-06-18
I've seen lots of problems getting hot swapping with expresscard and the solution to my eSATA card was to just run this in a terminal. Now I don't need to boot with the card installed and hot swapping is working.

sudo modprobe acpiphp

The card is a generic 'made in china' card. The sticker on the card is half yellow and half white(running length wise), says "Serial ATA II" in the yellow and "Express Card 34" in the red. There's also a red star across both the yellow and white at the expresscard connector end of the sticker. lspci -v shows this:

02:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03) (prog-if 01)
        Subsystem: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller
        Flags: fast devsel, IRQ 16
        Capabilities: <access denied>
        Kernel modules: ahci

---

