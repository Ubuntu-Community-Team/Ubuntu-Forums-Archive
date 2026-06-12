---
title: "Best IP update setup?"
date: 2006-07-13
forum: Server Platforms
---

### Post by jjr2527 on 2006-07-13
Hello:

I'm sure there are many ways to do this but I am looking for the "best" way to do it.  I have a cable internet connection through time warner that I would like to run my web server on.  The problem is that I do not have a static IP.  My domain name is registered with go daddy so I would also have to update the domain to hook up with my new IP every time it changed.

In windows I think this is done with zone edit and direct update but I never did that either.

To clarify at this point I consider "best" to mean simplest.

Thanks,

J

---

### Post by FredSambo on 2006-07-13
i use DynDNS [http://www.dyndns.com/](http://www.dyndns.com/) as my nameserver solution.  it automatically updates your dynamic IP address with their nameservers for you, so you can have a dynamic IP and still host websites.

it costs $25 per year though, but it works flawlessly.

there may be a free way to do the same thing, but i couldn't find it.

---

### Post by AndyW on 2006-07-14
a quick google search turned up this [http://www.everydns.net/](http://www.everydns.net/)
looks promising

---

### Post by az on 2006-07-14
> **FredSambo said:**
> i use DynDNS [http://www.dyndns.com/](http://www.dyndns.com/) as my nameserver solution.  it automatically updates your dynamic IP address with their nameservers for you, so you can have a dynamic IP and still host websites.

it costs $25 per year though, but it works flawlessly.

there may be a free way to do the same thing, but i couldn't find it.

[http://www.dyndns.com/services/dns/dyndns/features.html](http://www.dyndns.com/services/dns/dyndns/features.html)

Dyndns offers a free service.  You can use ddclient or any of the other dyndamic dns clients available.  You can chose to pay 25 bucks and use a custom domain name.

The free service allows you to use one of their domain names:
[http://www.dyndns.com/services/dns/dyndns/domains.html](http://www.dyndns.com/services/dns/dyndns/domains.html)

So, for example, you can set up a dynamic dns account with homeunix.net and so you would access your address with

jjr.homeunix.net

---

### Post by FredSambo on 2006-07-14
> You can chose to pay 25 bucks and use a custom domain name.


oh right, i did indeed use a custom domain name!

---

### Post by jjr2527 on 2006-07-14
I was referring to a service that I could use with a custom domain but azz's soloution may be helpful for other purposes.  Thanks.

---

### Post by az on 2006-07-14
> **jjr2527 said:**
> I was referring to a service that I could use with a custom domain but azz's soloution may be helpful for other purposes.  Thanks.

Some hosting providers offer a dynamic dns service for custom domains.  You already paid for the domain name, so you tell the service provider you paid for that to point to the other hosting provider.  That hosting provider offers you dynamic dns for your domain.

In my case, the cost difference in getting dynamic dns to host a domain I own is almost the same as what I would pay to get a static IP from my ISP.  And that is always more reliable.

---

### Post by MJN on 2006-07-14
I use [www.zoneedit.com]("http://www.zoneedit.com") with the 'Zoneclient' Python script regularly checking the current IP and updating the DNS accordingly. It's free for the first five domains,  has plenty of flexibility with regards to your DNS config, and you can buy additional credits for 'extra services' such as backup MX (will accept your mail if your machine is down, hold it for upto 10 days, and then send it all on when you're back online).

I've been with them several years and can highly recommend them - never (knowingly) had a single fault.

I'm not familiar with GoDaddy but the may charge you to delegate your name to someone elses name servers however.

Mathew

---

### Post by FredSambo on 2006-07-14
> I'm not familiar with GoDaddy but the may charge you to delegate your name to someone elses name servers however.

nope, they don't!

---

