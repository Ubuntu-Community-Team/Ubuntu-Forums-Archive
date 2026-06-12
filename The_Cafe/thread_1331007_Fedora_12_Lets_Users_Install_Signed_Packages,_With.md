---
title: "Fedora 12 Lets Users Install Signed Packages, Without Root Privileges"
date: 2009-11-18
forum: The Cafe
---

### Post by Jags_FL on 2009-11-18
From the **[Slashdot article]("http://linux.slashdot.org/story/09/11/18/2039229/Fedora-12-Lets-Users-Install-Signed-Packages-Sans-Root-Privileges")**:

"The new default policy for Fedora 12 [allows local, unprivileged users to install signed packages]("https://bugzilla.redhat.com/show_bug.cgi?id=534047") without root access. This change apparently went mostly unnoticed until after the Fedora 12 GA release, at which point it sparked a [mailing list thread]("https://www.redhat.com/archives/fedora-devel-list/2009-November/msg00926.html") that is, as of this writing, over 100 posts long."

---

### Post by alphaniner on 2009-11-18
And thus was laid the first brick of the road to hell.

Melodramatic perhaps, but this seems like a good way to lay the groundwork for security exploits.

---

### Post by emigrant on 2009-11-18
> **alphaniner said:**
> And thus was laid the first brick of the road to hell.
+1
and hope ubuntu won't follow the steps:roll:

---

### Post by kyuubi777 on 2009-11-18
wow.. that is probably the most all inclusive security fail since the generation of wep

---

### Post by Simon17 on 2009-11-18
No, Ubuntu just took the expressway.

---

### Post by Xbehave on 2009-11-18
How many of the people complaining have noexec* set on all user writeable directories?

Currently users can run whatever code they want anyway, this is only causing a fuss because most people don't realise

*not that that would help because you can still execute sh/bash/python/java/perl/etc AND code in any language that those languages have loaders for (so pretty much anything)

Atleast fedora runs security limits on unauthorised code (SELINUX) whereas if i download a binary and execute it on ubuntu nothing is limiting it (apparmor doesn't support a * profile)

---

### Post by MaxIBoy on 2009-11-18
I think this is a good idea! But this behavior should **not** be the  default, and it should be control-able on a per-user basis and require  root access to enable.


EDIT: Some of the people in this thread don't know what "signed" means. It means that the package has been tested safe by the Fedora packagers and has not been tampered with in any way. And so what if you can install some package without root access? You still can't use the program you installed to do damage unless you *run* it with root access. At least, you can't do worse than this: ```
rm -rf ~
``` (DON'T RUN THAT COMMAND!)

---

### Post by alphaniner on 2009-11-18
> **MaxIBoy said:**
> I think this is a good idea! But this behavior should **not** be the default

Precisely.  The default part is what I consider to be a bad idea.

---

### Post by Frak on 2009-11-18
> **Simon17 said:**
> No, Ubuntu just took the expressway.
This.

---

### Post by Psumi on 2009-11-19
> **Simon17 said:**
> No, Ubuntu just took the expressway.

Mm hmm.

---

### Post by AdamWill on 2009-11-20
The brick has been removed, expressway turned back into fields, (insert florid metaphor of your choice here) - the policy will be changed. See [https://www.redhat.com/archives/fedora-announce-list/2009-November/msg00012.html](https://www.redhat.com/archives/fedora-announce-list/2009-November/msg00012.html) and [https://www.redhat.com/archives/fedora-devel-list/2009-November/msg01445.html](https://www.redhat.com/archives/fedora-devel-list/2009-November/msg01445.html) .

Well, that was an interesting...day. Feels like longer somehow. :)

---

