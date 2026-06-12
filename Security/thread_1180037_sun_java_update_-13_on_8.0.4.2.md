---
title: "sun java update -13 on 8.0.4.2"
date: 2009-06-06
forum: Security
---

### Post by Soul-Sing on 2009-06-06
Does anyone know why sun java isn't updated to update -13 on Hardy Heron?
This update is a major security update.
: [https://bugs.edge.launchpad.net/ubuntu/+source/sun-java6/+bug/360414](https://bugs.edge.launchpad.net/ubuntu/+source/sun-java6/+bug/360414)

---

### Post by Pjotr123 on 2009-06-06
Hardy Heron 8.04 is a current LTS version. Sun Java JRE should be kept safe in 8.04, even though it concerns a Multiverse package.

Sun has provided a security update long ago, but the updated version is only available for 9.04. That's not good.

---

### Post by Soul-Sing on 2009-06-06
> Sun has provided a security update long ago, but the updated version is only available for 9.04. That's not good.

Indeed, Opensuse is up to date.

---

### Post by Johan! on 2009-06-06
Related bugs:
[https://bugs.edge.launchpad.net/ubuntu/+source/sun-java6/+bug/360414](https://bugs.edge.launchpad.net/ubuntu/+source/sun-java6/+bug/360414)
[https://bugs.edge.launchpad.net/ubuntu/+source/sun-java6/+bug/288658](https://bugs.edge.launchpad.net/ubuntu/+source/sun-java6/+bug/288658)
[https://bugs.edge.launchpad.net/ubuntu/+source/sun-java6/+bug/187570](https://bugs.edge.launchpad.net/ubuntu/+source/sun-java6/+bug/187570)
[https://bugs.edge.launchpad.net/ubuntu/+source/sun-java6/+bug/330262](https://bugs.edge.launchpad.net/ubuntu/+source/sun-java6/+bug/330262)

I'd really like to know why Ubuntu isn't updating Java in current versions.
I'd also like to know why these bugs are not fixed. I don't even see any reaction from the Java maintainer.

---

### Post by cariboo on 2009-06-06
The developers normally don't read post here, you may be better off contacting the developer directly.

---

### Post by Soul-Sing on 2009-06-06
> **cariboo907 said:**
> The developers normally don't read post here, you may be better off contacting the developer directly.

They are contacted several weeks (month's?) ago.

---

### Post by Johan! on 2009-06-07
So there are no security updates for Java if you use an older, but still supported, Ubuntu version. When you ask a maintainer/dev about the situation, he does not reply.

This is not a good situation, in my opinion :-k

---

### Post by Pjotr123 on 2009-06-07
It's a serious matter. I am one of those who tried Launchpad and e-mailing the maintainer. In vain.

I really hope that this bit of extra public attention will help to wake the maintainer. Unfixed security is very bad for any Ubuntu version, but even more so for an LTS version.

---

### Post by testcees on 2009-06-21
Bump: Same for 8.04.3.

---

### Post by cariboo on 2009-06-21
The LTS version isn't updated to newer versions of the package, but there are security fixes. Have a look at this [list]("http://www.ubuntu.com/usn") of security fixes for 8.04.2

---

### Post by Soul-Sing on 2009-07-02
good news: [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/382918](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/382918)

sun java update-14 in hardy heron proposed...fix committed
although update-14 itself has no security issue's I assume that the update-13 security issue's are also solved now with this release/update.

---

