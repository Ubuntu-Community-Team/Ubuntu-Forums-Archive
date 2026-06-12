---
title: "Good compatible audio recording hardware"
date: 2011-03-16
forum: Ubuntu Studio
---

### Post by tjajab on 2011-03-16
Hi,

I'm on my way buying some home recording equipment. My demands are quite basic, phantom powered mic input and a stereo input for other instruments. The problem is to find hardware that works in Linux. I've checked out the ALSA compatibility matrix, but I find it hard to understand when something really works (pain-free :)).

As I really have no special favorite brand or product, I thought it would be easy to find at least one single product which came bundled with linux-drivers or was 100% compatible out of the box; however, it seems really hard. I do not know where to look.

Most of the posts I've read, and also much of the stuff at the ALSA page, is people wondering if device xyz works, and then a long thread with "well, if it has this or that chip it may work if you run these commands" etc. I also understand that the best thing is to try it out, but I was hoping to buy something I know already worked in Linux (specifically Ubuntu).

---

### Post by AutoStatic on 2011-03-16
> **tjajab said:**
> I'm on my way buying some home recording equipment. My demands are quite basic, phantom powered mic input and a stereo input for other instruments. The problem is to find hardware that works in Linux. I've checked out the ALSA compatibility matrix, but I find it hard to understand when something really works (pain-free :)).Hello tjajab,

So you're probably looking for a PCI(e) or USB soundcard? Some examples:
USB: [Roland/Cakewalk UA-25EX]("http://www.roland.com/products/en/UA-25EX/index.html")
PCI(e): [M-Audio]("http://www.m-audio.com/index.php?do=products.family&ID=PCIinterfaces")

> **tjajab said:**
> As I really have no special favorite brand or product, I thought it would be easy to find at least one single product which came bundled with linux-drivers or was 100% compatible out of the box; however, it seems really hard. I do not know where to look.That's because such a product does not exist.

Best,

Jeremy

---

### Post by tjajab on 2011-03-16
Thanks for the quick reply. I would prefer an USB device for ease of use. Does the Roland/Cakewalk UA-25EX work good in Linux?

Also, I've had lesser quality USB products which has worked fine in Linux out of the box, probably using some standard USB audio protocol.

---

### Post by AutoStatic on 2011-03-16
> **tjajab said:**
> Does the Roland/Cakewalk UA-25EX work good in Linux?Yes.

> **tjajab said:**
> Also, I've had lesser quality USB products which has worked fine in Linux out of the box, probably using some standard USB audio protocol.That's right, most USB1.1 audio devices, like the UA-25EX, comply to industry standards so one single driver suffices. And this driver is part of the ALSA driver-stack that is included in Ubuntu.

Best,

Jeremy

---

### Post by tjajab on 2011-03-18
Hi again,

it seems hard to get a UA-25EX. My local dealer says it is out of stock and his guess was that it will be replaced by another unit soon. I guess we can't count on that new device getting Linux support anytime soon, so now my question is:

Does someone have another suggestion of a similar external sound interface, working in Ubuntu, with phantom power and preferrably 24/96 recording?

Regards,
Andreas

---

### Post by sgx on 2011-03-18
Check this list, 

[http://www.linuxstudiopro.com/](http://www.linuxstudiopro.com/)

and verify with a thorough google search,
and also use the previous pages here for topics with users of such hardware detailing successful usage!
Cheers

---

### Post by tgalati4 on 2011-03-18
I like my M-Audio Delta 66.  It uses a PCI card and a connection to an IO box that has 2 mic pre's and 4 1/4" line-ins and 6 line-outs with digital outs as well.  It's an older card, but handles 24/96 well.  You can find them on ebay and craigslist.

---

### Post by AutoStatic on 2011-03-19
> **tjajab said:**
> I guess we can't count on that new device getting Linux support anytime soonHello Andreas, 

I guess we can count on it. Basically all Roland/Edirol USB sound cards work with Linux, even the USB2 ones!

> **tjajab said:**
> so now my question is:

Does someone have another suggestion of a similar external sound interface, working in Ubuntu, with phantom power and preferrably 24/96 recording?Any USB1.1 class compliant sound card should work. So pick a soundcard you like, check the manual if it mentions anything like the device being class compliant or not needing any drivers for Windows or Mac and you should be good to go.

Best,

Jeremy

---

### Post by cfhowlett on 2011-03-22
Works with Audacity, Ardour.  See my video...

[http://www.youtube.com/watch?v=xyVPCPRamTA]("http://www.youtube.com/watch?v=xyVPCPRamTA")

---

