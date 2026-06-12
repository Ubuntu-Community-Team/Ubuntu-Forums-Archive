---
title: "configuring output of apt-cache packages"
date: 2006-09-06
forum: Repositories &amp; Backports
---

### Post by plexie on 2006-09-06
I somehow need to strip the version number from packages.
these packages are generated from the apt-cache depends command

it can't be done by regular expressions, because numbers can also occur in the basename of the package, and characters can occur as minor version numbers..

Is there a way (like RPM's --queryformat) to configure the output of those packages?

I know aptitude solves this issue, but it's a restricted system and we are trying to limit the amount of installed packages.

thanks!

---

### Post by danderson3 on 2006-09-06
I can't help right now, but would like to keep
updated on your progress with this... pls keep me
posted - thx! David

---

