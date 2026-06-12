---
title: "DigitalMe on Ubuntu"
date: 2008-07-17
forum: The Cafe
---

### Post by meneer on 2008-07-17
Just reporting that the Bandit project presented a .deb package for the DigitalMe Identity Selector for xUbuntu. This package installed effortless on my Ubuntu 8.04 system, providing me with the digital wallet for Infocards. So, now I can now create Infocards myself, install managed Infocards from other Identity providers and login to Infocard enabled websites, all from my ubuntu workstation.

The install package can be found on the [DigitalMe download page]("http://code.bandit-project.org/trac/downloads?catfilter=DigitalMe").
There you can also find an install package (.xpi) for the Mozilla Firefox interface to DigitalMe.

More info about Infocard on [Kim Cameron's IdentityBlog]("http://identityblog.com")

This issue was raised earlier in this forum, see [this topic]("http://ubuntuforums.org/showthread.php?t=132403&highlight=infocard").

---

### Post by Redrazor39 on 2008-07-17
I thought this was a free mobileme for ubuntu :(

---

### Post by meneer on 2008-07-19
> **Redrazor39 said:**
> I thought this was a free mobileme for ubuntu :(

Sorry, just a great new development of another kind :)

---

### Post by Mr. Picklesworth on 2008-07-19
Nice to see this happening. With OpenID, this really will make the web a tidier, more connected system. Cardspace kind of confuses me, though. Why does a user want multiple identities to nudge around? Why not unify it all under a single identity?
From my perspective, it's a cool way of authenticating for web sites via one-way encryption (as it should be!), but there's this whole other component that I can't figure out :/

---

### Post by meneer on 2008-07-20
> **Mr. Picklesworth said:**
> Why does a user want multiple identities to nudge around? Why not unify it all under a single identity?

I use different identities for different purposes, just like in the real world. My drivers license allows me to drive a car, my passport to open a bank account, my railway card to travel. All these identities are managed by different bodies. I don't think that one body need to know how I use one of their identities, that's my business.

In the digital world it's just the same. Microsoft Passport failed because one digital identity is just not enough. It's not only about trust in the identity provider, it's about using one measure for one purpose. The great part about infocard is that I can control when to use whichever what identity.

So DigitalMe is really useful. I don't need to use more identities, it's my choice. I control my digital identity.

I can only point to [Kim Cameron's identityblog]("http://identityblog.com"). it's the first site on my netvibes homepage!

---

### Post by Mr. Picklesworth on 2008-07-20
Ah, I get it :)

Thanks, Meneer. One gold star for you!

---

### Post by Bill Day on 2008-08-12
After reading the [New York Times article]("http://www.nytimes.com/2008/08/10/technology/10digi.html?_r=1&em&oref=slogin") on information cards, I think this technology sounds quite interesting and useful.  I have been experimenting a little bit with both digitalme on Ubuntu and Cardspace on the other operating system (XP).  Although there are some interoperability issues, in general it seems to work fine on the few test sites I could find.

My question is whether there are any simple kits, tutorials, howtos, or other guidance on how to set up information card authentication on personal websites using Apache 2.0 and Ubuntu 8.04.  Any ideas?

---

### Post by meneer on 2008-08-22
> **Bill Day said:**
> My question is whether there are any simple kits, tutorials, howtos, or other guidance on how to set up information card authentication on personal websites using Apache 2.0 and Ubuntu 8.04.  Any ideas?

Let me point you to [this video by Kim Cameron]("http://www.identityblog.com/wp-content/images/2007/10/nohttps/nohttps.html") where he demonstrates an infocard relying party in less than 30 lines of code. PHP code that is! Recommended, like all other info on his site. 

There's also a nice book, Understanding Windows CardSpace by Vittorio Bertocci, Garrett Serack, and Caleb Baker. Lots of info.

---

### Post by janfsd on 2009-03-29
This might be a bit old topic, but since I am making a school project about Cardspace, I tried it in Linux. The deb file on the site is old, however it is very easy to use the svn version and compile it, following the instructions in the site.

---

### Post by Bill Day on 2009-04-01
Hmm, I tried the svn version an got it to compile, but it is basically nonfunctional.  It will neither create nor import a card.

---

### Post by janfsd on 2009-04-12
Yes, I stumbled upon the same problem. However the latest stable version might work (which is newer than the ubuntu package).

EDIT: after checking the latest svn version, it works! I can say that the problem wasn't that it didn't create the cards, it just didn't show them.

---

### Post by Bill Day on 2009-04-15
Thanks.  I updated and recompiled, and it seems to work now.

---

### Post by janfsd on 2009-04-23
> **Bill Day said:**
> Thanks.  I updated and recompiled, and it seems to work now.

Does the firefox plugin work for you?

---

### Post by Bill Day on 2009-04-23
Yes, at least with [http://www.bandit-project.org](http://www.bandit-project.org).  I don't know of many other sites I can use to test it.  Another frustration is that DigitalMe does not seem to work with Verisign cards.  Any luck on your end?

---

