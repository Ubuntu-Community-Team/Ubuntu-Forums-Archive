---
title: "Complicated postfix configuration --Need some help"
date: 2008-09-13
forum: Server Platforms
---

### Post by ScottRobinson on 2008-09-13
Ok i have been using postfix at my last couple gigs as a geo-router for mail. Meaning i have a diverse backend exchange environment with one central incoming port. Postfix then routes the mail based on location (via ldap lookup) to the various servers. This new gig though is asking for some things that i haven't dealth with before so i wanted to run them past the group for some help.

I need postfix to rewite all of the users subdomains into a main domain for incoming and outgoing mail. Meaning:

user@domain.com  --> user@division1.domain.com
user@domain.com  <-- user@division1.domain.com

Now for the extra interesting part, they want all of the lookups to happen from ldap. No problem, except that the environement is huge and they want everything to come from a mysql database. I in the past have just feed ldap information into flat files for postfix to read now i need to feed and update that information into a mysql db.

So i am reading though all of the manuals and most of what i want to be done can be but i don't see anything combining all of these things like feeding mysql ldap info which in turn feeds postfix.

Any help would be appreciated, i am trying to learn all of this as i go and have the basics of postfix down, now i just need some help with the more complicated stuff.


Thanks
Scott

---

### Post by windependence on 2008-09-13
Take a look at this:

[http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-and-dovecot-on-ubuntu8.04](http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-and-dovecot-on-ubuntu8.04)

Maybe not exactly what you want but might give you some ideas.

-Tim

---

### Post by ScottRobinson on 2008-09-13
that is the kind of things i have been reading That gives mention on how to do direct ldap lookups. Due to the size of the company and the message traffic being processed this delay for ldap lookup of each mail message would cause a severe backlog. This is the reasoning behind putting it on mysql. Basically i want to do the lookups from mysql and just populate the tables once every 30 minutes to an hour with fresh ldap data.

Scott

---

