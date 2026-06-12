---
title: "Open source based alternatives for Exchange"
date: 2011-06-06
forum: Server Platforms
---

### Post by tapi0n on 2011-06-06
This is driving me crazy. 

I'm looking for an on-site mailserver for a fictional company of about 2000 employees, that number could increase but not drastically.

I've found an interesting alternative in [Kerio Connect]("http://www.kerio.com/connect") because of its functionalities. Also because with this I could use [Kerio Operator]("http://www.kerio.com/operator"), which would would be nice since there's need for VoIp.

Now this only seems available for small businesses. When looking for open source based mail server alternatives for exchange, for large companies, I always end up on an alternative that is available for small to medium sized companies.

I just can't imagine there not being an alternative for large companies. Or are they really bound to use microsoft?
Or maybe I'm getting it wrong by assuming 2000 employees is considered to be a large company?

---

### Post by Lars Noodén on 2011-06-06
Well, you could set up procmail to randomly lose 30% of [your mail](http://bsdly.blogspot.com/2011/02/problem-isnt-email-its-microsoft.html) or cause other problems...

More constructively, if you are only looking for e-mail, then you have these:
[simta](http://rsug.itd.umich.edu/software/simta/), [Dovecot](http://www.dovecot.org/), [Postfix](http://www.postfix.org/), [Exim](http://www.exim.org/), or [Sendmail](http://www.sendmail.org/)

They can all be used interchangeably.

If you want groupware, then your best bet is [Kolab](http://www.kolab.org/), [Citadel](http://www.citadel.org/) or [OpenGroupware](http://www.opengroupware.org/). Zimbra and Bedework also can be mentioned.

---

### Post by collisionystm on 2011-06-06
> **tapi0n said:**
> This is driving me crazy. 

I'm looking for an on-site mailserver for a fictional company of about 2000 employees, that number could increase but not drastically.

I've found an interesting alternative in [Kerio Connect]("http://www.kerio.com/connect") because of its functionalities. Also because with this I could use [Kerio Operator]("http://www.kerio.com/operator"), which would would be nice since there's need for VoIp.

Now this only seems available for small businesses. When looking for open source based mail server alternatives for exchange, for large companies, I always end up on an alternative that is available for small to medium sized companies.

I just can't imagine there not being an alternative for large companies. Or are they really bound to use microsoft?
Or maybe I'm getting it wrong by assuming 2000 employees is considered to be a large company?


Zimbra or Zentyal. Zentyal says small business, but it has ldap and windows integration ability. If you build it on a good enough server you will be fine. It is so simple a 5 year old could set it up

---

### Post by Lars Noodén on 2011-06-06
> **tapi0n said:**
> 
Or maybe I'm getting it wrong by assuming 2000 employees is considered to be a large company?

That's still usually considered [small to medium](http://www.lib.strath.ac.uk/busweb/guides/smedefine.htm) in the US.

---

### Post by tapi0n on 2011-06-06
Thanks I'll definitely look into the suggested alternatives.

> **Lars Noodén said:**
> That's still usually considered [small to medium]("http://www.lib.strath.ac.uk/busweb/guides/smedefine.htm") in the US.

medium is around 500 over here so I guess that could be a reason :). Do you by any chance have a source that could verify this? (it's for a paper)

Edit: In Belgium you can check various business numbers online. But this is just for Belgian companies. Is there something like that for global companies too?

Edit: I feel like such a stupid, didn't realise you posted a link.

---

### Post by Lars Noodén on 2011-06-07
[EU Definition of micro, small and medium-sized enterprises](http://europa.eu/legislation_summaries/enterprise/business_environment/n26026_en.htm) from 2003.

---

### Post by tapi0n on 2011-06-07
> A medium-sized enterprise is defined as an enterprise which employs  fewer than 250 persons and whose annual turnover does not exceed EUR 50  million or whose annual balance-sheet total does not exceed EUR 43  million.

So I'd say my company is catogarized as a large company?

---

### Post by Lars Noodén on 2011-06-07
> **tapi0n said:**
> So I'd say my company is catogarized as a large company?

Could be.   I couldn't find a recent definition, the EU definition expired back in 2005.  A lot has changed since then.  But as far as the open source technology goes, it is small or medium.  The mail servers can handle a lot compared to MS Exchange, which seems to choke on any test I've chosen to try on it.

---

### Post by tapi0n on 2011-06-07
So what you're saying is. Even though open source distributers say it's for small and medium sized companies, it can always be "stretched" a little and pushed to the limits?

---

