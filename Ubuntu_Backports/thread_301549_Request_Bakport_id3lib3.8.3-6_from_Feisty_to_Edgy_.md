---
title: "Request: Bakport id3lib3.8.3-6 from Feisty to Edgy and Dapper"
date: 2006-11-17
forum: Ubuntu Backports
---

### Post by GTvulse on 2006-11-17
As decribed in id3lib's [bug #54136]("https://launchpad.net/distros/ubuntu/+source/id3lib3.8.3/+bug/54136"), EasyTag is broken because id3lib corrupts tags encoded in UNICODE vector encodings; for example I've had id3 tags with Japanese and Chinese content be damaged by EasyTag due to this bug.

[URL="https://launchpad.net/distros/ubuntu/+source/id3lib3.8.3/3.8.3-6"]
id3lib3.8.3-6[/URL] corrects this brokenness [by including a long standing patch]("https://launchpad.net/distros/ubuntu/feisty/+source/id3lib3.8.3/+changelog") created by the EasyTag developers (id3lib hasn't been further  developed for 3 years already, BTW).

---

### Post by mazirian on 2006-11-17
Motion seconded!  Would you please provide a link to the patch?

EDIT:  Uh, n/m, I guess I was temporarily blind.

---

### Post by jetthe on 2006-11-17
Builds succesfully with prevu, package for Edgy is available at [http://brutus.ath.cx/backports/edgy/libid3-3.8.3c2a_3.8.3-6~6.10dalom.com1_i386.deb](http://brutus.ath.cx/backports/edgy/libid3-3.8.3c2a_3.8.3-6~6.10dalom.com1_i386.deb)  (works perfectly for me)
I've built a Dapper package as well, haven't had time to test it yet though... [http://brutus.ath.cx/backports/dapper/libid3-3.8.3c2a_3.8.3-6~6.06dalom.com1_i386.deb](http://brutus.ath.cx/backports/dapper/libid3-3.8.3c2a_3.8.3-6~6.06dalom.com1_i386.deb)



2006-11-18: Request located on [http://launchpad.net/products/dapper-backports/+bug/72322](http://launchpad.net/products/dapper-backports/+bug/72322)  (for both edgy-backports and dapper-backports)

/jetthe

---

### Post by towsonu2003 on 2006-11-18
I requested the fix to be backported to dapper and edgy in [https://launchpad.net/distros/ubuntu/+source/id3lib3.8.3/+bug/54136](https://launchpad.net/distros/ubuntu/+source/id3lib3.8.3/+bug/54136) . Not sure how that exactly works, but it's supposed to work :)

---

### Post by GTvulse on 2006-11-18
The official bug ticket then, its mine :-) Please keep an eye on [https://launchpad.net/bugs/72187](https://launchpad.net/bugs/72187) and make your voice heard there, where it carries real weight.

---

### Post by jetthe on 2006-11-18
> **dradul said:**
> The official bug ticket then, its mine :-) Please keep an eye on [https://launchpad.net/bugs/72187](https://launchpad.net/bugs/72187) and make your voice heard there, where it carries real weight.


Ouch, that's why I didn't find it, it wasn't in any of the backport projects.  Kind of confusing when bugs filed in individual packages regarding backports doesn't show up on the backports project page. Oh well, we now have a dupe of a dupe of a dupe. ](*,)

---

### Post by GTvulse on 2006-11-18
> **jetthe said:**
> Ouch, that's why I didn't find it, it wasn't in any of the backport projects.  Kind of confusing when bugs filed in individual packages regarding backports doesn't show up on the backports project page. Oh well, we now have a dupe of a dupe of a dupe. ](*,)

I just marked mine as a duplicate of yours.

---

### Post by GTvulse on 2006-11-20
Edgy backport has been approved, see [https://launchpad.net/bugs/72322](https://launchpad.net/bugs/72322), Dapper backport may appear soon.

---

### Post by GTvulse on 2006-11-30
For the Dapper users, please go to the bug report above and confirm if the fix works for you. You may need to build the libraries with the help of [pbuilder]("https://wiki.ubuntu.com/PbuilderHowto").

---

