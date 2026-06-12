---
title: "Help - directing my ip to my domain"
date: 2011-07-25
forum: Server Platforms
---

### Post by Steviedallas on 2011-07-25
I've setup a LAMP server at home & i'm trying to get a webserver running. I'm having trouble finding information on how to "point" my domain at my IP. 

The site is up & accessible. I own the domain, but I don't know where to go from here.

I believe I need to change the dns servers on godaddy, but what to?

Is there a free service which will update my IP when it changes?

Thanks for your help (first post!)

---

### Post by Chrus on 2011-07-25
Does your ISP provide you with a static IP? Or are you on a dynamic IP?

You will need to let godaddy know what IP you are using... however, if you are on a dynamic IP, this will change constantly. So it might be worth paying a little extra and getting your ISP to provide you with a static IP.

If this site is just for your personal use, you could look into using something like DYNDNS ([http://www.dyndns.com/]("http://www.dyndns.com/")), a free service that will provide you with a URL that is updated when you IP changes, so it always points to your site.

---

### Post by Steviedallas on 2011-07-25
> **Chrus said:**
> Does your ISP provide you with a static IP? Or are you on a dynamic IP?

You will need to let godaddy know what IP you are using... however, if you are on a dynamic IP, this will change constantly. So it might be worth paying a little extra and getting your ISP to provide you with a static IP.

If this site is just for your personal use, you could look into using something like DYNDNS ([http://www.dyndns.com/]("http://www.dyndns.com/")), a free service that will provide you with a URL that is updated when you IP changes, so it always points to your site.
It's dynamic, unfortunately.

I'm still sort of new to this. Correct me if I'm wrong. In other words, DYNDNS provides a free hostname (exampledomain.dyndns.com)?

So, the answer is talking to my ISP.

Are there pay(or free) services that point my domain to my dynamic IP, but monitor/change my IP if necessary?

Thanks for your help!

---

### Post by Chrus on 2011-07-26
[QUOTE=Steviedallas;11086548]
I'm still sort of new to this. Correct me if I'm wrong. In other words, DYNDNS provides a free hostname (exampledomain.dyndns.com)?
[QUOTE]

Thats correct. Useful if you need to access your home computers remotly, not so useful if you are trying to host a public facing website.

Your best bet would be to contact your ISP and see about getting a static IP put on your account.

Keep in mind tho that some ISP's will have something in the contract about you not being allowed to host a public website on your account. And if they do let you host your own website, all traffic will be going to your personal computer (so make sure its secure), and any trafic to your site will be counted towards your monthly download limit.

---

### Post by Habitual on 2011-07-28
Static IP from your ISP and [https://secure.wikimedia.org/wikipedia/en/wiki/Domain_Name_System#Address_resolution_mechanism](https://secure.wikimedia.org/wikipedia/en/wiki/Domain_Name_System#Address_resolution_mechanism)

---

### Post by volkswagner on 2011-07-28
> **Steviedallas said:**
> 

Are there pay(or free) services that point my domain to my dynamic IP, but monitor/change my IP if necessary?

Thanks for your help!

There are pay services (using your own domain name) from places like no-ip.com and dyndns.com.  The going rate is approx $25/yr for one domain (reduced rate/domain for multiple domains).  This does not seem like a lot, but if you have multiple domains, it becomes a no brainer to get a VPS for situations where you want reliable web hosting (no worries about power failure, Internet outage, etc.) and full control over the server itself plus no need to pay the electric bill for a 24/7 machine.

If you decide to go the dynamic route, check your router as some have built in support for DynDns and no-ip, but some may have no support or support for only one service.

If this is just a hobby machine and short outage is not an issue, just point your DNS to your ip and manually update it when it changes.  Some people get more than a year before the ip changes.  You can even setup a script to send an email when the ip changes.

---

### Post by Steviedallas on 2011-07-29
Thanks for the additional info guys! I'm gonna go with DYNDNS for now.

I fought with brighthouse, then to Earthlink, then Timewarner. I couldn't get anywhere with them :mad:

---

