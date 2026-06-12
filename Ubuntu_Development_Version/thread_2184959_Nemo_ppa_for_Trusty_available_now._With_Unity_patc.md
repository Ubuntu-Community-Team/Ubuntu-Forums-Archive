---
title: "Nemo ppa for Trusty available now. With Unity patches and no cinnamon dependencies."
date: 2013-10-31
forum: Ubuntu Development Version
---

### Post by philinux on 2013-10-31
14.04 build just added yesterday.

[http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html](http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html)

I'll be off testing this later on my trusty box.

---

### Post by kansasnoob on 2013-10-31
That's awesome!

---

### Post by philinux on 2013-10-31
> **kansasnoob said:**
> That's awesome!

Indeed. Nautilus/files has lost its shine. Fantastic list of features.

---

### Post by tad1073 on 2013-10-31
That's what I get when I tried to install nemo.

```
The following packages have unmet dependencies:
 nemo : Depends: cinnamon-translations but it is not installable
E: Unable to correct problems, you have held broken packages.
```

---

### Post by philinux on 2013-10-31
The guy Andrew does say that is a dependency.  If you post a comment on the linked page he will reply.

---

### Post by tad1073 on 2013-10-31
> **philinux said:**
> The guy Andrew does say that is a dependency.  If you post a comment on the linked page he will reply.

Done.

---

### Post by QDR06VV9 on 2013-11-01
> **philinux said:**
> 14.04 build just added yesterday.

[http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html](http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html)

I'll be off testing this later on my trusty box.

Flat Love it running on Gnome-Shell.
Made Nemo Default.
I too feel nautilus has lost it's shine.

---

### Post by tad1073 on 2013-11-02
> **tad1073 said:**
> That's what I get when I tried to install nemo.

```
The following packages have unmet dependencies:
 nemo : Depends: cinnamon-translations but it is not installable
E: Unable to correct problems, you have held broken packages.
```

I just tried to install nemo again but I am getting the same error. ](*,)

---

### Post by mc4man on 2013-11-02
> **tad1073 said:**
> I just tried to install nemo again but I am getting the same error. ](*,)

In lieu of  trusty package then just download & manually install the  package of cinnamon-translations from the   saucy  build,  - 
[https://launchpad.net/~webupd8team/+archive/nemo/+build/5180887](https://launchpad.net/~webupd8team/+archive/nemo/+build/5180887)
Then install nemo

Note; the i386, (..all.deb) is also for amd64

---

### Post by QDR06VV9 on 2013-11-04
> **mc4man said:**
> In lieu of  trusty package then just download & manually install the  package of cinnamon-translations from the   saucy  build,  - 
[https://launchpad.net/~webupd8team/+archive/nemo/+build/5180887](https://launchpad.net/~webupd8team/+archive/nemo/+build/5180887)
Then install nemo

[COLOR=#ff0000]_Note; the i386, (..all.deb) is also for amd64_[/COLOR]

Sorry i should have posted earilier^^
Thanks mc4man!!
Installs perfectly on saucy from the link above, and with the all.deb for trusty..
Have to say I love the work flow now..
Regards

---

### Post by Yahoé on 2013-11-04
> **tad1073 said:**
> I just tried to install nemo again but I am getting the same error. ](*,)

Andrew from Webupd8 has fixed the issue. Yo can now install from his PPA without any dependency problem.

---

