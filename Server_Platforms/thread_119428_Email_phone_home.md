---
title: "Email phone home"
date: 2006-01-19
forum: Server Platforms
---

### Post by ollyshaw on 2006-01-19
Hi everyone,

In the last couple of days there appears to something sending emails in groups of 4 about 3 times a day. I have currently blocked port 25 for all but access to my proper mail server.

I have isolated an example of the problem from /var/log/messages now that the firewall is droppng these packets.

Any help of ideas are much appriciated,

Olly

---

### Post by ollyshaw on 2006-01-19
Problem solved, the mail was attempting to send via my smtp google account. 

I dont know how i set this in postfix as i cant now unset this!

I have done a dpkg-reconfigure postfix and I have selected local only.

Can anyone tell me what happens now if i try to mail an external address using postfix.

Sorry for the false alarm,

Olly

---

