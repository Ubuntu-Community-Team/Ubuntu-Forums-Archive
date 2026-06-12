---
title: "Apache 2.0 vs Apache 1.3"
date: 2005-11-23
forum: Server Platforms
---

### Post by casper_2095 on 2005-11-23
Hi

I see Ubuntu defaults to Apache 2.0 whereas the majority of hosting providers (well mine at least) are offering Apache 1.3.

What issues are likely to arise if I develop with v2.0 then try to deploy onto v1.3?

---

### Post by simon w on 2005-11-24
Well that depends on what your are developing and what, if any, modules you require...

---

### Post by Nap_BlownApart on 2006-09-15
Casper is making a significant point.
My web hoster, as well as clients for whom I do web applic. development are all running Apache 1.3.

Is it possible to get a package up for 1.3?  That way it could be at least an option through Synaptic or Aptitude?

Cheers,
Nap

---

### Post by FakeOutdoorsman on 2006-09-15
Apace 1.3.32-2 is listed in Synaptic for me because I added the Universe and Multiverse repositories.  You can do that with [easyUbuntu]("http://easyubuntu.freecontrib.org/") or with "System" > "Administration" > "Software Properties".  You'll either want to develop specifically for Apache 1.3 or move to an Apache 2.0 host.
[URL="https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096"]
Adding the Universe and Multiverse Repositories[/URL]

---

### Post by Nap_BlownApart on 2006-09-16
Fake,

I've done the same as you with my **/etc/apt/sources.list** but Synaptic on my systems has 1.3.34 listed.  I'm in Australia, if that makes a difference?

Has anyone else out there found 1.3.37 mentioned?

Cheers,
Nap

---

### Post by FakeOutdoorsman on 2006-09-16
My sources has the *us* prefix. Example:

[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)

Perhaps yours are *au* and they might contain different packages.  I'm not sure though.

---

### Post by Nap_BlownApart on 2006-09-16
You are right, mine is 'au'.
Thanks for that.

Any other country codes out there? (Ones that might have 1.3.37 mentioned?)

---

