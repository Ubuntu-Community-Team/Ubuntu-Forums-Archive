---
title: "Backports and security updates"
date: 2005-10-18
forum: Ubuntu Backports
---

### Post by WW on 2005-10-18
How are security updates integrated with backports?

(Sorry if this is in a FAQ somewhere. I didn't find anything in my forum search.)

---

### Post by geearf on 2005-10-18
I guess by the version tag first you''ll get one, and if the version of the other is greater, then you'l get it and so on ..

A security patch to a specific ubuntu program should not work well if you have a backport version, but usually you will get the file rather than the diff I think.

---

### Post by WW on 2005-10-18
I guess a more specific question is this:  Are the people who are maintaining the backports also updating the backports when security vulnerabilities are discovered?

---

### Post by Seth on 2005-10-18
Methinks not.

---

### Post by duffman25 on 2005-10-19
[QUOTE=Seth]Methinks not.[/QUOTE]
I think "sometimes". If a backport package has a vulnerability discovered, then a new upstream fix will enter the current development branch. This new package will likely be backported again, so there you have the new version of the package with the security fix + some updates. I'm correct? This is only true if the backport team backport every new version of the already backported packages.

---

### Post by duffman25 on 2005-10-19
[QUOTE=duffman25]I think "sometimes". If a backport package has a vulnerability discovered, then a new upstream fix will enter the current development branch. This new package will likely be backported again, so there you have the new version of the package with the security fix + some updates. I'm correct? This is only true if the backport team backport every new version of the already backported packages.[/QUOTE]

That last line sound like a tongue-twister. ;)

---

