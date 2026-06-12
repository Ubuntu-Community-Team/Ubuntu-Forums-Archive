---
title: "Creating a registry key for Zattoo"
date: 2009-12-04
forum: Wine
---

### Post by Eterniam on 2009-12-04
Hey there,

I'm trying to install Zattoo by following the guide on this page:
[http://appdb.winehq.org/objectManage...sion&iId=17343]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=17343")

I've got to opening regedit, but I don't know what to do for this line:

4. create the key HKCU\AppEvents\Schemes\Apps\Explorer\Navigating\.current
If you could let me know how to do this, that would be great. I'm still new to Linux, so please assume that I know nothing when explaining :)

Cheers

---

### Post by davidmohammed on 2009-12-07
... drop to a terminal window and type regedit.  Navigate through the tree view and create the reg key.

As an aside - Zattoo is broken in karmic - wine release 1.33.  I would advise you to download and install the tech preview version from the zattoo website.

---

### Post by Eterniam on 2009-12-08
Ok, thanks David, will do.

---

### Post by RasterBurn on 2010-03-11
i know this topic is a bit old, and has probably been solved, but zattoo has an x86 release of their viewer.

---

