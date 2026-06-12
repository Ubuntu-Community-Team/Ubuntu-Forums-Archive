---
title: "Ubuntu Package Updates?"
date: 2010-12-02
forum: Server Platforms
---

### Post by dogzilla on 2010-12-02
I've chosen Ubuntu Lucid LTS as our platform for rolling out our cloud-based server solution. One problem we've noticed is the lack of security updates in the package management system dealing with our LAMP stack. For example, updating to the latest current versions of PHP (5.3.3), Apache (2.2.17) and MySQL (5.1.53) through the package system is difficult if not impossible. While we can certainly deal with this by building from source, it obviates one of the really nice parts of Ubuntu - namely the package system.

How do other folks deal with this issue? I understand Canonical wants to provide stable snapshots, but security needs often require updates to the latest versions within a quick timeframe, so I can't believe that building form source is the only solution here, and we're not talking about niche software either - basically the core of the LAMP stack. 

Any thoughts would be greatly appreciated.

---

### Post by snowpine on 2010-12-02
Welcome to the forums!

The short answer to your question is that most Linux distributions (including Ubuntu) address this issue by "backporting" security patches from the latest package version to the currently-supported, stable package version.  

Here is an article from Red Hat that explains it better: 

[https://access.redhat.com/security/updates/backporting/?sc_cid=3093](https://access.redhat.com/security/updates/backporting/?sc_cid=3093)

The obvious solution, if the LTS releases are too stable for your needs, is to use the regular Ubuntu releases, which give you a fresh infusion of new software every 6 months.

---

