---
title: "Why no 802.11n??"
date: 2007-10-08
forum: System76 Support
---

### Post by peestandingup on 2007-10-08
Even though 802.11n is still not a "standard" most manufacturers are offering them anyways in preparation for it to become one.

Just wondering why you guys don't at least offer the option on any of your machines?? Can any of the cards you provide have the N speeds enabled later, sorta like Apple did???

I'd hate to pay this much for a brand spankin' new machine to be stuck in G-land for the next 3 years.

---

### Post by thomasaaron on 2007-10-08
Actually, while you can make the "n" cards work under Feisty, they don't work natively.

They do, however, work natively under Gutsy. So, once Gutsy, is released, we will start including them in our offerings.

One caveat: There is currently a shortage of the cards that might not be cleared up before early November. So that is a factor too.

---

### Post by tedrampart on 2007-10-08
are the intel network devices in the laptops currently mini cards?  would it be possible to swap them out for say an n card later on when the support is there?  or would it be something like needing an express or pcmcia wireless card as a replacement?

---

### Post by peestandingup on 2007-10-08
Im wondering that too. If we buy a machine after you guys preinstall Gutsy that doesn't have an "n" card, can we install one later ourselves or will that void the warranty??

---

### Post by thomasaaron on 2007-10-09
Yep.

You can install one later and it will not void your warranty.

---

### Post by tedrampart on 2007-10-09
so we could install one later?  thats refreshing..

---

### Post by jml on 2007-10-09
That must mean that System 76 does not lock out non-standard wireless cards like HP and IBM/Lenovo does.

Joe

---

### Post by cward002 on 2008-01-10
That's awesome!! which cover on the bottom of the Gazelle Performance holds the 
NIC Card? Is it the small rectangular one in the middle of the laptop?

---

### Post by thomasaaron on 2008-01-10
Depends on which Gazelle you're talking about.

On the older ones (S62J*), it is beneath the panel that runs along the side of the computer that has the vga port.

On the new Gazelles, it is beneath the largest panel.

Best,
T

---

### Post by cward002 on 2008-01-10
Thanks  a lot Tom.

---

### Post by cward002 on 2008-01-10
Are the cards in these laptops PCI Express cards or are they regular PCI? (GAZP2)

Thanks again

Colin

---

### Post by palintheus on 2008-01-10
running the following in a terminal should let you know if the card is PCI Express

```
$ lspci | grep PCI\ Express
```

---

### Post by cward002 on 2008-01-11
Thanks Palintheus

now I'm really afraid because I think the card I ordered is PCI and not PCI Express

---

### Post by palintheus on 2008-01-11
what was the ouput of the command? make sure you typed it exactly otherwise it won't work.

---

### Post by cward002 on 2008-01-11
actually I can't try it right now because I am at work but I will do it as soon as I get home and let you know ( After I stop crying or celebrating)

---

### Post by cward002 on 2008-01-11
Thanks again Palintheus

---

### Post by thomasaaron on 2008-01-11
The wireless cards are Mini-PCI-Express adapters.

---

### Post by cward002 on 2008-01-11
Thanks Tom that's what I was afraid of. I'm pretty sure the card I bought is a Mini-PCI and not an express. oh well. I'll just return it and keep looking

---

### Post by cward002 on 2008-01-11
here is the output of the command

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
colin@dopey-dolphin:~$ 

It is definitely PCI express 

I found a Mini PCI Express wireless N adapterfrom OxfordTec.com

I am a little bit leery however as it is a ralink. Although they do say it is Linux compatible so we'll see

here is the link if anyone is interested:

[http://www.oxfordtec.com/us/p148/GIGABYTE-GN-WS30N-802.11N-b/g/n-draft-2.0-Ralink-RT2800-series-chipset/product_info.html](http://www.oxfordtec.com/us/p148/GIGABYTE-GN-WS30N-802.11N-b/g/n-draft-2.0-Ralink-RT2800-series-chipset/product_info.html)

---

### Post by palintheus on 2008-01-12
You may just google 'Ralink RT2800 ubuntu' from a couple of the results it looks like they have a GPL Linux driver for it, but there also seems to be a couple of bugs reported on it in LP, so just do a little research ;)

---

### Post by cward002 on 2008-01-12
Thanks again Palintheus

that mkes me feel quite a bit better. There are definitely risks to being an early adopter but it really feels good when it works!!! And when it doesn't work right away, I always learn something!!!

---

### Post by palintheus on 2008-01-12
Would you mind hitting the little star link in the posts that helped ;) thankya!

---

### Post by Blario on 2008-04-14
So these laptops connect with 802.11n speed??  What chipset are they using so that I may buy laptop card with the same chipset?  

Thanks so much!

---

### Post by thomasaaron on 2008-04-15
Intel Pro Wirless 4965.

---

### Post by Blario on 2008-04-16
Thanks, I'll pick that up ASAP

---

### Post by Blario on 2008-04-16
Are there any other N cards that can work with Ubuntu?  I'm having a hard time finding this one.  Any one know where it can be found?  Any other cards that use this same chipset (driver?) ?

---

### Post by thomasaaron on 2008-04-16
Probably, but System76 does not test with any others. So, I can't say for sure.

---

### Post by buster8079 on 2008-05-22
FYI: Intel Pro Wirless 4965 (i.e., 802.11n) will not work on the [Koala Mini]("http://system76.com/product_info.php?cPath=27&products_id=83") (per System 76).

The Koala is not set up to take the proper antenna configuration for the n-draft card.

The 4965 wireless card has three connectors on it to accept antenna wires. If your computer doesn't have
three antenna wires to connect to the card, it will not work correctly.

Again, Koala Mini no go with the wireless N.

---

### Post by Blario on 2008-06-05
So basically, a card with an antennae built into it has to be verfied as compatible.  

I have a T60. T'm not sure if it has antennaes inside the case

---

