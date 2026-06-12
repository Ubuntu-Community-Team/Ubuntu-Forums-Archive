---
title: "docs for dancer-services?"
date: 2007-11-23
forum: Server Platforms
---

### Post by wolfear on 2007-11-23
Hey folks,

Does anyone know whare I can find a decent set of docs for configuring the dancer-services for dancer-ircd?
I have been googleing for hours and can't seem to find anything.

I set everything up by following this tutorial (which I found through google):
[http://knightlust.blogspot.com/2007/08/setting-up-dancer-ircd-in-kubuntu.html]("http://knightlust.blogspot.com/2007/08/setting-up-dancer-ircd-in-kubuntu.html")
I have the dancer server running fine and I can connect locally with no problems.
But I'm at a loss as to why none of the services are working.
Any help is greatly appreciated.

---

### Post by bmathis on 2007-11-23
umm... sourceforge project pages? [http://dancer.sourceforge.net/#docs]("http://dancer.sourceforge.net/#docs")

---

### Post by wolfear on 2007-11-23
Thanks for the reply.
I checked those earlier..they are way out of date and don't mention dancer services at all that I could find.

I have the ircd up and running just fine, just can't find anything related to the dancer services (nickserv,opserv, etc).
Guess if all else fails, I'll try ircd-hybrid and hybserv again.

---

### Post by teledyn on 2008-01-07
I have the same symptoms, a working ircd, zero services, and no clues in either the dancer logs -- i fear we may be SOL on this one.  I'm hoping to find the sources somewhere and maybe there's some clues in those, and for the smarty-pants who thought it was as easy as a link on dancer.sf.net, heh, that's not the IRCD Dance, it's the IRC *bot* called Dancer ;)

so ... is there any other IRCD that is recommended by Ubuntu?  How did this package get into Ubuntu if everything is supposedly checked by a package maintainer?  I love some of the docs, they'll say to check the password in services N when that param has no password, or they'll give a long list of examples and say "these are for Hybrid and do not work with Dancer" :lolflag:

---

### Post by wolfear on 2008-01-08
I finally eneded up installing Unreal ircd along with Anope for services

Luckily it was primarily just a learning project on an old system I use for "playing" because I learned there is a monsterous lack of documentation and if asking for help from anyone connected with an ircd, you will probably get very little but an "if you have to ask then you don't need to running one"  attitude, although there were a few exceptions.

Be prepared to spend a LOT of time setting up an icrd and getting the services configured properly.

---

