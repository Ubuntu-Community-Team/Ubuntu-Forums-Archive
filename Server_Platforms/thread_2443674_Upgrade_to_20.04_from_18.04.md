---
title: "Upgrade to 20.04 from 18.04"
date: 2020-05-18
forum: Server Platforms
---

### Post by lists-an on 2020-05-18
Hello, I went ahead and enacted the do-release-upgrade -d command and the server responded with:
====
This session appears to be running under ssh. It is not recommended
to perform a upgrade over ssh currently because in case of failure it
is harder to recover.
====

Any advice on the matter?  It wanted to open a new SSH session with a different port (that I have blocked).. so I just aborted.

Thanks,
Donovan

---

### Post by darkod on 2020-05-18
That is a normal message during release upgrade. It is also normal to activate listener on alternative ssh port to give you another option of connecting, just in case.

However, unless you have a really good reason to rush the upgrade, I would wait for 20.04.1 when the upgrade option will be automatically offered without using -d.

Waiting until the first point release also gives them a chance to iron out bugs and issues noticed after release.

---

### Post by LHammonds on 2020-05-19
I agree with darkod about holding off on doing an in-place upgrade until the 1st point release.  But you know your system and that's your decision.

As a side note, I never use the upgrade-in-place option mainly because I don't want any chance of extended downtime for any of my services.  I will install a fresh 20.04 machine and install / configure each of the services based on 20.04 standards and migrate the data over from the older machine.  Once everything is verified as running perfect, I simply swap the IP addresses to make the new box the production server.

The option to upgrade in-place is JUST FOR THE OS.  Any applications / services you have installed such as websites, databases, etc. may break because of underlying changes in software (e.g. libraries).  Example: 18.04 by default installs php 7.2 and 20.04 by default installs php 7.4 and any website that relies on functions that were deprecated between 7.2 and 7.4 will break...thus requiring updated website code or removing php 7.4 and forcing the install of the older php 7.2 (not recommended).

LHammonds

---

