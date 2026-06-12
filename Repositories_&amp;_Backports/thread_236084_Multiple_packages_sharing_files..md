---
title: "Multiple packages sharing files."
date: 2006-08-14
forum: Repositories &amp; Backports
---

### Post by OpsVentus on 2006-08-14
Hello all,

I've been looking around and do not know where else to put this question but here.

My problem as follows:
I have wrote a couple of programs which all use the same icon. I have put that icon in '/usr/share/windkracht8/icon.png'. Now I package those programs thus when I want to install the first one it puts the icon in the share dir. When I want to install the second program apt-get complains icon.png is allready there and cannot overwrite, it is used by the other package.
But the second time it doesn't have to overwrite it.

Is it possible for programs to share the same file? In a way that apt-get puts it there when installing the first program and when the last program is removed apt-get removes it?

Cheers,
Bart.

---

### Post by simonn on 2006-08-14
No. Different packages should not contain the same file.

Two choices:

1) Put it in its own package, e.g. opsventus-common-icons.deb, and make in required by any packages that need it.

or

2) Give each package it's own icon file with a different name.

Both have plus and minus points.

---

### Post by OpsVentus on 2006-08-15
Pitty, going for the second option I think, it's only 3 kb or such.

Thanks,
Bart.

---

