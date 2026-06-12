---
title: "How do I set up a DNS server in Ubuntu server, and connect it to my online domain?"
date: 2013-03-22
forum: Server Platforms
---

### Post by Murillio4 on 2013-03-22
Hi people

I'm renting a Domain with a Domain server at hostgator.com. But I dont got enough space for my website to run. So I decided to create my own DNS server and connect it to the Domain. I tried to google it but couldnt find how to connect my DNS to my Domain, I found only how to create it local. Can some of you ubuntu experts out there help me with this?

---

### Post by darkod on 2013-03-23
If you don't have enough space at the provider, you need a web server, not dns server. The domain registrar control panel will usually do all dns functions you need, it's rarely needed to make your own dns.

If you need space for the website, that's a different thing. Also, running your own web server at home might be blocked by your ISP.

First from your computer at home go to [http://www.canyouseeme.org/](http://www.canyouseeme.org/) and check if your port 80 is open or not. Also if you need https check port 443.

If they are closed by the ISP there is not much you can do to run a web server at home.

---

