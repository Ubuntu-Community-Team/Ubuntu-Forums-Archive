---
title: "Problems with Java3d-SDK"
date: 2005-12-06
forum: Repositories &amp; Backports
---

### Post by NLFSoftware on 2005-12-06
Hello all

I have try to intall java3d-SDK
but the synaptic crash when try to install it.

I have try to remove it whit the dpkg, the dselect and aptitude but always have an error and a recomendation to reinstall the package, but when I try to upgrade the synaptic crash again.

I think that the best option is to removeit manually but I dont now how to doit, so I asking for some help on this issue.

If there is any other way to resolve my problem please let me know.

I new on this things :) 

Thanks in advance.

---

### Post by noigeaR on 2005-12-09
I don't see Java3d-SDK in my repositories so I don't know how you actually tried to install this with synaptic, but if you downloaded a .deb package from the net  ,tried to install this and the install failed you can remove the package with ```
sudo apt-get remove java3d-sdk
``` (That's if the package name is java3d-sdk, change the command to the correct name otherwise)

---

