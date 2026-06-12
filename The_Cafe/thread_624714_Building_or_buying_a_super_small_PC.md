---
title: "Building or buying a super small PC"
date: 2007-11-27
forum: The Cafe
---

### Post by jethro10 on 2007-11-27
Hi,

My wife has a shiny new Internet Radio / Upnp Client and she uses it a lot for streaming music to it from the linux box with Mediatomb Upnp server.

Now when the PC is not on. I tried a Dlink NAS disk with upnp server built in but quite frankly its rubbish. I've now become an expert researcher on upnp facilities in NAS devices and they all seem flaky.

So what's the smallest or easiest low cost / low power intel based Mini PC to run ubuntu on. Preferably headless if possibly, but how to power it down?

Needs to be wireless.
Are my needs unsolvable?

J

---

### Post by gn2 on 2007-11-27
Have you looked at the Linksys NSLU2 ?

[http://en.wikipedia.org/wiki/NSLU2](http://en.wikipedia.org/wiki/NSLU2)
[http://www.nslu2-linux.org/](http://www.nslu2-linux.org/)

---

### Post by mips on 2007-11-27
How about going the VIA cpu route?

[http://www.mini-itx.com/](http://www.mini-itx.com/)
[www.epiacenter.com]("http://www.epiacenter.com")

If wallmart has stock you could even buy one from them for US$200 and it will do the job just fine.

---

### Post by Chrisj303 on 2007-11-27
The Mac Mini..

[IMG]http://a248.e.akamai.net/7/248/8352/987/store.apple.com/Catalog/uk/Images/macmini/img/product-product.jpg[/IMG]

---

### Post by Zipster90 on 2007-11-27
This one from System76 has 7.10 already installed and wireless is built in for just over $500.

[[IMG]http://system76.com/images/koala_main_large.jpg[/IMG]]("http://system76.com/product_info.php?cPath=27&products_id=53")

---

### Post by popch on 2007-11-27
Damn Small Linux appears to sell small machines, too.

---

### Post by glupee on 2007-11-27
[http://www.logicsupply.com/](http://www.logicsupply.com/)

---

### Post by jethro10 on 2007-11-27
Thanks folks

sensible and concise answers.

J

---

### Post by jethro10 on 2007-11-29
Me Again,
I think i've found my ideal product as it runs mediatomb, one of the best upnp servers.

[http://www.excito.com/products.html](http://www.excito.com/products.html)

It is a headless linux mini server with low, low power consumption and basically runs debian. Much more sophisticated than I thought these N.A.S. boxes were.

Now to extend the question.
Can anyone comment on their use of this product or is there other similar Super N.A.S.'s out there ?

J

---

### Post by gn2 on 2007-11-29
> **jethro10 said:**
> Me Again,
I think i've found my ideal product as it runs mediatomb, one of the best upnp servers.

[http://www.excito.com/products.html](http://www.excito.com/products.html)

It is a headless linux mini server with low, low power consumption and basically runs debian. Much more sophisticated than I thought these N.A.S. boxes were.

Now to extend the question.
Can anyone comment on their use of this product or is there other similar Super N.A.S.'s out there ?

J

Have you seen the price of those things?
Do more research on the NSLU2, it can perform an astonishing range of tasks with the right firmware, has easily swappable hard drives and is far less expensive.

Review of the Bubba here: [http://www.pcw.co.uk/2190724](http://www.pcw.co.uk/2190724)
A debate on it's merits (or otherwise) here: [http://forums.vnunet.com/thread.jspa?messageID=830397&#830397](http://forums.vnunet.com/thread.jspa?messageID=830397&#830397)

---

### Post by ssam on 2007-11-29
via epia.

i run one headless mostly as a backup server and jukebox. MII 600MHz fanless.

pressing the power button on the case starts a shutdown. (equivilent to 'sudo halt'). this the default on a minimal install, and probably any ubuntu system where gnome or KDE are not running

i think you could chnage the behaveour in
/etc/acpi/powerbtn.sh
if you needed

---

### Post by jethro10 on 2007-11-29
> **ssam said:**
> via epia.

i run one headless mostly as a backup server and jukebox. MII 600MHz fanless.

pressing the power button on the case starts a shutdown. (equivilent to 'sudo halt'). this the default on a minimal install, and probably any ubuntu system where gnome or KDE are not running

i think you could chnage the behaveour in
/etc/acpi/powerbtn.sh
if you needed

I rather like that sound of that, I forgot about these small PC boards.
J

---

