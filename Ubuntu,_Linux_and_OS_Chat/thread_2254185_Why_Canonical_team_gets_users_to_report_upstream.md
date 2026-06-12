---
title: "Why Canonical team gets users to report upstream?"
date: 2014-11-25
forum: Ubuntu, Linux and OS Chat
---

### Post by Pilot6 on 2014-11-25
Recently I reported some bugs. I was asked to make upstream linux reports.

It takes so mush effort to do this, when nothing is set up for that? For instance a plain text mailer.
I send mails using gmail web interface and it is not sutable for that. It looks like noone is interested, but the bug reporter.
If you do not do it in a right way, someone with @canonical mail address starts complaining on that and getting me do it again.

Isn't it resposibility of distro maintainers to report upstream?

Also I made a couple of trivial patches.  Same thing. I was advised to send it upstream, but there they made me re do it 10 times.
Each time they were not satisfied with something. Again, why the only interested person to fix something is the reporter?

It is very unmotivating to report anything again. I can fix bugs myself and keep it locally, if noone is interested.

---

### Post by buzzingrobot on 2014-11-26
It makes sense for bug reports to be sent directly upstream.

A package has a single upstream source, while there are very likely hundreds of distributions that distribute that package. Relaying bug reports via distributions would flood upstream developers with confusing, duplicate, reports.

The links back to the originator of the bug report would be severed.  Devs often need to query a bug report originator for more information and clarification. Putting distributions in the middle of all that adds layers of unnecessary bureaucracy and additional workload with no upside.

Tools like Launchpad and Bugzilla provide easy ways for users to report bugs and for upstream to deal directly with the originator.

---

### Post by Pilot6 on 2014-11-26
But there is nothing regarding Bugzilla in this manual. 
[https://wiki.ubuntu.com/Bugs/Upstream/kernel](https://wiki.ubuntu.com/Bugs/Upstream/kernel)

But they give link to this manual. I know it is better, but for a user it is a real pain in the ass to create an E-mail in a right way.

---

### Post by buzzingrobot on 2014-11-26
> **Pilot6 said:**
> But there is nothing regarding Bugzilla in this manual. 
[https://wiki.ubuntu.com/Bugs/Upstream/kernel](https://wiki.ubuntu.com/Bugs/Upstream/kernel)


That wiki page is specific to filing upstream kernel bugs, not a general procedure for filing any upstream bug report. (Canonical maintains the kernels installed in Ubuntu.)

> ... a real pain in the ass to create an E-mail in a right way.

Developers/maintainers establish the procedures via which they will accept bug reports.  Some projects use Bugzilla sites, some Launchpad, some ask for reports on Github, etc. 

The requirements outlined in that wiki page are taken directly from [www.kernel.org](www.kernel.org), as it says at the top of the page.  I.e., they are the kernel bug reporting procedures set in place by Linus Torvalds, et al, not Canonical.

---

### Post by Pilot6 on 2014-11-26
I asked why Canonical people do not report bugs upstream themselves? But give a link to that manual.

---

### Post by buzzingrobot on 2014-11-26
> **Pilot6 said:**
> I asked why Canonical people do not report bugs upstream themselves? But give a link to that manual.

I imagine they do report bugs upstream, when they uncover bugs in upstream code.

if you reported a bug that the Canonical kernel team determined was their responsibility -- their code -- presumably they'd accept it.

If it's not their code, the report needs to go upstream, filed by the person who claims to have found the bug, which is you.  We can't expect Canonical to file our unverified bug reports  on someone else's project.

---

### Post by Elfy on 2014-11-26
> **Pilot6 said:**
> I asked why Canonical people do not report bugs upstream themselves? But give a link to that manual.

At the end of the day it's 'your' bug - take ownership of it - report upstream and that is a plus for **everyone** using the package - not just people using *buntu.

---

