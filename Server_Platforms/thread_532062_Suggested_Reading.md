---
title: "Suggested Reading"
date: 2007-08-22
forum: Server Platforms
---

### Post by Linuturk on 2007-08-22
I'm looking to setup a server at my home to handle many tasks, including but not limited to:

LDAP
DHCP
DNS
iptables 
LAMP
File Server
Samba
Print Services
rtorrent
Mail

I basically want to setup a complete network running from one box to handle my other computer's data and get some experience in Enterprise level Linux domain administration.

I'm looking for some reading that does several things:

a) Explain the broader concepts behind these services, such as how postfix interacts with the DNS, and my domain name registrar, how to redirect /home directories using LDAP, and integrating these things with a mix of Windows and Linux clients. Remote access, with X forwarding (on Windows and Linux), and the many other interactions and things you can do with the collection of apps I've listed.

b) help make sure my domain is secure, and running as efficiently as possible.

c) give instructions that doesn't rely on a specific distribution. (I'm thinking of going Debian Stable)

I would like recommendations on reading materials that will help me accomplish these goals. I prefer physical books.

---

### Post by Mr. C. on 2007-08-22
This is a good amount of learning, and I like the way you want to approach this.

I *highly* recommend the **Linux Administration Handbook**, and possibly the  more Unix generic **Unix System Administration Handbook** by Evi Nemeth, Snyder, Seebass, Hein, published by Prentice Hall.  The authors are well-known experts in the field.  I used their books for the courses I taught not long ago.  Here's my online materials if you have any interest - they overview the books to some degree, and have practical lab-lessons for learning the fundamentals:

[http://cis68c1.mikecappella.com](http://cis68c1.mikecappella.com)
[http://cis68c2.mikecappella.com](http://cis68c2.mikecappella.com)

With the book(s), and the online labs/homework, you should be able to setup the standard services, and work towards the others (LDAP, mail server, apache, etc.).  This was too much material to cover in 1 quarter, so I cut the more difficult, complex services.

MrC

---

### Post by Linuturk on 2007-08-24
Thank you for the recommendations. I'm looking into them now.

Do you happen to be anywhere near Florida?

---

### Post by Mr. C. on 2007-08-24
You're welcome.

If you consider 3000 miles west nearby! :-)

MrC

---

