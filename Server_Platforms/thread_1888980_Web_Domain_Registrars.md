---
title: "Web Domain Registrars"
date: 2011-11-30
forum: Server Platforms
---

### Post by createdcreature on 2011-11-30
Is there a registrar offering a 'pay once-last forever' approach? Also, do you know any good services of mapping the domain to your IP?

---

### Post by deonis on 2011-11-30
DynDns is very cheap and even free service if you refresh your account every month...

---

### Post by jonobr on 2011-11-30
Hi there


ICANN are the origination in charge and their rules require that domain names be registered on an annual or some such period.

From the [ICANN FAQ]("http://www.icann.org/en/faq/#regtime")

> [B]How long does a registration last? Can it be renewed?

Each registrar has the flexibility to offer initial and renewal registrations in one-year increments, provided that the maximum remaining unexpired term shall not exceed ten years.[/B]

The registrars are companies like godaddy dyndns etc

---

### Post by createdcreature on 2011-11-30
OK, but what about the domain mapping?

---

### Post by jonobr on 2011-11-30
as deonis said, you get service from dyndns but there are a bunch out there that offer all sorts of different things.

Given I mostly do it for business I dont have a preference on regsitrar as mostly its a price thing for me.

---

### Post by SeijiSensei on 2011-12-01
> **Robert Moyse said:**
> OK, but what about the domain mapping?

Host your own DNS.

---

### Post by createdcreature on 2011-12-03
How on earth do I do that?

---

### Post by trogdor1138 on 2011-12-04
There's some more information that's needed. Is this for a domain you're hosting at home, or for your business? Have you paid for a static IP, or is it through an ISP that changes it?

It sounds like you might be in a little over your head to set up your own DNS. The support pages recommend you use the BIND9 client; you can read up about it in the wiki and the Ubuntu Server installation pages. I'm not saying that you shouldn't try (a lot of my learning has come from trial and error), but it's probably a bit much for a first step.

If you've got a static IP, I would just use your registrar's DNS servers. These are generally quick to implement changes and can be administered from your account with them. Any of the big registrar's should offer basic DNS service for free, with additional charges for more services that you probably don't need.

If you're hosting from home on a dynamic IP you'll want to look into something like DynDNS or X-name. Services like these provide small clients that run on your network and then update your DNS when your IP refreshes. You can even use a service like DNS-O-Matic to update several different services simultaneously (OpenDNS, X-name, etc.) to have redundancy in your DNS setup. Honestly though, unless you're really doing this on the cheap I would just cough up for the static IP.

Once you have one of these solutions in place you can start experimenting with getting your own DNS server up and running in Ubuntu. Setting the above up will force you to learn more about MX, CNAME and other kinds of records so you'll understand what you're doing better.

---

### Post by newbie-user on 2011-12-04
freedns.afraid.org offers free dns.

I think most domain name registrars offer some sort of pay once plan.  I recently got a domain for 10 years with Godaddy.  Networksolutions also has 100-year plans.

I believe most of the big-name domain name registrars offer dns with domain name registration.  Networksolutions, Yahoo and Godaddy do.  I've used all three.

---

### Post by jonobr on 2011-12-05
> 100-year plans.

Friggin hell, must be the rough economy...

I remember in my day.... (leans back in rocking chair and smokes pipe)

---

### Post by CharlesA on 2011-12-05
> **jonobr said:**
> Friggin hell, must be the rough economy...

I remember in my day.... (leans back in rocking chair and smokes pipe)
I have my domain name for 10 years, I cannot even imagine what to do with a domain that is good for 100 years (or how much that would cost)

---

### Post by bab1 on 2011-12-05
> **CharlesA said:**
> I have my domain name for 10 years, I cannot even imagine what to do with a domain that is good for 100 years (or how much that would cost)

If it were a corporate identity (i.e Coca Cola, MacDonald's. Disney, etc) I could see locking up the the domain name.

---

### Post by CharlesA on 2011-12-05
> **bab1 said:**
> If it were a corporate identity (i.e Coca Cola, MacDonald's. Disney, etc) I could see locking up the the domain name.
That's true. I wonder if any of those companies will still be around in 100 years.

---

### Post by bab1 on 2011-12-05
> **CharlesA said:**
> That's true. I wonder if any of those companies will still be around in 100 years.

In business being around for 100 years is not necessarily the point.  With control for 100 years, and being a viable entity, makes the domain name a valuable asset now.

We are now way off topic and in the weeds.  LOL :D

---

### Post by CharlesA on 2011-12-05
> **bab1 said:**
> In business being around for 100 years is not necessarily the point.  With control for 100 years, and being a viable entity, makes the domain name a valuable asset now.

We are now way off topic and in the weeds.  LOL :D
Good point.

Nothing to see here, folks!

---

