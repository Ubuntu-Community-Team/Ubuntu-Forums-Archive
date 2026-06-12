---
title: "Static IP vs. Dyndns.org for Postfix"
date: 2009-03-17
forum: Server Platforms
---

### Post by artheus on 2009-03-17
Hey all!

I've had a lot of trouble these last couple of days, trying to fix my Postfix. And I've gotten alot of answers in different forums about my problems. But a major unsolved question of mine is why my postfix smtp won't send out mails to non-local recievers.
Well. I've gotten some answers that says that the reciever mail servers don't trust smtp-servers with an dynamic ip adresse.
And today I stumbled on to a guy at school, that have got a lot of experience with networking, but none with linux. But he told me about dyndns.org. And he said that dyndns.org should solve my problem with postfix.
I created an account at dyndns.org today, and I configured a ddclient deamon, and my ddns is now working properly.
But still no luck with postfix.
And I spoke on the phone with my ISP today, and they told me that they can't provide me with an static IP adress.

So my question is. Where do I go from here? To get my smtp server working?
I really don't want to rely on any other smtp than my very own.

Cheers,
Artheus

---

### Post by vpsville on 2009-03-17
Well you could rent a small virtual server and install postfix on it.  It would come with a static IP and you could set rDNS and SPF so that your outgoing mail won't be flagged as spam.

You will need a domain name as well but those are super cheap nowadays.

---

### Post by schettj on 2009-03-17
> **artheus said:**
> 
So my question is. Where do I go from here? To get my smtp server working?
I really don't want to rely on any other smtp than my very own.

Yeah, on residential ISPs, you're lucky if they don't block your smtp server. And no, even with dyndns your IP is still dynamic, and you're not trusted (my mail server would reject your mail, for example)

I agree, if you must run your own email server, get a domain name and host it somewhere that offers email, or get a small hosted server somewhere "out there" with a first class static ip.

Or, get an new ISP ;)

---

### Post by volkswagner on 2009-03-17
> **artheus said:**
> .....
I really don't want to rely on any other smtp than my very own.

Cheers,
Artheus

As schettj pointed out, dyndns won't help, as the outside mail servers will still see your IP address.  These residential addresses are on some dirty blacklist somewhere... :(

How much outgoing mail do you anticipate?

To "rely" on your ISP for smtp service, seems they should have a more reliable hardware setup than us folks can afford...LOL

Have you actually received any bounced mail, ie: have you sent mail that was returned with an error number and explanation?  

Is using your ISP's SMTP server forbidden or frowned upon?

If you want to use your own server at home, the only viable solution is to use the SMTP server of your ISP.  Let it be known, if your concern is how the received mail will look to the recipient, it will be addressed from your servers domain not your ISP's address in the "from" field.

---

### Post by windependence on 2009-03-18
You really need a static IP if you are going o run a full blown mail server. You will also need properly set-up PTR (reverse DNS) records so that your mail doesn't get trashed as being spoofed.

No-ip has a reflector solution that may work for some situations. Everyone mentions dyndns, but almost no-one mentions no-ip, which IMHO is better. The mail reflector costs $39.95 per year.

[http://www.no-ip.com/services/managed_mail/inbound_port_25_unblock.html](http://www.no-ip.com/services/managed_mail/inbound_port_25_unblock.html)

-Tim

---

### Post by hyper_ch on 2009-03-19
a simple solution would be to relay the outgoing email from your server through your ISP. You will then require an email account at your isp and you just tell postfix to sned outgoing email through your ISP - that way it will be ok

---

