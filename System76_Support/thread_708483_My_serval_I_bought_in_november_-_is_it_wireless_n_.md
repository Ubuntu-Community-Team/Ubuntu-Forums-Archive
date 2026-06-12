---
title: "My serval I bought in november - is it wireless n capable ?"
date: 2008-02-26
forum: System76 Support
---

### Post by Squish on 2008-02-26
I noticed that on your site, you laptops are now wireless N ~ only like a month after I bought mine. Did the hardware change? or is mine wireless n capable as well? if not, how would I upgrade it?

---

### Post by thomasaaron on 2008-02-26
The *computer* is capable. But I don't know what card was being sold when you purchased. In November, it was probably the 3945 card, which is *not* an n card.

Post the output of: ```
lspci | grep -i wireless
``` and see if it comes up with the 3945 card. If it does, you will need to install an n card. Otherwise, you already have an n card.

Email me at support for the preferred n card model number.

---

### Post by Squish on 2008-02-27
ahhh, its wireless g...
huh...

So what do I do to make it wirelsess n? What would it cost roughly?

---

### Post by thomasaaron on 2008-02-27
You would just need to take out the wireless card that is in it and install an intel pro-wireless 4965 AGN card.

The procedure is pretty simple and it should cost much. Maybe $40.

We don't sell these cards separately, but just google "buy 4965" and you'll find them.

You should probably call support for instructions before you dig in.

---

