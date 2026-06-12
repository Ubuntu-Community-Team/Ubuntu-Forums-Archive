---
title: "cloud based x.509 certificate authority"
date: 2016-09-19
forum: Server Platforms
---

### Post by Vegan on 2016-09-19
Azure etc are stuffed to the gills with virtual machines

So considering the problems with current x.509 shops maybe my business idea can find some action?

LAMP has lots of hats for more rabbits so why not leverage MySQL for some new ideas? Clients are nothing but a row in a database and a cron task can check to see who needs to be spammed to renew their account etc

seems to be not much to code up with PHP or BASH

making certificates is not rocket science but the idea was to make my server an authority server so my appliances need to be secure as possible

---

### Post by QIII on 2016-09-19
Hello!

Is there a support request here, or is this a conversation starter?

---

### Post by Vegan on 2016-09-19
more of trying to figure out what all i need to do to get a service up and running

the hardest part, is becoming an "authority"

---

### Post by MAFoElffen on 2016-09-20
Most people forget that there is another important piece to this... a "certificate," as most refer, is short for "trusted certificate", which means that is was verified by a trusted source. That trusted source comes from a trusted certificate authority from a trust hierarchy.

Thinking along the Lines of a SysAdmin, one of the the industry standards for CA's is GlobalSign. For more information read this:
[https://www.globalsign.com/en/ssl-information-center/what-are-certification-authorities-trust-hierarchies/](https://www.globalsign.com/en/ssl-information-center/what-are-certification-authorities-trust-hierarchies/) 

There are many cert stores, but the trick is to become known as being "trusted." I often see web ad's for cheap ssl certs from sources I've never heard of before, but that does not guaranty that they will make it through a trusted CA store in the hierrarchy. Each root CA store has it's own policies on what it takes to become an authority with them (Microsoft, Apple, Mozilla, Opera, etc.). What deters most people is the cost and auditing requirements.

---

### Post by Vegan on 2016-09-20
i have considered this mostly for benefit of smaller operations who may not have the coin for dealing with the overhead of a fortune 500 shop

---

### Post by Habitual on 2016-09-20
> **Vegan said:**
> more of trying to figure out what all i need to do to get a service up and running

the hardest part, is becoming an "authority"
Have you seen [Becoming a X.509 Certificate Authority]("http://www.davidpashley.com/articles/becoming-a-x-509-certificate-authority/") ?
I can't vouch as I haven't read/tried it but it seems thorough.

Hope this helps.

Subscribed with interest.

---

### Post by Vegan on 2016-09-20
Thanks, that page on becoming an authority seems to be rather comprehensive. Which is a good start to learn what all is needed to get the ball rolling.

I hope that some effort will become successful as this will be an interesting venture once it becomes operational

I have noticed some competitors have been broken into by miscreants

---

