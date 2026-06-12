---
title: "Why some new packages are not available in older Ubuntu releases?"
date: 2007-07-03
forum: Repositories &amp; Backports
---

### Post by vairoj on 2007-07-03
I have a long-standing question about Ubuntu packages. When a new version of a package available in a new Ubuntu release, why does not it also available in the prior releases? For a concrete example, I want to update subversion package to 1.4.x but subversion 1.4.3 is only available in Feisty. I do not want to upgrade to Feisty yet since I still prefer my server to run a Long-Term-Support version (Dapper). So in this case, am I supposed to install the package manually instead of relying on Ubuntu repository?

Talking about LTS, what does LTS really mean? Since packages like subversion does not get updated. Does LTS only cover core packages and security patches?

---

### Post by smartboyathome on 2007-07-03
LTS get core and security packages still, but that is about it. I would upgrade to Feisty if I were you, as the packages in Dapper will only get older.

---

### Post by tgalati4 on 2007-07-04
That is the dilemma.  You want a stable machine for server use, but you need an up-to-date machine for development work.  You can manually install SVN or look for a *.deb package and install it manually.  It's not difficult.  You really only need to upgrade the packages that have features otherwise not available.  

You risk a less stable machine under Feisty, but try the Live CD first and see how long it runs before you run into problems.  If it works for several days then install it.

---

### Post by vairoj on 2007-07-05
Ok, I think I get the picture now. It still makes sense for me to use LTS since the only app I need to manually install to get the new version is Subversion.

---

