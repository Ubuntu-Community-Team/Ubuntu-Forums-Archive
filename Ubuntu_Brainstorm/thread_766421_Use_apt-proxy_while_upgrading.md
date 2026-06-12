---
title: "Use apt-proxy while upgrading"
date: 2008-04-25
forum: Ubuntu Brainstorm
---

### Post by Archmage on 2008-04-25
There is nothing wrong if you change the source.list to an actually working one when upgrading, but **PLEASE** give the users that use apt-proxy in the source.list to use there working apt-proxy serve to upgrade.

E.g.

The following source.list:

```

deb http://APTPROXY:9999/ubuntu hardy main restricted universe multiverse
deb http://APTPROXY:9999/ubuntu-security hardy-security main restricted universe multiverse

```

Don't do this, when someone use the Update Manager or the "sudo do-release-upgrade" and there is a working apt-proxy-server:

```

deb http://archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse

```

Instead do this:

```

deb http://APTPROXY:9999/ubuntu intrepid main restricted universe multiverse
deb http://APTPROXY:9999/ubuntu-security intrepid-security main restricted universe multiverse

```

---

