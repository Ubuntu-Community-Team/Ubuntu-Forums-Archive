---
title: "Is canonical forcing people to use ESM to patch vulnerabilities?"
date: 2023-08-17
forum: Ubuntu, Linux and OS Chat
---

### Post by paperdragon on 2023-08-17
Hi everyone, 

I'm a Infrastructure engineer that is trying to gain Cyber Essentials Plus accreditation for my organisation. As part of that, I'm having to ensure all of the vulnerabilities that are classed as High or above in severity, are patched. One of the vulnerabilities I've got on a couple of ubuntu servers running Exim is this: [https://ubuntu.com/security/notices/USN-6169-1](https://ubuntu.com/security/notices/USN-6169-1) - a GSASL library needs to be updated. This vulnerability affects both 20.04 and 22.04 LTS versions of Ubuntu, as well as a few other ESM versions. No as far as I can tell, the only way to fix this vuln is to update the package to an ESM version of the package, and thus it requires an Ubuntu Pro subscription to update the package. 

Why is it that there's an Ubuntu LTS vulnerability that is only patchable by moving to ESM? Surely this goes against the ethos of Ubuntu? Am I missing something here?

Thanks,
Gareth

---

### Post by guiverc on 2023-08-17
It's a *community* sourced package, which have **NEVER** come with security fixes from the [Ubuntu Security Team]("https://wiki.ubuntu.com/SecurityTeam"). 

There is no difference now, to earlier, EXCEPT security fixes are now ***optionally*** available for more more than the normal 'main' if you enable ESM.  If you elect not to use ESM, there is no change to before Ubuntu Pro's introduction (*packages found in main still get security fixes; not so for universe packages*).

What you're missing is you can now get the Ubuntu Security Team managing more than just the 'main' repository packages *if you enable ESM*, ie. a new optional service is available.  If you don't use ESM, there is no change ('universe' still doesn't get security fixes as before; only whatever bugs are filed & fixed by the community)

[https://discourse.ubuntu.com/t/ubuntu-pro-faq/34042](https://discourse.ubuntu.com/t/ubuntu-pro-faq/34042)

---

### Post by ian-weisser on 2023-08-17
> **paperdragon said:**
> Surely this goes against the ethos of Ubuntu?

The ethos of Ubuntu includes, among other things, improvement from community participation and community contribution.

Expecting "somebody else" to track CVEs, patch those packages, test, and upload for you (for free) is arguably against the ethos.
Ubuntu Pro means that you can satisfy your contribution by payment instead of pitching in to do the work.

There is absolutely nothing preventing any community member or group from tracking Universe CVEs and patching them for everybody's benefit. Community MOTUs will happily upload them.
The market for paid Ubuntu Pro exists mostly because too few folks (including thousands of enterprises with paid staffs) are contributing to that patching effort.

---

### Post by paperdragon on 2023-08-17
> Expecting "somebody else" to track CVEs, patch those packages, test, and upload for you (for free) is arguably against the ethos.
Ubuntu Pro means that you can satisfy your contribution by payment instead of pitching in to do the work.

I'd not really thought of it like that, and of course your are entirely correct. I guess it's time for me to pitch Ubuntu Pro to my boss :D

Thanks for your insights.

---

### Post by ian-weisser on 2023-08-17
There are other alternatives:

You could cherry-pick the patch and apply it yourself. Patching is a skill, but it's not a difficult skill to learn.

You could use an alternative SASL. Some cost, some don't.

You could test your clients some other way to ensure they are not malicious.

You could migrate to the six-month releases of Ubuntu that are immune to this attack.

There are others.

The best path must be judged by you, of course. Random internet folks don;t know your needs or constraints.

---

