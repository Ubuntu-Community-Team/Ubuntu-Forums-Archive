---
title: "Ubuntu 20.04 LTS install Apache2 2.4.51"
date: 2021-10-08
forum: Server Platforms
---

### Post by coppolino97 on 2021-10-08
Hi all,
I have a Ubuntu 20.04 LTS Virtual machine.
This VM is a web server and I would upgrade to the latest Apache2 version (Apache2 2.4.51).
It is a company policy.

How can I upgrade? I noted that I am running "2.4.41" release.
I would upgrade to the latest Apache2 release to fix all previous issues.

How can I get latest Apache2 update?

Best regards

---

### Post by LHammonds on 2021-10-09
> **coppolino97 said:**
> 
I have a Ubuntu 20.04 LTS Virtual machine.
I am running "2.4.41" release.

I am also running Ubuntu web servers on Long-Term Support.
The current version is 20.04.3 LTS running kernel 5.4.0-88 and Apache 2.4.41

This "is" the latest and most-current version for the Long-Term Support server.

> **coppolino97 said:**
> 
I would upgrade to the latest Apache2 version (Apache2 2.4.51).

If you remove Apache and manually install a specific version, it will likely not auto-update with the apt-get which means you will need to baby this server for every release...which might mean you will run into and experience bleeding-edge bugs with those versions.

The whole point of LTS is a stable platform that enjoys updates that typically do NOT break application functionality (security updates in particular).

So in terms of your companies policy to be running the current version, you are already there.  If you company wants bleeding edge, then the stable platform was not the right fit...but I would recommend against running a production server on bleeding-edge versions.  But that's your call.

LHammonds

---

