---
title: "Downgrading a package, older version in different repo"
date: 2007-04-19
forum: Repositories &amp; Backports
---

### Post by rshields on 2007-04-19
I'm running Feisty at the moment which has rdesktop 1.5.0 . It is segfaulting a lot. I want to downgrade to the previous version, 1.4.1, which is in the edgy and edgy backports repos:

[http://packages.ubuntu.com/edgy/x11/rdesktop](http://packages.ubuntu.com/edgy/x11/rdesktop)

How would I go about installing the older version? Do I need to temporarily add the edgy repo to my sources.list or is there some other way I can grab a .deb?

Thanks :)

---

### Post by rshields on 2007-04-19
I figured it out. I just added the edgy repos to my sources.list:

```

deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted

```

Did a:

```

sudo aptitude update

```

Then did a:

```

sudo aptitude remove rdesktop

```

The first solution was to remove ubuntu-desktop and another package that have rdesktop as dependencies. Errr, no thanks. So I said no to that and the second option was to downgrade to rdesktop 1.4.1, the version in the edgy repo.

Problem solved!

---

