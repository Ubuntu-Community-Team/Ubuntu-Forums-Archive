---
title: "Adblock Plus in Quantal repository"
date: 2012-09-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Sworddragon on 2012-09-27
Normally I'm installing all Addons for Firefox manually but I thought I can use the package manager to do this. I know Adblock Plus was already available in some older versions of Ubuntu but I can't find it in Quantal. I have tried adblock-plus and xul-ext-adblock-plus but with no success. Was the package renamed or even removed? If it was removed what is the reason for this?

---

### Post by funicorn on 2012-09-27
mozilla addons are installed with permission 755. Global installation is not good.

---

### Post by cariboo on 2012-09-27
> **Sworddragon said:**
> Normally I'm installing all Addons for Firefox manually but I thought I can use the package manager to do this. I know Adblock Plus was already available in some older versions of Ubuntu but I can't find it in Quantal. I have tried adblock-plus and xul-ext-adblock-plus but with no success. Was the package renamed or even removed? If it was removed what is the reason for this?

Searching in synaptic, I don't see an adblock add-in for firefox in the repositories.

---

### Post by vasa1 on 2012-09-27
It's *possible* that AdBlock Plus was available from repos but I very much doubt it ever was.
It's always been available from [AMO]("https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/"), which, IMO, is the correct place to get it (apart from Palant's own site).

---

### Post by jbicha on 2012-09-28
Adblock plus is still available in [Debian]("http://packages.qa.debian.org/adblock-plus"), but like most Mozilla addons was removed from Ubuntu because they are too much of a burden to rebuild and update along with the Mozilla Rapid Release strategy.

---

### Post by Sworddragon on 2012-09-28
> **vasa1 said:**
> It's *possible* that AdBlock Plus was available from repos but I very much doubt it ever was.

For example it is in Lucid: [http://packages.ubuntu.com/lucid/xul-ext-adblock-plus](http://packages.ubuntu.com/lucid/xul-ext-adblock-plus)


> **jbicha said:**
> Adblock plus is still available in [Debian]("http://packages.qa.debian.org/adblock-plus"), but like most Mozilla addons was removed from Ubuntu because they are too much of a burden to rebuild and update along with the Mozilla Rapid Release strategy.

In this case I have still to install it manually.

---

### Post by Elfy on 2012-09-28
> **Sworddragon said:**
> ...In this case I have still to install it manually.

Yes.

---

