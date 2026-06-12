---
title: "apt-transport-https: a bridge to nowhere?"
date: 2017-03-18
forum: Security
---

### Post by macho3 on 2017-03-18
I am glad to see that apt-transport-https is available in the standard repositories, but disappointed that the standard repositories don't seem to support it. Or at least s/http/https/ for sources.list didn't work on my system.

Where would be the best place to flag this as an issue for the maintainers? It would be nice if installation and upgrades weren't all vulnerable to MITM. Thanks!

---

### Post by macho3 on 2017-03-18
Same applies to apt-transport-tor, which Debian seems to support.

---

### Post by howefield on 2017-03-18
The mailing list ?

Maintainer: [Ubuntu Developers]("mailto:ubuntu-devel-discuss@lists.ubuntu.com") (Mail Archive)

---

### Post by deadflowr on 2017-03-18
> Where would be the best place to flag this as an issue for the maintainers? 
The issues been flagged, once or twice before:
[https://bugs.launchpad.net/ubuntu/+bug/1464064]("https://bugs.launchpad.net/ubuntu/+bug/1464064")

https mirrors exist.
They are few and far between, but they exist.
Here's sample list: [https://www.reddit.com/r/Ubuntu/comments/3q53kc/list_of_ubuntu_repository_mirrors_available_over/]("https://www.reddit.com/r/Ubuntu/comments/3q53kc/list_of_ubuntu_repository_mirrors_available_over/")

---

