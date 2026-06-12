---
title: "linux-image-extra-$(uname -r) in azure"
date: 2018-06-18
forum: Ubuntu Cloud and Juju
---

### Post by bryan43 on 2018-06-18
On 16.04, I think there is a missing package that needs to be added. This isn't a request for a new package, but a bug, as I think it's necessary and required.

The linux-image-extra-$(uname -r) contains modules I need on the server; however, there doesn't exist any package for "linux-image-extra-4.15.0-1013-azure". "linux-image-azure" depends on linux-image-4.15.0-1013-azure, which updated the other day, so now I have issues.

I think the "linux-image-extra-4.15.0-1013-azure" package needs to be added and some meta package needs to be modified/added that depends on that package.

---

### Post by jeremy31 on 2018-06-18
Is there any result for ```
apt rdepends linux-image-extra-4.15.0-1013-azure
```

---

### Post by bryan43 on 2018-06-18
No, it says "No packages found".  Also, "apt-cache show linux-image-extra-4.15.0-1013-azure" says the package doesn't exist.

---

### Post by mc4man on 2018-06-18
all built from that source is shown here (I think
[https://packages.ubuntu.com/source/xenial-updates/linux-azure](https://packages.ubuntu.com/source/xenial-updates/linux-azure)
Is it possible what you need is in linux-modules-extra-4.15.0-1013-azure?

---

### Post by bryan43 on 2018-06-19
It does look like the "[COLOR=#000000]linux-modules-extra-4.15.0-1013-azure" package contains the files I need.  My next question/issue is that "apt-cache rdepends [/COLOR][COLOR=#000000]linux-modules-extra-4.15.0-1013-azure" shows that nothing depends on it, so I have no way of keeping that package up-to-date.  Can anyone help with that issue?[/COLOR]

---

### Post by jeremy31 on 2018-06-19
You could file a bug report at bugs.launchpad.net/ubuntu

---

### Post by bryan43 on 2018-06-19
Report filed, [https://bugs.launchpad.net/ubuntu/+source/linux-azure/+bug/1777676](https://bugs.launchpad.net/ubuntu/+source/linux-azure/+bug/1777676)

---

### Post by mc4man on 2018-06-19
Hopefully your report provides some answers..
What does come to mind is that if the azure modules package for 4.15 gets an update you'd probably receive it. 
As far as 16.04 there may not be any further kernel upgrades past 4.15 so the lack of a modules dep in a meta package could be more of a possible issue in 18.04 than 16.04

---

