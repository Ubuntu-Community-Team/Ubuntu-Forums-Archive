---
title: "Which Ubuntu version for server on production"
date: 2012-01-14
forum: Server Platforms
---

### Post by fernandoch on 2012-01-14
Which Ubuntu version would you install on a production server? And why?

Thank you.

---

### Post by amauk on 2012-01-14
Latest LTS
Why? 5 year support (as opposed to 18 months with non-LTS)

---

### Post by fernandoch on 2012-01-14
Good choice, but then you don't have the latest software... do you?

---

### Post by amauk on 2012-01-14
No, but do you really want the "latest" unstable software on your production server?
probably not

In any situation there's always a new/unstable vs. older/stable trade-off, be that workstation or server
It's just that server sysadmins tend to be more conservative when it comes to API/ABI stability

---

### Post by KdotJ on 2012-01-14
To add weight, definately go for stabilty over bleeding edge. 5 year support is a good shout too, less release upgrades means less chance of things to go wrong.

---

### Post by 2F4U on 2012-01-14
> **fernandoch said:**
> Good choice, but then you don't have the latest software... do you?

And you also don't have the latest bugs in that software. Testing environments may be the exception for for anything else install LTS.

---

### Post by fernandoch on 2012-01-14
I understand your thoughts, but for example for the mediawiki package, Oneiric is still on version 1.15.5 

[http://packages.ubuntu.com/oneiric/mediawiki](http://packages.ubuntu.com/oneiric/mediawiki)

and the version from the site is on 1.18.1

[http://www.mediawiki.org/wiki/Download](http://www.mediawiki.org/wiki/Download)

A lot of difference, isn't it?

---

### Post by craigp84 on 2012-01-14
It's not an issue fernandoch, if you need the newer version of a software package (perhaps there's a new feature that's required by the business), you just build / package it yourself.

Stable every time* over bleeding edge.

* There are *always* exceptions to any rule :-)

---

### Post by CharlesA on 2012-01-14
> **craigp84 said:**
> It's not an issue fernandoch, if you need the newer version of a software package (perhaps there's a new feature that's required by the business), you just build / package it yourself.

Stable every time* over bleeding edge.

* There are *always* exceptions to any rule :-)

This, pretty much. I run Lucid on my server at home, if I need something at a newer version, I install from source.

---

### Post by fernandoch on 2012-01-18
But then if you don't have the latest version of mediawiki or apache, you won't be exposed to hackers?

---

### Post by craigp84 on 2012-01-18
> **fernandoch said:**
> But then if you don't have the latest version of mediawiki or apache, you won't be exposed to hackers?

Security fixes are backported. New features aren't normally added when you apt-get upgrade a package, but bug fixed (inc security bugs) come down the line.

---

### Post by fernandoch on 2012-01-18
Is there a way to track them? Are they published somewhere?

---

### Post by craigp84 on 2012-01-18
> **fernandoch said:**
> Is there a way to track them? Are they published somewhere?

Yeah view the changelog for the updated package. If you want to check online visit packages.ubuntu.com and you can navigate from there for a chosen package.

---

### Post by fernandoch on 2012-01-18
Thank you, but I cannot see any changelog

[http://packages.ubuntu.com/lucid/mediawiki](http://packages.ubuntu.com/lucid/mediawiki)

where is it located?

---

### Post by craigp84 on 2012-01-18
The changelog link on the right hand side of the page.

[http://changelogs.ubuntu.com/changelogs/pool/universe/m/mediawiki/mediawiki_1.15.1-1ubuntu2.1/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/m/mediawiki/mediawiki_1.15.1-1ubuntu2.1/changelog)

The first entry in the file is an example backport of a security fix.

---

### Post by fernandoch on 2012-01-18
Thank you very much.

---

