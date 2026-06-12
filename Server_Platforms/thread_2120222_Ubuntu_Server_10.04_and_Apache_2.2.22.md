---
title: "Ubuntu Server 10.04 and Apache 2.2.22"
date: 2013-02-26
forum: Server Platforms
---

### Post by cabaro on 2013-02-26
Hi,

i'm running servers with apache 2.2.14 currently installed and i would need to get them updated to 2.2.22 version. We got some positives on a security scan.
Is there any way (preferably by apt) to get it installed?

Is the only way to upgrade to 12.04 server version?


Thank you all in advance

/cab

---

### Post by KnownSyntax on 2013-02-26
I'm going to say that you will have to upgrade versions, as the 10.04 release will have that version of Apache forever (since they only will perform maintenance fixes on any package that comes with Ubuntu on the LTS unless it's a new version of Apache or of that package). 

You can upgrade for the version you want or stay at where you are if it's working out good enough for you.

---

### Post by cabaro on 2013-02-26
> **KnownSyntax said:**
> I'm going to say that you will have to upgrade versions, as the 10.04 release will have that version of Apache forever (since they only will perform maintenance fixes on any package that comes with Ubuntu on the LTS unless it's a new version of Apache or of that package). 

You can upgrade for the version you want or stay at where you are if it's working out good enough for you.

Thanks for your quick reply.
We might need to upgrade to 12.04 then.

/cab

---

### Post by cabaro on 2013-02-26
Actually just upgrading apache 2.2.14 to the latest apache2.2.14-5ubuntu8.10 fixed the security issues.

---

