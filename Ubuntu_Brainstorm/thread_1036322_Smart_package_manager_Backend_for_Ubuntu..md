---
title: "Smart package manager Backend for Ubuntu."
date: 2009-01-10
forum: Ubuntu Brainstorm
---

### Post by Slug71 on 2009-01-10
Well since Canonical has been funding this project since 2005 and also has Devs(one of its main ones i think) working on it along with others from other Distros and Projects i figured why not bring it to Ubuntu. It sounds pretty good and should be about ready for mainline use. I think it could be a good backend for Synaptic or Packagekit and is supported by both.

C/P from Smart's Website:

> The Smart Package Manager project has the ambitious objective of creating smart and portable algorithms for solving adequately the problem of managing software upgrades and installation. This tool works in all major distributions and will bring notable advantages over native tools currently in use (APT, APT-RPM, YUM, URPMI, etc).

Notice that this project is not a magical bridge between every distribution in the planet. Instead, this is software offering better package management for these distributions when working with their native packages. Using multiple packaging systems at the same time (like rpm and dpkg) is possible but would require packages from those systems to follow the same packaging guidelines. As this is not the case at the moment, mixing package systems is not recommended. 

A link to the Website for more info:
[http://labix.org/smart](http://labix.org/smart)
Parties involved with the project can be found under Credits on the Main page.


[[IMG]http://brainstorm.ubuntu.com/idea/17172/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/17172/)

---

### Post by smartboyathome on 2009-01-10
Isn't that basically what PackageKit is doing? I thought PackageKit was slated for inclusion.

---

### Post by Slug71 on 2009-01-10
> **smartboyathome said:**
> Isn't that basically what PackageKit is doing? I thought PackageKit was slated for inclusion.

Packagekit is slated for inclusion but you can have Smart as the backend.
Both are available in Synaptic.

---

### Post by smartboyathome on 2009-01-10
> **Slug71 said:**
> Packagekit is slated for inclusion but you can have Smart as the backend.
Both are available in Synaptic.

I thought Smart was the front end to dpkg. If that is so, does that mean we get rid of apt? :(

---

### Post by Slug71 on 2009-01-10
> **smartboyathome said:**
> I thought Smart was the front end to dpkg. If that is so, does that mean we get rid of apt? :(

Yeh it seems it replaces APT. I know many people wont like that but i dont see why Canonical would fund something if it has no intention of using it. I could be wrong though and thats pretty much the reason i started the poll.
It does seems pretty good though.

---

