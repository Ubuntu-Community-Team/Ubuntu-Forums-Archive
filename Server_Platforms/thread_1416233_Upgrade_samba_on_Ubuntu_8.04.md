---
title: "Upgrade samba on Ubuntu 8.04"
date: 2010-02-25
forum: Server Platforms
---

### Post by GabrielSyme on 2010-02-25
I am running Ubuntu 8.04 LTS as my Samba/LDAP PDC on my network. Unfortunately, I need to get a newer version of samba than the current repositories for 8.04 provide. I need the Samba 3.4.0 that has been updated for Ubuntu 8.10 to allow Windows 7 to join domain as outlined [here]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/462626") (I am currently running 3.0.28a I think).
Is there a way to set 8.04 to use the 9.10 repositories and use apt-get to install samba 3.4.0 from them?

---

### Post by cdenley on 2010-02-26
No. The samba packages probably depend on a bunch of other packages with versions which aren't available in the hardy repository. It may be possible to install samba and all its dependencies from the karmic repo, but then you would end up with a partial upgrade which could cause problems if it even works at all. I would pick a release and stick with it. I don't think upgrading from 8.04 to 9.10 is supported, though. 10.04 should be released in a couple months.

---

### Post by GabrielSyme on 2010-02-26
So am I going to need to build from source to get a version of Samba that works with Windows 7? I suppose I might be able to wait for 10.04. Does Ubuntu usually provide an upgrade path from one LTS version to the next?

---

### Post by cdenley on 2010-02-26
> **GabrielSyme said:**
> Does Ubuntu usually provide an upgrade path from one LTS version to the next?

Most definitely.

---

