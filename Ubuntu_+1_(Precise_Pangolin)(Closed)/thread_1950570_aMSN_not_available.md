---
title: "aMSN not available?"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by scradock on 2012-04-01
This program is apparently no longer available in the repos; trying to install from /pool/universe/a/ from an oneiric repo generates a failure in Software Center saying that libfarsight0.10-0 is not available.

Has anyone found a work-around? For some reason none of my Precise installs has the .deb in its /var/cache/apt/archives/, even though the program is installed and working in every one except the latest pre-Beta2 installed a couple of days ago.

---

### Post by ubuntu27 on 2012-04-01
You are right. aMSN is not in Ubuntu Precise's repo for me.

As for the debs not being in that directory, perhaps you cleaned it recently using programs such as **bleachbit**?

---

### Post by scradock on 2012-04-01
> **ubuntu27 said:**
> You are right. aMSN is not in Ubuntu Precise's repo for me.

As for the debs not being in that directory, perhaps you cleaned it recently using programs such as **bleachbit**?

Nope; never used anything like that. However, there was some changeover a few weeks ago when libfarsight got removed and libfarstream was brought in, and that "demoted" aMSN to "local" status. I'm guessing that .debs with "local" status don't get cached....

Now trying to pull in old debs from an oneiric install requires me to go back to libfarsight0.10-0, which also wants libgupnp-igd-1.0-3, which has been replaced by version 1.0-4... It's not looking good!

Whatever happened to backward-compatibility?

---

### Post by howefield on 2012-04-01
[https://launchpad.net/ubuntu/precise/+source/amsn/0.98.4-0ubuntu3](https://launchpad.net/ubuntu/precise/+source/amsn/0.98.4-0ubuntu3)

---

### Post by scradock on 2012-04-01
> **howefield said:**
> [https://launchpad.net/ubuntu/precise/+source/amsn/0.98.4-0ubuntu3](https://launchpad.net/ubuntu/precise/+source/amsn/0.98.4-0ubuntu3)

Thanks - that is sad reading. I don't find the alternatives "better", myself, but no doubt others do. Another opportunity to allow personal preferences has gone...

---

