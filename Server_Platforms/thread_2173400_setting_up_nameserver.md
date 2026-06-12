---
title: "setting up nameserver"
date: 2013-09-09
forum: Server Platforms
---

### Post by adam15 on 2013-09-09
I am trying to setup my own nameserver so I can host my own websites and I have everything up and running except for the nameservers. I have tried a few things but nothing is working when I try to change the ns1.sample.com and ns2.sample.com at my registrar it tells me not valid nameservers


Can any one help me out with this porblem i am having and I am a beginner

---

### Post by Lars Noodén on 2013-09-09
Why not use the name server(s) provided by your registrar?  You can set up your own DNS but that should only be done if you have a reason not to use the existing infrastructure.  Using the registrar's DNS will still allow you to host your own services.

---

### Post by adam15 on 2013-09-09
yes but i have to pay hosting fees with my registar to use there nameserver i want to cut down that cost and do it myself

---

### Post by Lars Noodén on 2013-09-09
Hosting is usually a separate service from DNS.  When you register a domain name, say for 7 EUR per year, the price includes DNS.  Stuff like Apache2, Perl, MySQL/Postgresql, and so on is a separate package.  That's something you can host yourself, is that what you are refering to?

---

### Post by |{urse on 2013-09-09
Setting up pointers and mx records is a pain! Just use your registrar to point as mentioned above. Google setup "A name" (insert your registrars name here).

---

### Post by adam15 on 2013-09-09
yes i am already hosting everything on my own servers so i pay for hosting that I am not using so I need to get nameservers in place to point my domains at my registar at instead of paying for them

---

### Post by David_Pecot on 2013-09-09
> I am trying to setup my own nameserver so I can host my own websites and  I have everything up and running except for the nameservers. I have  tried a few things but nothing is working when I try to change the  ns1.sample.com and ns2.sample.com at my registrar it tells me not valid  nameservers

Unless you have a nameserver at ns1.sample.com (and have a DNS server to resolve the name) then that won't work.  And since you obviously don't have a DNS server, it's a chicken-egg problem.  You'd have to put in the actual IP address of the server, maybe, assuming you have a working DNS server.  Maybe it could resolve it's own address.  That sounds like the ultimate DNS chicken-egg problem too.


Anyway, You still need to register the domain, and you have to pay for that.  Included is the nameserver service.  So just use the nameserver where you registered.  Don't use the nameservers at the hosting site.  Use the nameservers where you registered your domain (i.e., NameCheap, Register.com, GoDaddy, or whatever it was).  If you paid for registration at the hosting site, then maybe switch your domain registration to a registrar.  Or don't.  It's pretty much about the same, anyway, probably - web hosting (bare minimum) is pretty cheap, and registration is more.  So don't worry about paying for services you aren't using - you are using the domain registration service, and that's most of what you are paying for.  That said, if you decide to move to a registrar I would recommend NameCheap.com - they don't pester you with marketing about extra services.  And they are (as advertised) pretty cheap.

---

### Post by Kevin_Arnold on 2013-09-09
The other posters are correct. Any registrar is going to have a place to enter an A record instead of forwarding the name servers.  You have to pay a registrar for the name no matter what.  

I use hover.com but anything will do.

---

### Post by adam15 on 2013-09-10
i understand that i have to pay for the domain every year that i know but I can host my own sites and point them to my nameservers so that i dont have to pay for the hosting features i just have to pay for the domain name then

---

### Post by Kevin_Arnold on 2013-09-10
> **adam15 said:**
> i understand that i have to pay for the domain every year that i know but I can host my own sites and point them to my nameservers so that i dont have to pay for the hosting features i just have to pay for the domain name then

I understand what you're saying but you're confused on what you really need. You don't need to point the domain to your name servers, you just need to point an A record to the IP address of your server. You still don't have to pay for hosting, the server can still be hosted at your house or whatever you plan to do, you just don't need to run a name server. Your registrar has name servers that you can use for free.

What registrar are you using, we can walk you through getting it all set up.

---

### Post by adam15 on 2013-09-10
> **Kevin_Arnold said:**
> I understand what you're saying but you're confused on what you really need. You don't need to point the domain to your name servers, you just need to point an A record to the IP address of your server. You still don't have to pay for hosting, the server can still be hosted at your house or whatever you plan to do, you just don't need to run a name server. Your registrar has name servers that you can use for free.

What registrar are you using, we can walk you through getting it all set up.


I am useing hostmonster   I canceled my hosting and they took all of my a records away and told me I have to pay to have access to there nameservers and well as place dns records  that is why i am trying to set my own up   but if you can help me where i dont have to pay them but for the domain name that would be good as well

---

### Post by Kevin_Arnold on 2013-09-11
> **adam15 said:**
> I am useing hostmonster   I canceled my hosting and they took all of my a records away and told me I have to pay to have access to there nameservers and well as place dns records  that is why i am trying to set my own up   but if you can help me where i dont have to pay them but for the domain name that would be good as well

If you stopped paying them, you no longer own the domain. You'll need to re-register the domain somewhere (use any of the registrar suggestions we've already given you above) or see if hostmonster will let you just pay for the domain.

Just because you paid for it once doesn't mean you get to keep access. It sounds like your best bet is going to be to transfer the domain to another registrar and use their name servers. Most domain names are between $5-$15/year so it isn't much money.

---

### Post by adam15 on 2013-09-11
> **Kevin_Arnold said:**
> I understand what you're saying but you're confused on what you really need. You don't need to point the domain to your name servers, you just need to point an A record to the IP address of your server. You still don't have to pay for hosting, the server can still be hosted at your house or whatever you plan to do, you just don't need to run a name server. Your registrar has name servers that you can use for free.

What registrar are you using, we can walk you through getting it all set up.


I know that i have to pay for the domain every year that is fine but host monster makes me pay for hosting to have access to there nameservers and to add a records

that is what i dont want to pay for they are charging me 150 a year for hosting to have access to add a records

---

### Post by Lars Noodén on 2013-09-11
It looks like there are two things going on here.  One is domain name registration and the other is hosting.  From looking at HostMonster's web site very, very briefly it looks like they bundle the two for the first year for $5 a month or something like that.  

You can easily provide your own hosting, but DNS is something you get as part of registering a domain name.  If you are unsatisfied with HostMonster's DNS costs, what you can do is to transfer the domain over to another registrar.  In doing so you will have to pay for another year, but that will add to the existing months you have left on that domain.  It's a two or three step process which your new registrar can help you with.  It will require some cooperation from your old registrar to free up your domain name in such a way that it can be *safely* transfered, but unless they are scammers that is not likely to be a problem either.

In general it is considered important to register your domain(s) with a different registrar than where you are hosting.  If they have both, then there is too little room for negotiation when things turn bad.

---

### Post by adam15 on 2013-09-11
> **Lars Noodén said:**
> It looks like there are two things going on here.  One is domain name registration and the other is hosting.  From looking at HostMonster's web site very, very briefly it looks like they bundle the two for the first year for $5 a month or something like that.  

You can easily provide your own hosting, but DNS is something you get as part of registering a domain name.  If you are unsatisfied with HostMonster's DNS costs, what you can do is to transfer the domain over to another registrar.  In doing so you will have to pay for another year, but that will add to the existing months you have left on that domain.  It's a two or three step process which your new registrar can help you with.  It will require some cooperation from your old registrar to free up your domain name in such a way that it can be *safely* transfered, but unless they are scammers that is not likely to be a problem either.

In general it is considered important to register your domain(s) with a different registrar than where you are hosting.  If they have both, then there is too little room for negotiation when things turn bad.

What register do you recommend as hostmonster doesn't give you access to add dns records at all they told me i have to point them to my own nameservers in order to add a records in

---

### Post by Lars Noodén on 2013-09-12
You'll have to do a bit of searching to find which registrars are best.  There are a lot of good ones and a lot of bad ones.  I've used Gandi in the past, but that was many years ago when I last did comparison shopping and prices have changed since then.  You should be able to find a lot of reviews, like this one from last year:
[http://lifehacker.com/5943452/five-best-domain-name-registrars](http://lifehacker.com/5943452/five-best-domain-name-registrars)

You'll notice that it is different than from a few years ago:
[http://lifehacker.com/5683682/five-best-domain-name-registrars](http://lifehacker.com/5683682/five-best-domain-name-registrars)

Check for things like being able to transfer to another registrar and having the domain actually registered in your name.  If things look dodgy, then they probably are.  There are scams out there which try to get you to sign over actual ownership of the domain.  Then you're stuck.  But there are good ones out there, too.

Again, even if the registrar is good and you register your domain name there, use another company for actual hosting or do hosting yourself.

---

### Post by |{urse on 2013-11-29
This is a bit of a necro, BUT hopefully OP took lars' advice, getting locked out of both the registrar and the host at once can be a nightmare, +1 at using a seperate registrar and a seperate host!

---

