---
title: "Virtualization to secure old java version"
date: 2013-06-01
forum: Virtualisation
---

### Post by bhunji on 2013-06-01
I'd like to use an unmaintained program [http://jequation.sourceforge.net/](http://jequation.sourceforge.net/)

It requires java 1.4 or 1.5, which is obviously a security risk. Would running it inside a virtualbox VM be secure? The VM wouldn't need network access.

---

### Post by 2F4U on 2013-06-01
Running these versions is only a security risk if the it is possible to exploit the risks. In order to exploit a security risk you would need to run malicious software or someone/something would need to be able to access the machine from outside. So, if you have the software inside a VM without network access, the only risk would be malicious software. But since you are in control what software is installed, it should be save.

---

