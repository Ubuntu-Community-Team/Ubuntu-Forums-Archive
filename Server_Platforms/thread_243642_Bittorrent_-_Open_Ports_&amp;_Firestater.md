---
title: "Bittorrent - Open Ports &amp; Firestater"
date: 2006-08-25
forum: Server Platforms
---

### Post by nerm on 2006-08-25
Hello All,

I'm a a total newbie to Ubuntu and have for the first time forayed into the murky world of Bittorent, to get hold of TV programmes that I have missed.

I have installed Azureus and configured my router to forward TCP and UDP packets to my machine when directed to the port I have dedicated for Bittorrent data in Azureus e.g. 66666. 

I also set Firestarter to allow inbound traffic from 'anyone' on port 66666, (by adding a rule on the 'Policy' tab) so Azureus can get my Bittorrent data.

Everything worked fine and I got a copy of the show I was after.

However, by leaving this port (66666) 'open' to incoming traffic am I setting myself up for trouble?

I noticed that Firestarter was blocking lots of attempted connections from lots of different IP addresses through this port and my network monitor was blinking (the packets arriving from those hosts I presume). Is this normal behaviour, or am I right to worry?

Apologies if I'm going over old ground, feel free to tell me off.

Many Thanks

---

### Post by skymt on 2006-08-28
Perfectly normal. Everyone gets lots of junk packets when they're on Bittorrent. Firestarter, in my experience, serves mainly to freak out people who don't know any better (including me one memorable time that I won't get into).

The only risk of opening a port for BT is a hole in the Bittorrent client you use. This is unlikely (I've never heard of it), but possible. It's not much riskier than surfing with Firefox or chatting with Gaim. A hole in either one could be used to crack your system, but it's very unlikely.

---

### Post by nerm on 2006-08-31
Thanks. It's good to have someone provide some reassuring info.

---

