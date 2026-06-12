---
title: "CherryTree Upgrade Not Available?"
date: 2016-03-11
forum: Repositories &amp; Backports
---

### Post by KitchM on 2016-03-11
I am using Xubuntu 14.04 LTS and CherryTree 0.32.0.  Every time it is opened, a pop-up notes that there is an upgrade available to 0.36.6.  However, there is nothing in the Ubuntu Software Center.  (However, the picture there does show a version of 0.33.3.)

Does anyone know where the latest upgrade is located for installation?

Thanks.

---

### Post by gordintoronto on 2016-03-12
To install the latest version, you would need to go to the cherrytree web site. That will have negative results down the road, since you would never get automatic updates.

---

### Post by KitchM on 2016-04-03
Kinda defeats the whole point of auto updates from a central repo, doesn't it.

I guess the issue should have been implied; where is the ubuntu version update?????

---

### Post by howefield on 2016-04-04
> **KitchM said:**
> Kinda defeats the whole point of auto updates from a central repo, doesn't it.

I guess the issue should have been implied; where is the ubuntu version update?????

With each release of Ubuntu eg 14.04, the repositories are frozen, so most packages get security and bug updates but not version updates although I believe there are one or two exceptions to this rule. As long as you have 14.04 you will have that version of Cherrytree unless you go and find an updated version and manually install.

For info, the versions for the various Ubuntu releases are...

```
Source Package cherrytree

precise (editors): 0.23.1-1 [universe] 
Binary packages: cherrytree
trusty (editors): 0.32.0-1 [universe] 
Binary packages: cherrytree
vivid (editors): 0.35.7-1 [universe] 
Binary packages: cherrytree
wily (editors): 0.35.10-1 [universe] 
Binary packages: cherrytree
xenial (editors): 0.36.4-1 [universe] 
Binary packages: cherrytree
```

---

