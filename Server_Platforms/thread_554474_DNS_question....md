---
title: "DNS question..."
date: 2007-09-19
forum: Server Platforms
---

### Post by CptPicard on 2007-09-19
Hi everyone,

Please educate me a little. I am fairly experienced with Linux in general but pretty inexperienced in running a real-world server, and in particular DNS sometimes mystifies me, as it is pretty much the only service that you just don't need to configure in any sense for your own machines.

Recently I was preparing to change my friend's website (with a .net domain) onto our new dedicated server from a shared host. As I was setting up everything, I set up the DNS zone file  in anticipation of eventually handling the DNS for the domain from the new server. I was expecting that he would have to contact the domain registrar, the previous hosting company or something in order to authorize the switch.

We were quite surprised to see that one day the domain had started to automagically point at the new server, and the new server's DNS server had just taken over just like that, without the old host "putting up a fight" of any kind. The domain was essentially hijacked by the new server, but at least it was *our* server...

I mean seriously, can you just create a new SOA like that :confused:  I'm obviously missing something in the way DNS functions in general...

---

### Post by twistedtwig on 2007-09-19
was the old server running "world wide" DNS, i.e. serving DNS queries to anyone rather than just to the local network?

my guess would be that if it was then it is holding its own DNS record and when you switched it across it started to filter out to the other DNS servers.. .but I am no great DNS person and only got my local dns working recently.

hopefully someone better than me can give a more detailed answer.

---

### Post by CptPicard on 2007-09-19
(I cleared up the wording a bit, it was actually wrong in parts -- the old site was hosted by an ISP and the new server is our own dedicated -- but the essential dilemma remains...)

Yes, this is the authoritative DNS server for the domain... and this filtering out to the other servers is what has apparently been happening, but I think this is just weird as it would mean that you could start stealing other people's .net domains by just simply creating your own DNS server to compete with the existing one... :)

---

### Post by twistedtwig on 2007-09-19
Yes that does sound werid... If someone else was hosting your domain then they would "presumably" be the only authorized people to have the DNS record (at least be where it points to).  When I have changed from one provider to another I had to go through an authorization process of saying it is now possible to be moved, then say who it will be moving to.

don't know if digg 'ing the domain might help?  (am only just reading up on dig so I don't know the ins and outs of it yet).

---

### Post by CptPicard on 2007-09-19
Checking the whois info, the domain registrar that is the ISP that used to host the old site is still the registrar and the technical and billing contact... but nameservers have switched nicely over to the new server, without any notice from the ISP, and "last updated" is around beginning of August when we did all of this :)

I honestly don't even understand how the new server's records have been "leaking" out into the wild... how would anyone know where to go look for them? The same new server does host the records for another domain... so... do nameservers request *everything* in some other nameserver's zone files, just in case there is a new domain to be handled and diffused forward?

---

### Post by twistedtwig on 2007-09-19
don't think thats the case.... but.. well.. it seems really odd doesn't it.

I would contact the ISP they may have a bug in their system that means other "not so nice people" could steal DNS records.

Have you tried resolving it from outside your network, i.e. it deffiently uses a different name server.  err dig @a.root-server.com yourdomain.com or something along those lines should check that I think. (sorry if I am saying really obvious stuff)

---

### Post by CptPicard on 2007-09-19
I'm not a dig expert either, but it seems like querying .net root servers doesn't return a proper answer section... however, the answer section I *do* get gets the value from my own local ADSL ISP's nameservers, which means I'm not seeing just an artefact of some own configuration issue... besides, the whois information is pretty blunt about the authoritative nameserver for the domain, and that IP very much belongs to our new dedicated server :)

I would be really surprised if they had a bug that just hands over a domain whenever some other server starts to claim it as its own, they are one of the biggest hosting companies in Europe...

---

### Post by twistedtwig on 2007-09-19
lol... well I am stumped... No idea how you could have got it without there being some contact with the ISP.

would be interested to see if anyone else has some ideas though.

GL

---

### Post by jenson on 2007-09-19
Hi guys,

I'm not sure what is the actual problem but maybe can try to help a bit?

What I understand is, when you initially purchase a domain name, and if the domain name control is in your hands, and you can simply point it from your domain control panel or whatever you might want to call it, and point it to the main and alternative DNS server of your choice, then they will automatically be redirected to your new server and everything should be resolved not later than 72 hours (unless network really congested, which is very unlikely), and you are NOT stealing domain from anyone, since initially you are the "owner" of the domain, as you purchase it or the ISP give you as a free bundle when you get something from them, for example, hosting package, or server hosting and etc.

Does what I just said clarify things a bit? As I don't know what's your actual problem, so I might be uttering rubbish here if it doesn't make sense to you =) and please pardon me for my poor English.

Regards,
Jenson

---

### Post by twistedtwig on 2007-09-19
oh that could make sense you know.

---

### Post by CptPicard on 2007-09-20
Nope, it doesn't, as I've specifically said that we have not done anything to authorize the switch, and this is exactly what does not make sense to me :)

---

### Post by twistedtwig on 2007-09-20
I don't think he meant that.

As I understand it it could be that you have always been a alternate DNS so when it was on the old server it was using it there. and when you took the zone files across that updated the ISP.

just guessing mind

---

### Post by CptPicard on 2007-09-20
Hmm... ok. Well, that's not possible anyway, the new server should be completely strange to the ISP, as we haven't told anything about it to the ISP and the new server is completely elsewhere...

---

### Post by gmbizzle on 2007-09-20
Sorry if I missed anything, but I understand that you setup your own dns server for your domain, and without authorizing the switch, the domain resolved to the new server. Assuming that I have that correct, the only way I can see this working is if you only viewed the domain locally, as I would think that anything setup locally would override a remote dns. If that's not the case, then I really have no idea. I'd think that the registrar still has the ISP's DNS server in their records

---

### Post by CptPicard on 2007-09-20
Well.. that's my assumption too.. thank you for confirming it :) However it does not match reality :D

---

### Post by MJN on 2007-09-20
If you posted your domain (sorry if I missed it) we would be able to look at how the domain is configured from the perspective of the rest of the world - I suspect the symptoms you have seen are down to your local position. Also include the authoritive name servers that existed before you made the switch (intentionally or otherwise).
 
Anything else is just stabbing in the dark - DNS interrogation is by definition very simple, but without knowing the domain we're relying on nothing more than crystal balls! ;)
 
Mathew

---

### Post by CptPicard on 2007-09-20
Hmmm... ok, I suppose giving the information out is not harmful :) The domain in question is siuntio.net, and its current nameservers are ns1.voittoporukka.fi and ns2.voittoporukka.fi. All are on the same box (the "dedicated server" I've been talking of) which has IPs 66.197.169.85, .86. "Voittoporukka.fi" is another domain we've been hosting on this machine for years.

I would be very, very surprised if anyone outside of my location, my friend's location or another server's location (which is in France) got the "old" result that the domain siuntio.net still points to the old webspace at Active 24 :)

---

### Post by MJN on 2007-09-20
Somebody must have actioned the update to the .net zone, I suspect Active24 (as the domain's tag holder). DNS doesn't allow usurper authority over domains - the inherent hierarchy requires the parent domains to be amended and in this case it can only be done by the .net zone admins at the requested of registrars.
 
Without knowing exactly what you and your friend did (and how) it's not really possible to pinpoint exactly at what stage this happened but suffice to say you can't just set up a new DNS server with 'someone elses' zone and make it authoritive to the rest of the world.
 
Bear in mind that the servers listed in whois are not necessarilly those listed in the .net zone (they should be of course but there can be mismatches). Hence, given the .net zone updated at some stage as well as the whois info then, given only Active24 can update the whois, it is a safe bet to assume it is they that made the change - drop them a line to enquire when/why and find out what you did that triggered this action (probably via a web configuration tool of theirs).
 
Mathew

---

### Post by CptPicard on 2007-09-20
Okay, thanks. Getting someone more knowledgeable than me to confirm something like this to me was pretty much what I was after -- I hate it when I don't quite understand what is going on ;)

My hunch is that somehow Active24 has been just doing this on their own, as certainly I have not been using any control panels to authorize anything and my friend -- to whom this domain belongs to -- is not technical enough to. Now the mystery remains how the zone info has been just leaking out into the outside world so that Active24 *knows* to take action... :)

---

### Post by MJN on 2007-09-20
> **CptPicard said:**
> Now the mystery remains how the zone info has been just leaking out into the outside world so that Active24 *knows* to take action... :)
 
That's an assumption too far - despite how it may be looking that's not how it works... Send Active24 an e-mail as I'm sure they'd be able to pinpoint the trigger that made the change (and then I bet you'll say 'ah yes... that makes sense'). Oh, and do tell the rest of us so the mystery can be put to bed!
 
Mathew

---

