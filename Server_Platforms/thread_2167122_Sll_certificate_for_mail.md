---
title: "Sll certificate for mail"
date: 2013-08-12
forum: Server Platforms
---

### Post by Bondar_Mircea on 2013-08-12
I want to buy ssl certificate for my mail server. I use postfix,dovecot with mysql support with self signed certificate. I want to buy certificate for this mail server but do not know what kind of certificate do I need and where to buy it?

---

### Post by 1clue on 2013-08-12
I use Thawte, based in Great Britain.  I haven't been doing mail servers for a lot of years but I think it's the same as the web site cert.  They'll have that info on the site.

That said, I usually do a little bit of price shopping when the time comes.  I don't get the cheapest thing out there, but I'll see where the majority of reputable providers are and make sure I'm not paying way too much.

---

### Post by kpothi on 2013-08-14
There are different [types of SSL certificates](http://en.wikipedia.org/wiki/Digital_certificates) available in the market. You may choose depending on your needs. The cheapest is domain validated (**DV**, sometimes called as **class 1**) SSL certificate. Since, there is no manual intervention is needed in this method, you may even get it for free, especially, if it is for personal use. A search in your preferred search engine may help further.

---

### Post by sandyd on 2013-08-14
Startcom offers some free I think ([https://www.startssl.com/](https://www.startssl.com/))

---

### Post by kpothi on 2013-08-16
> **sandyd said:**
> Startcom offers some free I think ([https://www.startssl.com/](https://www.startssl.com/))

Indeed. I've been using their class 1 certificate for the second year in a row on [my personal site](https://www.tinywp.in). The guidelines to register in the site and to get an SSL certificate is bit complicated, yet, their SSL certificate works great for personal use (and I'm sure it'd work for companies too, but those certificates are not free).

---

