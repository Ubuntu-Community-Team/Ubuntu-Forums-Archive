---
title: "Slackware: How does one manage the packages?"
date: 2008-02-21
forum: Slackware and derivatives
---

### Post by newnet on 2008-02-21
I installed the base system.  So now I should be installing xorg.  The problem: No package manager.  How does the common Slackware user manage to install something with a lot of dependencies without a package manager?  Apt was not even included as a choice when selecting the packages during installation.

---

### Post by Existentialist on 2008-02-21
Slackware uses the basic TGZ to install packages.  When I first started using slackware I found this article about package management in slackware.  Maybe it will be of some help to you (it's a pdf):

[http://www.linuxpackages.net/gen_pdf.php?file=pkgtools.html](http://www.linuxpackages.net/gen_pdf.php?file=pkgtools.html)

Here is another good article about installing packages:

[http://www.slackbook.org/html/package-management.html](http://www.slackbook.org/html/package-management.html)

For the most part, you are going to have to read the readme files that come with the packages.  Slackware is a great distro to learn the finer points of managing a linux system, it just has a much steeper learning curve.  Try searching Google for any questions, as there is a lot of information out there for it.

---

### Post by Bachstelze on 2008-02-22
> **newnet said:**
> I installed the base system.  So now I should be installing xorg.

That's very easy :

```
mkdir ~/xorgpackages
cd ~/xorgpackages
wget ftp://ftp.lip6.fr/pub/linux/distributions/slackware/slackware-12.0/slackware/x/*.tgz
installpkg *.tgz
```

Wait a few minutes, you're done.

---

