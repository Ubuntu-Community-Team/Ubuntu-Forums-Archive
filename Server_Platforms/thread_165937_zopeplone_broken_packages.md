---
title: "zope/plone broken packages"
date: 2006-04-25
forum: Server Platforms
---

### Post by phitoo on 2006-04-25
Zope 2.7/2.8 and Plone in dapper will not install because of dependencies on python 2.3 and it seems that support for python 2.3 is being or has been dropped. There is at least one bug filed for this issue. 

Is anyone aware of any discussion around this topic? I'm kind of anxious about it.

Thanks
Philippe

---

### Post by iball on 2006-04-26
I don't know about support of Zope and Plone in Dapper, however it should be possible to install from source.  Download Zope 2.8 and install it (there are instructions on the zope website).  Then install Plone, which is basically just a Zope "product" and so untar-ing it to the zope products directory will   install Plone.  See [http://docs.neuroinf.de/PloneBook/ch2.rst]("http://docs.neuroinf.de/PloneBook/ch2.rst") for details on installing Plone manually.

If you need Zope / Plone and support is not in Dapper at the moment, it may be there in the final release, or perhaps you should use straight Debian.  I have Zope 2.8 and Plone 2.1 running on my Debian server, and I installed it as above.  Debian Sarge comes with Zope 2.8, and Plone 2.

I hope this helps
--Ian

---

### Post by phitoo on 2006-04-26
I was hoping to standardize our servers on dapper as soon as it goes stable. But we have an intranet running on plone (on gentoo). I'm looking at using breezy and delay the move to dapper.

Thanks
Philippe

---

### Post by retype on 2006-04-28
plone 2.1.2 and zope 2.8 packages are broken on Dapper drake, I hope they are going to fix it.

---

### Post by miahfost on 2006-05-03
I have not seen anything in the Launchpad bug tracker so I doubt it is on Ubuntu's radar. When I go to the Launchpad to track Zope bugs all I see is Zope 3.0 or higher which is not what we need to use, since Zope 3.0 is a completely different product.

[https://launchpad.net/products/zope](https://launchpad.net/products/zope)

Is there bug tracking for Zope 2.8 somewhere?

---

### Post by phitoo on 2006-05-05
Bugs 34973 and 35998 are relevant. There are a few others.

There are people tracking the issue but I think it may not be a simple issue.

---

