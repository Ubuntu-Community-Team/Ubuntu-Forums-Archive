---
title: "Google SMTP STARTTLS Troubles (Ubuntu Server 10.04)"
date: 2013-04-23
forum: Server Platforms
---

### Post by Valkerie on 2013-04-23
This is driving me crazy. I've been working on this when I get the sudden urge and just today I run into yet another problem. This time it is a matter of SMTP. Running solo I would get errors reaching the other server. My test was my gmail account and if I could reach it. I don't have a problem recieving mail at all, but sending is another story. My errors would be...

Pushed out of my logs. Damn. Alright basically I would get things like "no route to host" or "connection timed out" YET... when I resolved the FQDN's and pinged the IP's I didn't have a problem finding the server. Hmm. My server must be hitting google's server, but not the service, or is it?

Yada yada yada...

Wait... no one else on other domains recieved their emails. Strange. Ok it's a local problem. I'm pretty sure the problem resides in postfix. I decided to go the route of using google's SMTP server for outbound messages. I configure postfix, am able to reach the server, can reach the service, AND... more errors. This time I'm having STARTTLS errors, more specifically postfix just does not want to use a STARTTLS command... and I'm a bit frizzled tonight. So I'm going to tap out for the night and see if a nice dream won't bring me the answer. In the mean time I'd like to ask any knowledgeable person on this forum about postfix, google SMTP, and STARTTLS.

I am literally RIGHT THERE at being finished. Just a little more and I have a fully functional service. Here's the message my server bounces me back with on every message:


host smtp.gmail.com[74.125.129.108] said: 530 5.7.0     Must issue a STARTTLS command first. ak1sm28311234pbc.10 - gsmtp (in reply     to MAIL FROM command)

Any takers?

---

### Post by schragge on 2013-04-23
Gmail uses port 587 for STARTTLS, ensure that you are using the right port. See [here](http://stackoverflow.com/a/11049483) for how to check gmail connection by hand.

---

