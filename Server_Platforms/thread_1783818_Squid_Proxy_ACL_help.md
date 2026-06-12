---
title: "Squid Proxy ACL help"
date: 2011-06-16
forum: Server Platforms
---

### Post by brent1975 on 2011-06-16
Here is what i am trying to do. I am using squid as a cache system for users in the house I am also wanting to use it to filter out the not so good sites for the younger kids,  It appears that there is several different ways to perform this task.

1. is to label a name such as sex, drugs, etc...

2. is to use an actual domain name sex.com, drugs.com

I have seen some examples of people making specific file in the /etc/squid/restricted-sites.acl and /etc/squid/allowed-sites.acl

I would like to set it where everything is open except if the value falls in the list that is provided in /etc/squid/restricted-sites.acl

Also is there a way to use tags in this as well? like for example if I was to use the restricted-sites.acl to add specific domains like sex.com drugs.com can I add tags like sex,drugs,etc?  If so I would like to be able to incorporate both into the one file.

Just to keep the restricted clean and in 1 place and without cluttering up the squid conf file which all the examples I seen have you add all the domains and tag to it.

any suggestions on how I could get this to work? or if it is even possible?

---

### Post by brent1975 on 2011-06-16
Anyone have any examples that I can work off of?

---

### Post by Lars Noodén on 2011-06-17
You're probably looking more for filter software like [Dansguardian](http://dansguardian.org/?page=whatisdg).  However, these attempts at solving social problems with technology are doomed to failure after burning a lot of effort.

---

### Post by i.r.id10t on 2011-06-17
For what I use squid for (kiosks on campus) it is easier to deny access to everything and then allow what I want ...

---

### Post by SeijiSensei on 2011-06-17
You'd have to write dozens and dozens of ACLs to make this work.  I suggest using OpenDNS for name resolution.  You might want to use their "[Family Shield]("http://www.opendns.com/landings/familyshield")" service.

---

### Post by Lars Noodén on 2011-06-17
SeijiSensei, how does FamilyShield / OpenDNS make its money?

---

### Post by SeijiSensei on 2011-06-17
> **Lars Noodén said:**
> SeijiSensei, how does FamilyShield / OpenDNS make its money?

Probably it's cross-subsidized from their [subscription services]("http://www.opendns.com/work").  You'd need to ask them.

---

