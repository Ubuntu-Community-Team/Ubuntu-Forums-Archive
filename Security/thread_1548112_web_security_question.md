---
title: "web security question"
date: 2010-08-07
forum: Security
---

### Post by methodtwo on 2010-08-07
Hi there
I would like to serve some stuff that i've written. I would like to do this so that i can gain skills in apache administration.This will only, effectively, be my homepages though. So i guess that using my ubuntu desktop 10.04 will be good enough right?.However even though i'm only serving a small amount if stuff i still want it to be as secure as possible.I can't find anything on putting apache in a chroot jail on ubuntu or on ubuntu server. There is one document that i found that tells you how to do it on debian etch.Would following this howto be enough to set apache up in such a way?.There's also not much on apache with ssl. Bearing this in mind would you recommend that i installed debain instead to serve securely on?. I don't want to use one of the BSDs because i'm not a great sys admin and linux is much easier to upgrade, or so i've heard.
So any advice would be great. I mainly need advice on chrooting apache and whether or not to use debain, not on whether or not to use freeBSD.
Thank you for your time, regards

---

### Post by clrg on 2010-08-08
If you keep your Apache up to date, there is no need of jailing it. About half of the websites out there are served by Apache, if it had serious security problems, that wouldn't be the case. I recommend you read some papers on webserver hardening.

Penetrating a patched, securely configured and properly firewalled webserver takes a lot of time and resources (if its even possible (without social engineering)). I doubt your website contains information worth trying it.

---

### Post by lisati on 2010-08-08
The default apache configuration options are fairly sensible and won't necessarily leave you wide open to attack.

If you're concerned, there are one or two things you can do, such as installing mod-defensible, which will help prevent the rogues and rascals doing mischief.

---

