---
title: "Delta Debian ....A possibility ?"
date: 2012-01-29
forum: The Cafe
---

### Post by linuxyogi on 2012-01-29
I recently was using Fedora 16. One great thing about Fedora is the delta rpm package management. I was 

wondering if something similar can be implemented on Debian/Ubuntu. 

Are people working to bring the feature to debian ?

---

### Post by haqking on 2012-01-29
> **linuxyogi said:**
> I recently was using Fedora 16. One great thing about Fedora is the delta rpm package management. I was 

wondering if something similar can be implemented on Debian/Ubuntu. 

Are people working to bring the feature to debian ?

Ubuntu is not debian though obviously

[http://debdelta.debian.net/](http://debdelta.debian.net/)

---

### Post by MadCow108 on 2012-01-29
debian has delta upgrade since ages and it works great, its just ubuntu thats really slow on adoption.
there were some efforts last cycle but they died away.
The lack of pdiff index updates which debian has since years would also make it a lot less useful.

---

### Post by grahammechanical on 2012-01-29
For those of us, like me, who have no idea of what this thread is about and who thought, as I did, that it was about Debian using the Redhat rpm file format for its packages, there is this link:

[http://debdelta.debian.net/]("http://debdelta.debian.net/")

It seems, to me, that this is another example of a lot of effort being put into Linux by just one person. Do we appreciate all this work?

If this were fully developed and implemented then it would be very useful for those with dial-up modems.

I have just found this:

[http://manpages.ubuntu.com/manpages/precise/man1/debdelta.1.html]("http://manpages.ubuntu.com/manpages/precise/man1/debdelta.1.html")

Regards.

---

### Post by linuxyogi on 2012-01-29
> **MadCow108 said:**
> debian has delta upgrade since ages and it works great, its just ubuntu thats really slow on adoption.
there were some efforts last cycle but they died away.
The lack of pdiff index updates which debian has since years would also make it a lot less useful.

I should have asked  Delta Debian under Ubuntu....A possibility ?

---

### Post by hhh on 2012-01-29
I don't know, is it?

[http://packages.ubuntu.com/search?searchon=names&keywords=debdelta](http://packages.ubuntu.com/search?searchon=names&keywords=debdelta)

---

### Post by MadCow108 on 2012-01-29
> **hhh said:**
> I don't know, is it?

[http://packages.ubuntu.com/search?searchon=names&keywords=debdelta](http://packages.ubuntu.com/search?searchon=names&keywords=debdelta)

it won't work because there is no server holding ubuntu deltas.

---

### Post by hhh on 2012-01-29
> **MadCow108 said:**
> it won't work because there is no server holding ubuntu deltas.
Then how come I was just able to download the deb?...

[http://packages.ubuntu.com/oneiric/i386/debdelta/download](http://packages.ubuntu.com/oneiric/i386/debdelta/download)
[http://packages.ubuntu.com/oneiric/amd64/debdelta/download](http://packages.ubuntu.com/oneiric/amd64/debdelta/download)

---

### Post by FuturePilot on 2012-01-29
> **hhh said:**
> Then how come I was just able to download the deb?...

[http://packages.ubuntu.com/oneiric/i386/debdelta/download](http://packages.ubuntu.com/oneiric/i386/debdelta/download)
[http://packages.ubuntu.com/oneiric/amd64/debdelta/download](http://packages.ubuntu.com/oneiric/amd64/debdelta/download)

Sure the debdelta package is available but it will do absolutely nothing if installed because there are no Ubuntu delta packages.

---

### Post by Lucradia on 2012-01-29
> **FuturePilot said:**
> Sure the debdelta package is available but it will do absolutely nothing if installed because there are no Ubuntu delta packages.

I wish the like button was still around.

---

### Post by Dangertux on 2012-01-29
You could always try using the Debian stable repos, but...That might end up making your buntu not so buntu anymore ;-)

---

### Post by Lucradia on 2012-01-29
> **Dangertux said:**
> You could always try using the Debian stable repos, but...That might end up making your buntu not so buntu anymore ;-)

It also may break ubuntu actually. Some things in ubuntu can't be used proper in Debian, and vice versa due to the changes between the versioning system and other things.

---

### Post by hhh on 2012-01-29
> **Lucradia said:**
> I wish the like button was still around.
Sorry for making a mistake.

Why does Ubuntu have unusable binaries in their repository?

-This has been a feature request since 2006...
[http://askubuntu.com/questions/10167/will-11-04-include-delta-updates](http://askubuntu.com/questions/10167/will-11-04-include-delta-updates)

---

### Post by FuturePilot on 2012-01-30
> **hhh said:**
> Sorry for making a mistake.

Why does Ubuntu have unusable binaries in their repository?

-This has been a feature request since 2006...
[http://askubuntu.com/questions/10167/will-11-04-include-delta-updates](http://askubuntu.com/questions/10167/will-11-04-include-delta-updates)

Probably because it just got pulled in during the sync with Debian.

---

