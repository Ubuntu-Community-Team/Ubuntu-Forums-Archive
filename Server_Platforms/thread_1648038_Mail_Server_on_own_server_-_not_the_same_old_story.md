---
title: "Mail Server on own server - not the same old story"
date: 2010-12-18
forum: Server Platforms
---

### Post by neomod on 2010-12-18
After days and days spent in reading guides, how-to, forum post and much more, I still have some doubts regarding the possibility of developing a personal mail server having a fully functional ubuntu server. ( of course this is due to my lack of knowledge...hehe :) )

First thing I wish to understand is the focal point "*Can I have my private mail server pointing to [email]mymail@myinventeddomain.whatev[/email]er ONLY IF I have previously registered ( bought )  **myinventeddomain.whatever?*"

Second thing is: " *Could it be a work-around setting up a free dynamic name server ( pointing to my server, where a LAMP stack is already fully functional ) and then use this "name" to create my email*? " [COLOR=Green]*[/COLOR]
- [COLOR=Green](*) Example[/COLOR]: using my own server, already accessible from outside my lan using a free dyndns name, I'm able to access and manage some web-based services. Is it possible to apply concept two at this situation? The base idea is to have my own email service, with my own domain like [email]neomod@thenameiwant.xxx[/email] , so I can create email-based notification between my server and some other email addresses without relying onto some public service ( let's say google or my own isp mail server ).

I have read about the common solution in theese cases ( Postfix ) but in each guide, tutorial, faq or similar I could have read there is no explanation about " How to choose/obtain your own domain name".

Reading forum discussion situation isn't better, because some one clearly states that I need to by a domain name ( ex. godaddy, aruba, etc. ) while some others say that I can realize it on my own just using dinamic dns name and a few other things.

So beg my pardon if this question might seems stupid, but since I already own a domain name+webhost I reallu wish to understand before spending other money.

Thank you in advance for reading!

---

### Post by clrg on 2010-12-18
Its rather simple. 
1. Buy the domain you want
2. Register your DNS server as the domain master
3. Create a MX record on your DNS server
4. Install and configure mail daemon
5. Done :)

I don't think having dynamic IPs is a good idea. Get a fixed one, solves many problems.

---

### Post by neomod on 2010-12-18
Thankyou very much for yor answer.

According to point 1 and 2, as far as I can understand the best solution is registering for domain+DNS Control Option and then setting up personal DNS

For point 3 I'm not sure if my registrant offers this option...better if i ask before buy.

( the dynamic IP problem could be solved using a service like dyndns or no-ip togheter with an updater daemon, better if included in my router? )

---

### Post by neomod on 2010-12-18
> **clrg said:**
> Its rather simple. 
2. Register your DNS server as the domain master


They should point to my IP right ? ( instead of the classical NS1.MYDOMAIN.COM ) But since I'm forced to use dynamic ip, should they point to a Dynamic DNS Domain Name ?

---

### Post by CharlesA on 2010-12-18
> **neomod said:**
> They should point to my IP right ? ( instead of the classical NS1.MYDOMAIN.COM ) But since I'm forced to use dynamic ip, should they point to a Dynamic DNS Domain Name ?

The A record, would need to point to your ip address. You can't use another domain name, as far as I know.

> **neomod said:**
> Thankyou very much for yor answer.

According to point 1 and 2, as far as I can understand the best solution is registering for domain+DNS Control Option and then setting up personal DNS

For point 3 I'm not sure if my registrant offers this option...better if i ask before buy.

( the dynamic IP problem could be solved using a service like dyndns or no-ip togheter with an updater daemon, better if included in my router? )

If your registrar offers DNS services, they should allow you to create an MX record.

---

