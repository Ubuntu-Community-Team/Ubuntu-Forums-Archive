---
title: "DIY web client from home"
date: 2012-12-24
forum: The Cafe
---

### Post by EmmEight on 2012-12-24
So I want a website.

A place for my friends/family to be able to visit me.

In other words I want a dot com.

**I will host from home.**

Opinions please (I know weird)):P

Cheapest Domain provider?
Best Domain provider?
Best linux-based hosting platform?
Best DIY website infrastructure? Drupal?

Currently running ubuntu server with public and private access.. SSH, SFTP, FTP, VNC 

HTML, PHP, MySQL, whiz, what am I missing?

Come on Ubuntu, Lay it on me!

---

### Post by Lars Noodén on 2012-12-24
You ISP probably won't give you a static IP number for your home network unless you pay extra and change your contract.  You can work around that a little by using a [dynamic DNS service](https://help.ubuntu.com/community/DynamicDNS).  That will give you an A name.  Then you need to register a domain name with a DNS registrar.  Use that to create a CNAME and point to your A name. 

Or you could just rent a VPS.  Just be sure that your VPS hosting company and your registrar are not the same company.  You need the flexiblity to move that having them separate will give you.

---

### Post by EmmEight on 2012-12-24
Thanks for the quick response!

I take it you have problems with a VPS hosting company, being the same as a registrar company.


Do we have an ubuntu friendly registrar?

If I chose to spend money, I would like it matter.

7/8 RogerWaters

---

### Post by Lars Noodén on 2012-12-24
I've had problems in the past and know others that have had problems.  However, by having a separate registrar meant that the site could be 'moved' to a better hosting company quickly and without delay.  Most of them are pretty good, but sometimes companies change and a good one can turn bad.  So it's better to be prepared.  

About which one to choose, that's a changing landscape and you'll have to research the situation as it happens to be today.

---

### Post by EmmEight on 2012-12-24
> **EmmEight said:**
> 
**I will host from home.**

Thanks for the tip. I will be sure to take it into consideration, as it happens to be today. Happy holidays!

Anyone else?

---

