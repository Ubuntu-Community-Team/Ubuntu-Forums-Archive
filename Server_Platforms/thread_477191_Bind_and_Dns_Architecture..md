---
title: "Bind and Dns Architecture."
date: 2007-06-18
forum: Server Platforms
---

### Post by tvlad on 2007-06-18
Hello, i've tried to google for some links about setting up Bind and links about the Dns Architecture as a whole, i either found howto's dating six years back, or not very useful information for me.

I was wondering if you could help me out with some quality documentation about setting up Bind, chrooting it and also about how dns works because i want to have a pretty clear picture.

Thank you.

---

### Post by turinglabs on 2007-06-18
A howto is here: [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

The best references I've seen are still printed books. O'reilly's "DNS & BIND"  (The latest edition is at [http://www.oreilly.com/catalog/dns5/](http://www.oreilly.com/catalog/dns5/)). For how DNS works, Steven's TCP Illustrated vol. 1 ([http://www.kohala.com/start/tcpipiv1.html](http://www.kohala.com/start/tcpipiv1.html)) is a classic (and not just for DNS). 

Don't forget, the core DNS protocol has been around forever, so you don't need a "new" reference to learn the basic protocol internals. For the software, BIND v9 is the latest, see  [http://www.bind9.net/manuals](http://www.bind9.net/manuals) . There are some newer extensions to DNS that came about in RFC form in the past few years, see dnssec.net for details.

---

