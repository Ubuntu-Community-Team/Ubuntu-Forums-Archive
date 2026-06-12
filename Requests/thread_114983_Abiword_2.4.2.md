---
title: "Abiword 2.4.2"
date: 2006-01-09
forum: Requests
---

### Post by MichaëlVD on 2006-01-09
According to the [changelog]("http://www.abisource.com/changelogs/2.4.2.phtml"), Abiword 2.4.2 features improved opendocument support. Therefore, I think it would be interesting if it could be backported.
I díd read the backporting requirements, but I have no idea whether this request fulfills all those requirements, especially the second requirement, since I don't even understand what it means:
> New packages MUST build cleanly from Debian source archives. That is, "apt-get build dep PACKAGE; apt-get source -b PACKAGE" must produce a working package in order for it to be backportable. No 'hacking dependencies' or 'skipping build-dep' or any force flags of any kind.

---

### Post by jdong on 2006-01-09
The most important part of the guidelines is that the package of the version requested has to be in Dapper (packages.ubuntu.com/abiword). In this case, only 2.4.1 is in Dapper, as with Breezy.

The other requirements are for more advanced users to evaluate; don't worry if you don't understand them.

---

### Post by MichaëlVD on 2006-01-17
[QUOTE=jdong]In this case, only 2.4.1 is in Dapper, as with Breezy[/QUOTE]

by now, 2.4.2 arrived in Dapper!

---

