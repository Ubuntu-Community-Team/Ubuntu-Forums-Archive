---
title: "How to have a bunch of recommended packages?"
date: 2012-08-12
forum: Ubuntu Application Development
---

### Post by hakermania on 2012-08-12
Can I have a set of recommended packages in my package?

Let's say I am building package1. This recommends package2, package3 and package4, but all of them need to be installed in order to provide a specific functionality!

For example, it would be no use for the user to install only the recommended packages package2 and package3 without the package4.

How can I tell it at debian/control that these recommended packages have immediate relation between them and cannot be installed separately?:confused:

---

### Post by Cheesehead on 2012-08-12
See [http://www.debian.org/doc/debian-policy/ch-relationships.html#s-binarydeps](http://www.debian.org/doc/debian-policy/ch-relationships.html#s-binarydeps) for how to do it.

---

### Post by hakermania on 2012-08-12
Thanks, I will have a look t&#822;o&#822;m&#822;o&#822;r&#822;r&#822;o&#822;w&#822; later today (it is 2:17 here :P)

---

