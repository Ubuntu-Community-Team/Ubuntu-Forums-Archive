---
title: "[SOLVED] Bind9 and a mail problem"
date: 2008-02-16
forum: Server Platforms
---

### Post by cornflake000 on 2008-02-16
Greetings....

I have a new Bind9 server running on Ubuntu-server Gusty.  It is running great for everything... except the mail is not arriving when sent from non local sources.

Here's the general setup of my network....

MailserverX runs 5 domains on postfix. no probs
- it has ns1.bigtime.com and ns2.bigtime.com for DNS

I decided to try my hand at my own SOA... so I constructed:

ns1.dinkeyserver.com which runs 1 domain
- it uses ns1.dinkeyserver.com as Primary and ns1.bigtime.com for Slave

Everything pings, digs, nslookups, tracerts... my primary resolves www, subdomains, in-addrs, PTRs, the slave is receiving, my logs show no errors.

BUT....  the mail that is sent to MailserverX for the zone on the new ns1.dinkeyserver  is not arriving.  There is no log on my mailserver showing a bounce or reject; it just doesn't get there.   The senders get a delay notice then a 'can't find' error.

Again, anyone can get to the websites without a hitch.  Anyone can send mail as long as it's not to the domain on my new ns.  Sorry for the aliases above I just thought they were more explanatory.  I think my configs are ok... or are they?  If I need to pass them to you, I will.  Maybe the problem is external....

I would appreciate any insights.  I'm kinda stumped....

martin

---

### Post by Brazen on 2008-02-16
You need to check your mx record.  The sending machine should be able to find an mx record for your mail domain.  For instance, my company email is [email]brazen@company.com[/email].  If I run 'host company.com' from my home computer it returns:

company.com mail is handled by 10 mail1.company.com.

now mail1.company.com is the actual dns name of the mail server ( the number 10 is the "weight" in case you have redundant mail servers ).  So if I ping mail1.company.com then I get the public ip address of the mail server.

Also, sorry but I only have time to skim your message, so I could be way off, but the mx record is something to check.

---

### Post by cornflake000 on 2008-02-17
Thanks for the comeback...

It seems the MX is ok... dig shows it as ok from here but a few minutes ago I noticed that if I do a dig from a site out of this area like on a web site across the country, it shows the wrong IP.  It' an IP that is mine but not the correct one.  My server has the correct information and when I do the dig from this location, it comes out with the correct IP.

This is a bit strange to me....  any ideas???

m

---

### Post by faulkes on 2008-02-17
> **cornflake000 said:**
> Thanks for the comeback...

It seems the MX is ok... dig shows it as ok from here but a few minutes ago I noticed that if I do a dig from a site out of this area like on a web site across the country, it shows the wrong IP.  It' an IP that is mine but not the correct one.  My server has the correct information and when I do the dig from this location, it comes out with the correct IP.

This is a bit strange to me....  any ideas???

m

There are two possible items I can think of offhand.

1.  That when you updated your bind zone file, you did not update the zone serial.

2.  That propagation of your zone has not yet reached all the root servers.

If you can provide the domain name to which you are having issues with I may be able to provide additional assistance.  If you are concerned about privacy, you can certainly send it to me in PM and I will treat it in confidence (although I will reply to this thread with any findings).

Faulkes

---

### Post by faulkes on 2008-02-17
From dig:
```

;; QUESTION SECTION:
;xxxxxxxx.com.                 IN      A

;; ANSWER SECTION:
xxxxxxxx.com.          259200  IN      A      yyy.yyy.yyy.yyy

```

So, your domain IP address appears to be properly setup

From dig:
```

;; QUESTION SECTION:
;xxxxxxxx.com.                 IN      MX

;; AUTHORITY SECTION:
xxxxxxxx.com.          10800   IN      SOA     xxxxxxxx.com.

```

The MX record for your domain does not appear to exist.

From dig:
```

;; QUESTION SECTION:
;pop3.xxxxxxxx.com.            IN      MX

;; ANSWER SECTION:
pop3.xxxxxxxx.com.     259200  IN      MX      10 pop3.xxxxxxxx.com.

```

The MX record for your domain appears to be incorrectly pointed.

xxxxxxxx.com should have it's MX 10 record as pop3.xxxxxxxx.com

pop3.xxxxxxxx.com should not have an MX record.

Step 1 would be to fix the MX record and the go from there.

Faulkes

---

### Post by DDuong on 2008-02-17
Can you also list your zone file please?  If you don't feel too comfortable in doing that, you can replace your hostname with something else etc...

---

### Post by cornflake000 on 2008-02-17
Faulkes.......

THAT WAS IT!  Yes!!

Details details..... I love'm!

They can be illusive at times but then... that's the game!

Thank you sir!

martin t


.... now, how do I mark this SOLVED!!!!

---

### Post by faulkes on 2008-02-17
> **cornflake000 said:**
> 

.... now, how do I mark this SOLVED!!!!

Under "Thread Tools" towards the upper right, click the down arrow and select "Mark this thread as solved".

As well, within the posts, you will see next to you where you have you the "Edit" and "Quote" reply areas, a small medal like icon, you can click that to give thanks to invidiuals who contributed to solving your problem.

Faulkes

---

