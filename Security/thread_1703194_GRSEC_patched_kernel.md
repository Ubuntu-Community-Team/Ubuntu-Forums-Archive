---
title: "GRSEC patched kernel"
date: 2011-03-09
forum: Security
---

### Post by skraps on 2011-03-09
Has anyone implemented this type of kernel with ubuntu? [http://grsecurity.net](http://grsecurity.net)

---

### Post by wacky_sung on 2011-03-09
It is kinda troublesome in which you may have to remove apparmor.

Look at the guide [here]("http://grsecurity.net/quickstart.pdf").

---

### Post by skraps on 2011-03-09
Iv went thru the grsec guide. But dont quite have a good understanding of kernel security. Does the benifits of AppArmor outweigh grsecs advantages?

---

### Post by bodhi.zazen on 2011-03-09
> **skraps said:**
> Has anyone implemented this type of kernel with ubuntu? [http://grsecurity.net](http://grsecurity.net)

Yes I have with "gentoo-hardened".

In general it seems to work well.

To be honest, if you are using Ubuntu I would go with Apparmor, if you want selinux, go with Fedora.

With that in mind, pax and grsecurity will take some tweaking / monitoring if you want to use graphical applications.

---

### Post by bodhi.zazen on 2011-03-09
> **skraps said:**
> Iv went thru the grsec guide. But dont quite have a good understanding of kernel security. Does the benifits of AppArmor outweigh grsecs advantages?

Only in that apparmor is included by default in Ubuntu and you will have to remove it to install grsecurity.

grsecuity will also entail building a custom kernel (you will have to apply the patch to a vanilla kernel).

---

### Post by skraps on 2011-03-09
So grsec is more of a security patch to leave to high end server applications. Not desktops. Is from what Im gathering.

---

### Post by bodhi.zazen on 2011-03-09
> **skraps said:**
> So grsec is more of a security patch to leave to high end server applications. Not desktops. Is from what Im gathering.

Depends on how much you want to tweak security. There is no reason you can not use it on a desktop.

You should start by reading the gentoo documentation (it is not really all that gentoo specific) and the grsecurity wiki.

[http://www.gentoo.org/proj/en/hardened/pax-quickstart.xml](http://www.gentoo.org/proj/en/hardened/pax-quickstart.xml)

[http://www.gentoo.org/proj/en/hardened/grsecurity.xml](http://www.gentoo.org/proj/en/hardened/grsecurity.xml)

[http://en.wikibooks.org/wiki/Grsecurity](http://en.wikibooks.org/wiki/Grsecurity)

After reading those 3 pages, in their entirety, you can decide if you want to build a kernel.

I assume you know how to apply the grsecuity patch and compile a kernel ...

---

### Post by skraps on 2011-03-09
Iv built one kernel, never without the original config so I dont mis any required modules.

---

