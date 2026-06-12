---
title: "Linux Directory Service Open Standard"
date: 2007-06-07
forum: Server Platforms
---

### Post by joubertdj on 2007-06-07
Dear Linux/Ubuntu Community

Being a Linux supporter, with my first original installation probably 12 years ago (SuSE 4.2 With the carton cover... kept it for sentimental reasons...) I have seen Linux grow (Like many of you) and also the way it grows faster... in the form of open standards... open standards reliefs the burden of patents and fosters co-operation and competition (Not fact, just an observation).

I suggest that we as the Linux community develop an open standard for a Directory Service. This will then promote and enhance the acceptance rate of software services such as web servers, database servers, mail servers, file servers, print servers, etc. to "integrate" within any developed implementation of the Directory Service Open Standard...

I tried to contact The Linux Foundation, but was unsuccessful... Someone such as Ubuntu or Canonical should spearhead this initiative... for I am because of you...

Just starting to code the Linux Directory Server will be futile in my opinion, as it is not based upon something concrete which somebody else could adhere too.

Yours sincerely,

McDave

---

### Post by Stephen Howard on 2007-06-07
Do you mean LDAP??

---

### Post by joubertdj on 2007-06-07
My fault at that... generic monologue...

I actually meant the tools/functions associated...
I currently have great difficulty with LDAP and my attempt at a central update server ... our bandwidth is limited and would like a server to keep a central repository of the current and up-to-date packages... certain users should get certain software and other users should get other... LTSP also in the picture...

---

### Post by Stephen Howard on 2007-06-07
Have you had a look at [this]("http://people.debian.org/~torsten/ldapnss.html")?  It might help you with the configuration.

---

### Post by joubertdj on 2007-06-07
Thanks... Think I will take a break before I continue... Might loosen the nerve and the sarcasm :)
Thanks for your help.

---

### Post by elst on 2007-06-09
FWIW, the code already exists (Fedora Directory Server), but it has Java dependencies which effectively block it from being packaged and distributed with  Debian/Ubuntu right now.

There is an Ubuntu Directory Services team on Launchpad, but as far as I know, there isn't any development happening at present.

---

