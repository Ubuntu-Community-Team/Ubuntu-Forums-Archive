---
title: "Feature Development Marketplace"
date: 2008-06-11
forum: Ubuntu Brainstorm
---

### Post by ikarus2k on 2008-06-11
Ubuntu, could you please set up a marketplace for developers?

There are features that aren't necessarily of general interest (i.e. Banshee Watch Folders), or it takes long to implement them. I can't afford to hire somebody to add them, but maybe somebody else would like to have them too, and chip in. This would be advantageous for both developers (who get paid) and users (who get their features faster implemented).

How this might work:
I want *Banshee Watch Folders*, thus I create a Request/Task for this. Mandatory, I have to add 5$ to start this off. An interested developer sees the request and bids for it ("I'll do it. It will take 2 days and I'll need 40$ for this"). Another dev might have a better bid. 
Here I need help, should it be somehow moderated (by the request starter, or highest bidder?), or the first one to complete the request should get the accumulated money (this would create duplicate work).

---

### Post by olskar on 2008-06-11
> **ikarus2k said:**
> Ubuntu, could you please set up a marketplace for developers?

There are features that aren't necessarily of general interest (i.e. Banshee Watch Folders), or it takes long to implement them. I can't afford to hire somebody to add them, but maybe somebody else would like to have them too, and chip in. This would be advantageous for both developers (who get paid) and users (who get their features faster implemented).

How this might work:
I want *Banshee Watch Folders*, thus I create a Request/Task for this. Mandatory, I have to add 5$ to start this off. An interested developer sees the request and bids for it ("I'll do it. It will take 2 days and I'll need 40$ for this"). Another dev might have a better bid. 
Here I need help, should it be somehow moderated (by the request starter, or highest bidder?), or the first one to complete the request should get the accumulated money (this would create duplicate work).

First one to complete the request is not a very good idea since, as you say, that creates dublicate work

---

### Post by smartboyathome on 2008-06-11
This used to be implimented in launchpad (maybe it still is), though I haven't seen it used for a while.

---

### Post by ikarus2k on 2008-06-11
Do you know why the service was closed? If it wasn't closed, how can one access it?

Please elaborate on your post.

---

### Post by smartboyathome on 2008-06-11
I can't, it is just something I picked up from a similar topic on the same subject. I suggest looking around this forum for the topic.

---

### Post by bruce89 on 2008-06-11
Ubuntu (Canonical) does very little (no) development on upstream projects, so I don't see why Ubuntu would do this.

A GNOME git server would be interesting however (or some kind of DVCS).

---

### Post by nitePhyyre on 2008-07-15
If they don't do upstream work, what exactly DO they do?

---

### Post by smartboyathome on 2008-07-15
> **nitePhyyre said:**
> If they don't do upstream work, what exactly DO they do?

They create a distribution of the latest packages and then bugfix them to make them more stable.

---

### Post by nitePhyyre on 2008-07-16
> **smartboyathome said:**
> They create a distribution of the latest packages and then bugfix them to make them more stable.

> **smartboyathome said:**
> You just don't get Linux, then. Ubuntu is just a "distrobution" (aka distro) of programs compiled on top of the Linux kernel. They don't fix anything themselves usually, but have upstream fix it due to them knowing the code better.

Is "upstream" a fancy term for 3rd party developers? I was under the impression that debian was the upstream for ubuntu cause ubuntu is a derivative. I'm confused a bit by the development process of ubuntu.

Another question, could you give more details on the bug fixes? Like, does that mean that a package can be different for each distro? Do the bug fixes go back upstream or do teams just sit on them?

Does any of that make sense or am i just so far off base that i type gibberish?

Oh and for the topic of this post, duplicate work might not be a bad thing, this way everyone who put in money could vote for the best implementation.  Let's say once a dev finishes a request, everyone else gets a week to get their implentation in. Sort of like the way yahoo answers works. Sure it makes the system a litte more cutthroat, but it might drive better features.

---

### Post by smartboyathome on 2008-07-17
> **nitePhyyre said:**
> Is "upstream" a fancy term for 3rd party developers? I was under the impression that debian was the upstream for ubuntu cause ubuntu is a derivative. I'm confused a bit by the development process of ubuntu.

Debian is "upstream" from Ubuntu, but Ubuntu also has projects which are farther upstream than that. Upstream is pretty much a fancy term for 3rd party developers, but ones that work on the code itself in order for a bug to be fixed in all distros. When I say, ie, an idea would have to be done by GNOME, I mean that Ubuntu doesn't impliment that type of stuff, and that instead you should talk to GNOME to get it implimented.

> **nitePhyyre said:**
> Another question, could you give more details on the bug fixes? Like, does that mean that a package can be different for each distro? Do the bug fixes go back upstream or do teams just sit on them?

A package can be different for each distro, but Ubuntu tries not to do that to a point, because they try to share the fixes with each distro. If they didn't, the packages would become basically a fork of the package itself, which Ubuntu is trying not to do.

> **nitePhyyre said:**
> Does any of that make sense or am i just so far off base that i type gibberish?

It makes sense. :)

> **nitePhyyre said:**
> Oh and for the topic of this post, duplicate work might not be a bad thing, this way everyone who put in money could vote for the best implementation.  Let's say once a dev finishes a request, everyone else gets a week to get their implentation in. Sort of like the way yahoo answers works. Sure it makes the system a litte more cutthroat, but it might drive better features.

This would cause too much strain, I think. If a developer that has the skills to do it doesn't find it until 2 days before the code is due, then what would that developer do? I would say if this happens, give the user a choice of exactly how long they want to wait before the code is due.

---

### Post by bruce89 on 2008-07-17
> **smartboyathome said:**
> They create a distribution of the latest packages and then bugfix them to make them more stable.

Of course, most bugfixes come from upstream.

---

### Post by smartboyathome on 2008-07-17
> **bruce89 said:**
> Of course, most bugfixes come from upstream.

What I meant was that the bugs usually get found upstream and then reported upstream to be fixed. Sorry for the confusion. :(

---

