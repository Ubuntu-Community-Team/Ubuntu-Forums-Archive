---
title: "Virtual Private Server, please help!"
date: 2021-01-21
forum: Ubuntu, Linux and OS Chat
---

### Post by 24superuser on 2021-01-21
I'm running Centos 8, server, and need a private virtual server to simple web hosting for individual training so spend some hours to find a free one, for couple of day. Digital Ocean, Azure and Google they either require credit card info or telephone and address confirmation. Have been through reddit as well but no advice.Could anyone give any advice for a good free one, being able to register without any private info ? There are also so,e older post in here, but muck older to be used or has become absolute, literally from 2005.

---

### Post by coffeecat on 2021-01-21
Not an Ubuntu support question.

*Thread moved to **Ubuntu, Linux & OS Chat.***

---

### Post by TheFu on 2021-01-21
Amazon had a free trial tier (micro-server) for 365 days, but I don't know whether that exists still or if it worked without 
a) amazon account
b) payment method connected to amazon account

A few years ago, my LUG was kicked off our freely provided VPS because too many other people were abusing the offer by running crypto-mining 24/7 on these free servers. We never did, but the VPS provider felt they needed to kick everyone off to be fair.  We ended up moving to someone's home on a Comcast business account - which isn't cheap. I have one too.

Lots of people moved their hosting to github or into CloudFlare caching. You can have the server hosted at home long enough for cloudflare to make a copy, then take your home server down and cloudflare will serve the pages, at least a year, so I've heard.
[https://www.cloudflare.com/learning/cdn/caching-static-and-dynamic-content/](https://www.cloudflare.com/learning/cdn/caching-static-and-dynamic-content/)

Nearlyfreespeech.net is super cheap - like $0.30 a month.  I don't keep up with their payment options, but it is all pre-paid. Back when they started, people would put a $10 bill into an envelope and mail it to open an account. I don't know if they still do that or what legal mandates are necessary.  $10 would go pretty far ... or it could be eaten up in a crazy busy month, but the following month, the bandwidth bill would drop back to $0.30/month, probably.  They aren't noob friendly. If you need more than sftp and ssh, this isn't the service for you.
[https://www.nearlyfreespeech.net/services/hosting](https://www.nearlyfreespeech.net/services/hosting)  Yep, it is still $0.01/day ... but they've added infrastructure. Looks to be about $6/yr total.

---

### Post by 24superuser on 2021-01-22
Thanks for your reply in details. 
  	 	 	 	   Uuumm... I agree that may reflect a &#8220;miner&#8217;s username&#8221; into professional eyes, as 24superuser. will try to come to another username if that would be the case <D

---

### Post by DuckHook on 2021-01-22
> **TheFu said:**
> Nearlyfreespeech.net is super cheap - like $0.30 a month…  Yep, it is still $0.01/day ... but they've added infrastructure. Looks to be about $6/yr total.
You never cease to amaze me with your wealth of info. It so happens that this option may be very timely and useful for me right now.

Thanks for sharing.

---

