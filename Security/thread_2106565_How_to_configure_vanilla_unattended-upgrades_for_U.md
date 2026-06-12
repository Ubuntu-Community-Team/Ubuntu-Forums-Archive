---
title: "How to configure vanilla unattended-upgrades for Ubuntu? &quot;hard question&quot;"
date: 2013-01-19
forum: Security
---

### Post by User9999 on 2013-01-19
Hi!

I need to use the vanilla debian flavor unattended-upgrades package on an ubuntu-server.
Would the snippet (/etc/apt/apt.conf.d/50unattended-upgrades) below work properly?

```
// Automatically upgrade packages from these origin patterns
Unattended-Upgrade::Origins-Pattern {
        "origin=Ubuntu,archive=stable,label=Ubuntu-Security";
};
```

Thank you!

---

### Post by Ms. Daisy on 2013-01-21
Did you look at this?

[https://help.ubuntu.com/community/AutomaticSecurityUpdates#Using_the_.22unattended-upgrades.22_package](https://help.ubuntu.com/community/AutomaticSecurityUpdates#Using_the_.22unattended-upgrades.22_package)

---

### Post by User9999 on 2013-01-26
> **Ms. Daisy said:**
> Did you look at this?

[https://help.ubuntu.com/community/AutomaticSecurityUpdates#Using_the_.22unattended-upgrades.22_package](https://help.ubuntu.com/community/AutomaticSecurityUpdates#Using_the_.22unattended-upgrades.22_package)

Thanks for the answer! However I need to configure the Debian version of the unattended-upgrades package, which appears to be using a different configuration style than the Ubuntu's unattended-upgrades.

In order to properly configure Debian's unattended-upgrades for Ubuntu, I need to know some *repository parameters* for quantal, like:
```

origin=Ubuntu         # seems ok
archive=stable        # or should I use "quantal" instead?
label=Ubuntu-Security # unsure about this

```

Thank you!

---

